---
title: "[SOLUCIONADO] No me sale sonido 5.1"
date: 2009-06-16
forum: Hardware
---

### Post by dcorrea on 2009-06-16
hola a todos!!!
solicito su ayuda una vez más...
no he podido configurar mi equipo para lograr sonido 5.1 en mi ubuntu 9.4
Como lo puedo hacer?

Saludos.

---

### Post by radixs on 2009-06-16
Primero que nada debemos saber cual es tu tarjeta de sonido ;)
si no sabes cual esta ocupando tipea en la terminal un

lspci

---

### Post by dcorrea on 2009-06-16
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:00.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
02:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

---

### Post by radixs on 2009-06-16
Prueba con esta configuracion:

crea el archivo .asoundrc en tu /home

```
sudo gedit /home/tu usuario/.asoundrc
```

en el añade lo siguiente:

```
pcm.!default { 

type plug 

slave.pcm "surround51" 

slave.channels 6 

ttable.0.0 0.5 
ttable.1.1 0.5 
ttable.0.2 0.5 
ttable.1.3 0.5 
ttable.0.4 0.5 
ttable.1.4 0.5 
ttable.0.5 0.5 
ttable.1.5 0.5 

route_policy duplicate 

}
```

avisa si te sirve ;)

---

### Post by dcorrea on 2009-06-16
lo acabo de hacer...
y sigue igual...

:(

---

### Post by Eddy_Kine on 2009-06-16
Sorry pero ¿Te fuiste al control de volumen y verificaste que estuvieran activados todos los parlantes?.. partamos por ahi y nos cuentas ;)

Adjunto archivo de muestra



PD: En hardware al un tip publicado por mi en donde puedes detallar tu hardware, hazlo y tenlo a mano por cualquier consulta

---

### Post by dcorrea on 2009-06-17
uhhh ahi sonaron casi todos!!!
solo me falta el subwoofer seguire investigando....
muchas gracias!!!

---

### Post by Carlos C on 2009-06-17
Hay que tener en cuenta lo que dice Eddy_Kine. A veces partimos por asumir problemas complejos, cuando muchas veces la solución pasa por partir por lo básico. Lo comento porque a mi también se me olvida eso muchas veces jeje.

---

### Post by dcorrea on 2009-06-17
Totalmente de acuerdo contigo Carlos C
....pa la proxima sere mas cuidadoso...antes de preguntar...:redface:
ya esta todo OK
Solucionado!!! una vez más !!

---

### Post by Eddy_Kine on 2009-06-23
No quiero revivir el post ya solucionado, pero en un inicio cuando instale Jaunty no tenia idea de por qué no se me oían los 5.1... y de pronto recordé que debía configurarlo :D
Mi profesor del colegio decia: "No hay preguntas tontas, solo tontos que no preguntan..." Me rei mucho, pero al fin entendí que entre mas se estudia e investiga, más preguntas surgen.
:KS

---

### Post by sacdker on 2010-01-31
hola bueno yo si tengo un problema tengo soundwofer solo suenan las dos traseras y ya no se como hacer mi tarjeta de sonido es una realteck integrada a una tarjeta madre asrock wolfdale1333 espero la respuesta gracias

---

### Post by mikiman1971 on 2010-06-03
Hola a todos,
he intentado la solución que habeis dado aquí, en este caso para la versió 10.04, pero sigue sin funcionar.

Según el terminal, después de crear .asoundrc:

miquel@miquel-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
02:04.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
---------------

He tocado y retocado la configuración del sonido pero no hay manera...

Gracias por la ayuda.

---

