---
title: "Problemas con upgrade de Intrepid a Jaunty"
date: 2009-04-24
forum: Hardware
---

### Post by leonardomdq on 2009-04-24
Hola a todos, soy usuario novato de Ubuntu, en este momento estoy usando Intrepid y quise hacer el upgrade a Jaunty pero me fue mal :( 
Tengo una notebook HP Pavilion dvd6720la con chip de video Intel, aceleradora 3d.
Con Intrepid la maquina me va muy bien, pero con Jaunty todo lo contrario, cuando termine la instalacion me encontre con que las ventas al cerrarlas estaban lentas, y cuando voy a preferencias de apariencias --> efectos visuales no me deja activar modo normal o extras porque busca controladores y no los encuentra.
Estube googleando y vi que esta reportado el ese bug , lo que queria saber si hay alguna manera de poder solucionar eso o no me queda otra esperar que saquen algun parche.

despues probe de actualizar la version mediante sudo update-manager -d y no pude tampoco, me devolvio lo siguiente:
```

W:Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2  La suma MD5 difiere
, W:Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2  La suma MD5 difiere
, E:Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

```Si alguien me puede dar una mano mas que agredecido.

Saludos

---

### Post by luks911 on 2009-04-24
Mirate este link[0], explica porque hay algunos problemas de performance en Jaunty con algunas placas intel y explica cómo solucionarlo. Es posible que venga por ese lado.
Si tenés alguna duda sobre cómo aplicar lo que dice ahí (nada complicado) avisá.


[0] [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

---

### Post by leonardomdq on 2009-04-24
Muchas gracias por responder.
luks911 ahi estube mirando y te digo la verdad no entiendo como hacer, soy novato en linux, migre de guindow$ hace unos dias nada mas, si me podes dar una mano te agredeceria, perdona la molestia.

Saludos

---

### Post by luks911 on 2009-04-24
La cuestión es que los problemas estarían solucionados con la última versión del kernel y de los drivers de Intel. Te paso las instrucciones que deberían solucionarlo y también qué hacer para revertirlo si no lo soluciona o hay problemas mayores. Lo que vas a hacer es instalar una versión del kernel y de los drivers más actualizados que no están en los repositorios de Ubuntu y algunas cosas de configuración para activarlos. Veamos.

1) Bajás los paquetes necesarios. Para eso, abrí una terminal (Aplicaciones > Accesorios > Terminal) y ejecutá lo siguiente:
```

wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm2_2.4.9-1_i386.deb http://ftp.us.debian.org/debian/pool/main/libd/libdrm/libdrm-intel1_2.4.9-1_i386.deb http://http.us.debian.org/debian/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.7.0-1_i386.deb
```

2) Instalás esos paquetes, te va a pedir tu contraseña, otra ves en la terminal:

```
sudo dpkg -i linux-headers-2.6.30-020630rc2_2.6.30-020630rc2_all.deb linux-headers-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb linux-image-2.6.30-020630rc2-generic_2.6.30-020630rc2_i386.deb libdrm2_2.4.9-1_i386.deb libdrm-intel1_2.4.9-1_i386.deb xserver-xorg-video-intel_2.7.0-1_i386.deb
```

3) Editás el archivo xorg.conf, lo abrís con

```
gksudo gedit /etc/X11/xorg.conf
``` 

ahí te fijas que la sección Device sea idéntica a esto
```

Section "Device"
Identifier    "Configured Video Device"
Option        "AccelMethod"            "uxa"
Option        “Tiling”            “false”
EndSection
```

si hay cualquier otra línea extra en esa sección la comentás (o sea que le agregás el signo # en el inicio) y si falta alguna la agregás. Es posible que no haya nada, copias y pegás lo de arriba.

Leyendo todo el link veo que faltaría un paso más. Pero parece que lo que hay que hacer varía según cuál sea la placa. Así que pegá acá el resultado del comando
```
lspci -vvnn 
``` así veo cómo se puede seguir.

Para revertir todo eso, tenés que ejecutar:

```
sudo apt-get install libdrm2/jaunty libdrm-intel1/jaunty xserver-xorg-video-intel/jaunty
```
```

sudo dpkg -r linux-headers-2.6.30-020630rc2 linux-headers-2.6.30-020630rc2-generic linux-image-2.6.30-020630rc2-generic
```
```
sudo dpkg-reconfigure xserver-xorg
```

Sólo "traduje" las instrucciones del link.

---

### Post by leonardomdq on 2009-04-24
aca te dejo la info

```

leonardo@leonardo-laptop:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 2298
    Region 0: Memory at f8000000 (64-bit, non-prefetchable) [size=1M]
    Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 1800 [size=8]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at f8604800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00007fff
    Memory behind bridge: f4000000-f5ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=04, subordinate=07, sec-latency=0
    I/O behind bridge: 00008000-0000bfff
    Memory behind bridge: f6000000-f7ffffff
    Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f8200000-f82fffff
    Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 18a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at f8604c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) (prog-if 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
    Memory behind bridge: f8300000-f83fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR+ <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 2300
    Region 0: I/O ports at 1c00 [size=8]
    Region 1: I/O ports at 18d4 [size=4]
    Region 2: I/O ports at 18d8 [size=8]
    Region 3: I/O ports at 18d0 [size=4]
    Region 4: I/O ports at 18e0 [size=32]
    Region 5: Memory at f8604000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 10
    Region 0: Memory at 88100000 (32-bit, non-prefetchable) [size=256]
    Region 4: I/O ports at 1c20 [size=32]
    Kernel modules: i2c-i801

02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137d]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 2299
    Region 0: I/O ports at c000 [size=256]
    Region 2: Memory at f8200000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

09:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at f8300000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

09:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 21
    Region 0: Memory at f8300800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

09:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 11
    Region 0: Memory at f8300c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc

09:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
    Subsystem: Hewlett-Packard Company Device [103c:30cc]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 11
    Region 0: Memory at f8301000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

09:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff) (prog-if ff)
    !!! Unknown header type 7f

leonardo@leonardo-laptop:~$ 

```

---

### Post by luks911 on 2009-04-24
BIen. Un dato más, ¿qué te devuelve esto?

```
cat /proc/mtrr
```

---

### Post by pablo.s on 2009-04-24
Tenés un placa de Intel que está
blacklisted.

Vean [este]("http://ubuntuforums.org/showthread.php?t=1130135") post, que explica una
pequeña solución.

---

### Post by luks911 on 2009-04-24
> **pablo.s said:**
> Tenés un placa de Intel que está
blacklisted.

Vean [este]("http://ubuntuforums.org/showthread.php?t=1130135") post, que explica una
pequeña solución.

Justo venía de ese hilo :-P Hay que preguntar ahí cuál es el script. Que debe ser más simple.

---

### Post by pablo.s on 2009-04-24
> **luks911 said:**
> Que debe ser más simple.

En gedit abrí un documento en blanco,
escribí:

[COLOR=Red][B]#!/bin/sh
SKIP_CHECKS=yes compiz --replace
-------------------------------------------------------------------

[/B][COLOR=Black]guardalo en tu /home como mycompiz.sh

 [/COLOR][/COLOR]en el menú Sistema - Aplicaciones de Inicio
(o algo similar, yo lo tengo en inglés)
presioná el botón que dice añadir,
llená los datos y cerrá todo.
Reiniciá la maquina y supuestamente ya
va a estar.

---

### Post by leonardomdq on 2009-04-25
Probe y nada, no se soluciono. Lo tengo instalado el Jaunty, me aconsejan igual que lo deje y espere que salga algun parche oficial?

---

### Post by luks911 on 2009-04-25
> **leonardomdq said:**
> Probe y nada, no se soluciono. Lo tengo instalado el Jaunty, me aconsejan igual que lo deje y espere que salga algun parche oficial?

¿Probaste corriendo eso ```
SKIP_CHECKS=yes compiz --replace
```en una terminal primero, antes de hacer el script? Digo, capaz que falta darle permisos de ejecución por ejemplo.

---

### Post by leonardomdq on 2009-04-25
recien probe con el comando, aca te dejo lo que me pone en el terminal

> 
leonardo@leonardo-laptop:~$ SKIP_CHECKS=yes compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
Ahi se queda esperando...

despues me decis que haga el script , asi esta bien?

> 
mycompiz.sh

#!/bin/sh
SKIP_CHECKS=yes compiz --replace

**Cuando quiero guardar el script en /home/mycompiz.sh me dice que no tengo permisos**

---

### Post by Hei Ku on 2009-04-25
Ponele

SKIP_CHECKS=yes compiz --replace &

Para que te devuelva el prompt y no quede ahi colgado mientras se este ejecutando Compiz.

---

### Post by leonardomdq on 2009-04-25
ahora me pone esto y se queda ahi

> 
leonardo@leonardo-laptop:~$ SKIP_CHECKS=yes compiz --replace &
[1] 5152
Checking for Xgl: leonardo@leonardo-laptop:~$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format



el script sigue diciendome que no tengo permisos.

---

### Post by Hei Ku on 2009-04-25
El script lo tenes que guardar de tu home en /home/<usuario>/, no en /home/. Por eso te dice que no tenes permiso.

---

### Post by leonardomdq on 2009-04-25
No hubo caso Hei Ku, intente todo lo que me pasaron y nada. Alguna otra solucion habra?

saludos

---

### Post by staar on 2009-04-25
ese paquete (libdrm-intel1) no se llama así en intrepid, se llama libdrm2

saludos

---

### Post by caudio on 2009-04-25
Buenas  gente! tengo el mismo problema, mi placa es una Intel

VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

Al igual que los demas, no tengo aceleracion 3d. el sistema anda bien, no lento, pero por ejemplo cuando entra el protector de pantalla la maquina se muere, intente jugar al Tux race y tambien. 

Probe con el script que mencionan pero no cambio en nada ese tipo de operaciones, sigo con salvapantallas deshabilitado, y sin poder cargar nada en 3d... :(

---

### Post by leonardomdq on 2009-04-30
sigo igual con el problema del video Intel, ninguna otra solucion habra ?

---

### Post by pablo.s on 2009-04-30
Dale chmod 755 nombre_de_script.sh

---

### Post by leonardomdq on 2009-04-30
te cuento probe actualizando el kernel y me freeza la pc, el script anterior tampoco me funciono.
Pablo voy a probar con lo que me decis y aviso como me fue.

*el video que tiene la notebook es **Mobile Intel 965 Express Family***

saludos

---

### Post by leonardomdq on 2009-05-23
Tengo instalado el kernel **2.6.30-rc2** , estube googleando y vi esta el **kernel 2.6.30-rc6, **sera conveniente actualizar a este ultimo?
este es el kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc6/")

segui esta guia que me pasaron unos mensajes mas arriba
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

gracias

---

### Post by guillermolisi on 2009-05-23
> **leonardomdq said:**
> Tengo instalado el kernel **2.6.30-rc2** , estube googleando y vi esta el **kernel 2.6.30-rc6, **sera conveniente actualizar a este ultimo?
este es el kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc6/")

segui esta guia que me pasaron unos mensajes mas arriba
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

gracias
Com bien indica su nombre, son versiones nominadas a ser finales pero que aun estan con algun trabajo en curso, generalmente no a niveles funcionales sino en arreglo de bugs.

Particularmente y si no hay razones conocidas que ameriten aplicar este tipo de kernels, recomiendo usar la ultima version estable o anterior. Es decir, si en alguna de esas versiones esta documentado que se soluciona correctamente el bug del chipset 965 de Intel, jugate a ver que pasa. Sino, vas a laburar inutilmente.

---

### Post by leonardomdq on 2009-05-23
Esta es la lista de cambios del kernel, no entiendo si trae algun parche para mi placa.
[http://lkml.org/lkml/2009/5/16/3](http://lkml.org/lkml/2009/5/16/3)

Para saber que placa de video tengo que comando tendria que ejecutar?

gracias nuevamente y por la ayuda que brindan siempre.

---

### Post by staar on 2009-05-23
la lista de cambios dice que se arreglaron algunos bugs con respecto a la familia de placas que tenés > On the driver front, there's some sata updates, some i915 graphics 
updates, and various other small things sprinkled all over. asi que podrías probarlo, y ver que pasa...

para saber que placa tenés, podes correr ```
lspci
``` la línea que empieza con VGA... es la del video...

saludos

---

### Post by guillermolisi on 2009-05-23
> **staar said:**
> la lista de cambios dice que se arreglaron algunos bugs con respecto a la familia de placas que tenés  asi que podrías probarlo, y ver que pasa...

para saber que placa tenés, podes correr ```
lspci
``` la línea que empieza con VGA... es la del video...

saludos
No entiendo, en tu primer post editaste y pusiste que tenias placa de video Intel 965, es asi o no ?

Luego, si el kernel arregla aspecto de la 915 es bastante probable que no lo haga con la 965 ya que la 965 posee una tecnologia de video totalmente diferente y nueva, tan nueva que es dificil encontrar alguna instalacion Linux que funcione bien (y a raiz de eso se reportaron bugs para que sean solucionados).

---

### Post by staar on 2009-05-23
> **guillermolisi said:**
> No entiendo, en tu primer post editaste y pusiste que tenias placa de video Intel 965, es asi o no ?

Luego, si el kernel arregla aspecto de la 915 es bastante probable que no lo haga con la 965 ya que la 965 posee una tecnologia de video totalmente diferente y nueva, tan nueva que es dificil encontrar alguna instalacion Linux que funcione bien (y a raiz de eso se reportaron bugs para que sean solucionados).

oops, error mio, leí mal, creí que tenía la 915, perdón :oops:

saludos

---

### Post by leonardomdq on 2009-05-23
gracias a los dos por la ayuda, si corrige en las placas Intel 915 no me sirve.

Aca les dejo el resultado del comando 
```
lspci
```

me dio como respuesta o siguiente:
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)


Gracias Guillermo y staar, entonses a seguir esperando, cuando lo vi pense que servia para mi placa.

Saludos

---

### Post by guillermolisi on 2009-05-23
> **leonardomdq said:**
> gracias a los dos por la ayuda, si corrige en las placas Intel 915 no me sirve.

Aca les dejo el resultado del comando 
```
lspci
```me dio como respuesta o siguiente:


Gracias Guillermo y staar, entonses a seguir esperando, cuando lo vi pense que servia para mi placa.

Saludos
Si te las arreglas con el Ingles, te paso dos links que busque en Ubuntu Bugs ([https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)) sobre tu placa de video:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/120834](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/120834)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/363900](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/363900)

---

### Post by leonardomdq on 2009-05-23
Guillermo la verdad de ingles no entiendo nada. Una lastima, puede estar ahi la solucion quizas.

---

### Post by guillermolisi on 2009-05-23
> **leonardomdq said:**
> Guillermo la verdad de ingles no entiendo nada. Una lastima, puede estar ahi la solucion quizas.
No, la solucion no esta ahi pero te explica cuales son los problemas detectados como para saber si el tuyo esta dentro de ellos.

Fijate en estos threads del Chile Team que parece le han encontrado una vuelta.

[http://ubuntuforums.org/showpost.php?p=7323031&postcount=1](http://ubuntuforums.org/showpost.php?p=7323031&postcount=1)
[http://ubuntuforums.org/showpost.php?p=7316394&postcount=1](http://ubuntuforums.org/showpost.php?p=7316394&postcount=1)

Comenta como te resulto.

---

### Post by leonardomdq on 2009-05-23
Ahora quedo mejor parece, lo que hice fue lo siguiente:

Agregue ** Option AccelMethod" "UXA"** dentro de la sección "Device" de tu xorg.conf

```

Section "Device"
        Identifier    "Configured Video Device"
        
**Option        "AccelMethod" "uxa"**
EndSection

```NOTA: Con la versión 9.04 varias tarjetas Intel cayeron dentro de una lista negra de Compiz y por esta razón, a pesar de habilitar UXA no podremos activar los efectos. Para que Compiz no tome en cuenta la lista negra, hay que agregar la línea

```
SKIP_CHECKS=yes
```dentro del archivo [B]/etc/xdg/compiz/compiz-manager


[/B]Otra cosa que habia hecho fue instalar el driver de intel de Intrepid y actualizar al kernel 2.6.30 rc2.

Ahora quedo mucho mas agil por la aceleracion 3D.

Muchas gracias por ayuda Guillermo.
Saludos

---

