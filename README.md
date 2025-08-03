# ai-assistant

nvidia driver 535 
ubuntu 22

install cuda after installing 
https://developer.nvidia.com/cuda-12-2-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=22.04&target_type=deb_local


kilo code -> can be used to run the local project

https://kilocode.ai/docs/providers/ollama 
OLLAMA_CONTEXT_LENGTH=131072 ollama serve

This model works quite well with summarizing the model. This is a local model.
hhao/qwen2.5-coder-tools:14b

well gemini works but it has limitation.

have set up the ml server 

Ref:
https://kilocode.ai/docs/advanced-usage/local-models

open
https://github.com/open-webui/open-webui

after checking the github project of ollama
it is found that i have to use v1

https://github.com/ollama/ollama/blob/main/server/routes.go#L1215 


```
sudo vim /etc/systemd/system/ollama.service
```

```
[Unit]
Description=Ollama Service
After=network-online.target

[Service]
ExecStart=/usr/local/bin/ollama serve
User=ollama
Group=ollama
Restart=always
RestartSec=3
Environment=OLLAMA_CONTEXT_LENGTH=131072 # <--- add this
Environment="PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"

[Install]
WantedBy=default.target

```