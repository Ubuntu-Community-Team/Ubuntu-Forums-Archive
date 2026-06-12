---
title: "No funciona escaner HP en mi LAN"
date: 2020-04-08
forum: Hardware
---

### Post by Daniel TL on 2020-04-08
Buenas tardes.

En mi LAN hogareña tengo 2 PCs conectadas (además de otros dispositivos varios). Ambas tienen Ubuntu 18.04 y en una de ellas tengo conectada por USB una Impresora Multifunción HP. Es una DeskJet F4280 y funciona bien, tanto la impresora como el escáner, en la PC local. Pero quiero compartir el escáner en la red doméstica, y no lo logro... 


He seguido todos los pasos que se indican en la documentación oficial: 

[https://help.ubuntu.com/community/SaneDaemonTutorial]("https://help.ubuntu.com/community/SaneDaemonTutorial") 

Pero el escáner no funciona desde la PC cliente. 


El servidor entiendo que está bien configurado, ya que desde la PC cliente puedo "ver" el puerto abierto en el servidor: 

```
$ nmap 192.168.x.yyy Starting Nmap 7.60 ( https://nmap.org ) at 2020-04-08 13:57 -03 Nmap scan report for 192.168.x.yyy 
Host is up (0.035s latency). Not shown: 997 closed ports
 PORT STATE SERVICE
111/tcp open rpcbind 
631/tcp open ipp 
6566/tcp open sane-port 

Nmap done: 1 IP address (1 host up) scanned in 2.47 seconds
``` 

Cuando inicio xsane desde la PC cliente me aparece un cartel indicando que no encuentra dispositivos... 

Si inicio xsane indicando la IP del servidor me aparece un cartel de "Operación no soportada"... 

```
$ xsane hpaio:net:192.168.x.yyy
``` 

Desde la PC cliente tampoco encuentro el escáner con el comando "scanimage":

 ```
$ scanimage -L
No scanners were identified. If you were expecting something different, check that the scanner is plugged in, turned on and detected by the sane-find-scanner tool (if appropriate). Please read the documentation which came with this software (README, FAQ, manpages).
``` 


¿Dónde puede estar el problema? ¿Qué puedo hacer para lograr que funcione el escáner en mi red? 

Les pido alguna sugerencia, alguna idea que me permita resolver este problema. 

Muchas gracias!!

---

