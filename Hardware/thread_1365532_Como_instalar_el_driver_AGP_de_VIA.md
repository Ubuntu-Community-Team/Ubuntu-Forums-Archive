---
title: "Como instalar el driver AGP de VIA"
date: 2009-12-27
forum: Hardware
---

### Post by ju4nj0 on 2009-12-27
El problema es que los driver AGP para la placa base Asus A7V880 no los tengo para linux, ni sé donde encontrarlos.
Cuando usaba windows instalaba los driver via y funcionaba todo perfectamente[FONT=monospace].

[/FONT]> $ lspci
00:00.0 Host bridge: VIA Technologies, Inc. KT880 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
[FONT=monospace]
[/FONT]> lsmod | grep agp
via_agp                12032  1
agpgart                32200  1 via_agp



> sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5
       resources: memory:fd000000-fdffffff memory:a0000000-afffffff(prefetchable) memory:fc000000-fcffffff memory:fe200000-fe21ffff(prefetchable)


> uname --all
Linux m1316-desktop 2.6.32-7-generic #10-Ubuntu SMP Sun Dec 6 13:43:20 UTC 2009 i686 GNU/Linux


 machas gracias 



 Asus A7V880
AMD Athlon(tm)  2800+
nVidia Corporation NV44A [GeForce 6200](rev a1)
 Subsystem: XFX Pine Group Inc.226a
1,5 G de Ram Kingston
HD SATA 200 G
ViewSonic N3260W

---

### Post by ju4nj0 on 2009-12-27
he reinstalado
he metido un paquete descargado de la pagina de via "VIA_UART_LinuxDriverPackage_V120"
instalado los driver desde la pagina de nvidia
y ya esta funcinando
ya tengo 3D
gracias
 ```
m1316@m1316-desktop:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:16 memory:fd000000-fdffffff memory:a0000000-afffffff(prefetchable) memory:fc000000-fcffffff memory:fe200000-fe21ffff(prefetchable)
m1316@m1316-desktop:~$
``````
m1316@m1316-desktop:~$ lsmod | grep agp
via_agp                 5206  1 
agpgart                31015  2 nvidia,via_agp
m1316@m1316-desktop:~$ 
``` Asus A7V880
AMD Athlon(tm)  2800+
nVidia Corporation NV44A [GeForce 6200](rev a1)
 Subsystem: XFX Pine Group Inc.226a
1,5 G de Ram Kingston
HD SATA 200 G
ViewSonic N3260W

---

