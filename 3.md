Now we have to install the library of GithubApy

    $ pip install PyGithub

In your code, write the access_token and call the library

    from github import Github 
    ACCESS_TOKEN = XXXX 
    client = Github(ACCESS_TOKEN, per_page=100)

Now you can get from this client the userName and the repoName

    user = client.get_user(<<USERNAME>>)
    repo = user.get_repo(<<REPONAME>>)

From this repo can have the stars, list of open issues, topics etc

    stars = [ s for s in repo.get_stargazers() ]
    print("Number of stargazers", len(stargazers))
    topics = repo.get_topics()
    print("Topics",topics)
    open_issues = repo.get_issues(state='open')
    for issue in open_issues:
        print(issue)
In case we dont have the name of the user and the repo, we can look for repositories depending on the language preferences 

    repositories = client.search_repositories(query='language:python')
    for repo in repositories:
        print(repo)