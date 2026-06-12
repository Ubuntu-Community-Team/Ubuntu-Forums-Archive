---
title: "[SOLUCIONADO] ayuda compaq presario v2615la"
date: 2009-05-26
forum: Hardware
---

### Post by hkrxd on 2009-05-26
miren mi tema es el siguiente:

tengo un portatil compaq v2615la como indique en el titulo, el cual tiene una tarjeta wifi broadcom (bcm4318 ) ... la cual no he podido instalar de ninguna manera... en ubuntu 9.04 jaunty.

probe el instalar el bcm43xx-fwcutter y luego ponerle el firmware del archivo wl_apsta.o que en muchos foros aparece... y no me sirvio..

luego probe hacerlo con ndiswrapper y tampoco...

que hago???

porfavor es urgente...!!!

---

### Post by felipeleven on 2009-05-26
> **hkrxd said:**
> miren mi tema es el siguiente:

tengo un portatil compaq v2615la como indique en el titulo, el cual tiene una tarjeta wifi broadcom (bcm4318)... la cual no he podido instalar de ninguna manera... en ubuntu 9.04 jaunty.

probe el instalar el bcm43xx-fwcutter y luego ponerle el firmware del archivo wl_apsta.o que en muchos foros aparece... y no me sirvio..

luego probe hacerlo con ndiswrapper y tampoco...

que hago???

porfavor es urgente...!!!

Una consulta:

En el panel gnome : Sistema->Administración->Controladores de hadware

¿Te aparece algún driver?

En mi caso, también tengo una tarjeta broadcom, y dentro de Controladores de hadware me aparece un driver llamado "STA", el cual me activa el wifi.

Por favor cuenta lo que te aparece.
Saludos

---

### Post by hkrxd on 2009-05-26
sabes que...
no aparece ningun controlador privativo....


nada de nada


es mas...
solo por probar hice

:~$ modprobe bcm43xx
FATAL: Module bcm43xx not found

luego ..

:~$ modprobe bcm4318
FATAL:Module bcm43xx not found

---

### Post by kamus on 2009-05-26
> **hkrxd said:**
> sabes que...
no aparece ningun controlador privativo....


nada de nada


es mas...
solo por probar hice

:~$ modprobe bcm43xx
FATAL: Module bcm43xx not found

luego ..

:~$ modprobe bcm4318
FATAL:Module bcm43xx not found

[[IMG]http://img139.imageshack.us/img139/3918/pantallazo1x.th.png[/IMG]](http://img139.imageshack.us/my.php?image=pantallazo1x.png)

Yo tengo un compaq v3218la, pero deberias tener el mismo chipset de la tarjeta de red inalambrica de todas maneras fijate que este activado ese controlador en el menu de controladores de hardware.

Salu2

---

### Post by hkrxd on 2009-05-26
es que no aparece nada en controladores del sistema.

---

### Post by felipeleven on 2009-05-26
> **hkrxd said:**
> es que no aparece nada en controladores del sistema.

Sabes que podría ser también, que tu tarjeta de wifi no funcione por problema de hadware.
Es sabido que muchos modelos de compaq y hp presentan una falla de fábrica que hace que la tarjeta del wifi deje de funcionar por el sobre calentamiento del chipset de la tarjeta de video (en la placa madre), a mi con mi compaq presario f565la  me ocurrió eso.

Mira este link:
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=es&cc=mx&docname=c01318754&dlc=es](http://h10025.www1.hp.com/ewfrf/wc/document?lc=es&cc=mx&docname=c01318754&dlc=es)

En esa página tu modelo no aparece dentro de los afectados, pero buscando por internet hay casos con tal problema usando tu modelo.

Ahora, puede que este equivocado, no sé si hayas usado otra plataforma (ej: windows xp) y hayas visto si te funciona o no el wifi, en caso de que te funcionara el problema que te nombre anteriormente no estaría presente. Cumplo con informarte sobre ese problema, sería irresponsable de mi parte no decirtelo.

---

### Post by Carlos C on 2009-05-26
Existe un detalle con las tarjetas bcm43 y es que no todas están soportadas por el driver b43, que es el que intentas usar cuando instalas el paquete b43-fwcutter. Para saber si tu tarjeta está soportada debes escribir en el terminal:
```
lspci -vnn | grep 14e4
```Vas a obtener un resultado parecido a este:
```
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```Lo que te importa es lo que está entre paréntesis cuadrados (corchetes):
```
[14e4:4318]
```considerando loque te salga a ti verifica que tu tarjeta esté soportada en la lista que aparece en el sitio de linuxwireless:

[http://linuxwireless.org/en/users/Drivers/b43#KnownPCIdevices](http://linuxwireless.org/en/users/Drivers/b43#KnownPCIdevices)

Si no está soportada debes usar ndiswrapper :(

---

### Post by hkrxd on 2009-05-27
ya lo solucione...

mas tarde subire la solucion y los archivos utilizados.

---

### Post by hkrxd on 2009-05-27
bueno. este script lo hice pensando en que alguien mas debe haber tenido el mismo problema que yo.

eso si! AVISO!!!!

antes que nada debo avisar que no tengo mucha experiencia en scripts. asique si alguien me hiciera el favor de revisarlo y decirme que esta mal le agradeceria mucho...

otro aviso. esto esta hecho pensando en que se quiere activar la tarjeta bcm4318 sin tener internet en el pc objetivo, pero teniendo los archivos que mas adelante adjunto en un dispositivo de almacenamiento

---

### Post by Carlos C on 2009-05-28
> **hkrxd said:**
> bueno. este script lo hice pensando en que alguien mas debe haber tenido el mismo problema que yo.

eso si! AVISO!!!!

antes que nada debo avisar que no tengo mucha experiencia en scripts. asique si alguien me hiciera el favor de revisarlo y decirme que esta mal le agradeceria mucho...

otro aviso. esto esta hecho pensando en que se quiere activar la tarjeta bcm4318 sin tener internet en el pc objetivo, pero teniendo los archivos que mas adelante adjunto en un dispositivo de almacenamiento
Ok, lo importante para mi es saber que utilizaste ndiswrapper. Ojalá hubiéramos podido saber si tu tarjeta esta soportada por el módulo b43, siguiendo los pasos que te sugerí. De todas maneras muchas gracias por el script.

Saludos!

---

### Post by hkrxd on 2009-05-28
Carlos C: nolo hice con el metodo que tu me habias dicho, poruqe ya lo habia intentado..

la bcm4318 efectivamente está soportada por el bcm43,

pero le falta el firmware (como a todas las broadcom de la serie bcm43xx, no se si otras), pero en especial para la bcm4318 los archivos de firmware que hay disponibles son todos demaciado viejos y por ende carecen de funcionabilidad... no pude encontrar unas firmas mas actuales, por lo que este metodo quedo descartado...

además de que en otros foros ahbia visto que al hacerlo validando el firmware de la tarjeta y usando el controlador bcm43 hay veces en las que presenta problemas la tarjeta...

sin ir mas lejos.... gracias a todos por su ayuda.. espero que a alguien mas le sirva lo que yo encontre.

---

### Post by hkrxd on 2009-05-28
pd: se me olvidaba... Carlos C tengo exactamente la tarjeta que mencionaste en el quote

del 

>  lspci -vnn | grep 14e4 

---

### Post by Carlos C on 2009-05-29
si es esa es extraño que no te funcione, porque es la que tengo yo y me funciona en Jaunty. Pero de todas maneras es bueno saber que existe más de un método para trabajar con ella.

---

### Post by josekstro on 2010-08-22
Disculpa hkrxd. trate de correr el script que viene en el archivo comprimido que subiste. Lo intente correr desde la terminal pero me dice que no puede abrirlo. soy nuevo en ubuntu asi que no tengo mucha experiencia, cualquier pequeña ayuda sera agradecida.

---

### Post by RafaelG on 2010-08-23
> **hkrxd said:**
> tengo un portatil compaq v2615la como indique en el titulo, el cual tiene una tarjeta wifi broadcom (bcm4318 ) ... la cual no he podido instalar de ninguna manera... en ubuntu 9.04 jaunty.


El dilema es cuando los ingenieros de Ubuntu solucionaran el problema por completo por que cada usuario que tiene este modelo de tarjeta termina presentando los mismos problemas hay varios post donde solicitan ayudan para los mismos modelos de la esta tarjeta. Hasta la version 8.10 todo bien pero cuando salio jaunty todo mal lo peor de todo es que  es una de las tarjetas mas vendidas en los Notebooks

---

### Post by Carlos C on 2010-08-23
Me parece bien raro, mi modelo es el mismo y funciona apenas instalo los controladores

---

