---
title: "mi webcam no lo reconoce ubuntu"
date: 2010-05-08
forum: Hardware
---

### Post by rockbert on 2010-05-08
mi problema es el siguiente:
 yo vivo en iquique y desde hace ya un poco mas de un año instale ubuntu 9.04 jaunty en mi pc, despues de haberme aburrido de xp :mad: , y hasta ahora no había tenido grandes problemas con ubuntu y de hecho estábamos felices en mi casa por la obvia e incomparable ventaja que ofrecía por encima del otro sistema operativo. Bueno el problema es que aprovechando las ventajas de la zona franca y por necesidad de mi hermana que habla lenguaje de señas fui a comprar una cámara web con las siguientes características:

fabricante: nekstel japan
modelo: HR-819DC
tipo: digital PC camera con microfono
coneccion: usb2.0
hiresoluving power: 2000x2500
formato video: 24-bit RBG
frame rate: 320x240 up to 30frame/sec(CIF)
S/N ratio: <48Db
dynamic range: <72Db
focus range: 5cm-intinity
compatible con windows 98 SE/ME/2000/XP/VISTA (pero eso no importa verdad)

el problema es que no logre de ninguna forma hacerla funcionar, y lo único que puedo hacer en subirle y bajarle unas luces manualmente que tiene incorporado. buscando trate de instalar EasyCam, Camorama, Cheese pero todo eso fue un fracaso. y mas encima parece que el sistema no lo lee, porque al ingresar el comando en el terminal:

> $ lsusb

me sale esto:


> Bus 001 Device 004: ID 1e4e:0100  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

en donde huawei es mi módem con conexión usb pero no veo la cam!!!
entonces si alguien sabe que esta pasando que me diga por favor

---

### Post by AlvaroV on 2010-05-09
Prueba ver la siguiente página:

[http://doutdex.wordpress.com/2007/05/13/como-agregar-camara-web-webcam-a-ubuntu/](http://doutdex.wordpress.com/2007/05/13/como-agregar-camara-web-webcam-a-ubuntu/)


Yo también tuve muchos problemas con la webcam pero un día probando y probando funciono, no me preguntes como lo hice porque no recuerdo la secuencia pero si se que tiene que ver con lo que aparece señalado como **"gspca** antiguo [B]spca5xx".  Instale haciendo pruebas algunos de estos drivers y de pronto mi webcam funciono. Si revisa Google y prueba.
[/B]

---

### Post by rockbert on 2010-05-09
no pasa nada, de hecho la marca y el modelo ni siquiera sale en la lista de compatibilidad, mmm debe ser porque nekstel japan normalmente se dedicaba a la fabricación de celulares, y no hace mucho empezaron a vender cam, puede que el driver aun no este disponible mmm, que mala suerte si fuera ese el caso:-(, de todas formas gracias seguiré probando como lo aconsejas hasta que salga

---

