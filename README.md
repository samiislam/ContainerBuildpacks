# Container Buildpacks

## Folder structure:
----

| Name                            | Content                                                   |
| :------------------------------ | :-------------------------------------------------------  |
| Folder: <a name="dotnet">dotnet</a> | The .Net Core Console Project |
| Folder: <a name="node">node</a> | The Node.js Project |
| Folder: <a name="python">python</a> | The Python Project |
| README.md | This file |

----

<br />
<br />


## Steps:
----
| Step                            | Command                                                   |
| :------------------------------ | :-------------------------------------------------------  |
| 1. Build myconsole | In folder [dotnet](#dotnet) : dotnet build myconsole/myconsole.csproj -c release |
| 2. Publish myconsole | In folder [dotnet](#dotnet) : dotnet publish myconsole/myconsole.csproj -c release -o console --no-restore |
| 3. Build docker image for console using Dockerfile | In folder [dotnet](#dotnet) : docker image build -f Dockerfile.dotnet --no-cache -t s/console:1.0 . |
| 4. Build docker image for node using Dockerfile | In folder [node](#node) : docker image build -f Dockerfile.node --no-cache -t s/node:1.0 . |
| 5. Build docker image for python using Dockerfile | In folder [python](#python) : docker image build -f Dockerfile.python --no-cache -t s/python:1.0 |
| 6. Build a docker image for console using pack build | In folder [dotnet](#dotnet) : pack build s/console:2.0 --builder gcr.io/buildpacks/builder:v1 |
| 7. Build a docker image for node using pack build | In folder [node](#node) : pack build s/node:2.0 --builder gcr.io/buildpacks/builder:v1 |
| 8. Build a docker image for python using pack build | In folder [python](#python) : pack build s/python:2.0 --builder gcr.io/buildpacks/builder:v1 --env GOOGLE_ENTRYPOINT="python main.py" |
----
