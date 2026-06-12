---
title: "Problema de conexion 3G con dispositivo ZTE"
date: 2012-12-30
forum: Hardware
---

### Post by yellowpaper on 2012-12-30
Hola muchachos , estoy acá para preguntarles sobre un problemita que tengo con la configuración del pendorchito ZTE de movistar.

La verdad es que no se que modelo en particular es , es muy parecido a este [http://articulo.mercadolibre.com.co/MCO-403493107-modem-zte-mf-190-de-claro-comcel-_JM](http://articulo.mercadolibre.com.co/MCO-403493107-modem-zte-mf-190-de-claro-comcel-_JM) pero de movistar y con la lucesita en la parte de atras no arriba.lsub da como pista que el modem usb es el ID 19d2:0124 ZTE WCDMA Technologies MSM . Dicho esto paso a comentar:

El modem son 3 cosas al mismo tiempo por lo que pude leer , un CDROM virtual , un dispositivo de almacenamiento masivo y un modem 3g ( a mi entender un celular pero sin pantalla).

La primera vez que se conecta , Linux lo trata como un CDROM a lo cual lo expulso y el pendorchito usb pasa a ser un modem 3G


dmesg cuando lo conecto 

```

[ 3105.600695] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 3105.600747] option 1-1:1.0: device disconnected
[ 3105.601220] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 3105.601274] option 1-1:1.1: device disconnected
[ 3105.602860] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 3105.602913] option 1-1:1.2: device disconnected
[ 3105.603245] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[ 3105.603291] option 1-1:1.3: device disconnected
[ 3105.603535] option: option_instat_callback: error -108
[ 3105.603645] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[ 3105.603682] option 1-1:1.4: device disconnected
[ 3110.912323] usb 1-1: new high-speed USB device number 12 using ehci_hcd
[ 3111.052804] scsi16 : usb-storage 1-1:1.0
[ 3112.054523] scsi 16:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 3112.059973] sr1: scsi-1 drive
[ 3112.060368] sr 16:0:0:0: Attached scsi CD-ROM sr1
[ 3112.060738] sr 16:0:0:0: Attached scsi generic sg3 type 5

```dmesg despues de expulsar el CDROM virtual

```

[ 3230.496211] usb 1-1: new high-speed USB device number 13 using ehci_hcd
[ 3230.634834] option 1-1:1.0: GSM modem (1-port) converter detected
[ 3230.635044] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 3230.635259] option 1-1:1.1: GSM modem (1-port) converter detected
[ 3230.635541] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 3230.635763] option 1-1:1.2: GSM modem (1-port) converter detected
[ 3230.635988] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[ 3230.636235] option 1-1:1.3: GSM modem (1-port) converter detected
[ 3230.636422] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3
[ 3230.636638] option 1-1:1.4: GSM modem (1-port) converter detected
[ 3230.636953] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB4
[ 3230.637595] scsi17 : usb-storage 1-1:1.6
[ 3231.637690] scsi 17:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 3231.638525] scsi 17:0:0:1: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[ 3231.642205] sr1: scsi-1 drive
[ 3231.642553] sr 17:0:0:0: Attached scsi CD-ROM sr1
[ 3231.644820] sr 17:0:0:0: Attached scsi generic sg3 type 5
[ 3231.648271] sd 17:0:0:1: Attached scsi generic sg4 type 0
[ 3231.654060] sd 17:0:0:1: [sdc] Attached SCSI removable disk

```Bueno hasta aca todos felices , incluso si me fijo en la applet de conexiones me sale 
"Banda ancha movil (con bastante señal y desactivado)"
"Movistar predeterminado"

Si la elijo para conectarme no se conecta y supongo que es por que el usuario y contraseña predeterminado esta mal.

Ok.. para no usar el applet de ubuntu  , utilizo wvdial.
Despues de buscar y buscar llegué a la siguiente configuracion de wvidal.conf

```

[Dialer up]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
APN = internet.gprs.unifon.com.ar
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB1
Username = internet
Password = internet
Carrier Check = no
Baud = 9600

```y ejecuto wvdial up

```

-> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 7200000  --->En este momento mi corazón galopa feliz
--> Carrier detected.  Starting PPP immediately.  -->Se me esboza una sonrisa
--> Starting pppd at saraza -->Esa sonrisa es una carcajada
--> Pid of pppd: 4numeros
--> Using interface ppp0  
--> Disconnecting at saracatunga -->La sonrisa y la carcajada se borran de un plumazo
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
--> Disconnecting at sungundrule

```Y lo gracioso del tema es que despues para que se repita esto

```

ATDT*99#
CONNECT 7200000 

```Tengo que desconectar el modem y volverlo a conectar y seguir todos esos pasos...
Supongo que es un problema de configuración por eso pregunto si alguno de ustedes tiene el mismo modem , y si puede diganme como lo hicieron andar...

SUERTE!

---

