---
title: "instalar placa tv pinacle 50i"
date: 2009-04-07
forum: Hardware
---

### Post by jesucristo7 on 2009-04-07
Como configuro la placa de tv pinacle 50i en ubuntu. Gracias.-

---

### Post by pablo.s on 2009-04-07
Se empieza escribiendo en una terminal

lspci

Y pegando en un nuevo mensaje lo que te devuelve.

---

### Post by jesucristo7 on 2009-04-07
gracias pablo...la seguimos...saludos

---

### Post by jesucristo7 on 2009-04-07
Esto me sale con lspci

marcelo@Pc:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
marcelo@Pc:~$

---

### Post by pablo.s on 2009-04-07
En ubuntu ar hay un [tutorial]("http://ubuntu-ar.org/node/122") para configurar
una tarjeta similar. En tu caso tendrias que cambiar
algunos parametros.
Por ejemplo: En lugar de saa7134 cambia por
saa7135
En lugar de card=3 pones card=77.

Veremos si hay algún suceso. Para probar si
sintoniza está el programa tvtime.

---

### Post by faktorqm on 2009-04-08
Una unica observacion, que no se si es maña mia o el tutorial ese es viejo, pero en el paso 4, lo que estas haciendo es decirle al kernel de linux que levante el modulo con esa opcion cuando arranca, pero yo lo hago directamente desde el archivo /etc/modules. Si te funciona, y cuando reinicias te deja de funcionar la placa, postea asi vemos esa posibilidad. Salu2!

---

### Post by jesucristo7 on 2009-04-08
Si todo bien pero donde cambio esos parametros?

---

### Post by jesucristo7 on 2009-04-08
esto les dice algo?

marcelo@Pc:~$ dmesg|grep saa713
[   42.908256] saa7130/34: v4l2 driver version 0.2.14 loaded
[   42.908344] saa7133[0]: found at 0000:01:01.0, rev: 208, irq: 21, latency: 32, mmio: 0xff8ff800
[   42.908352] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 40i/50i/110i (saa7133) [card=77,autodetected]
[   42.908369] saa7133[0]: board init: gpio is 200c000
[   43.048285] ir-kbd-i2c: Pinnacle PCTV detected at i2c-2/2-0047/ir0 [saa7133[0]]
[   43.079840] saa7133[0]: i2c eeprom 00: bd 11 2e 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   43.079855] saa7133[0]: i2c eeprom 10: ff e0 60 02 ff 20 ff ff ff ff ff ff ff ff ff ff
[   43.079866] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 30 98 ff 00 a0 ff 22 00 c2
[   43.079878] saa7133[0]: i2c eeprom 30: 96 ff 03 30 15 01 ff ff 0c 22 17 76 03 22 9d 5e
[   43.079889] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.079901] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.079912] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.079923] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.235600] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[   43.545975] saa7133[0]: registered device video0 [v4l2]
[   43.546007] saa7133[0]: registered device vbi0
[   43.546032] saa7133[0]: registered device radio0
[   43.598904] saa7134 ALSA driver for DMA sound loaded
[   43.598941] saa7133[0]/alsa: saa7133[0] at 0xff8ff800 irq 21 registered as card -2
marcelo@Pc:~$

---

### Post by jesucristo7 on 2009-04-08
No se como seguir, alguien que me de una mano, por favor.
Gracias.-

---

### Post by josecuervo86 on 2009-04-08
Bueno, proba poner esto en la terminal Y ver que pasa:

```
 modprobe saa7133 card=77
```

Estoy buscando pero no encuentro demasiado ;)

---

### Post by pablo.s on 2009-04-08
Te recomiendo instalar un programa para
sintonizar canales

sudo apt-get install scantv tvtime me-tv

y todas las dependencias. Paralelamente vas
probando si envia señal de tv. Por supuesto
que tendrás que conectar previamente el 
cable coaxil que te da la señal de antena o 
de cable.

Saludos.

---

### Post by josecuervo86 on 2009-04-08
Por si no leiste, antes que nada proba esto:

```
 modprobe saa7133 card=77
``` 

Si no va, proba este otro:

```
 modprobe saa7133 card=77 tuner=1
``` 

Aca te dejo un par de tutos que encontre que no son especificos de tu placa, pero te pueden guiar sabiendo que usas **saa7133** y **card 77**.

Antes que nada una aclaración, no se si ya lo sabes, pero cuando te dan una serie de codigos como los que te tire arriba, los tenes que escribir en una terminal.

Paso a linkearte los tutos:

Este supuestamente es general para las placas 713x, donde x es un numero cualquiera (en portugues): [http://ubuntuforum-br.org/index.php?topic=38955.0]("http://ubuntuforum-br.org/index.php?topic=38955.0")

Este es para saa7134, pero cambiando los parametros por saa7133 tendria que andar (en español): [http://www.forosuse.org/forosuse/printthread.php?t=18355]("http://www.forosuse.org/forosuse/printthread.php?t=18355")

Este es similar al primero, pero un poco modificado, tal vez te sirva (en rumano!! vos solo dale bola a los comandos de consola, jeje): [http://forum.ubuntu.ro/viewtopic.php?id=2406]("http://forum.ubuntu.ro/viewtopic.php?id=2406")

Este tuto esta completisimo, pero es para saa7134, de vuelta, creo que cambiandole los parametros por los tuyos tendria que andar (en español): [http://www.ubuntu-es.org/index.php?q=node/89351]("http://www.ubuntu-es.org/index.php?q=node/89351")

El ultimo! tambien para saa7134, incorpora algunos comandos que te convendria probar (en shileno, jeje): [http://kubuntuchile.wordpress.com/2006/06/19/tip-instalar-targeta-de-tv-pctronix/]("http://kubuntuchile.wordpress.com/2006/06/19/tip-instalar-targeta-de-tv-pctronix/")


Probalos, tomate tu tiempo, y si ninguno te anduvo, le vamos a buscar la vuelta.

Tengo una Users (si, una porqueria) en donde los flacos configuran la misma placa que tenes vos, pero siguen otros pasos. Por que no te la pongo como primera opcion? porque tambien es para saa7134! Me llama mucho la atención el cambio de esta a saa7133, ya que saa7134 esta mucho mas difundido y esta lleno de info en la red.

Avisa si alguno te funciono!!

Suerte

---

### Post by infernus92 on 2009-04-09
che... por favor... a mi me hicieron lo mismo cuando apenas empece... es recien iniciado... hablen con terminos simples... y expliquen cosas que par muchos son obvias...
como editar un archivo... o donde esta el terminal...
no se si cuesta mucho... pero al principio marca mucho la diferencia entre poder hacer algo y no tener idea de donde estas parado...

---

### Post by josecuervo86 on 2009-04-09
[QUOTE=jesucristo7]marcelo@Pc:~$ dmesg|grep saa713
[ 42.908256] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 42.908344] saa7133[0]: found at 0000:01:01.0, rev: 208, irq: 21, latency: 32, mmio: 0xff8ff800
[ 42.908352] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 40i/50i/110i (saa7133) [card=77,autodetected]
[ 42.908369] saa7133[0]: board init: gpio is 200c000
[ 43.048285] ir-kbd-i2c: Pinnacle PCTV detected at i2c-2/2-0047/ir0 [saa7133[0]]
[ 43.079840] saa7133[0]: i2c eeprom 00: bd 11 2e 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[ 43.079855] saa7133[0]: i2c eeprom 10: ff e0 60 02 ff 20 ff ff ff ff ff ff ff ff ff ff
[ 43.079866] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 30 98 ff 00 a0 ff 22 00 c2
[ 43.079878] saa7133[0]: i2c eeprom 30: 96 ff 03 30 15 01 ff ff 0c 22 17 76 03 22 9d 5e
[ 43.079889] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.079901] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.079912] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.079923] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 43.235600] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[ 43.545975] saa7133[0]: registered device video0 [v4l2]
[ 43.546007] saa7133[0]: registered device vbi0
[ 43.546032] saa7133[0]: registered device radio0
[ 43.598904] saa7134 ALSA driver for DMA sound loaded
[ 43.598941] saa7133[0]/alsa: saa7133[0] at 0xff8ff800 irq 21 registered as card -2
marcelo@Pc:~$[/QUOTE]

Si posteo este resultado, es por que sabe donde esta la terminal y como se usa ;)

---

### Post by jesucristo7 on 2009-04-10
hola pablo me sale esto, todavia no vi los tuto...despues te cuento.-

marcelo@Pc:~$ modprobe saa7133 card=77 tuner=1
FATAL: Module saa7133 not found.
marcelo@Pc:~$

---

### Post by josecuervo86 on 2009-04-10
Soy jose :P

Y el otro los probaste (sin tuner)??

---

### Post by jesucristo7 on 2009-04-13
si pablo lo probe y me sale FATAL, ahora veo las tuto, gracias.-

---

### Post by josecuervo86 on 2009-04-13
che y si probas poniendo 7134? con probar no perdes nada. Por que segun veo no te encuentra al saa7133. Es medio raro esto. En todos lados vi referencias a esta placa como 7134

---

### Post by faktorqm on 2009-04-13
> **jesucristo7 said:**
> esto les dice algo?

marcelo@Pc:~$ dmesg|grep saa713
[   42.908256] saa7130/34: v4l2 driver version 0.2.14 loaded
[   42.908344] saa7133[0]: found at 0000:01:01.0, rev: 208, irq: 21, latency: 32, mmio: 0xff8ff800
[   42.908352] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 40i/50i/110i (saa7133) [card=77,autodetected]
[   42.908369] saa7133[0]: board init: gpio is 200c000
[   43.048285] ir-kbd-i2c: Pinnacle PCTV detected at i2c-2/2-0047/ir0 [saa7133[0]]
[   43.079840] saa7133[0]: i2c eeprom 00: bd 11 2e 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   43.079855] saa7133[0]: i2c eeprom 10: ff e0 60 02 ff 20 ff ff ff ff ff ff ff ff ff ff
[   43.079866] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 30 98 ff 00 a0 ff 22 00 c2
[   43.079878] saa7133[0]: i2c eeprom 30: 96 ff 03 30 15 01 ff ff 0c 22 17 76 03 22 9d 5e
[   43.079889] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.079901] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.079912] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.079923] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.235600] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[   43.545975] saa7133[0]: registered device video0 [v4l2]
[   43.546007] saa7133[0]: registered device vbi0
[   43.546032] saa7133[0]: registered device radio0
[   43.598904] saa7134 ALSA driver for DMA sound loaded
[   43.598941] saa7133[0]/alsa: saa7133[0] at 0xff8ff800 irq 21 registered as card -2
marcelo@Pc:~$

Hola, ya esta amigo, no le des mas vueltas, no se que mas queres, ahi te dice que cargo bien el driver de video y el de sonido. Lo unico que tenes que hacer ahora es correr el tvtime o el que mas te guste y poner como dispositivo /dev/video0 o si tenes webcam /dev/video1 y empezar a sintonizar canales.

comenta como te fue salu2!

---

### Post by jesucristo7 on 2009-04-16
> **faktorqm said:**
> Hola, ya esta amigo, no le des mas vueltas, no se que mas queres, ahi te dice que cargo bien el driver de video y el de sonido. Lo unico que tenes que hacer ahora es correr el tvtime o el que mas te guste y poner como dispositivo /dev/video0 o si tenes webcam /dev/video1 y empezar a sintonizar canales.

comenta como te fue salu2!

Pero donde pongo como dispositivo /dev/video0?
Todavia no la puedo hacer andar!!!!

---

### Post by pablo.s on 2009-04-16
> **jesucristo7 said:**
> Pero donde pongo como dispositivo /dev/video0?

Momento, un poco de calma primero.
En una terminal escribí esto:

[COLOR=SeaGreen]**sudo apt-get install tvtime me-tv**[/COLOR]

ahora, segundo paso, sin cerrar la
terminal, escribi tvtime.

Te va a pedir que le dés información
de norma (PAL-N) y la parte del mundo
donde te encontras (custom)

--Aparece señal? Si aparece con las
teclas de arriba y abajo cambias de
canal.

--No aparece señal? Tenés que cambiar
en el menú que aparece al principio
de video0 a video1

---

### Post by AndresCastiblanco on 2009-04-28
> **pablo.s said:**
> Momento, un poco de calma primero.
En una terminal escribí esto:

[COLOR=SeaGreen]**sudo apt-get install tvtime me-tv**[/COLOR]

ahora, segundo paso, sin cerrar la
terminal, escribi tvtime.

Te va a pedir que le dés información
de norma (PAL-N) y la parte del mundo
donde te encontras (custom)

--Aparece señal? Si aparece con las
teclas de arriba y abajo cambias de
canal.

--No aparece señal? Tenés que cambiar
en el menú que aparece al principio
de video0 a video1


Gracias pablo.s tambien tengo una Pinnacle y puedo ver tv con el kdetv y ahora que explicaste lo del tvtime lo probe y me funciono, pude ver todos los canales, pero el sonido esta muerto y he buscado mucho y no he podido solucionarlo. 

Si sirve de algo posteo estos:

andres@Casti:~$ dmesg | grep Pinnacle
[   55.989870] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 40i/50i/11
0i (saa7133) [card=77,autodetected]
[   56.099765] input: Pinnacle PCTV as /devices/virtual/input/input5
[   56.155668] ir-kbd-i2c: Pinnacle PCTV detected at i2c-0/0-0047/ir0 [saa7133[0
]]
[ 1626.591732] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[ 1626.701146] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[ 2947.618587] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[ 2947.728020] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[ 3099.136953] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[ 3099.241750] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[ 4140.704029] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[ 4140.814841] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[ 4905.149633] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[ 4905.257458] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[ 5733.232476] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[ 5733.340298] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[ 8567.372008] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[ 8567.479835] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[ 9423.521530] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[ 9423.631876] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[10860.932449] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[10861.040274] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[11251.685499] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[11251.797291] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[12128.437726] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[12128.545552] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[13343.447772] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[13343.555607] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[13378.922488] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[13379.030313] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[13752.814739] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[13752.922565] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[15027.540359] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[15027.648183] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[15491.115793] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[15491.219625] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[16401.318030] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[16401.425857] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[17550.825848] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[17550.933672] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[19524.626624] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[19524.734448] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[19550.828315] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[19550.936139] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[21571.337667] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[21571.445490] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[21990.049574] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[21990.157372] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[22266.642914] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[22266.750739] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[22909.624650] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[22909.732476] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[27251.932845] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[27252.040673] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[27266.920643] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[27267.028514] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[28732.310384] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[28732.418305] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[28977.262844] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[28977.370670] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[30207.352537] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[30207.456375] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[30222.340336] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[30222.448162] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[30319.503443] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[30319.611291] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[30704.597606] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[30704.705435] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[32439.384333] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[32439.492159] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[32695.514744] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[32695.622567] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[33476.924952] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[33477.032788] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[33884.670536] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[33884.778370] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[34211.962036] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[34212.065871] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[34283.051246] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=1
[34283.161249] Pinnacle PCTV: unknown key: key=0x19 raw=0x19 down=0
[35715.066881] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[35715.174703] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[37463.906915] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[37464.014739] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0
[37992.900713] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=1
[37993.008537] Pinnacle PCTV: unknown key: key=0x63 raw=0x63 down=0


andres@Casti:~$ dmesg|grep saa71
[   55.989808] saa7130/34: v4l2 driver version 0.2.14 loaded
[   55.989864] saa7133[0]: found at 0000:04:01.0, rev: 209, irq: 19, latency: 64, mmio: 0xe6000000
[   55.989870] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 40i/50i/110i (saa7133) [card=77,autodetected]
[   55.989879] saa7133[0]: board init: gpio is 200c000
[   56.155668] ir-kbd-i2c: Pinnacle PCTV detected at i2c-0/0-0047/ir0 [saa7133[0]]
[   56.187561] saa7133[0]: i2c eeprom 00: bd 11 2e 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   56.187569] saa7133[0]: i2c eeprom 10: ff e0 60 02 ff 20 ff ff ff ff ff ff ff ff ff ff
[   56.187576] saa7133[0]: i2c eeprom 20: 01 2c 01 23 23 01 04 30 98 ff 00 e2 ff 22 00 c2
[   56.187583] saa7133[0]: i2c eeprom 30: 96 ff 03 30 15 01 ff 15 0e 6c a3 ea 03 c1 5a c6
[   56.187590] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.187597] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.187603] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.187610] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   56.307389] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   56.621682] saa7133[0]: registered device video0 [v4l2]
[   56.621699] saa7133[0]: registered device vbi0
[   56.621714] saa7133[0]: registered device radio0
[   56.709864] saa7134 ALSA driver for DMA sound loaded
[   56.709884] saa7133[0]/alsa: saa7133[0] at 0xe6000000 irq 19 registered as card -2
andres@Casti:~$          


Gracias por su ayuda

Casti:guitar:

---

### Post by pablo.s on 2009-04-28
Hola Andrés:
Teoricamente el sonido lo maneja
internamente, creo que vi en la placa
sintonizadora de mi padre que tiene
un jack stereo de salida, al estilo mini-
plug.
Te fijaste en el mezclador de audio
si no te habilita un control de volumen
de la placa sintonizadora?
No tengo muy fresco el tema, pero
a mi me habia pasado eso hace un par
de años cuando configuré la placa esta
que te cuento y habia que subirle el
volumen en el mezclador, fijandose que
debe aparecer separado del mezclador
de la placa de sonido.
Saludos.

---

### Post by AndresCastiblanco on 2009-04-29
Gracias por responder, te cuento que el miniplug que tiene la tarjeta es para el control remoto por infrarrojo.

Acerca del mezclador de audio, tienes razon en el Kmix aparecen dos tarjetas de audio y una es precisamente la SAA7134, que corresponde a la placa capturadora de TV, ya le habilite las entradas en el Kmix y subi el volumen abri el kdetv y fui a Preferencias/Configurar kdetv y en sonido donde dice "Seleccione el controlador para el mezclador: Complemento de mezclador ALSA y hay un boton Configurar el mezclador....alli pude escoger el mezclador SAA7134 pero en los Elementos del mezclador no aparece nada y le doy Aplicar y cuando lo vuelvo a abrir muestra el HDA Intel, es decir, no toma el mezclador de la Tarjetea de TV sino el de la placa principal del PC.

Hay alguna manera de solucionar esto?

Muchas gracias por su ayuda, es muv valiosa.

---

### Post by sanflores on 2010-11-02
Bueno, ya se que este tema es VIEJISIMO pero tengo el mismo problema, solo que llegue un poco mas lejos...

Misma placa que la mia, ubuntu 10.04 la autodetecta, y tengo video, agarra canales (Muchos, pero no TODOS), y no tengo sonido... salvo cuando tiro el comando:

tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

No me voy a rendir y si descubro la forma de hacerla andar... la publico por aca

---

