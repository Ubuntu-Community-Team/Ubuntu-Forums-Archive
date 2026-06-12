---
title: "Dell Studio 1555... Problemas"
date: 2009-06-20
forum: Instalación y Actualización
---

### Post by Pabloo0o0 on 2009-06-20
Holas, hace poco me llego mi laptop nuevo :D!
c2duo 2.0, 4gb ram y una ati de 256mb


Todo bien y hoy instale el ubuntu, como ya tengo ubuntu en mi desktop, queria tener lo mismo..

pero no me reconocio el wifi, ni el audio...
alguna sugerencia??

ahora estoy bajando la iso de dell de ubuntu.

---

### Post by Carlos C on 2009-06-20
Faltan algunos datos básicos, como tu versión de Ubuntu y la salida del comando:
```
lspci
```
Saludos.

---

### Post by mario2130 on 2009-06-20
> **Pabloo0o0 said:**
> Holas, hace poco me llego mi laptop nuevo :D!
c2duo 2.0, 4gb ram y una ati de 256mb


Todo bien y hoy instale el ubuntu, como ya tengo ubuntu en mi desktop, queria tener lo mismo..

pero no me reconocio el wifi, ni el audio...
alguna sugerencia??

ahora estoy bajando la iso de dell de ubuntu.

mira como dice Carlos C, tines que ver que realmente tienes que buscar, por ej. pones el comando 

lshw

este te mostrara todo lo de tu laptops, tonces en mi caso el audio se ve así
[html]
*-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller*********************
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

[/html]
y wifi asi
[html]
-network
                description: Wireless interface
                product: BCM4311 802.11b/g WLAN*************************
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:1d:60:b3:af:61
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10
[/html]
ya sabiendo en eso, que esta marcado con ***, sabes que tienes que buscar en san google. saludos

---

### Post by Pabloo0o0 on 2009-06-20
ahh gracias, voy  a buscar...

ahora estoy probando el ISO, de dell ubuntu, y me esta reconociendo todo, pero es una version  i686 :shock:  y no se q diferencia tiene con las de x64 ... pero lo malo q no reconoce los 4g ram.

---

### Post by moreback on 2009-06-20
Prueba con una versión de 64 bits entonces.

Lo del sonido puede ser que están los controles al mínimo.

---

### Post by Pabloo0o0 on 2009-06-20
volvi xD

Instale el ISO de DELL Ubuntu, me reconocio el wifi y el bluetooth..

resolvi el problema del audio con la ayuda de este post

[http://ubuntuforums.org/showthread.php?p=7490889#post7490889](http://ubuntuforums.org/showthread.php?p=7490889#post7490889)

ahora estoy viendo como me puede detectar los 4gb, ahora solo detecta 2.9

---

### Post by CdK1 on 2009-06-21
LO del WIFI está bastante claro... 
BCM4311

Instala el driver del BCM y listo, sobre al audio;

Corre alsaconf y prueba, debería servirte...

---

### Post by CdK1 on 2009-06-21
No estoy muy seguro, pero para los 4GB de RAM necesitas recompilar el kern, pero NO estoy seguro, y a esta menos...

---

### Post by Pabloo0o0 on 2009-06-21
> **CdK1 said:**
> No estoy muy seguro, pero para los 4GB de RAM necesitas recompilar el kern, pero NO estoy seguro, y a esta menos...

la primera solucion q encontre en internet fue instalar el kernel de server:o


```
sudo apt-get install linux-server linux-headers-server
```

y hasta ahora todo bien.. seguire buscando y probando otras soluciones :P

---

### Post by mario2130 on 2009-06-21
mm a mi tampoco me reconoce los 4G pero me pesca 3.6G mm pense que era un problema de ubuntu pero no habia indagado me sumare a tu campaña de averiguar que onda, haber si podemos llegar a algo concreto
saludos

---

### Post by Pabloo0o0 on 2009-06-21
> **mario2130 said:**
> mm a mi tampoco me reconoce los 4G pero me pesca 3.6G mm pense que era un problema de ubuntu pero no habia indagado me sumare a tu campaña de averiguar que onda, haber si podemos llegar a algo concreto
saludos

ahora instale linux server, como puse el post de mas arriba. hasta ahora todo bien instalando programas y no he tenido ningun problema :D

---

### Post by CdK1 on 2009-06-21
Exacto, o esta manera;

 sudo apt-get install linux-restricted-modules-server 
sudo apt-get install linux-headers-server 
sudo apt-get install linux-image-server linux-server

ó

Recompilar el kernel y dejarlo a medida ;)

---

### Post by moFeta on 2009-06-21
No será que tienes memoria de video compartida ?????

---

### Post by Pabloo0o0 on 2009-06-21
> **CdK1 said:**
> Exacto, o esta manera;

 sudo apt-get install linux-restricted-modules-server 
sudo apt-get install linux-headers-server 
sudo apt-get install linux-image-server linux-server

ó

Recompilar el kernel y dejarlo a medida ;)

ufff... no tengo ni la menor idea como recompilar el kernel .. buscare  :)

> **moFeta said:**
> No será que tienes memoria de video compartida ?????

noup, es independiente con 256mb :)

---

### Post by Carlos C on 2009-06-23
Este thread se presenta varias consultas que debieran ir en hilos separados. El título tampoco ayuda mucho, es demasiado general. Pabloo0o0, te pido que publiques cada problema por separado y escojas títulos que sean lo más descriptivos posibles de tu problema. La idea es que sea fácil dar con la información contenida en tu post mediante un buscador.
Para evitar mayor desorden procedo a cerrar esta conversación. Por favor, antes de volver a publicar lee el siguiente thread:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

---

