# base22
import requests

API_KEY = "YOUR_API_KEY"
ADDRESS = "0xYourWalletAddress"

url = (
    f"https://api.basescan.org/api"
    f"?module=account"
    f"&action=txlist"
    f"&address={ADDRESS}"
    f"&startblock=0"
    f"&endblock=99999999"
    f"&sort=asc"
    f"&apikey={API_KEY}"
)

response = requests.get(url)
data = response.json()

if data["status"] == "1":
    print("Total transactions:", len(data["result"]))
else:
    print(data["message"])
