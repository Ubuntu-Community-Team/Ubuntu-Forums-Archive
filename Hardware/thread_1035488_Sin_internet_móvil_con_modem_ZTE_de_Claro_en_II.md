---
title: "Sin internet móvil con modem ZTE de Claro en II"
date: 2009-01-09
forum: Hardware
---

### Post by marianom on 2009-01-09
Hola a todos,
 como lo dice el título, no me aparece la opción para conectarme a internet móvil en mi máquina cuando conecto el modem. El mismo es ignorado por la máquina (como debería ser ya que no tiene que tomarlo como un disco usb) pero en las conexiones del network manager no aparece CTI/Claro como opción de conexión (pese a que está configurada).

Algunas salidas:

```
mariano@kafka:~$ tail -f /var/log/messages
Jan  9 20:35:40 kafka kernel: [ 9976.760085] usb 7-1: new high speed USB device using ehci_hcd and address 10
Jan  9 20:35:40 kafka kernel: [ 9976.906240] usb 7-1: configuration #1 chosen from 1 choice
Jan  9 20:35:40 kafka kernel: [ 9976.907831] usb-storage: device ignored

```

```
mariano@kafka:~$ lsusb
Bus 007 Device 010: ID 19d2:2000  

```

El modem está con la luz en verde, lo que supongo indica que está ok para operar y de hecho funciona ok en la máquina de mi esposa.
¿Alguna idea para hacerlo arrancar?

---

### Post by staar on 2009-01-09
lo reconoce como puerto serial?

```
ls -l /dev/ttyUSB*
```

un link si te sirve [http://www.ubuntu-es.org/index.php?q=node/101170]("http://www.ubuntu-es.org/index.php?q=node/101170")

saludos

---

### Post by marianom on 2009-01-09
Nope, no es reconocido. En 8.04 con usb_modeswitch tras mucho esfuerzo lo reconocía pero no sucede lo mismo acá (en el lsusb está ok el vendor y el product pero parece ser que eso no ayuda en mucho).
Alguien sabe donde se guarda la configuracion sobre que modelo de modem elige cuando lo intenta montar?

---

### Post by marianom on 2009-01-09
Se me ocurrió que posiblemente lo esté desmontando como disco pero no esté cargando el módulo en el kernel así que le metí toda la parafernalia necesaria para que esto ocurra:

```
mariano@kafka:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031
Password or swipe finger:
mariano@kafka:~$ ls -l /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory
mariano@kafka:~$ sudo mknod /dev/ttyUSB0 c 188 0
mariano@kafka:~$ sudo mknod /dev/ttyUSB1 c 188 1
mariano@kafka:~$ sudo mknod /dev/ttyUSB2 c 188 2
mariano@kafka:~$ sudo chown root:dialout /dev/ttyUSB*
mariano@kafka:~$ sudo chmod 660 /dev/ttyUSB*
mariano@kafka:~$ ls -l /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2009-01-09 23:31 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2009-01-09 23:31 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2009-01-09 23:32 /dev/ttyUSB2
mariano@kafka:~$ sudo modprobe usbserial -r
mariano@kafka:~$ sudo modprobe usbserial vendor=0x19d2 product=0x0031

```

De todos modos, sin suerte hasta el momento. Si a alguien se le ocurre algo, que chifle.

---

### Post by guillermolisi on 2009-01-10
> **marianom said:**
> Hola a todos,
 como lo dice el título, no me aparece la opción para conectarme a internet móvil en mi máquina cuando conecto el modem. El mismo es ignorado por la máquina (como debería ser ya que no tiene que tomarlo como un disco usb) pero en las conexiones del network manager no aparece CTI/Claro como opción de conexión (pese a que está configurada).

Algunas salidas:

```
mariano@kafka:~$ tail -f /var/log/messages
Jan  9 20:35:40 kafka kernel: [ 9976.760085] usb 7-1: new high speed USB device using ehci_hcd and address 10
Jan  9 20:35:40 kafka kernel: [ 9976.906240] usb 7-1: configuration #1 chosen from 1 choice
Jan  9 20:35:40 kafka kernel: [ 9976.907831] usb-storage: device ignored

``````
mariano@kafka:~$ lsusb
Bus 007 Device 010: ID 19d2:2000  

```El modem está con la luz en verde, lo que supongo indica que está ok para operar y de hecho funciona ok en la máquina de mi esposa.
¿Alguna idea para hacerlo arrancar?
Mariano

Recientemente tuve una experiencia "reveladora", si cabe el termino, sobre estos aparatitos (bajo otro sistema operativo no-Linux).

La luz del modem indica que se conecta con la antena, no con la PC, y su color da idea del protocolo de comunicacion establecido (rojo => sin señal; verde => GPRS; azul => Edge; celeste => 3G).

Esos modems son a la vez pendrives (si les pones una memoria microSD) y poseen una ROM que simula una unidad CD-ROM donde esta el aplicativo para instalarlo en Windows (por ahora solo viene con eso) junto con drivers ad-hoc.

El equipo es, en si mismo, un celular sin teclado. Tiene un numero de telefono celular asociado, una tarjeta SIMM, un IMEI, etc.

En su documentacion se recomienda usarlo siempre con los cables, no directo (dicen que mejora su funcionamiento).

Con todo esto se me ocurre que tal vez lo mas logico seria que lo reconozca como un dispositivo USB (algo asi como un modem ADSL via USB) porque inclusive para conectarlo a la red hay que discar *99#.

En mi reciente experiencia, instalaba todo el software+drivers sin errores (en WinXP) y aun asi no reconocia al equipo (si a la ROM/fake CD). Tuve que deshabilitar los programas de seguridad que estaban activos (Ad-Watch y AVG8) para que la instalacion y posterior operacion fueran satisfactorias (en la documentacion nunca habla de llevar a cabo esto como prerequisito). Esto me paso con el modelo que tenes vos y con un Huawei de la misma operadora (con los Huawei de Movistar nunca tuve estos problemas).

Tu esposa que SO usa ?

---

### Post by marianom on 2009-01-10
Guille, coincido 100% en tu analisis. Mi esposa usa XP y el modem arrancó previa instalación de un soft personalizado sin problemas. 
Antes de intentar usar el modem en II, lo intenté en HH (hice el upgrade ayer) y me pasé unas cuantas horas revisando documentación sobre como hacerlo funcionar (entre ello, el sitio de Sismo quien tiene una suerte terrible para que le anden las cosas out of the box y vive así muy campante). En mi tiempo de investigación aprendí de modem usb, usr_modeswitch y los distintos problemas que a todos se le presentan cuando quieren usar estos modems. Lamentablemente estoy medio atrapado en un callejón sin salida con este problema ya que no estoy pudiendo que el modem (modelo 626, parecido pero distinto a todos los demás) se monte en el /dev/ttyUSB como debería. 
Está visto que me voy a tener que ensuciar realmente las manos para sacar andando esta porquería por más horas que deba invertir en el proceso.

---

### Post by atari130xe on 2009-01-11
Marianom, justamente estoy interesado en la oferta 3G de Claro pero como antes me gustaria saber si va o no vá con una pc de escritorio y más precisamente con Ubuntu me vino al pelo tu post. Googleando encontré algo sobre modems 3G USB en Ubuntu está en Inglés.

Espero te sirva de algo.

[http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/]("http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/")

---

### Post by staar on 2009-01-11
> **atari130xe said:**
> Marianom, justamente estoy interesado en la oferta 3G de Claro pero como antes me gustaria saber si va o no vá con una pc de escritorio y más precisamente con Ubuntu me vino al pelo tu post. Googleando encontré algo sobre modems 3G USB en Ubuntu está en Inglés.

Espero te sirva de algo.

[http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/]("http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/")

OJO!, no te confundas, este problema es especifico de este modelo de modem, los modems huawei, que es la otra marca que mas venden las operadoras, andan al pelo en ubuntu, solo conectarlo y seguir el asistente, yo tengo uno y lo uso como conexion principal, porque no existe otra cosa donde vivo, y anda muy bien, cero dramas, solo se calienta un poco, pero eso es otra cosa :D

saludos

---

### Post by marianom on 2009-01-12
Y de hecho no es que pase con todos los modems ZTE ya que está regada la web de gente que le funciona ok... a mi no me anda :(

Atari, ahora voy a echarle un ojo al link que me pasaste y les cuento.

---

### Post by marianom on 2009-01-12
> **marianom said:**
> Atari, ahora voy a echarle un ojo al link que me pasaste y les cuento.

Otro post de gente exitosa a la cual le anda todo desde cero... los odio ;)

---

### Post by guillermolisi on 2009-01-12
> **marianom said:**
> Otro post de gente exitosa a la cual le anda todo desde cero... los odio ;)

Mariano

Y si vas por lo practico y le pedis a Claro que te cambien el modem por un Huawei devolviendo el ZTE ? (con probar no perdes nada, el NO ya lo tenes asi que vas por el SI :) )

---

### Post by marianom on 2009-01-12
Mi segundo nombre es "Cabeza Dura" y no me voy a rendir tan fácil[1]. Se metieron con mi sistema operativo preferido y ahora esto es personal (no, es una línea Claro: ¡cuak!) 

[1] sea dicho de pasa para no mandarme la parte de heroe que tengo banda ancha en casa y la móvil solo la compramos para cuando tenemos una urgencia y andamos por nuestros pagos de esparcimiento donde no existe internet a kilometros a la distancia.

---

### Post by staar on 2009-01-14
echale un ojo a esto [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/269858]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/269858") ;)

saludos

---

### Post by marianom on 2009-01-14
No andan las medallitas por el momento así que te dejo mi agradecimiento por esta vía. Parece ser que es todo un problema. Lo seguiré de cerca.

---

### Post by guillermolisi on 2009-01-15
> **staar said:**
> echale un ojo a esto [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/269858]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/269858") ;)

saludos
Muy bueno el aporte, va una medallita virtual de mi parte para Staar.

Viste Mariano, es mas expeditivo cambiar el modem :D sobretodo que ahora ya sabes mas sobre el problema (te libera de un cierta cantidad de ansiedad)

---

### Post by marianom on 2009-01-16
> **guillermolisi said:**
> Viste Mariano, es mas expeditivo cambiar el modem :D sobretodo que ahora ya sabes mas sobre el problema (te libera de un cierta cantidad de ansiedad)

¿Sabés que te voy a tener que dar la razón? ¿Cómo es el dicho? "El diablo sabe por diablo..." ;)

---

### Post by Gux_arg on 2009-01-23
Me pasaba lo mismo y lo resolví de la siguiente manera.

Al conectar el dispositivo (ZTE MF626 de Claro) se reconocía como
ID 19d2:2000
y como dispositivo USB (pero sin montar).
 
Para realizar el cambio de dispositivo USB a modem, usé el programa usb_modeswitch que se baja de esta página
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
(están las instrucciones de como proceder).

El archivo usb_modeswitch.conf hay que configurarlo para el dispositivo ZTE MF628+ y ZTE MF626 (solo hay que quitar los # de ese dispositivo).

Cuando se ejecuta este programa en una terminal:
$  sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
si todo marcha bien el dispositivo cambia a modem.

Se puede comprobar con lsusb y da
ID 19d2:0031

Luego de unos 10 o 20 segundos (se apaga la luz y luego se vuelve a prender), tipear en la terminal
$ sudo /sbin/modprobe usbserial vendor=0x19d2 product=0x0031

A partir de este punto debería funcionar como modem. La mayoría de las páginas que consulté usaban el programa wvdial para conectarse. Yo no pude lograr que funcionara. Por lo que definí un archivo que reconozca el network manager. 
$ sudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi

El contenido del archivo (tomado de [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)) es el siguiente:
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- ZTE MF626 HSDPA USB Modem -->
<match key="@info.parent:usb.vendor_id" int="0x19d2">
<match key="@info.parent:usb.product_id" int="0x0031">
<match key="@info.parent:usb.interface.number" int="3">
<append key="modem.command_sets" type="strlist">GSM-07.07</append>
<append key="modem.command_sets" type="strlist">GSM-07.05</append>
<append key="info.capabilities" type="strlist">modem</append>
</match>
</match>
</match>
</device>
</deviceinfo>

Cuando agregué ese archivo y como tenía definida la conexión de Claro en el network manager, automáticamente reconoció el modem y me conectó a Claro.

Espero que la información te sirva y suerte con la conexión.

---

### Post by marianom on 2009-01-24
Hola Gux, dispensarás mi demora en responderte pero estoy de viaje laboral. Todos los pasos que citás los he seguido en Hardy sin éxito alguno pero no quita que los pruebe de nuevo en II. 
Cualquier novedad, la haré saber por esta vía.

---

### Post by gmunioz on 2009-01-24
Hola mar...:
Prueba lo siguiente:

Crea el archivo /etc/udev/rules.d/50-ztemf.rules con la orden en consola:

sudo /etc/udev/rules.d/50-ztemf.rules

Copia y pega en el archivo este contenido:

ACTION!="add", GOTO="ZTE_End"# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"
LABEL="ZTE_ZeroCD"

# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/sbin/rmmod usb_storage"
LABEL="ZTE_Modem"

# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",

# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"
LABEL="ZTE_End"

Guarda el archivo y a continuación edita el archivo /etc/wvdial.conf
Copia y pega el siguinete contenido:

[Dialer Defaults]
Modem = /dev/ttyACM0
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = AT+CFUN=1
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","internet.ctimovil.com.ar"
Init5 =
Init6 =
Init7 =
Init8 =
Init9 =
Phone = *99#
Phone1 =
Phone2 =
Phone3 =
Phone4 =
Dial Prefix =
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = 3616
Username = ctigprs
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Auto DNS = off

Posteriormente enchufa el modem y sin quitarlo reinicia el sistema.
Una vez iniciada y cargada la sesión, ejecuta en consola:
sudo wvdial

Si no conecta o informa error, ejecuta la orden reiteradas veces.
Saludos.
Gabriel.
**Solo doy soporte para Ubuntu** - *Mad Jaunty User*

---

### Post by Gux_arg on 2009-01-25
Hola Mariano,
Disculpá un error en las instrucciones. Donde dice quitar los # (del archivo de configuración de usb_modeswitch) debería decir los ; (punto y coma).
Las instrucciones que te conté las hice en II (no tengo Hardy).

---

### Post by sroland81 on 2009-02-18
Hola gente, lo hice andar con las instrucciones del cambiar de modalidad el Claro usb modem ZTE... la pregunta es esta... cuando inicio mi sesion en ubuntu despues de prender la notebook por ejemplo, tengo que ejecutar los 2 comandos para que cambie de modo y reconozca el modem el network manager... entonces para no hacerlo todas las veces lo agregue en mi rc.local y anda bien..... el tema es que no se si es por mala senial o que, que a veces se me desconecta el modem y cuando hago click en el network manager ya no me aparece el Claro como conexion... pero si vuelvo a ejecutar los 2 comandos, vuelve a aparecer en el network manager como conexion... que es lo que pasa? noto tambien que el modem se calienta bastante... puede ser por eso que se desconecte y que despues no se vea? quiza se desmonta.. no se... o sera por mala senial? hay alguna forma de saber si hay senial buena o mala? (perdonen que no tenga enies o tildes)
hay alguna forma de que estos 2 comandos se vuelvan a ejecutar solos cuando se desconecta espontaneamente el modem?... otra, si lo desconecto a mano, la conexion no se va del network manager... sigue estando y si hago click se conecta de nuevo...

los 2 comandos que agregue a mi rc.local son:

sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf

sudo /sbin/modprobe usbserial vendor=0x19d2 product=0x0031

gracias por la ayuda,

---

### Post by guillermolisi on 2009-02-19
> **sroland81 said:**
> Hola gente, lo hice andar con las instrucciones del cambiar de modalidad el Claro usb modem ZTE... la pregunta es esta... cuando inicio mi sesion en ubuntu despues de prender la notebook por ejemplo, tengo que ejecutar los 2 comandos para que cambie de modo y reconozca el modem el network manager... entonces para no hacerlo todas las veces lo agregue en mi rc.local y anda bien..... el tema es que no se si es por mala senial o que, que a veces se me desconecta el modem y cuando hago click en el network manager ya no me aparece el Claro como conexion... pero si vuelvo a ejecutar los 2 comandos, vuelve a aparecer en el network manager como conexion... que es lo que pasa? noto tambien que el modem se calienta bastante... puede ser por eso que se desconecte y que despues no se vea? quiza se desmonta.. no se... o sera por mala senial? hay alguna forma de saber si hay senial buena o mala? (perdonen que no tenga enies o tildes)
hay alguna forma de que estos 2 comandos se vuelvan a ejecutar solos cuando se desconecta espontaneamente el modem?... otra, si lo desconecto a mano, la conexion no se va del network manager... sigue estando y si hago click se conecta de nuevo...

los 2 comandos que agregue a mi rc.local son:

sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf

sudo /sbin/modprobe usbserial vendor=0x19d2 product=0x0031

gracias por la ayuda,
El LED del modem te dice si tiene señal y que protocolo esta usando con sus colores (rojo es que no tiene señal, verde es GPRS, azul Edge y celeste o cyan es 3G).

Por otra parte, si llamas a atencion al cliente en Claro ellos pueden decirte como llegan a modem y darte una referencia del nivel de señal que detecten (me entere haciendoles reclamos por uno del mismo modelo durante diciembre ultimo).

---

### Post by sroland81 on 2009-02-20
No me queda claro lo de los colores... pues haciendo un adsltest en una pagina local de aca que te mide la conexion me da unos 400 - 450 kbps y el color del led es verde me parece... capaz es otro de esos colores que decis pero no me coy cuenta la diferencia... pero si fuera el verde el que veo, no podria ser GPRS no? que velocidad tiene el GPRS? por lo que sabia es como un modem telefonico... unos 56Kbps... lo de la desconexion me pasa que me pregunta la contrasenia y bueno... despues de meterla varias veces entra o no.... hasta que lo desenchufo un rato y ahi camina... pero a veces cuando se desconecta no me aparece mas en el Network manager... sera eso algun bug o error en el modem que lo deja desmontado o reseteado o algo asi? es posible que con algun update este hardware quede soportado automaticamente o hay que esperar a otro ubuntu?

gracias..

---

### Post by osnave78 on 2009-03-27
Hola Guz_arg: seguí las instrucciones para un Linux OpenSUSE, pero no me navega, el modem lo compre a COMCEL de Colombia.

Gracias.

---

### Post by abokser on 2009-05-10
Hola a todos!

Bueno, me sumo al tema. Por lo que pude ver no hay problema con los modems Huawei, el tema es con algunos otros.

Yo tengo un BESS UM100 y me ocurre exactamente lo mismo,  no lo reconoce como ttyUSBn sino como una unidad de disco removible, así nunca va andar.

Hasta ahora no le encontré la vuelta.

Encima yo tengo 2 instalaciones una Ubuntu y otra Kubuntu (ambas jj), en Kubuntu ni siquiera me permite abrir la pestaña de banda ancha movil en el configurador de red.

¿Alguien experimentó con Kubuntu?

Saludos

Alejandro

---

### Post by atari130xe on 2010-05-30
> **abokser said:**
> Hola a todos!

Bueno, me sumo al tema. Por lo que pude ver no hay problema con los modems Huawei, el tema es con algunos otros.

Yo tengo un BESS UM100 y me ocurre exactamente lo mismo,  no lo reconoce como ttyUSBn sino como una unidad de disco removible, así nunca va andar.

Hasta ahora no le encontré la vuelta.

Encima yo tengo 2 instalaciones una Ubuntu y otra Kubuntu (ambas jj), en Kubuntu ni siquiera me permite abrir la pestaña de banda ancha movil en el configurador de red.

¿Alguien experimentó con Kubuntu?

Saludos

Alejandro

Mi hna tiene un modem de esa marca el ZTE MF626 es similar, y lo hice funcionar con Linux Mint, solo lo conectas y te va a aparecer como CD lo "expulsas" y luego queda como modem, a partir de ahi tenés que usar wvdialconf y una vez que sepas en que puerto es detectado ttyUSB1, 2 o 3 usas gnomePPP un programita que te permite conectar dial up pero que sirve perfectamente para conectarse con un modem USB 3G. Espero te sirva el dato.

Te dejo el link que utilicé yo (acá mismo en el foro de Argentina) con el paso a paso para hacerlo funcionar (funciona muy bien))

[http://ubuntuforums.org/showthread.php?t=1391818&highlight=modem+ZTE+MF626]("http://ubuntuforums.org/showthread.php?t=1391818&highlight=modem+ZTE+MF626")

---

