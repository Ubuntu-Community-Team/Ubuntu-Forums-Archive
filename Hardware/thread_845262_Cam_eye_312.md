---
title: "Cam eye 312"
date: 2008-06-30
forum: Hardware
---

### Post by ramiro_md on 2008-06-30
Hla amigos, resulta que compre una webcam con mic incorporado de esa snuevas..(genius eye 312)  para que mi abuelo llame a sus familiares en italia y canada con skype. La cuestion es que en win$ anda joya ya que me vinieron todos los drvs e instaladores, queria saber si tiene sioporte para linux (ubuntu)..porqe en el cd no hay y en la pagina no encontre mucho =S..y no quiero tener que reiniciar la compu cada 2 x 3 =p,,,Desde ya muchas gracias.

---

### Post by Mauro22 on 2008-06-30
Conectala y hace un lsusb en la consola para que que chip usa.


Con eso sabras un poco mas donde buscar.

---

### Post by ramiro_md on 2008-06-30
Mauro ese coando me devolvio los siguiente:

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 093a:2622 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000 

Deduci que la cam tenia algo que ver con Pixart Imaging, Inc. Y busuqe en google, donde en muchos foros vi que debia instalar gspcav1..lo cual hice..pero amsn y skype no me reconocen la cam todavia. =S

---

### Post by ramiro_md on 2008-06-30
gspca tampoco funciono. =)

---

### Post by faktorqm on 2008-07-01
Bueno, tu cam anda bajo gnu/linux asi que si no te anda es por que no pusiste el programa correcto digamos.

solucion 1: Instalar el modulo para el v4l y decirle a los programas de usar v4l a partir de aca:

```
sudo apt-get install gspca-source
```

solucion 2: encontre esto:

[http://mxhaard.free.fr/spca50x/Doc/GeniusCamLook312p/2.6.9/](http://mxhaard.free.fr/spca50x/Doc/GeniusCamLook312p/2.6.9/)

y ahi mismo te dice lo que tenes que hacer para que te ande la cam. Seria cuestion de que pruebes y nos cuentes como te fue.

solucion 3: Bajar esto [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz) y compilarlo. Los pasos son:

Instalar el build-essential, los headers del kernel, automake, autoconf, etcetcetc.

```

$ tar -zxvf gspcav1-20071224.tar.gz
$ cd gspcav1-20071224
$ sudo ./gspca_build

```

Esto mismo es la solucion 1 pero mas "trabajosa digamos". Si te pregunta en algun lado (no lo ejecute por que no quiero tener en mi compu un modulo al "cohete") tenes que poner pixart o algo asi.

Bueno, espero que te haya servido de algo. Salu2!!!

---

### Post by ramiro_md on 2008-07-01
Faktorqm hice el punto 1 y 3 pero sigo sin respuesta che =S

---

### Post by ramiro_md on 2008-10-12
Instale los drivers "gspca" y un programa llamado "wxCam". CUando ejecuto este programa me tira un error que dejo adjuntado. Algo de que no encuetra el directorio /dev/video0. Entro a la carpeta /dev y trato de buscar alguna carpeta similar y nada :S. No se que hacer, porque los drivers se instalan xD

---

### Post by faktorqm on 2008-10-14
y...... proba que te dice esto a ver:

```
sudo modprobe gspca
```

y despues proba la camara, y sino, postea la salida de ```
lsmod
```

Salu2!

---

### Post by ramiro_md on 2008-10-14
Faktorqm el primer comando (sudo modprobe gspca) no me devolvió absolutamente nada, tal vez no tenía que hacerlo.
El segundo (lsmod) me devolvión una "tabla" de información bastante extensa, pero las primeras líneas creo que son las que me interesan, las dejo posteadas acá:

Module                  Size  Used by
gspca                 643920  0 
videodev               29440  1 gspca
v4l2_common            18304  1 videodev
v4l1_compat            15492  1 videodev

---

### Post by faktorqm on 2008-10-14
Bien ahi! estas aprendiendo! :KS

Ahi tenes el modulo levantado con las cosas de video levantadas... el comando lo hiciste bien, por eso no te devolvio nada, eso significa que levanto el modulo y ya. Probaste la camara "asi" con los modulos levantados? VLC te la muestra? Salu2!

---

### Post by ramiro_md on 2008-10-14
Con cheese no hay caso :S con un programa que se llama "webcam application" menos :P y con vlc no se como capturar con la cam. 
No puede ser qu sea tan ignorante :P

---

### Post by zvze on 2008-10-20
Yo tambien tengo esta camara y no esta soportada en el gspcav1

lsusb
Bus 002 Device 002: ID 093a:2622 Pixart Imaging, Inc. 

La camara trabaja con un chip compuesto y usa pac7311
(Esto lo obtuve haciendo sniffing a los puertos usb)
Audio: (093a:2622 Rev_0100&M1_01)
Video: (093a:2622 Rev_0100&M1_00)

Tambien abriendo la camara obtuve lo siguiente:
 
Chipset de Audio: Tean ML 1 94V-0

Y otro para el Video: No lo pude obtener [En este caso es el que nos interesa]

... De todas maneras se hizo creer al gspca que la camara era detectada... para esto baje source de el kernel 2.6.7 (ya tra el modulo incorparado) y alli busque el pac7311

Ya teniendo el source del kernel en tu PC
/usr/src/linux-2.6.27.1/drivers/media/video/gspca$

editando pac7311 te das cuenta de lo siguiente:

```

/* -- module initialisation -- */
static __devinitdata struct usb_device_id device_table[] = {
	{USB_DEVICE(0x093a, 0x2600), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x2601), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x2603), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x2608), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x260e), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x260f), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x2621), .driver_info = SENSOR_PAC7302},
	{USB_DEVICE(0x093a, 0x2624), .driver_info = SENSOR_PAC7302},
	{USB_DEVICE(0x093a, 0x2626), .driver_info = SENSOR_PAC7302},
	{USB_DEVICE(0x093a, 0x262a), .driver_info = SENSOR_PAC7302},
	{}
};
MODULE_DEVICE_TABLE(usb, device_table);


```


En fin la camara no es soportada..

trate agregandole la siguiente linea:

```

	{USB_DEVICE(0x093a, 0x2622), .driver_info = SENSOR_PAC7302},

```

Compile el kernel ya estando editada esta linea, hice que detectara la camara pero no funciono correctamente. En conclusion Si puedes saber cual es el Chipset que usa para el video [y no el PID: 2622 que el del chip compuesto] se puede hacer correr la camara...

Si lo tienes hazme saber y asi te ayudare a solucionar. Thanks :guitar:

---

### Post by erdosain9 on 2008-10-21
Hola a todos.  Pues estoy en la misma, así que me sumo al "tema".
Cómo hago para "Si puedes saber cual es el Chipset que usa para el video"... cómo hago para saberlo???
Saludos.

---

### Post by UglyDuck on 2008-10-28
Si decís que tiene un PAC7311 por qué pusiste

```

	{USB_DEVICE(0x093a, 0x2622), .driver_info = SENSOR_PAC7302},

```

y no

```

	{USB_DEVICE(0x093a, 0x2622), .driver_info = SENSOR_PAC7311},

```

Saludos.

---

### Post by zvze on 2008-10-30
> **UglyDuck said:**
> Si decís que tiene un PAC7311 por qué pusiste

```

	{USB_DEVICE(0x093a, 0x2622), .driver_info = SENSOR_PAC7302},

```

y no

```

	{USB_DEVICE(0x093a, 0x2622), .driver_info = SENSOR_PAC7311},

```

Saludos.



Me paso la de confu... volvi el compilar el modulo esta vez arreglando el error:

```
zvze@myb0x:~$ lsmod|grep gspca
gspca_pac7311          22016  0 
gspca_main             29184  1 gspca_pac7311
videodev               41600  1 gspca_main

```

Como puedes ver el modulo esta cargado e igual sigue sin funcionar.

---

### Post by erdosain9 on 2009-05-02
Hola.  Esta webcam sigue sin funcionar??? intenté hacerla funcar pero nada... alguien sabe algo???
Salutes

---

### Post by Mauro22 on 2009-05-02
Ya esta posteado aca:

[http://ubuntuforums.org/showthread.php?t=845262&highlight=genius+eye+312&page=2](http://ubuntuforums.org/showthread.php?t=845262&highlight=genius+eye+312&page=2)

y ya hiciste tu consulta ahi tambien.


Lo revisé y no se me ocurre nada, si encontras algo postea ahi asi queda todo en un solo hilo.

---

### Post by Hei Ku on 2009-05-02
Unidas las dos threads.

Poné: lsusb

Y postea el resultado, a ver que tira tu camara.

---

### Post by squall192 on 2009-05-05
buenas gente
soy algo novato en linux, entre en esto hace poco :P
tengo debian lenny 2.6.26-2-686 y buscado y buscado tratando de usar mi cam genius eye 312 y no pasa nada les agradeciria una enormidad si pudiesen darme una ayuda o sugerencias
esto es el resultado de lsusb
```

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 093a:2622 Pixart Imaging, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```tambien hize los pasos 1 y 3 que en este thread se detalla sin resultados favorables como a ramiro
el paso 2 no lo entendi T-T

estas fueron las salidas con el modprobe gspca y posterior lsmod
```

Module                  Size  Used by
gspca                 640580  0 
videodev               27520  1 gspca
v4l1_compat            12260  1 videodev
```y aun asi nada de nada con cheese, si se les courre algo plz estare pendiente
gracias.


al parecer aqui sale la solución pero no logro llevarla a cabo
[http://cateee.net/lkddb/web-lkddb/USB_GSPCA_PAC7311.html](http://cateee.net/lkddb/web-lkddb/USB_GSPCA_PAC7311.html)
ayuda plz

---

### Post by faktorqm on 2009-05-08
Por lo que dice ahi, ya viene incluido en el kernel a partir de la version que dice el sitio, si no siempre podes compilar desde el fuente, que se yo. lo que no entiendo es cual es su pregunta, digo, cual es la parte que no entienden que hay que hacer? cuenten a ver que hicieron y como o como es que no pueden o que les falta asi los podemos ayudar mejor. salu2!

---

### Post by lordgabb on 2009-05-13
Bueno, yo tengo el mismo problema. Paso los detalles:
#lsusb
```
Bus 001 Device 003: ID 093a:2622 Pixart Imaging, Inc.
Bus 001 Device 002: ID 0458:0019 KYE Systems Corp. (Mouse Systems)
Bus 001 Device 001: ID 0000:0000
```

#cat /proc/bus/usb/devices 
(como veran, mi trackball es detectado perfectamente S: Manufacturer=KYE)
```
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0458 ProdID=0019 Rev= 0.00
S:  Manufacturer=KYE
S:  Product=EasyTrack Optical U+P
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=10ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=093a ProdID=2622 Rev= 1.00
C:* #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 1 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 128 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 2 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 256 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 3 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 384 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 4 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 512 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 5 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 640 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 6 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 768 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 7 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 896 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 8 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=04(O) Atr=03(Int.) MxPS=   2 Ivl=50ms
E:  Ad=85(I) Atr=01(Isoc) MxPS=1023 Ivl=1ms
E:  Ad=06(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=89(I) Atr=01(Isoc) MxPS=  32 Ivl=1ms
I:  If#= 2 Alt= 2 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=89(I) Atr=01(Isoc) MxPS=  96 Ivl=1ms
I:  If#= 2 Alt= 3 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=89(I) Atr=01(Isoc) MxPS=  32 Ivl=1ms
I:  If#= 2 Alt= 4 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=89(I) Atr=01(Isoc) MxPS=  32 Ivl=1ms
```

#modprobe -v gspca
```
insmod /lib/modules/2.6.18-4-k7/kernel/drivers/usb/media/gspca.ko
```

#dmesg
```
usbcore: registered new driver gspca
/tmp/gspca/gspcav1-20071224/gspca_core.c: gspca driver 01.00.20 registered
```

#lsmod | grep -i gspca
```
gspca                 647760  0
videodev               21440  1 gspca
usbcore               113412  9 gspca,usb_storage,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd,ohci_hcd
```

#ls -la /dev/vid*
(Creo que acá debería aparecer /dev/video0 como dispositivo para usar)
```
ls: /dev/vid*: No existe el fichero o el directorio
```

Esto lo hice con el driver compilado por mi de: [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)
Siguiendo las instrucciones que vienen en el README.

Como en /proc/bus/usb/devices no aparece,  me resulta raro que el kernel diga que la soporta. No debería aparecer listada con fabricante y modelo? Porque aparece solamente como P:  Vendor=093a ProdID=2622 Rev= 1.00 y no hay datos en S: (datos de fabricante).
De más esta decir que sin /dev/video0 funcione cheese o gqcam.
También en otra PC probé crearlo con el siguiente comando, pero no funciono:
#mknod /dev/video0  c  81  0   
No se si los datos usados son correctos ( c 81 0), porque me supera. Si saben como obtener esos 3 parámetros por favor diganme así hago mas pruebas.

También en la otra PC instale v4l (casi todo), libpt-* , libusb, cheese, gqcam y varias cosas mas, sin éxito. Las PCs son iguales, y los datos que postie acá son los mismos para las 2 PCs.

Si pueden detectar donde estoy fallando y si tiro la camarita a la basura, avisenme.

Desde ya muchas gracias.
Lord Gabb.

PD:: probe la camarita con Wintendo XP y anda bien, no es problema de hard.

---

### Post by razor7 on 2009-10-02
Hola!, en este hilo esta solucionado...

Aca la solución
[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=6976559&postcount=7](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=6976559&postcount=7)

Si no anda...probar con esto
[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=7464009&postcount=11](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=7464009&postcount=11)

Lo probe con una Genius Eye 312 en ubuntu 9.04 y cheese, anda correctamente!, lo único es que me sale la imagen al revés...no se por que

Saludos.

---

### Post by Pan0ramix on 2010-09-26
Bueno, que revisé todo el thread y veo que un año despues seguimos con el mismo problema. Esta Webcam Genius Modelo Eye312 con Mic incorporado me presenta el mismo problema.
Levanta la cámara pero la imagen SALE INVERTIDA.

Agradeceré si me comentan el estado de este tema y si se ha podido resolver. Estamos a 14 dias de la salida de 10.10 y espero no tener que migrar de nuevo para ver si se arregla. El post es del 2008!

Por cierto, algunos chistosos en otros foros me han dicho que inverta la cámara :(:confused:

---

### Post by ramiro_md on 2010-09-28
> **Pan0ramix said:**
> Bueno, que revisé todo el thread y veo que un año despues seguimos con el mismo problema. Esta Webcam Genius Modelo Eye312 con Mic incorporado me presenta el mismo problema.
Levanta la cámara pero la imagen SALE INVERTIDA.

Agradeceré si me comentan el estado de este tema y si se ha podido resolver. Estamos a 14 dias de la salida de 10.10 y espero no tener que migrar de nuevo para ver si se arregla. El post es del 2008!

Por cierto, algunos chistosos en otros foros me han dicho que inverta la cámara :(:confused:

jajaja es como lo solucionè yo :D...ahora en serio...emm no use mucho la webcam, pero no recuerdo haber tenido ese drama...sale invertida en el programa de mensajeria que usas ? o en vlc tambièn ?

---

### Post by atari130xe on 2010-09-28
probaron con esto?

[http://ubuntuforums.org/showpost.php?p=7768082&postcount=20]("http://ubuntuforums.org/showpost.php?p=7768082&postcount=20")

---

### Post by Pan0ramix on 2010-09-28
> **ramiro_md said:**
> jajaja es como lo solucionè yo :D...ahora en serio...emm no use mucho la webcam, pero no recuerdo haber tenido ese drama...sale invertida en el programa de mensajeria que usas ? o en vlc tambièn ?
 
Sale en todas las apps que usen la webcam...
VLC, Skype, en Cheese tiene una opción para invertir y se ve bien cuando la uso, pero no funciona con Skype (que para lo que mas uso la camarita).
 
Me voy a fijar el link sugerido mas arriba y les aviso como me fué.

---

### Post by oxio on 2010-09-29
Holas!
soy nuevo en este foro y encontré (hace media hora xD) la forma de solucionar el tema este :P... honestamente, me da flojera postearlo todo de nuevo, por lo que les mando el link donde puse la posible solución (en debian squeeze, al menos)

[http://www.esdebian.org/foro/43625/configurar-camara-genius-eye-312](http://www.esdebian.org/foro/43625/configurar-camara-genius-eye-312)

incluye una compilación de módulos D:...
con esa versión, a mi me funcionó perfecto la cámara, al menos con cheese)

espero les sirva :D

---

### Post by Pan0ramix on 2010-09-30
Gracias Oxio. Voy a probar la solución y luego comento cómo me fue en mi distro.

---

### Post by Pan0ramix on 2010-10-10
NO. No anduvo. Lamentablemente no funciona la solución propuesta. Por un lado el procedimiento con el tar es engorroso. Abrí un terminal y segui las instrucciones como root y nada. No compila y la instrucción responde con una 'orden no encontrada'. El archivito de la cam lo tengo y ni idea donde plantarlo. Que no hay algo más sencillo digo yo? Ya salió Maverick... habrán resuelto el tema con esta nueva edición?

---

### Post by oxio on 2010-10-12
q raro o_O
a mi me funcionó de una con eso... probaste a seguir las instrucciones de dentro del archivo?... 

por las nuevas ediciones: supongo que lo arreglarán siempre y cuando vengan con los nuevos controladores de gscpa, porque los que venían con lenny eran los de la página del módulo, cuya última actualización fue el 2007

---

### Post by faktorqm on 2010-10-13
> **Pan0ramix said:**
> NO. No anduvo. Lamentablemente no funciona la solución propuesta. Por un lado el procedimiento con el tar es engorroso. Abrí un terminal y segui las instrucciones como root y nada. No compila y la instrucción responde con una 'orden no encontrada'. El archivito de la cam lo tengo y ni idea donde plantarlo. Que no hay algo más sencillo digo yo? Ya salió Maverick... habrán resuelto el tema con esta nueva edición?

El procedimiento con el tar es engorroso? click derecho -> extraer (no hace falta usar linea de comandos)

Cual es el error que te tira en la terminal? "y nada" no suele ser un buen indicador de problema. Para hacer compilaciones de este tipo necesitas tener instaladas algunas cosas que el autor omite, a saber:

```
sudo apt-get install build-essential autoconf automake m4 binutils
```

no me acuerdo si build-essential era con guion o no, si no te anda sacalo. si te parece muy engorroso, anda a sistema -> administracion -> gestor de paquetes synaptic e seleccionalos uno por uno

Cuando tengas todo eso hecho, lo unico que tenes que hacer es abrir una terminal, irte al directorio donde lo descomprimiste y escribir:

```
sudo make gspca_pac7311.ko
```

y despues

```
sudo make install
```

y despues 

```
sudo modprobe -r gspca_main
```

y despues 

```
sudo modprobe gspca_pac7311
```

y probas. Si algo de todo te fallo postea la salida de la terminal (copia y pega lo que te diga) para ver como se soluciona. Saludos.

---

### Post by Pan0ramix on 2010-10-30
Pincha querido, muchas gracias por tu participación. Mis disculpas en la demora al responder a tu recomendación pero he estado ocupado y lejos de mi querido ubuntu.

Es verdad, necesité instalar el build-essential (es con guión) y pareció que la cosa iba a resultar finalmente. Pues fui a la carpeta donde descargué el tar, lo descomprimí en una carpeta con el nombre 'gspca-2.10.18' (si, el procedimiento de extraer el tar es una p*******z, me refería a toda la vuelta que el autor sugería para instalar una parte del mismo). 
Dentro de esta carpeta tenemos tres elementos, a saber: carpeta build, archivo ReadMe y archivo Makefile.
Parados alli desde el Terminal ejecuto:
pan0ramix@optiplex:~/Descargas/Comprimidos$ sudo make gspca_pac7311.ko
make: *** No hay ninguna regla para construir el objetivo `gspca_pac7311.ko'.  Alto.
Sonamos! Ahi quedó la cosa. Voy y pruebo repetir en la carpeta Build, naninga.
Es todo por ahora, espero que tengas algun aporte mas.

---

### Post by al-go on 2011-01-11
Amigos, quizá a estas alturas ya habrán resuelto el problema de la imagen invertida con la webcam Eye 312. Tengo Ubuntu 10.04 y por muchos días estuve navegando tratando de encontrar solución al problema que tenía con la susodicha cámara. Hasta que encontré esta información sencilla:

Por consola:
 
***$ sudo apt-get install v4l2ucp***


Luego de instalado **v4l2cup**, acceder a System > Preferences > Video4Linux  Control Panel y ahi activamos el checkbox de Vflip ubicado en la parte  inferior, cerramos y listo! Ah, y si también tienen el problemita de la imagen espejo, pueden corregirla tildando la ventanita de *mirror*. 

A mi me ha funcionado a la perfección cuando estaba a punto de lanzar al tacho la camarita.  Espero les funcione a ustedes también.

Esta información la encontré en:

[http://fraterneo.blogspot.com/2010/07/how-to-corregir-imagen-invertida.html](http://fraterneo.blogspot.com/2010/07/how-to-corregir-imagen-invertida.html)

Saludos

---

### Post by Pan0ramix on 2011-02-19
al-go! GRACIAS!!!

Si, finalmente LLEGÓ la solución al bendito problema, y todo en una sola línea de consola. Excelente. Asi fue como acabo de solucionar este problema que se me presentaba en Skype con la webcam Eye 312 Genius. 

La verdad, es que me había dado por vencido. Me dije, ya vendrá la solución con alguna actualización del sistema. Pues no fue asi, Skype sigue en Beta para Linux y no corrige ese error.

Gracias por postear la solución. Solicito al moderador que pase el post a [SOLVED].

---

### Post by Pan0ramix on 2011-02-19
> **al-go said:**
> 

Por consola:
 
***$ sudo apt-get install v4l2ucp*** 


Luego de instalado **v4l2cup**, acceder a System > Preferences > Video4Linux  Control Panel y ahi activamos el checkbox de Vflip ubicado en la parte  inferior, cerramos y listo! Ah, y si también tienen el problemita de la imagen espejo, pueden corregirla tildando la ventanita de *mirror*. 



Corrijo para que quede claro:

***$ sudo apt-get install v4l2cup*** (es v-corta, cuatro, ele, dos, cup)

---

### Post by mama21mama on 2011-02-19
a ver yo tenia un problema parecido, el kernel linux la reconocía pero cargaba mal los parámetros; claro hablo de otro modelo.

probé este script y anduvo; 

1º editas este archivo 

```
sudo nano /usr/bin/webcam
```

```
 
      #!/bin/bash
      modprobe gspca_main autoexpo=0 gamma=5
      modprobe gspca_sunplus
      modprobe videodev
      cvlc v4l2://

```

guardas este contenido dentro.

2º le damos permiso de ejecución 
```
sudo chmod +x /usr/bin/webcam
```

y ejecutamos.

si ves en el cvlc quiere decir que posiblemente ande en skype, cierras la ventana del vlc por que la cam solo permite una instancia y proba el skype.

Suerte


[Fuente]("http://mamalibre.eshost.com.ar/?q=content/webcam-la-fuerza-en-skype")

---

### Post by Pan0ramix on 2011-02-26
Lamento informar que luego de andar con lo sugerido por al-go inicié dias despues una sesión y volvió a tumbarse la imagen. Verdaderamente no entiendo qué puede estar pasando... ya revisé todos y cada uno de los parámetros y estan bien. 

Mama21: Forzar si, pero ¿te funcionó sobre qué webcam? En el bin no tengo archivo webcam, hay uno webcamstudio y otro -x-install-vloopback. La edición, ¿dónde se incluyen esas líneas?

---

### Post by Pan0ramix on 2011-02-26
Copio aqui el contenido de webcamstudio:

```
#!/bin/bash
# WebcamStudio for GNU/Linux Launcher
# Patrick Balleux 2009
# Version 0.55a
INSTALLDIR=/usr/lib/webcamstudio
JAVA_DIR=/usr/lib/jvm/java-6-openjdk/bin
if [ -f $JAVA_DIR/java ]
then
    JAVA_DIR=/usr/lib/jvm/java-6-openjdk/bin
else
    JAVA_DIR=/usr/lib/jvm/java-6-sun/bin
fi
echo "Using JRE: $JAVA_DIR"

PADSP=
if [ -f /usr/bin/padsp ] 
then
    PADSP="/usr/bin/padsp"
else
    PADSP=""
fi
if [ -e /dev/raw1394 ] 
then
    if [ ! -w /dev/raw1394 ]
    then
        gksudo --description "You have a Firewire device available but it is not readable.  Enter you password to make it readable." chmod 444 /dev/raw1394
    fi
fi
$PADSP $JAVA_DIR/java -jar $INSTALLDIR/WebcamStudio.jar

```

---

