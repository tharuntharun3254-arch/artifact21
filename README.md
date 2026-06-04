import requests

username = input("Enter GitHub username: ")

url = f"https://api.github.com/users/{username}/repos"
response = requests.get(url)

if response.status_code == 200:
    repos = response.json()
    print(f"\nRepositories of {username}:\n")

    for repo in repos:
        print(f"Name: {repo['name']}")
        print(f"URL : {repo['html_url']}")
        print("-" * 40)
else:
    print("User not found or API error.")
