---
title: "Fotos pixeladas en pantalla wide"
date: 2009-08-24
forum: Hardware
---

### Post by stepiuvilkas on 2009-08-24
Tengo Ubuntu Jaunty,  cambié por un monitor wide, y tuve que configurar el **xorg.conf **y poner: 

Section “Monitor” 
Identifier “Generic Monitor” 
Option “DPMS” 
HorizSync 30-71 
VertRefresh 50-65 
EndSection 

De esta forma se ve bien,   sin embargo cuando entro a facebook las fotos se ven pixeladas, y los videos de youtube se ven entrecortados. 

Tienen idea cual puede ser el problema??? 

La placa de video es una generica integrada la placa madre.

Gracias

Stepiuvilkas

---

### Post by pablo.s on 2009-08-24
> **stepiuvilkas said:**
> La placa de video es una generica integrada la placa madre.

Si posteás lo que te devuelve
el comando
```
lspci
```en una terminal, vamos a poder
asesorarte de acuerdo a la
"genericidad" de la placa.

---

### Post by stepiuvilkas on 2009-08-25
Hola, ante todo gracias por responder.  Te paso lo que me devolvió el comando:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


> **pablo.s said:**
> Si posteás lo que te devuelve
el comando
```
lspci
```en una terminal, vamos a poder
asesorarte de acuerdo a la
"genericidad" de la placa.

---

### Post by stepiuvilkas on 2009-08-25
Hola, ante todo gracias por responder. El problema lo tengo para visualizar las fotos en Facebook,  y los videos de youtube, con el resto de las páginas no tengo problemas para ver las fotos.  Con Win XP se ve diez puntos también, asi que supongo que tengo algo mal en la configuración. 
 Te paso lo que me devolvió el comando:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by stepiuvilkas on 2009-08-31
Me respondo a mi mismo,  no la solución, sino la alternativa.  Despues de mucho buscar encontré que Ubuntu Jaunty tiene muchos problemas de compatibilidad con las placas de video integradas intel (yo tengo una Intel 82865G).  Hay algunos foros donde se publican soluciones pero yo no di pie con bola. Cansado de probar instalé Ubuntu 8.10 y todo solucionado. 
Muy muy decepcionado con Ubuntu Jaunty:(. Seguramente exista una alternativa a reinstalar otra versión anterior para solucionar el problema.  Pero es muy fastidioso perder tantas horas tratando de lograr compatibilidad con una placa super común.

Gracias


> **stepiuvilkas said:**
> Hola, ante todo gracias por responder. El problema lo tengo para visualizar las fotos en Facebook,  y los videos de youtube, con el resto de las páginas no tengo problemas para ver las fotos.  Con Win XP se ve diez puntos también, asi que supongo que tengo algo mal en la configuración. 
 Te paso lo que me devolvió el comando:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

