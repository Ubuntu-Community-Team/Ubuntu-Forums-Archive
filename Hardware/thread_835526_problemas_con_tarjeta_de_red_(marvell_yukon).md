---
title: "problemas con tarjeta de red (marvell yukon)"
date: 2008-06-20
forum: Hardware
---

### Post by juma2312 on 2008-06-20
Bueno mi nombre es Juan Manuel, tengo 18 años, la cosa es que hace tiempo que queria instalar ubuntu en mi pc y ayer me saque las ganas, instale la version 8.04, la cosa es que ubuntu no reconoce mi tarjeta de red puesta como eth0, mi mother es una asus p5pe-vm y y la tarjeta de red incorporada es una marvell Yukon 88E8001/8003/8010, para mi buena suerte viene con drivers para linux....trate de seguir las instrucciones...pero la verdad que no logre nada, asi que por favor, si alguien es tan amable como para explicarme le agradeceria un monton, desde ya gracias, saludos a la comunidad ubuntera

PD: dejo adjuntados los drivers con el readme

---

### Post by faktorqm on 2008-06-20
Hola, lo único que tenes que tocar es una línea en el archivo de instalación, que es un problema derivado desde muchas versiones de Ubuntu y que nunca supe por que no lo arreglaron. Se trata de que elige mal el intérprete de comandos en bash (Bourne Again Shell) en lugar de elegirlo
automáticamente. Es decir, piensa que sh es distinto de bash. La verdad que si bien sé qué es lo que pasa, no sé por qué pasa, asi que mejor me callo y voy con la solución:

Hacés click derecho sobre el archivo que posteaste, extraer aqui... y en la carpeta que se crea vas a encontrar un archivo que se llama install.sh asi que a ese le hacés click derecho -> abrir con editor de textos y te lo abre, y la primera linea dice

```
#!/bin/sh
```

y la tenés que cambiar por

```
#!/bin/bash
```

es una nimiedad como verás, pero la salida sin este cambio era ésta:

```
faktorqm@the-edge:~/Escritorio$ cd DriverInstall/
faktorqm@the-edge:~/Escritorio/DriverInstall$ ls
install.sh  README  sk98lin.4  sk98lin.tar.bz2
faktorqm@the-edge:~/Escritorio/DriverInstall$ sudo ./install.sh 
[sudo] password for faktorqm: 
./install.sh: 69: Syntax error: "(" unexpected
faktorqm@the-edge:~/Escritorio/DriverInstall$
```

y con el cambio es la que debería ser:

```
faktorqm@the-edge:~/Escritorio/DriverInstall$ sudo ./install.sh 


Installation script for sk98lin driver.
Version 8.30.2.3 (Dec-14-2005)
(C)Copyright 2003-2005 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


1) installation
2) generate patch
3) exit
Choose your favorite installation method: 3
Exit.
faktorqm@the-edge:~/Escritorio/DriverInstall$ 
```

Espero que te haya servido, y bienvenido al foro! :KS Salu2!!!

---

### Post by juma2312 on 2008-06-20
gracias, en cuanto pueda intento el cambio en el codiga, muchisimas gracias, cualquier cosa me paso de vuelta por aca, abrazo!

---

### Post by juma2312 on 2008-06-20
problemas de vuelta, hice lo que me dijiste y todo iba barbaro, puse que instalara, y empezo a instalar, el tema es que una de las partes fallo, y se cancelo la instalacion, el fallo dice que no se encuentran los headers del kernell, cualquier cosa adjunto el codigo, gracias de vuelta!

---

### Post by Hei Ku on 2008-06-20
tenes que instalar el paquete de headers del kernel.
Entra a Synaptics, busca por headers e instala el paquete de headers que corresponda a tu kernel. 
Tambien fijate si tenes instalado el paquete build-essential, que seguramente lo vas a necesitar.
Despues de eso volve a probar.

---

### Post by juma2312 on 2008-06-20
gracias, ya mismo pruebo a ver que onda, abrazo

pd: el paquete built-essential creo que lo tengo

---

### Post by juma2312 on 2008-06-21
Bueno....todavia no logro instalar los drivers...me siento terrible boludo, jeje, pero bueno, intente buscar los headers en sinaptic, y los encontre...pero me dice que tengo todo instalado...asi que no se cual es la historia, voy a adjuntar el codigo que me sale cuando intento instalar a ver si alguien puede decirme porque falla la instalacion, muchas gracias desde ya, abrazo

Juan

---

### Post by Hei Ku on 2008-06-21
me parece que este script debe ser para redhat o alguna distro similar, que tienen algunas cosas en otro lado.

La pista me la da este mensaje:
crate a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

---

### Post by juma2312 on 2008-06-21
Alguna idea de que puedo hacer para que funcione?? o directamente estos drivers no me sirven?? muchas gracias!

---

### Post by Hei Ku on 2008-06-21
te manejas con el ingles?
Aca hay un thread para una placa muy parecida. Fijate que el ultimo post es una explicacion detallada

[http://ubuntuforums.org/showthread.php?t=781022](http://ubuntuforums.org/showthread.php?t=781022)

PD: si no entendes el ingles, avisame y lo traducimos y posteamos aca.

---

### Post by juma2312 on 2008-06-21
el ingles no es problema...me complica mas bien la parte tecnica del asunto...lo de agregar las lienas y eso...pero me voy a tratar de arreglar...cualquier cosa me paso de vuelta, muchas gracias!

---

### Post by Hei Ku on 2008-06-21
paso a paso, como dice Mostaza, :D y tomate tu tiempo, pero parece que la explicacion esta bien detallada, asi que no deberias tener problemas.

---

### Post by juma2312 on 2008-06-21
SOY DE CARTON!!!!, ahora cada vez que quiero usar la terminal me aparece esto:

"unable to resolve host juan-desktop"

no tengo ni idea de que significa ni como hacer para dejarlo como estaba antes...

---

### Post by Hei Ku on 2008-06-21
primero que nada, no sos de carton, esas cosas pasan.
segundo, contame que hiciste antes que te apareciera ese error. me suena a que cambiaste el nombre de la maquina o algo asi.

EDIT:

postea la salida de este comando:

```

cat /etc/hosts

```

---

### Post by juma2312 on 2008-06-21
un amigo que tenia un problema muy similar al mio, me comento que escribiendo no se que cosa se me solucionaba el problema, y ta, intente y no solo no funciono, sino que me paso eso, cuando pueda te digo que me salio de ese comando que me pasaste, abrazo

---

### Post by faktorqm on 2008-06-21
Hola, necesitas un par de paquetes. Instalalos con:

```
sudo apt-get install linux-kernel-devel fakeroot build-essential autoconf automake binutils
```

Luego, para acceder a una terminal, podes probar con apretar la ocmbinacion de teclas "CTRL + ALT + F2". Para volver al entorno gráfico en cualquier momento es "CTRL + ALT + F7". Sino lo podes buscar con el synaptics los paquetes que te puse ahi y luego ejecutar el instalador desde una terminal. Salu2!!

---

### Post by juma2312 on 2008-06-21
por culpa del "unable to resolve host juan-desktop" no puedo probrar ninguna de las soluciones...,

hei ku: adjunte lo que me salio cuando meti el comando que me pasaste,

abrazo

pd:toy considerando borrar ubuntu y volverlo a instalar...

---

### Post by faktorqm on 2008-06-21
El mio dice:

```
faktorqm@the-edge:~$ cat /etc/hosts
127.0.0.1	localhost
192.168.1.2	the-edge

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
faktorqm@the-edge:~$ 

```

Y el tuyo no dice nada, asi que tendria que decir:

```

127.0.0.1	localhost
192.168.1.2	juan-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

En realidad no se, o sea, comparo el mio con el tuyo y listo, de ultima ahi e podes poner tu direccion ip ... no se. sino probalo con 127.0.0.1.
Si no podes abrir ninguna terminal, podes abrir el Editor de textos, pero tenes que apretar "ALT + F2" y en el cuadro que te aparece escribir "gksudo gedit" y luego abrir... e ir a /etc y ubicar el archivo hosts. Cambiar,  en grabar y reiniciar. Una vez hecho eso deberia dejarte. Cualquier cosa Hei Ku que me corija :KS

---

### Post by Hei Ku on 2008-06-21
en realidad, la direccion IP depende de tu maquina, asi que en vez de 192.168.1.2, yo usaria directamente 127.0.0.1 para las dos

eso deberia solucionar el problema.

---

### Post by juma2312 on 2008-06-21
justo habia averiguado como hacerlo...asi que finalmente recupere el control de mi pc...ahora tengo un problema cuando escribo este comando:


sudo apt-get install linux-kernel-devel fakeroot build-essential autoconf automake binutils

sudo apt-get install linux-kernel-devel fakeroot build-essential autoconf automake binutils

me dice que no encuentra el paquete linux-kernel-devel y no se instala....como no puedo configurar la tarjeta de red hasta que instale estos drivers no tengo internet en ubuntu...y solo tengo internet en windows....alguna idea de como conseguir ese paquete faltante?

abrazo!

---

### Post by Hei Ku on 2008-06-22
fijate en getdeb.net

---

### Post by faktorqm on 2008-06-22
Mejor desde el win bajate paquete por paquete en [http://packages.ubuntu.com/](http://packages.ubuntu.com/) (ojo con las dependencias) e instalalos a mano y listo. (perdoname, por un segundo me olvide que eran los de la placa de red y con el apt-get no los ibas a bajar nunca... asi que mejor bajarlos desde otra ubicacion)

---

### Post by juma2312 on 2008-06-22
encontre el pack linux-kernel-devel pero no es compatible con mi version de kernel...no encuentro el que es para la mia...asi que voy a tratar de actualizar el kernel, abrazo

---

### Post by juma2312 on 2008-06-22
me baje el linux-kernel-devel...pero como dijo faktorqm no me fije bien en las dependencias (que no tengo idea de que son) y cuando intente instalarlo me salio: dependency not satifiable (curl), no tengo ni idea de que es el curl tampco :), como se cual paquete del linux-kernel-devel me sirve o sea de mi dependecia?????

abrazo, gracias por la ayuda!

---

### Post by faktorqm on 2008-06-22
Hola, en [http://packages.ubuntu.com/hardy/linux-kernel-devel](http://packages.ubuntu.com/hardy/linux-kernel-devel) los paquetes que te muestra en rojo son las dependencias. Vas a notar que a su vez cada paquete tiene mas dependencias, asi que mejor consulta la lista de paquetes de una instalacion por defecto que esta en el thread de modems de adsl cortesia del compañero vor.
Estas metido en un lindo quilombillo, espero que no te rindas. Salu2!!

---

### Post by juma2312 on 2008-06-22
por ahora no me voy a rendir....me bajare todos los paquetes y probare todos hasta que de con el de mis dependencias...lo que me re calienta es que tengo los drivers y por una chotada no se instalan!!!, bueno...cualquier cosa aviso a ver que onda...gracias!

---

### Post by juma2312 on 2008-06-22
aca, jodiendo de vuelta...intente instalar paquete por paquete pero siempre me falta tal o cual dependencia...tengo otra duda...cuando entro a la parte de conexiones aparecen dos....una que es la del modem y la otra que dice algo asi como "red cableada" o red por cable...habra alguna forma de configurar adsl por ahi??, gracias

---

### Post by juma2312 on 2008-06-22
bueno muchachos finalmente logre tener mi bendito adsl... por mas que no logre instalar esos drivers...encontre una guia que me salvo la plata, la guia es de ueagle y rp-pppoe asi que ta, muchas gracias a ambos, abrazo!

---

### Post by faktorqm on 2008-06-23
pero.. que tiene que ver el modem de adsl con la placa de red? salu2!

---

