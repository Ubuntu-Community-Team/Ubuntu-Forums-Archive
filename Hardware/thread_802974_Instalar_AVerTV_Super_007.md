---
title: "Instalar AVerTV Super 007"
date: 2008-05-21
forum: Hardware
---

### Post by freedert on 2008-05-21
Saludos gente! mi nombre es Diego creo que no me presente en el foro.

Tengo un dramita con una digitalizadora de TV que compre hace poco y quiero hacerla andar en Ubuntu 8.04, es una ¨Avermedia AVerTV Super 007¨, detalles aqui: 
[http://www.avermedia.com/avertv/product/ProductDetail.aspx?Id=22](http://www.avermedia.com/avertv/product/ProductDetail.aspx?Id=22)
Lei googleando por ahi que algunas personas la hicieron andar pero no tengo idea como, Ubuntu no me la reconoce.
Esto es lo que me tira un lshw:
```
*-multimedia
                description: Multimedia controller
                product: SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 1
                bus info: pci@0000:05:01.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=64 maxlatency=32 mingnt=84 module=saa7134

```


Alguien tiene alguna idea?

gracias :)

---

### Post by User21 on 2008-05-22
Te voy tirando una data de a poco, ya que no soy especialista, pero al menos hice funcionar la mia! :D 
Antes que nada, tira un lsmod .. si aparece algo como saa71xx, donde xx es un par de numeros , removelo con el siguiente comando:
```
rmmod saa71xx
``` (No olvides poner los numeros que correspondan!)
Si te devuelve:
```
ERROR: Module saa7134 is in use by saa71xx_dvb,saa71xx_alsa 
``` pues vas a tener que remover esos tambien! Ya que dependen entre si. 
Una vez removidos todos los comandos, podes ver si estan con:```
lsmod
```Si no aparecen en la lista, perfecto! Ya estamos listo para setear los datos que queremos. Para hacerlo, debemos especificar que modulo queremos que sea cargado por Ubuntu. Hay VARIAS POSIBILIDADES y vas a tener que probar con ensayo y error, porque no se cual es la CORRECTA! 
```
sudo modprobe saa7134 card=xx tuner=x remote=1 pll=1
``` Donde xx es un numero segun lista de tarjetas de TV como[** esta**]("http://personal.telefonica.terra.es/web/ceec/otros/tarjetas.html"), y la x es el sintonizador, segun la lista que aparece al final de la anterior. Para empezar, yo probaria con las placas Nº 6, 13, 41, **107**, 123 y 124. Como sintonizador probaria el 5, Phillips PAL. Pero creo que le tenes que dar probando! Ya se que sumado a los sintonizadores, las posibilidades son demasiadas, pero CREEME que te lo reduje bastante! ;) 
De todas formas, si tenes las especificaciones de la placa, o viendola a simple vista, podes detectar que sintonizador usa! 
Es necesario ademas, que tengas instalado TVTIME (u otro) para poder testear el funcionamiento de la placa de TV! Tambien debes setear correctamente TVTIME! 
Ruta al dispositivo (/dev/video0    o   /dev/video) ; Norma: PAL-NC ; Origen de señal: Television ; Cable o Antena, eso queda a tu eleccion.  entre otras cositas... 
Ahora, reconocida la tarjeta de TV, podes usarla con cualquier programa de TV o FM según la ruta al dispositivo (/dev/video1 y /dev/radio0 , en mi caso particular).

Como paso final, edita el archivo de opciones de los modulos, de manera que cada vez que arranque Ubuntu, me reconozca apropiadamente la tarjeta:```
sudo gedit /etc/modprobe.d/options
```y al final del mismo, tipeas el comando modprobe que usaste:```
options saa7134 card=6 tuner=5 radio=1 remote=1
```por ejemplo. Suerte! Cualquier cosa, contactame por mensajeria.

---

### Post by User21 on 2008-05-22
Buscando un poco mas, encontre:
[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007](http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007)

[http://listas.fi.uba.ar/pipermail/lug/2007-December/026905.html](http://listas.fi.uba.ar/pipermail/lug/2007-December/026905.html)

En ellos, se usa el card=107 ! Probalo! 
Suerte!

---

### Post by freedert on 2008-05-22
Hola man, gracias por la ayuda!! ahi estube probando un poco lo que me pusiste, hasta **modprobe saa7134 card=xx tuner=x remote=1 pll=1** hice todo, tambien instale el tv time pero probe con todos los tipos de cards y al parecer no funciona, o al menos el tvtime me muestra pantalla negra, no me pregunto el source de la placa cuando instale el tv time, eso ay que configurarlo tambien en alguna parte?

despues estube probando en:
[http://ubuntuforums.org/showthread.php?t=587056&page=3](http://ubuntuforums.org/showthread.php?t=587056&page=3)
y cuando tengo que instalar lo del Mercurial, instalar el driver y demas, ahora estoy tratando de hacer lo del firmware siguiendo toda esa guia, te cuento cuando lo termine!

---

