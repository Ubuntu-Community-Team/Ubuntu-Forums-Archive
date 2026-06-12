---
title: "Otra mas...Ahora es el Audio"
date: 2009-07-07
forum: Hardware
---

### Post by varcom on 2009-07-07
Bueno, el tema es que colocando el comando aplay -l, sale que no se encontro tarjeta de sonido.
 
La tarjeta de sonido es Onboard, la mather es una Biostar P4M80-M4, y sino me equivoco la tarjeta de sonido onboard es una realteck  ALC655.
AC97 sound Codec
 
Bueno si pueden ayudarme les agradecere muchisimo.
Estoy aprendiendo, y parece que de la forma mas dificil, a fallas no mas.
 
Gracias.

---

### Post by guillermolisi on 2009-07-08
> **varcom said:**
> Bueno, el tema es que colocando el comando aplay -l, sale que no se encontro tarjeta de sonido.
 
La tarjeta de sonido es Onboard, la mather es una Biostar P4M80-M4, y sino me equivoco la tarjeta de sonido onboard es una realteck  ALC655.
AC97 sound Codec
 
Bueno si pueden ayudarme les agradecere muchisimo.
Estoy aprendiendo, y parece que de la forma mas dificil, a fallas no mas.
 
Gracias.

Abri una consola/terminal e ingresa el comando lspci asi vemos como reconoce, si es que lo hace, a la placa de audio tu SO.

Mostranos el resultado.

---

### Post by varcom on 2009-07-15
> **guillermolisi said:**
> Abri una consola/terminal e ingresa el comando lspci asi vemos como reconoce, si es que lo hace, a la placa de audio tu SO.

Mostranos el resultado.

No la detecta ni por asomo...
para mi que aunque es ONboard , se me cayo en el traslado..jajaja
Esto es lo que aparece al tirar el comando:
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

Buneo si alguien me puede dar una mano, desde ya gracias.

---

### Post by guillermolisi on 2009-07-15
Si, por lo menos lo que resulta de la salida del lspci es que no hay ningun componente de audio (como para que sea reconocido).

La placa de audio es la que vos decis (confirmado leyendo el manual de la motherboard) asi que se me ocurre, como para agotar instancias, que revises la configuracion del BIOS en busca de que la placa de audio no se encuentre deshabilitada.

Por casualidad la probaste con otro sistema operativo con exito ?
Alguna vez anduvo el audio ?

---

