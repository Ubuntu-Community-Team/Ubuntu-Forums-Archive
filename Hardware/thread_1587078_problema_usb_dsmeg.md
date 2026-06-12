---
title: "problema usb dsmeg"
date: 2010-10-02
forum: Hardware
---

### Post by xtremox on 2010-10-02
siempre me sale este mismo error ubuntu 10.04 pero cuando booteo desde usb no pasa

alguna solucion?

xtremox@manuel-PC:~$ dmesg
 hub 1-5:1.0: over-current change on port 1
[ 1512.103324] hub 1-5:1.0: over-current change on port 1
[ 1512.359177] hub 1-5:1.0: over-current change on port 1
[ 1512.615148] hub 1-5:1.0: over-current change on port 1
[ 1512.871134] hub 1-5:1.0: over-current change on port 1
y asi un largo etc

:confused:

---

### Post by Carlos C on 2010-10-03
No me queda muy claro el problema, por favor danos más detalles ¿Qué tipo de hardware tienes conectado a tu usb cuando ocurre ese error? Cuando inicias desde un usb, te refieres a una unidad pendrive? Porque es posible es posible que la diferencia esté en que tengas conectado un disco duro externo cuando el error ocurre. Es algo que pasaba con un disco externo bastante antiguo que solía tener y me veía obligado a desconectarlo antes de iniciar el sistema.

---

### Post by manco1911 on 2010-10-03
Proba antes que anda hacer una actualizacion del sistema.
Con una actualizacion completa deberias solucionarlo si es un problema simple. 

De todas formas, has lo que te dice Carlos y danos un por mas de informacion. 

Tu hardware.
Cuando surge el problema. 
Antes pasaba?
Despues de que cambio empezo..

---

### Post by xtremox on 2010-10-06
> **manco1911 said:**
> Proba antes que anda hacer una actualizacion del sistema.
Con una actualizacion completa deberias solucionarlo si es un problema simple. 

De todas formas, has lo que te dice Carlos y danos un por mas de informacion. 

Tu hardware.
Cuando surge el problema. 
Antes pasaba?
Despues de que cambio empezo..

solo instale el lector sd empezo ah aparecer cuando boteo desde usb lo hago desde una tarjeta sd y no aparece el problema

ahora ise un sudo aptitude full-upgrade y se soluciono :)

el problema lo ocasionaba el lector de tarjetas :) yo pensaba que era el hub usb pero raro me parecia en la caja decia que era para linux :D pero el lector de tarjeta es el problematico :D

hardware
> xtremox@xtremox-desktop:~$ lsusb
Bus 002 Device 003: ID 0a48:3233 I/O Interconnect Multimedia Card Reader
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0471:084a Philips (mp4)
Bus 001 Device 006: ID 0079:0011 DragonRise Inc.(joystic y funcionando) 
Bus 001 Device 004: ID 0a48:6560 I/O Interconnect 
Bus 001 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> xtremox@xtremox-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 405] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
01:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

caracteristicas:

AMD SEMPROM 3000+ 1,6 GHZ, disco duro wester digital 250 gigas sata, ram 1 giga

---

