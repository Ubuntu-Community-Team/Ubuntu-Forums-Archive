---
title: "Huawei e660A - Modem 3g"
date: 2008-08-25
forum: Hardware
---

### Post by nahuelb on 2008-08-25
Hola yo soy nahuel estube en las jornadas que se desarrollarn en la ub, estube hablando con Factor y el problema mio es que tengo una placa pcmcia huawey e660a y no puedo hacerla andar en ubuntu 8.04.
Les mando unos log para que vean que es lo que reconoce el sistema.

Bueno desde ya agradezco su ayuda y los invito a ver las fotos que saque en las jornadas en [www.fotoreport.com.ar](www.fotoreport.com.ar) 

LA tarjeta pcmecia esta colocada pero ubunto no reconoce nada, al desconectarla el log me pone esto:
---------------------------------------------------------
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.669098] usb 6-1: USB disconnect, address 3
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.669555] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.669740] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.669921] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.669935] airprime 6-1:1.0: device disconnected
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.670243] airprime ttyUSB3: airprime converter now disconnected from ttyUSB3
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.670422] airprime ttyUSB4: airprime converter now disconnected from ttyUSB4
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.670599] airprime ttyUSB5: airprime converter now disconnected from ttyUSB5
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.670613] airprime 6-1:1.1: device disconnected
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.697719] pccard: card ejected from slot 0
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.732502] ohci_hcd 0000:05:00.0: remove, state 0
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.732515] usb usb6: USB disconnect, address 1
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.732761] ohci_hcd 0000:05:00.0: USB bus 6 deregistered
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.732808] ACPI: PCI interrupt for device 0000:05:00.0 disabled
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.732862] ohci_hcd 0000:05:00.1: remove, state 0
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.732869] usb usb7: USB disconnect, address 1
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.733065] ohci_hcd 0000:05:00.1: USB bus 7 deregistered
Aug 24 20:58:38 nahuel-laptop kernel: [ 4182.733093] ACPI: PCI interrupt for device 0000:05:00.1 disabled

-------------------------------------------------------------
Al conectarla nuevamente el log me registra esto: 

Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.210750] pccard: CardBus card inserted into slot 0
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.211094] PCI: Enabling device 0000:05:00.0 (0000 -> 0002)
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.211102] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.211129] ohci_hcd 0000:05:00.0: OHCI Host Controller
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.211162] ohci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 6
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.211179] ohci_hcd 0000:05:00.0: irq 16, io mem 0x68000000
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.313150] usb usb6: configuration #1 chosen from 1 choice
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.313561] hub 6-0:1.0: USB hub found
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.313804] hub 6-0:1.0: 1 port detected
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.426884] PCI: Enabling device 0000:05:00.1 (0000 -> 0002)
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.426895] ACPI: PCI Interrupt 0000:05:00.1[B] -> GSI 16 (level, low) -> IRQ 16
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.426924] ohci_hcd 0000:05:00.1: OHCI Host Controller
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.426948] ohci_hcd 0000:05:00.1: new USB bus registered, assigned bus number 7
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.426964] ohci_hcd 0000:05:00.1: irq 16, io mem 0x68001000
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.512388] usb usb7: configuration #1 chosen from 1 choice
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.512872] hub 7-0:1.0: USB hub found
Aug 24 21:01:10 nahuel-laptop kernel: [ 4334.513118] hub 7-0:1.0: 1 port detected
Aug 24 21:01:15 nahuel-laptop kernel: [ 4338.933798] usb 6-1: new full speed USB device using ohci_hcd and address 2
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.145695] usb 6-1: configuration #1 chosen from 1 choice
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.177537] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.178377] usb 6-1: USB disconnect, address 2
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.672933] usb 6-1: new full speed USB device using ohci_hcd and address 3
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.884944] usb 6-1: configuration #1 chosen from 1 choice
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.908519] usb-storage: probe of 6-1:1.0 failed with error -5
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.908542] airprime 6-1:1.0: GSM modem (1-port) converter detected
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.910026] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.920787] usb-storage: probe of 6-1:1.1 failed with error -5
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.920810] airprime 6-1:1.1: GSM modem (1-port) converter detected
Aug 24 21:01:15 nahuel-laptop kernel: [ 4339.920974] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
Aug 24 21:01:16 nahuel-laptop kernel: [ 4339.984631] scsi9 : SCSI emulation for USB Mass Storage devices
Aug 24 21:01:21 nahuel-laptop kernel: [ 4345.003679] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Aug 24 21:01:21 nahuel-laptop kernel: [ 4345.080577] sr1: scsi-1 drive
Aug 24 21:01:21 nahuel-laptop kernel: [ 4345.080684] sr 9:0:0:0: Attached scsi generic sg2 type 5
-------------------------------------------------------------------------

---

### Post by faktorqm on 2008-08-25
Bueno, le pediria el favor a algun admin que abra un nuevo thread con el post del Huawei E660A, antes que nada. 

Te cuento, estuve buscando a ver que pasaba con este tipo de aparatos y nada, parece que ya esta todo medio cocinado el tema. (yo pense que era mas dificil...)

Hay un programa que se llama wader (asistente para conexiones 3G) pero no soporta el modelo tuyo oficialmente. es decir, capaz te anda capaz no. 

Aca [http://www.nabble.com/-ANNOUNCE--ModemManager-(for-GSM-and-CDMA)-td18756782.html](http://www.nabble.com/-ANNOUNCE--ModemManager-(for-GSM-and-CDMA)-td18756782.html) dice que van a hacer algo tipo network manager pero que se va a llamar modem manager (no lo lei todo)pero no importa por que de todas maneras no es driver, sino un programa que controla.

Aca hay un chabon que lo configuro con gnome-ppp (OJO! NO es tu modelo de modem, pero te lo pongo para que veas la configuracion y de ultima lo pruebes, total es gratis...) [http://www.itspax.com.br/tlog/index.php?q=2007/12/configurando-claro-3g-hsdpa-usb-no.html](http://www.itspax.com.br/tlog/index.php?q=2007/12/configurando-claro-3g-hsdpa-usb-no.html)

Despues esta wvdial, esto es lo que usa en realidad gnome-ppp, es decir, gnome-ppp es un frontend de wvdial. [http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)

Ahora bien, existe un programa que se llama "Vodafone Mobile Connect Card driver" [http://en.wikipedia.org/wiki/Vodafone_Mobile_Connect_Card_driver_for_Linux](http://en.wikipedia.org/wiki/Vodafone_Mobile_Connect_Card_driver_for_Linux)
y éste si soporta tu placa. 

COMENTARIO APARTE: Vodafone es una empresa de España, no se como es el tema de configuracion de parametros para Argentina... Yo supongo que vas a tener que terminar llamando a cti para preguntarles...

instalador: [https://forge.betavine.net/frs/download.php/269/vodafone-mobile-connect-card-driver-for-linux-2.0.beta3-ALL-i386-installer.run](https://forge.betavine.net/frs/download.php/269/vodafone-mobile-connect-card-driver-for-linux-2.0.beta3-ALL-i386-installer.run)

El instalador funciona tanto para UBUNTU 7.10 como para UBUNTU 8.4, NO ASI PARA 64 bits, te tenes que bajar otro archivo. (pagina con los instaladores: [https://forge.betavine.net/frs/?group_id=12&release_id=116](https://forge.betavine.net/frs/?group_id=12&release_id=116))
Tenes que tener conexion a internet y los paquetes actualizados al dia. (Tambien tenes que tener el repositorio ***UNIVERSE* ACTIVADO**)
Entonces una vez que te aseguras de tener todo esto, vas a aplicaciones -> accesorios -> terminal y haces:

```
chmod +x vodafone-mobile-connect-card-driver-for-linux-2.0.beta3-ALL-i386-installer.run
```
Eso es para darle permiso de ejecucion al instalador, ahora lo ejecutamos: 

```
chmod +x vodafone-mobile-connect-card-driver-for-linux-2.0.beta3-ALL-i386-installer.run
```

Cuando terminas deberias ir a Aplicaciones -> Internet -> vodafone-mobile-connect-card-driver-for-linux y bueno, de ahi en mas no te puedo ayudar mas hasta que no lo hagas y me postees screenshots si tenes algun problema. suerte con eso y salu2!!!

EDITO: En la lista un chabon se queria conectar con un 3G y aca [http://www.taringa.net/posts/info/1221276/huawei-e226--con-claro-arg-funcionando-en-ubuntu.html](http://www.taringa.net/posts/info/1221276/huawei-e226--con-claro-arg-funcionando-en-ubuntu.html) encontre los parametros de cti para argentina, asi que ni siquiera tenes que llamar. Sigo revisando el tema. Cualquier cosa que hayas encontrado y que pueda servir pasamelo. Salu2!

---

### Post by sajnox on 2008-08-25
> **faktorqm said:**
> Bueno, le pediria el favor a algun admin que abra un nuevo thread con el post del Huawei E660A, antes que nada. 



Hecho

---

