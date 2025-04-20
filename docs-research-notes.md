---
title: Research Notes
topicType: note
tags: notes research explore
---

## Overview

Want to understand the capabilities of the demo and how it could utilize it for a potential POC / Demo.  

__Requirements__
1. You need a Google GEMINI Key -- https://aistudio.google.com/apikey they show up in your google cloud console as Generative AI Keys
2. You need `uv` a python package manager tooling configured 


### Demo

1. FrontEnd UI

First run the UI Application / Server by navigating to the folder and running the `uv run` command or reference directly

```shell

cd demo/ui

# If running first time you need `uv` installed so you can run package install
uv sync

uv run main.py
```

This will get you the local UI running on port `1200` [http://0.0.0.0:12000/](http://0.0.0.0:12000/)


2. Run Sample Agents

The goal is to be able to subscribe agents into this panel [http://0.0.0.0:12000/agents](http://0.0.0.0:12000/agents)

Sample agents are found [here](https://github.com/searchpartyhq/A2A/tree/main/samples/python) -- `samples/python` there is a `readme` with instructions about each sample agent.  Each with their own instructions on how to run, but most are just a `uv sync; uv run .`

__IMPORTANT:__ Once you had the agent running locally, example `localhost:10000` that is what you use in the UI to link, it doesn't want `http://` or `https://` protocols.


### Research

1. Learning that `uv run .` bootstraps the `__main__.py` which is how the __Agents__ samples work.  Just helpful to know this detail about `uv run` packaging and understanding this is on purpose as it helps the python interpreter use _relative_ imports `from .lib import utils`.  Also it means the folder of code is ready to be deployed/run as a package as `__main__.py` is used by the python-tooling eco-system.

2. Breaking down the Agent Samples

- __Currency Converter__ Built with LangGraph (python), can easily be triggered with `What is exchange rate between USD and GBP?` 
- __Reimbursement Form__ Built with GoogleADK (python), tried trigger with `I want an expense reimbursement form` and the Agent broke and caught the UI in a request-loop that requires the server/crash-stop.
- 