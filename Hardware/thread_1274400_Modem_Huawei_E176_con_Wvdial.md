---
title: "Modem Huawei E176 con Wvdial"
date: 2009-09-24
forum: Hardware
---

### Post by asterix77 on 2009-09-24
Para todos aquellos que por un motivo u otro han desintalado Network Manager (como yo que lo hice porque instalé wicd y automáticamente me desintaló el NM, ya que tenía problemas con unas redes inalámbricas, y que los solucioné facilmente con el wicd). Les cuento que edité el archivo /etc/wvdial.conf de la siguiente forma.

[Dialer Defaults]

Auto DNS = off
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","imovil.entelpcs.cl"
Modem Type = USB Modem
Phone = *99***1#
ISDN = 0
Username = entelpcs
Password = entelpcs
Ask Password = 0
Dial Command = ATD
Stupid Mode = 1
Compuserve = 0


Una vez guardado solo basta ejecutar en la terminal
#sudo wvdial

Y listo, conectado a internet a través de mi modem huawei E176 de Entel PCS

Tengo entendido que el Network Manager reconoce bastante bien este modem usb, pero por si alguien no lo usa, al menos tendrá esta alternativa.

Saludos

---

### Post by lucic88 on 2009-11-06
can you write this in english please?

---

### Post by asterix77 on 2009-11-06
For those who for one reason or another have uninstalled Network Manager (like me who did it because I installed wicd and automatically uninstalling the NM, since he had some problems with wireless networks, and that easily solved with wicd). I tell them that I edited the / etc / wvdial.conf as follows.

#sudo gedit /etc/wdial


[Dialer Defaults]

Auto DNS = off
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","**imovil.entelpcs.cl**"
Modem Type = USB Modem
Phone = ***99***1**#
ISDN = 0
Username = **entelpcs**
Password = **entelpcs**
Ask Password = 0
Dial Command = ATD
Stupid Mode = 1
Compuserve = 0


The text in bold should be changed by the configuration of your country


Once saved only just run in terminal 
 # sudo wvdial 

 And smart, connected to the internet through my modem Huawei E176 Entel PCS 

I understand that the Network Manager recognizes quite well the usb modem, but if someone does not use it at least have that option. 

 Greetings

---

### Post by Carlos C on 2009-11-06
> **lucic88 said:**
> can you write this in english please?

I remind you that this is the Chilean Loco Forum:

> Ubuntu Forums Code of Conduct
**[SIZE=4]Posting to the Forums:[/SIZE]**
  **Section I - General Policy:**
 
9. Please strive to communicate with other users as effectively as possible: 
[LIST=1]
[*]
[LIST]
[*]Please try to write your posts in English **unless** you are participating in a Loco Forum, **where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff**.
[/LIST]
 
[/LIST]
Saludos.

---

### Post by moreback on 2009-11-06
"And smart" jajaja Google Traductor?

Igual buen post, wvdial es fácil de configurar, de hecho fue lo primero que usé cuando hice funcionar mi modem Samsung en Ubuntu.

Saludos!

---

### Post by asterix77 on 2009-11-09
Ja Ja. No me había dado cuenta, y tienes razón Google traductor. Hay que aprovechar las herramientas de la web. En todo caso es uno de los buenas páginas traductoras que he visto.

Saludos

---

### Post by dekomen on 2010-08-08
Buenas, aclaro que como la mayoria soy nuevo en el tema linux, en particular ubuntu. Un amigo vino ayer a casa a instalarme el ubuntu 10.4, lo dejamos instalado y el tema q seguia era el de configurar mi modem Huawei e175 de ancel. He buscado por todos lados, y en la mayoria de los lugares me hablan del Wvdial. Ya edite el archivo wvdial.conf con los datos que leia en los foros pero me salta un error cuando le doy
sudo wvdial
me dice que no puede reconocer el device ttyUSB0, que fue el que le puse en el wvdial.conf, el cual estaba en todos los foros que lei.
si alguien me puede pasar un archivo wvdial.conf con las cosas exactas que tengo q escribir, se lo agradesco y tambien si alguien me puede decir porque no reconoce ese device. Aclaro que yo tengo mi username y password para el adsl
saludos y gracias

---

### Post by dekomen on 2010-08-08
Buenas, busque que era lo que me pasaba que no reconocia el modem y creo que lo solucione. ahora cuando ecribo en el prompt "sudo wvdial" me sale el siguiente error

--> Modem initialized.

--> Idle Seconds = 3000, disabling automatic reconnect.

--> Sending: ATD*99#

--> Waiting for carrier.
ATD*99#
ERROR

--> Invalid dial command.

--> Disconnecting at Sun Aug  8 13:30:44 2010

Que puede ser lo que tengo mal en el wvdial.conf? 
espero respuesta gracias

---

### Post by asterix77 on 2010-08-09
Hola Dekomen

El post es un tanto antiguo, por lo que la forma en que me he conectado ahora a cambiado.

Ahora me conecto más facilmente a través de la aplicación Vodafone-Mobile-Connect-Card-Driver.

Te dejo el link para que descargues 3 paquetes que debes instalar (me da la impresión que wvdial no se ejecuta porque falta el usb-modeswitch en tu caso)

[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

Debes escoger tu distro (me imagino ubuntu), ecoger tu arquitectura (32 ó 64 bit), y descargar   ozerocdoff,   usb-modeswitch, y finalmente vodafone-mobile-connect. Este último debes instalarlo al final.

Tras la instalación te aparecerá un ícono en Aplicaciones ----->Internet -------> Vodafone MobileConnect; tras abrirse por primera vez, te consultará datos para saber quien es tu proveedor de servicios, solo tienes que clicar y listo.

Eso si, no sé porqué solo me funciona cuando conecto el modem antes de arrancar el sistema, pero bueeeeee.....


Saludos y comenta como te va.

---

