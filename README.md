# vlmcsd est un remplacement du serveur KMS de Microsoft.

> Il contient vlmcs, un client de test KMS, principalement à des fins de débogage, qui peut également "charger" un serveur KMS authentique conçu pour fonctionner sur un appareil toujours allumé ou souvent allumé, par exemple un routeur, une boîte NAS, ...destiné à aider les personnes ayant perdu l'activation de leurs licences légalement acquises, par exemple en raison d'un changement de matériel (carte mère, CPU, ...)

> vlmcsd n'est pas un outil d'activation ou de crack en un clic destiné à activer des copies illégales de logiciels (Windows, Office, Project, Visio)

## Info / À propos de ce docker
Docker basé sur le système d'exploitation Alpine avec vlmcsd compilé à partir de la "source" (Wind4 GitHub)

## Utilisation du serveur :
> $ docker run -d -p 1688:1688 --restart=always --name vlmcsd mikolatero/vlmcsd

## Pour voir les journaux docker :
Maintenant (grâce à embii74) le processus vlmcsd envoie les journaux à docker.
> $ docker logs vlmcsd (remplacez 'vlmcsd' par le nom du docker)

## Client
### Windows
>slmgr.vbs -upk  
>slmgr.vbs -ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX  
>slmgr.vbs -skms DOCKER_IP:PORT  
>slmgr.vbs -ato  
>slmgr.vbs -dlv  

### Office x86
>cd \Program Files (x86)\Microsoft Office\Office16  
>cscript ospp.vbs /sethst:DOCKER_IP  
>cscript ospp.vbs /setprt:PORT  
>cscript ospp.vbs /inpkey:xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
>cscript ospp.vbs /act  
>cscript ospp.vbs /dstatusall  

### Office x86_64
>cd \Program Files\Microsoft Office\Office16  
>cscript ospp.vbs /sethst:DOCKER_IP  
>cscript ospp.vbs /setprt:PORT  
>cscript ospp.vbs /inpkey:xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
>cscript ospp.vbs /act  
>cscript ospp.vbs /dstatusall  

## Sources
> https://forums.mydigitallife.info/threads/50234-Emulated-KMS-Servers-on-non-Windows-platforms  
https://github.com/Wind4/vlmcsd

## Clés GVLK
> Windows: https://docs.microsoft.com/en-us/windows-server/get-started/kmsclientkeys  
> Office 2013: https://technet.microsoft.com/en-us/library/dn385360.aspx  
> Office 2016 & 2019 & 2021: https://technet.microsoft.com/en-us/library/dn385360(v=office.16).aspx

## Lien Docker
> https://hub.docker.com/r/mikolatero/vlmcsd/
