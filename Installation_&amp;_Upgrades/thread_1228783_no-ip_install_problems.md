---
title: "no-ip install problems"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by milocario on 2009-08-01
I have problems installing no-ip in my ubuntu server. When I use “sudo atp-get install no-ip” I get the following: 

> arturo@servidor:~$ sudo apt-get install no-ip
[sudo] password for arturo:
Leyendo lista de paquetes... Hecho
Creando Ã¡rbol de dependencias
Leyendo la informaciÃ³n de estado... Hecho
Se instalarÃ¡n los siguientes paquetes NUEVOS:
  no-ip
0 actualizados, 1 se instalarÃ¡n, 0 para eliminar y 132 no actualizados.
Necesito descargar 21.4kB de archivos.
Se utilizarÃ¡n 135kB de espacio de disco adicional despuÃ©s de desempaquetar.
AVISO: Â¡No se han podido autenticar los siguientes paquetes!
  no-ip
Â¿Instalar estos paquetes sin verificaciÃ³n [s/N]? s
Err [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) gutsy/universe no-ip 2.1.3-3build1
  404 Not Found [IP: 91.189.88.45 80]
Imposible obtener [http://mx.archive.ubuntu.com/ubuntu/pool/universe/n/no-ip/no-ip_2.1.3-3build1_i386.deb](http://mx.archive.ubuntu.com/ubuntu/pool/universe/n/no-ip/no-ip_2.1.3-3build1_i386.deb)  404 Not Found [IP: 91.189.88.45 80]
E: No se pudieron obtener algunos archivos, Â¿quizÃ¡s deba ejecutar
apt-get update o deba intentarlo de nuevo con --fix-missing?
arturo@servidor:~$apt-get update and apt-get install --fix-missin don't work either. 

What should I do?

---

### Post by dandnsmith on 2009-08-01
That archive has nothing between release 2.1.1 and 2.1.7 for no-ip.
Something in your archive lists doesn't tie up - I'd be expecting it to go for the latest build, or latest compatible with your OS release.
Perhaps you could say which release you have installed, and someone more informed than I can point you to the resolution path to follow.

Lo siento ...

---

### Post by milocario on 2009-08-01
I have Ubuntu 7.10 gutsy
About linux the command uname -a says:
> Linux servidor 2.6.22-14-server #1 SMP Sun Oct 14 23:34:23 GMT 2007 i686 GNU/Linux

---

