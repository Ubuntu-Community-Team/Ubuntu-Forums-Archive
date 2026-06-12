---
title: "Conectarse a la red inalambrica"
date: 2009-06-29
forum: Hardware
---

### Post by tralala321 on 2009-06-29
hola tengo un acer aspire 5000 y aunque tengo encendida la conexion a la red inalambrica (luz naranja), no me puedo conectar a la red de mi casa aunque coloco todos los datos que me piden.
Cual puede ser el problema????
:???:

---

### Post by Carlos C on 2009-06-30
Hola, primero tenemos que saber qué tarjeta wifi tienes. Por favor abre el terminal y escribe:
```
lspci |grep Ethernet && lspci |grep Wireless && lspci |grep Network
```
Copia acá lo que te salga.
Saludos

---

### Post by moreback on 2009-06-30
Yo creo que se necesita información de la encriptación usada en la red inalámbrica casera.

---

### Post by Carlos C on 2009-06-30
> **moreback said:**
> Yo creo que se necesita información de la encriptación usada en la red inalámbrica casera.
cierto, cierto.

---

### Post by tralala321 on 2009-06-30
holis, aca esta lo q salio cuando escribi el codigo q me dijieron

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
tralala@tralala-laptop:~$  



y eso de la informacion de la encriptacion es lo que da el programa del router??? si es q es eso, ya lo puse y no pasa nada

):P

---

### Post by moreback on 2009-06-30
> **tralala321 said:**
> 
y eso de la informacion de la encriptacion es lo que da el programa del router??? si es q es eso, ya lo puse y no pasa nada

):P


Protocolo de encriptación principalmente: WEP, WPA, largo de la contraseña, etc, etc.

---

### Post by kamus on 2009-06-30
> **tralala321 said:**
> hola tengo un acer aspire 5000 y aunque tengo encendida la conexion a la red inalambrica (luz naranja), no me puedo conectar a la red de mi casa aunque coloco todos los datos que me piden.
Cual puede ser el problema????
:???:

El administrador de redes detecto tu red inalambrica (essid) u otras redes?, Si NO la encuentra o no aparece en el network-manager la opcion, seguramente es porque no esta bien configurado el controlador de la tarjeta de red wireless, aqui tendras que poner la informacion que te estan pidiendo los chicos anteriormente.

Saludos

---

### Post by CdK1 on 2009-06-30
Antes que todo: 

Supongo que la red "wifi" es accesible, es decir la haz probado con otros laptop, por ende FUNCIONA
Además, cuando señalas que tienes problemas con el cifrado, necesito que hagas esto:

Cuando estés llenando los datos para conectarte y trates de hacerlo, corre en una terminal este comando "dmesg" y pega lo que sale
además supongo que, como funciona la wifi, puedes ver las redes verdad?, sino es así, no tienes nada configurado, etc, haz lo que señalo a continuación.-


Suponiendo que no tienes nada instalado y configurado respecto de la Wifi, tienes dos maneras de instalar los drivers;


Pasos previos:

sudo modprobe -r bcm43xx ==> Por si hubiese algo 

gedit /etc/modprobe.d/blacklist Y agregamos al final;

blacklist bcm43xx       ==> Esto es para que no se cargue al inicio

sudo apt-get insta build-essential module-assistant ndiswrapper-common

Ejecutas;

sudo m-a update 
sudo m-a prepare
sudo m-a a-i ndiswrapper
sudo modprobe ndiswrapper 

wget [http://www.antoniomtz.org/files/drivers-32.tar.gz](http://www.antoniomtz.org/files/drivers-32.tar.gz)

tar vxzf drivers-32.tar.gz 

Salndrán los siguientes archivos:

bcmwl5.sys
bcmwl5.inf

Lo instalas de la siguiente manera;

sudo ndiswrapper -i bcmwl5.inf 

Verificas;

sudo ndiswrapper -l

Debería salirte algo similar a esto;

[B][B]bcmwl5 driver installed...


[/B][/B]Si sale algo como eso, haz esto;

sudo gedit /etc/modules Y agregas;

ndiswrapper           ==> Eso es para cargar el módulo al inicio

Reinicias y te conectas usando "wicd" o "Network Manager"


Instalación desde los repositorios;

Es más fácil;

sudo apt-get install b43-fwcutter
cd /usr/share/b43-fwcutter
sudo ./install_bcm43xx_firmware.sh 
sudo /etc/init.d/networking restart

Y usando wicd o Network Manager desde Gnome te conectas...

---

### Post by moreback on 2009-07-01
> **tralala321 said:**
> hola tengo un acer aspire 5000 y aunque tengo encendida la conexion a la red inalambrica (luz naranja), **no me puedo conectar a la red de mi casa aunque coloco todos los datos que me piden.**
Cual puede ser el problema????
:???:


Mija, he revisado varias veces su consulta e insisto que tiene que haber algo con el tipo de encriptación de su red inalámbrica. ¿Sería tan amable de pegarnos un pantallazo de la ventana que le pide los datos de conexión?

Gracias.

---

### Post by tralala321 on 2009-07-01
cuando escribo esto: sudo m-a a-i ndiswrapper

sale esto:

module-assistant, mensaje de fallo &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
     &#9474;                                                                    &#9474; 
     &#9474; Falló la instalación del fuente de ndiswrapper-source.             &#8593; 
     &#9474;                                                                    &#9646; 
     &#9474; Se ignora este paquete. Quizá necesite añadir algo a su lista de   
     &#9474; fuentes, quizás los archivos «contrib» o «non-free».               
     &#9474;                                                        

entonces se me ocurrio ir a synaptic e instalar lo q dijiera non-free  y contrib; enotnces al intentar nuevamente salio lo mismo


y... emm ya no esta la lucecita amarilla, lo q me parece raro es q en los controladores de hardware si esta el Broadcom B43 activo   T_T  .......... y por eso ya no podria enviar un pantallazo.


Molesto mucho??? lo sientoo

---

### Post by moreback on 2009-07-01
Ojalá pudieras subir el pantallazo.

Lo otro es que revisaras la configuración del router inalámbrico para que vieras realmente que cifrado está usando.

Saludos.

---

### Post by CdK1 on 2009-07-01
Trata de conectarte y pon dmesg en la consola, ve que te tira...

---

