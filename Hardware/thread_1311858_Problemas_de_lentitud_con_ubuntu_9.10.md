---
title: "Problemas de lentitud con ubuntu 9.10"
date: 2009-11-02
forum: Hardware
---

### Post by loloman on 2009-11-02
Instale karmic desde 0 pero de momentos todo anda terriblemente lento y otras no tanto pero lento, teclado, mouse y mas todo lo referente al video y musica, en un principio pense que eran los drives de Nvidea y instale la vercion 190.42 estable pero nada cambio y manejarlo se hace insoportable, alguna idea de lo que pasa ?

Mi hardware es:
Amd athlon 64 3500+, MB msi k8t neo2, 1.5GB, video 6600gt 512

este es el sof agregado,

repositorios Medibuntu,
  
ubuntu-restricted-extras 
vlc
smplayer
w32codecs
wine
compizconfig-settings-manager
gparted
fusion-icon 
sysinfo 
ntfs-3g
java

poder escribir esto me llevo 10 minutos

---

### Post by Applelnx on 2009-11-03
Hola, el problema lo tuviste siempre, desde que instalaste ubuntu al principio? Por lo poco que se me suena que es el compiz

---

### Post by loloman on 2009-11-03
Nunca ha pasado en las anteriores versiones, el compiz no es ya lo he probado no hace ninguna diferencia, se nota mas cuando reprodusco un video o sonido donde se relantiza toda la pc y no hay caso hasta reiniciarla, crei que eran los codecs pero en una instalacion limpia sin nada y sin los drivers de Nvidea sigue con el mismo problema, hay momento que funciona todo bien pero despues cae, no logro encontrar la causa tambien lo noto cuando instalo una aplicacion con apt o synatic y con firefox se muere, tambien pense que mi disco de instalacion pudiera estar corrupto pero he bajado la iso 3 veces y grabe 6 cd, pero nada 

he vuelto al 9.04 y ningun problema, cosa extraña pero seguire buscando a ver si alguien tiene el mismo problema

---

### Post by alfplayer on 2009-11-04
Preguntas que pueden ayudar a resolver el problema: Funciona todo bien con el live cd? Hay algún proceso que esté usando demasiado el CPU (se puede ver con el monitor de sistema)? Un problema más serio sería una falla en los drivers de la controladora de discos.

---

### Post by loloman on 2009-11-09
Con el Live-cd funciona sin problemas, el problema comienza después de instalar los drivers de Nvidea, desactivo el compiz pero el problema persiste, el consumo de memoria no pasa de los 200mb (1.5G)y en el momento que se pone todo leennnttooo, no hay ningún proceso que consuman mucha cpu en el monitor de sistema parece todo normal ????

esto es frustran te ...

---

