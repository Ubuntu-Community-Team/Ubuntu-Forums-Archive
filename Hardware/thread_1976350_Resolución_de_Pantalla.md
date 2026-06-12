---
title: "Resolución de Pantalla"
date: 2012-05-08
forum: Hardware
---

### Post by Lio56 on 2012-05-08
Buenas !!!
Estoy super contento sepanlo

Ahora lo que me falta es arreglar la resolución de la pantalla. Tengo un monitor de 23" wide y UBUNTU lo puso en 1920x1080.

Cuando le bajo la resolución, la barra superior donde esta la hora y el  iconito para apagar la computadora me queda fuera de la pantalla.
Es como que no se ajusta todo a la nueva resolución seteada por mi.

Alguien sabe que puede estar pasando?

Muchas gracias
Saludos
Lio

---

### Post by euzkoarima on 2012-05-08
No se que está pasando, pero la única manera que se me ocurre es que pase esto es que la resolución que estás pasando no tenga una proporción soportada por el monitor (en realidad si así fuera no te la debería dejar elegir tampoco, pero bueno, puede pasar)

Fijate que vos tenés 1920x1080 o sea 16:9
Si pasás, p. ej, a 1440x900 es 16:10 y se perdería algo o arriba o abajo.

Contanos a que resolución lo pasas

Saludos,
Eduardo

---

### Post by Lio56 on 2012-05-08
HOLAAAA mira creo que lo que pasa es como tenia le fondo de pantalla de China que es 1920x1080 al bajar la resolución se perdia parte de la pantalla.
Cambie el fondo de pantalla a Colores baje la resolución  y WALA  funcionó mi nombre de usuario y el iconito de Power siempre quedaban visibiles en el extremo superior derecho.
Despues volvi al wallpaper the china  y se achico a la resolucion nueva.

Igual te tiro una que no la podes creer me faltan muchas resoluciones intermendias  como por ejemplo 1024×768
por es que es que faltan resoluciones?

Me gustaria tenes mas resoluciones en 16:9 mi monitor es WIDE  supongo  que la relacion 16:9 es la mejor. Aunque tambien pude ver 16:10.
Esto es lo que me gusta de linux vas aprendiendo a medida que lo usas... pero tambien es cierto como dije en otro post... Yo algunas veces quiero ser sencillamente usuario y no preocuparme por nada.... o sencillamente usar la compu como una herramienta....

Como puedo incluir 1024x768 ??? si no me aparece????

Saludos gracias
Lio

---

### Post by Lio56 on 2012-05-08
Averigué mas y 1280x720 y relación 16:9 lo que no es cómo saber  si mi monitor es 16:9 o 16:10
que tengo que hacer medirlo???

---

### Post by euzkoarima on 2012-05-09
> **Lio56 said:**
> Averigué mas y 1280x720 y relación 16:9 lo que no es cómo saber  si mi monitor es 16:9 o 16:10
que tengo que hacer medirlo???

Con la especificación técnica del modelo de tu monitor (pag. web o manual que trajo al comprarlo)

Las resoluciones posibles dependen de:
[LIST]
[*]El monitor
[*]La placa gráfica
[*]El driver que tengas instalado
[/LIST]

Ojo, que el monitor tenga resolucion HD (1920x1080) no significa, necesariamente, que deba tener 1024x768. Puede que la tengal, como puede que no.

Saludos,
Eduardo

---

### Post by Lio56 on 2012-05-09
Uyyy tenes razon

En la página 19 de mi manual [http://downloadcenter.samsung.com/content/UM/200910/20091008104107796/BN59-00841H-02Eng.pdf](http://downloadcenter.samsung.com/content/UM/200910/20091008104107796/BN59-00841H-02Eng.pdf)
no esta la resolucion 1280x720. 

NOOOOOOOOOOO!!!!!!!!!!!!!!!!! NO!!!!!!!!!!!!!!!!!!!!!! PORQUEEEEEEE!!!!!!!! (al estilo tano passman)

Puedo preguntar porque si me aparecía en WinXP ? Digo porque ahora que uno sabe un poquito mas, esa resolución no deberia poder ser soportada...
¿Alguna idea?

GRacias
Saludos
Lio

---

### Post by euzkoarima on 2012-05-09
No estoy muy seguro, pero supongo que era un error (o "feature" depende como lo presenten) del driver.
Supongo que debían ocurrir una de dos cosas, o no mostraba nada (o basura x estar fuera de resolución) o te mostraba una resolución que si tenía, que no era la que te decía sino una "cercana"

Saludos
Eduardo

---

### Post by Lio56 on 2012-05-09
bien ahora tengo un problema la caja de mi monitor dice P2370H pero en la carcasa esta escrito P2370 (sin la H)

Pero me fije y los dos manuales tienen las mimas resoluciones
En la página 19 de mi manual [http://downloadcenter.samsung.com/co...841H-02Eng.pdf]("http://downloadcenter.samsung.com/content/UM/200910/20091008104107796/BN59-00841H-02Eng.pdf")

Estas son las resoluciones del manual
VESA, 640 x 480
* VESA, 800 x 600
* VESA, 1024 x 768
* VESA, 1280 x 800
* VESA, 1280 x 960
* VESA, 1280 x 1024
* VESA, 1440 x 900 
VESA, 1600 x 1200 
* VESA, 1680 x 1050 
* VESA, 1920 x 1080 


Pero UBUNTU me muestra todas las que tienen * de la lista anterior y ademas estas 900x540, 900x600, 1152x864, 1360x768 (config actual creo que es 16:9), 1400x1050.

Entonces como UBUNTU no me muestra todas las resoluciones me pregunto si el driver es correcto????

En el manual lo unico que encontre es Display area 509.76 mm (H) x 286.74 mm (V) 
si dividis 509.76 / 286.74 = 16 / 9 entonces creo que es 16:9 es correcto esto????

gracias saludos
Lio

---

### Post by guillermolisi on 2012-05-10
Vesa no es el driver correcto para resolver la situacion, casualmente por ello observas los problemas que mencionas, ya que VESA es un driver generico sin aceleracion grafica.

Creo que llegamos al punto inicial: Que placa de video estas usando, marca y modelo ?

Podrias mostrarnos las salidas de ```
sudo lshw
``` y de /var/log/Xorg.0.log ?

---

### Post by Lio56 on 2012-05-10
OJO en el manual decia VESA
llego a la noche a casa hago eso :) y te muestro copy&paste la salida de la pantalla

les digo algo estoy super emocionado, pute0, porque a veces se hace dificil pero es GENIAL
te juro que estoy todo el dia pensando mirando el foro estoy muy contento.

despues mas adelante quiero configurar el linux para acceder a la PC de casa desde la oficina o desde la casa de un amigo etc

Abrazoooo
LIO

---

### Post by Lio56 on 2012-05-10
Acá les paso los datos que me pidieron.

Mi Motherboard con video onboard es un ECS ELITEGROUP GF8200A. 
CHIPSET    º NVIDIA GeForce8200 Series
º NVIDIA MCP78S Single Chipset

GRAPHICS    º On Chip ( NVIDIA GeForce8200 based with 2D/3D graphic engine)
º Integrated DirectX10 graphics processor
º Share Memory: Maximum up to 512MB

Perdón si me quedo un poco largo el post...

Gracias
Saludos
Leandro

[HTML]
    descripción: Equipo de escritorio
    producto: GeForce 8000 series ()
    fabricante: ECS
    versión: 1.0
    anchura: 64 bits
    capacidades: smbios-2.6 dmi-2.6 vsyscall32
    configuración: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       descripción: Placa base
       producto: GeForce 8000 series
       fabricante: ECS
       id físico: 0
       versión: 1.0
     *-firmware
          descripción: BIOS
          fabricante: American Megatrends Inc.
          id físico: 0
          versión: 080015
          date: 07/15/2009
          tamaño: 64KiB
          capacidad: 960KiB
          capacidades: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          descripción: CPU
          producto: AMD Athlon(tm) II X2 240 Processor
          fabricante: Hynix Semiconductor (Hyundai Electronics)
          id físico: 3
          información del bus: cpu@0
          versión: AMD Athlon(tm) II X2 240 Processor
          serie: To Be Filled By O.E.M.
          ranura: CPU 1
          tamaño: 800MHz
          capacidad: 2800MHz
          anchura: 64 bits
          reloj: 200MHz
          capacidades: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
          configuración: cores=2 enabledcores=2
        *-cache:0
             descripción: L1 caché
             id físico: 5
             ranura: L1-Cache
             tamaño: 256KiB
             capacidad: 256KiB
             capacidades: pipeline-burst internal varies data
        *-cache:1
             descripción: L2 caché
             id físico: 6
             ranura: L2-Cache
             tamaño: 2MiB
             capacidad: 2MiB
             capacidades: pipeline-burst internal varies unified
     *-memory:0
          descripción: Memoria de sistema
          id físico: 26
          ranura: Placa de sistema o placa base
          tamaño: 4GiB
        *-bank:0
             descripción: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-04-18 06:53+0000X-Generator: Launchpad (build 15099)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-04-18 06:53+0000X-Generator: Launchpad (build 15099) [vacío]
             producto: ModulePartNumber00
             fabricante: Manufacturer00
             id físico: 0
             serie: SerNum00
             ranura: DIMM0
        *-bank:1
             descripción: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-04-18 06:53+0000X-Generator: Launchpad (build 15099)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-04-18 06:53+0000X-Generator: Launchpad (build 15099) [vacío]
             producto: ModulePartNumber01
             fabricante: Manufacturer01
             id físico: 1
             serie: SerNum01
             ranura: DIMM1
        *-bank:2
             descripción: DIMM DDR2 Síncrono 400 MHz (2,5 ns)
             producto: OCZ2G8002G
             fabricante: Manufacturer02
             id físico: 2
             serie: 00000000
             ranura: DIMM2
             tamaño: 2GiB
             anchura: 64 bits
             reloj: 400MHz (2.5ns)
        *-bank:3
             descripción: DIMM DDR2 Síncrono 400 MHz (2,5 ns)
             producto: OCZ2G8002G
             fabricante: Manufacturer03
             id físico: 3
             serie: 00000000
             ranura: DIMM3
             tamaño: 2GiB
             anchura: 64 bits
             reloj: 400MHz (2.5ns)
     *-memory:1 NO RECLAMADO
          descripción: RAM memory
          producto: MCP78S [GeForce 8200] Memory Controller
          fabricante: NVIDIA Corporation
          id físico: 4
          información del bus: pci@0000:00:00.0
          versión: a2
          anchura: 32 bits
          reloj: 66MHz (15.2ns)
          capacidades: ht bus_master cap_list
          configuración: latency=0
     *-isa
          descripción: ISA bridge
          producto: MCP78S [GeForce 8200] LPC Bridge
          fabricante: NVIDIA Corporation
          id físico: 1
          información del bus: pci@0000:00:01.0
          versión: a2
          anchura: 32 bits
          reloj: 66MHz
          capacidades: isa bus_master
          configuración: latency=0
          recursos: ioport:2f00(size=256)
     *-serial
          descripción: SMBus
          producto: MCP78S [GeForce 8200] SMBus
          fabricante: NVIDIA Corporation
          id físico: 1.1
          información del bus: pci@0000:00:01.1
          versión: a1
          anchura: 32 bits
          reloj: 66MHz
          capacidades: pm cap_list
          configuración: driver=nForce2_smbus latency=0
          recursos: irq:11 ioport:2900(size=64) ioport:2d00(size=64) ioport:2e00(size=64)
     *-memory:2 NO RECLAMADO
          descripción: RAM memory
          producto: MCP78S [GeForce 8200] Memory Controller
          fabricante: NVIDIA Corporation
          id físico: 1.2
          información del bus: pci@0000:00:01.2
          versión: a1
          anchura: 32 bits
          reloj: 66MHz (15.2ns)
          configuración: latency=0
     *-processor NO RECLAMADO
          descripción: Co-processor
          producto: MCP78S [GeForce 8200] Co-Processor
          fabricante: NVIDIA Corporation
          id físico: 1.3
          información del bus: pci@0000:00:01.3
          versión: a2
          anchura: 32 bits
          reloj: 66MHz
          capacidades: bus_master
          configuración: latency=0 maxlatency=1 mingnt=3
          recursos: memoria:fbe80000-fbefffff
     *-memory:3 NO RECLAMADO
          descripción: RAM memory
          producto: MCP78S [GeForce 8200] Memory Controller
          fabricante: NVIDIA Corporation
          id físico: 1.4
          información del bus: pci@0000:00:01.4
          versión: a1
          anchura: 32 bits
          reloj: 66MHz (15.2ns)
          configuración: latency=0
     *-usb:0
          descripción: USB controller
          producto: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          fabricante: NVIDIA Corporation
          id físico: 2
          información del bus: pci@0000:00:02.0
          versión: a1
          anchura: 32 bits
          reloj: 66MHz
          capacidades: pm ohci bus_master cap_list
          configuración: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          recursos: irq:23 memoria:fbe7f000-fbe7ffff
     *-usb:1
          descripción: USB controller
          producto: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          fabricante: NVIDIA Corporation
          id físico: 2.1
          información del bus: pci@0000:00:02.1
          versión: a1
          anchura: 32 bits
          reloj: 66MHz
          capacidades: debug pm ehci bus_master cap_list
          configuración: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          recursos: irq:22 memoria:fbe7ec00-fbe7ecff
     *-usb:2
          descripción: USB controller
          producto: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          fabricante: NVIDIA Corporation
          id físico: 5
          información del bus: pci@0000:00:04.0
          versión: a1
          anchura: 32 bits
          reloj: 66MHz
          capacidades: pm ohci bus_master cap_list
          configuración: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          recursos: irq:21 memoria:fbe7d000-fbe7dfff
     *-usb:3
          descripción: USB controller
          producto: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          fabricante: NVIDIA Corporation
          id físico: 4.1
          información del bus: pci@0000:00:04.1
          versión: a1
          anchura: 32 bits
          reloj: 66MHz
          capacidades: debug pm ehci bus_master cap_list
          configuración: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          recursos: irq:20 memoria:fbe7e800-fbe7e8ff
     *-ide:0
          descripción: IDE interface
          producto: MCP78S [GeForce 8200] IDE
          fabricante: NVIDIA Corporation
          id físico: 6
          información del bus: pci@0000:00:06.0
          versión: a1
          anchura: 32 bits
          reloj: 66MHz
          capacidades: ide pm bus_master cap_list
          configuración: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          recursos: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-multimedia
          descripción: Audio device
          producto: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          fabricante: NVIDIA Corporation
          id físico: 7
          información del bus: pci@0000:00:07.0
          versión: a1
          anchura: 32 bits
          reloj: 66MHz
          capacidades: pm bus_master cap_list
          configuración: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          recursos: irq:22 memoria:fbe78000-fbe7bfff
     *-pci:0
          descripción: PCI bridge
          producto: MCP78S [GeForce 8200] PCI Bridge
          fabricante: NVIDIA Corporation
          id físico: 8
          información del bus: pci@0000:00:08.0
          versión: a1
          anchura: 32 bits
          reloj: 66MHz
          capacidades: pci ht subtractive_decode bus_master cap_list
          recursos: ioport:c000(size=4096) memoria:fbf00000-fbffffff
        *-network
             descripción: Ethernet interface
             producto: RTL-8139/8139C/8139C+
             fabricante: Realtek Semiconductor Co., Ltd.
             id físico: 4
             información del bus: pci@0000:01:04.0
             nombre lógico: eth1
             versión: 10
             serie: 00:c0:df:0e:75:b3
             tamaño: 10Mbit/s
             capacidad: 100Mbit/s
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuración: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
             recursos: irq:19 ioport:c800(size=256) memoria:fbfffc00-fbfffcff
     *-ide:1
          descripción: IDE interface
          producto: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          fabricante: NVIDIA Corporation
          id físico: 9
          información del bus: pci@0000:00:09.0
          nombre lógico: scsi1
          nombre lógico: scsi2
          versión: a2
          anchura: 32 bits
          reloj: 66MHz
          capacidades: ide pm msi ht bus_master cap_list emulated
          configuración: driver=ahci latency=0 maxlatency=1 mingnt=3
          recursos: irq:40 ioport:b480(size=8) ioport:b400(size=4) ioport:b080(size=8) ioport:b000(size=4) ioport:ac00(size=16) memoria:fbe76000-fbe77fff
        *-disk
             descripción: ATA Disk
             producto: WDC WD5000AADS-0
             fabricante: Western Digital
             id físico: 0
             información del bus: scsi@1:0.0.0
             nombre lógico: /dev/sda
             versión: 01.0
             serie: WD-WMAV90254757
             tamaño: 465GiB (500GB)
             capacidades: partitioned partitioned:dos
             configuración: ansiversion=5 signature=42e742e6
           *-volume:0
                descripción: Windows NTFS volumen
                id físico: 1
                información del bus: scsi@1:0.0.0,1
                nombre lógico: /dev/sda1
                versión: 3.1
                serie: 6cf3-ed00
                tamaño: 98MiB
                capacidad: 100MiB
                capacidades: primary bootable ntfs initialized
                configuración: clustersize=4096 created=2012-05-07 15:33:52 filesystem=ntfs label=Reservado para el sistema state=clean
           *-volume:1
                descripción: Windows NTFS volumen
                id físico: 2
                información del bus: scsi@1:0.0.0,2
                nombre lógico: /dev/sda2
                versión: 3.1
                serie: be967a17-5dda-e34d-a53d-34e07e7a671a
                tamaño: 119GiB
                capacidad: 119GiB
                capacidades: primary ntfs initialized
                configuración: clustersize=4096 created=2012-05-07 15:34:05 filesystem=ntfs state=clean
           *-volume:2
                descripción: Extended partition
                id físico: 3
                información del bus: scsi@1:0.0.0,3
                nombre lógico: /dev/sda3
                tamaño: 345GiB
                capacidad: 345GiB
                capacidades: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   descripción: Linux filesystem partition
                   id físico: 5
                   nombre lógico: /dev/sda5
                   nombre lógico: /
                   capacidad: 76GiB
                   configuración: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   descripción: HPFS/NTFS partition
                   id físico: 6
                   nombre lógico: /dev/sda6
                   nombre lógico: /home/DiscoDatos
                   capacidad: 250GiB
                   configuración: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-logicalvolume:2
                   descripción: Linux swap / Solaris partition
                   id físico: 7
                   nombre lógico: /dev/sda7
                   capacidad: 19GiB
                   capacidades: nofs
        *-cdrom
             descripción: DVD writer
             producto: DVD-RW  DVR-212D
             fabricante: PIONEER
             id físico: 1
             información del bus: scsi@2:0.0.0
             nombre lógico: /dev/cdrom
             nombre lógico: /dev/cdrw
             nombre lógico: /dev/dvd
             nombre lógico: /dev/dvdrw
             nombre lógico: /dev/sr0
             nombre lógico: /media/WINXP SP3 UE
             versión: 1.15
             capacidades: removable audio cd-r cd-rw dvd dvd-r
             configuración: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                id físico: 0
                nombre lógico: /dev/cdrom
                nombre lógico: /media/WINXP SP3 UE
                configuración: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
     *-pci:1
          descripción: PCI bridge
          producto: MCP78S [GeForce 8200] PCI Express Bridge
          fabricante: NVIDIA Corporation
          id físico: b
          información del bus: pci@0000:00:0b.0
          versión: a1
          anchura: 32 bits
          reloj: 33MHz
          capacidades: pci pm ht normal_decode bus_master cap_list
          recursos: ioport:d000(size=4096) memoria:fc000000-fdefffff ioport:f0000000(size=167772160)
        *-display
             descripción: VGA compatible controller
             producto: C77 [GeForce 8200]
             fabricante: NVIDIA Corporation
             id físico: 0
             información del bus: pci@0000:02:00.0
             versión: a2
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi vga_controller bus_master cap_list rom
             configuración: driver=nvidia latency=0
             recursos: irq:21 memoria:fc000000-fcffffff memoria:f0000000-f7ffffff memoria:f8000000-f9ffffff ioport:dc00(size=128) memoria:fdee0000-fdefffff
     *-pci:2
          descripción: PCI bridge
          producto: MCP78S [GeForce 8200] PCI Express Bridge
          fabricante: NVIDIA Corporation
          id físico: 10
          información del bus: pci@0000:00:10.0
          versión: a1
          anchura: 32 bits
          reloj: 33MHz
          capacidades: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuración: driver=pcieport
          recursos: irq:19
     *-pci:3
          descripción: PCI bridge
          producto: MCP78S [GeForce 8200] PCI Express Bridge
          fabricante: NVIDIA Corporation
          id físico: 12
          información del bus: pci@0000:00:12.0
          versión: a1
          anchura: 32 bits
          reloj: 33MHz
          capacidades: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuración: driver=pcieport
          recursos: irq:18
     *-pci:4
          descripción: PCI bridge
          producto: MCP78S [GeForce 8200] PCI Bridge
          fabricante: NVIDIA Corporation
          id físico: 13
          información del bus: pci@0000:00:13.0
          versión: a1
          anchura: 32 bits
          reloj: 33MHz
          capacidades: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuración: driver=pcieport
          recursos: irq:17
     *-pci:5
          descripción: PCI bridge
          producto: MCP78S [GeForce 8200] PCI Bridge
          fabricante: NVIDIA Corporation
          id físico: 14
          información del bus: pci@0000:00:14.0
          versión: a1
          anchura: 32 bits
          reloj: 33MHz
          capacidades: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuración: driver=pcieport
          recursos: irq:16 ioport:e000(size=4096) memoria:fdf00000-fdffffff
        *-network
             descripción: Ethernet interface
             producto: RTL8111/8168B PCI Express Gigabit Ethernet controller
             fabricante: Realtek Semiconductor Co., Ltd.
             id físico: 0
             información del bus: pci@0000:06:00.0
             nombre lógico: eth0
             versión: 01
             serie: 00:1e:90:f0:97:09
             tamaño: 100Mbit/s
             capacidad: 1Gbit/s
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
             recursos: irq:41 ioport:e800(size=256) memoria:fdfff000-fdffffff memoria:fdfc0000-fdfdffff
     *-pci:6
          descripción: Host bridge
          producto: Family 10h Processor HyperTransport Configuration
          fabricante: Hynix Semiconductor (Hyundai Electronics)
          id físico: 100
          información del bus: pci@0000:00:18.0
          versión: 00
          anchura: 32 bits
          reloj: 33MHz
     *-pci:7
          descripción: Host bridge
          producto: Family 10h Processor Address Map
          fabricante: Hynix Semiconductor (Hyundai Electronics)
          id físico: 101
          información del bus: pci@0000:00:18.1
          versión: 00
          anchura: 32 bits
          reloj: 33MHz
     *-pci:8
          descripción: Host bridge
          producto: Family 10h Processor DRAM Controller
          fabricante: Hynix Semiconductor (Hyundai Electronics)
          id físico: 102
          información del bus: pci@0000:00:18.2
          versión: 00
          anchura: 32 bits
          reloj: 33MHz
     *-pci:9
          descripción: Host bridge
          producto: Family 10h Processor Miscellaneous Control
          fabricante: Hynix Semiconductor (Hyundai Electronics)
          id físico: 103
          información del bus: pci@0000:00:18.3
          versión: 00
          anchura: 32 bits
          reloj: 33MHz
          configuración: driver=k10temp
          recursos: irq:0
     *-pci:10
          descripción: Host bridge
          producto: Family 10h Processor Link Control
          fabricante: Hynix Semiconductor (Hyundai Electronics)
          id físico: 104
          información del bus: pci@0000:00:18.4
          versión: 00
          anchura: 32 bits
          reloj: 33MHz
leus@leus-GeForce8000:~$ 
[/HTML]Aca va lo del archivo /var/log/Xorg.0.log 

[HTML]
[    14.272] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    14.272] X Protocol Version 11, Revision 0
[    14.272] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    14.272] Current Operating System: Linux leus-GeForce8000 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64
[    14.272] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=014e7ba3-1ba8-4958-87dc-e306971cefd3 ro quiet splash vt.handoff=7
[    14.272] Build Date: 20 April 2012  05:12:02AM
[    14.272] xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see http://www.ubuntu.com/support) 
[    14.272] Current version of pixman: 0.24.4
[    14.272]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.272] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.272] (==) Log file: "/var/log/Xorg.0.log", Time: Wed May  9 18:55:59 2012
[    14.272] (==) Using config file: "/etc/X11/xorg.conf"
[    14.272] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.272] (==) No Layout section.  Using the first Screen section.
[    14.272] (==) No screen section available. Using defaults.
[    14.272] (**) |-->Screen "Default Screen Section" (0)
[    14.272] (**) |   |-->Monitor "<default monitor>"
[    14.273] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    14.273] (**) |   |-->Device "Default Device"
[    14.273] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.273] (==) Automatically adding devices
[    14.273] (==) Automatically enabling devices
[    14.273] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.273]     Entry deleted from font path.
[    14.273] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.273]     Entry deleted from font path.
[    14.273] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.273]     Entry deleted from font path.
[    14.273] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.273]     Entry deleted from font path.
[    14.273] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.273]     Entry deleted from font path.
[    14.273] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.273]     Entry deleted from font path.
[    14.273] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    14.273] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.273] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.273] (II) Loader magic: 0x7f30f96cfb00
[    14.273] (II) Module ABI versions:
[    14.273]     X.Org ANSI C Emulation: 0.4
[    14.273]     X.Org Video Driver: 11.0
[    14.273]     X.Org XInput driver : 16.0
[    14.273]     X.Org Server Extension : 6.0
[    14.274] (--) PCI:*(0:2:0:0) 10de:0849:1019:2646 rev 162, Mem @ 0xfc000000/16777216, 0xf0000000/134217728, 0xf8000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
[    14.274] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.274] (II) LoadModule: "extmod"
[    14.274] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.274] (II) Module extmod: vendor="X.Org Foundation"
[    14.274]     compiled for 1.11.3, module version = 1.0.0
[    14.274]     Module class: X.Org Server Extension
[    14.274]     ABI class: X.Org Server Extension, version 6.0
[    14.274] (II) Loading extension MIT-SCREEN-SAVER
[    14.274] (II) Loading extension XFree86-VidModeExtension
[    14.274] (II) Loading extension XFree86-DGA
[    14.274] (II) Loading extension DPMS
[    14.274] (II) Loading extension XVideo
[    14.274] (II) Loading extension XVideo-MotionCompensation
[    14.274] (II) Loading extension X-Resource
[    14.274] (II) LoadModule: "dbe"
[    14.274] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.274] (II) Module dbe: vendor="X.Org Foundation"
[    14.274]     compiled for 1.11.3, module version = 1.0.0
[    14.274]     Module class: X.Org Server Extension
[    14.274]     ABI class: X.Org Server Extension, version 6.0
[    14.274] (II) Loading extension DOUBLE-BUFFER
[    14.274] (II) LoadModule: "glx"
[    14.275] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    14.286] (II) Module glx: vendor="NVIDIA Corporation"
[    14.286]     compiled for 4.0.2, module version = 1.0.0
[    14.286]     Module class: X.Org Server Extension
[    14.286] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    14.286] (II) Loading extension GLX
[    14.286] (II) LoadModule: "record"
[    14.287] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.287] (II) Module record: vendor="X.Org Foundation"
[    14.287]     compiled for 1.11.3, module version = 1.13.0
[    14.287]     Module class: X.Org Server Extension
[    14.287]     ABI class: X.Org Server Extension, version 6.0
[    14.287] (II) Loading extension RECORD
[    14.287] (II) LoadModule: "dri"
[    14.287] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.287] (II) Module dri: vendor="X.Org Foundation"
[    14.287]     compiled for 1.11.3, module version = 1.0.0
[    14.287]     ABI class: X.Org Server Extension, version 6.0
[    14.287] (II) Loading extension XFree86-DRI
[    14.287] (II) LoadModule: "dri2"
[    14.287] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.287] (II) Module dri2: vendor="X.Org Foundation"
[    14.287]     compiled for 1.11.3, module version = 1.2.0
[    14.287]     ABI class: X.Org Server Extension, version 6.0
[    14.287] (II) Loading extension DRI2
[    14.287] (==) Matched nvidia as autoconfigured driver 0
[    14.287] (==) Matched nouveau as autoconfigured driver 1
[    14.287] (==) Matched nv as autoconfigured driver 2
[    14.287] (==) Matched vesa as autoconfigured driver 3
[    14.287] (==) Matched fbdev as autoconfigured driver 4
[    14.287] (==) Assigned the driver to the xf86ConfigLayout
[    14.287] (II) LoadModule: "nvidia"
[    14.287] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    14.288] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.288]     compiled for 4.0.2, module version = 1.0.0
[    14.288]     Module class: X.Org Video Driver
[    14.288] (II) LoadModule: "nouveau"
[    14.288] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.288] (II) Module nouveau: vendor="X.Org Foundation"
[    14.288]     compiled for 1.11.3, module version = 0.0.16
[    14.288]     Module class: X.Org Video Driver
[    14.288]     ABI class: X.Org Video Driver, version 11.0
[    14.288] (II) LoadModule: "nv"
[    14.303] (WW) Warning, couldn't open module nv
[    14.303] (II) UnloadModule: "nv"
[    14.303] (II) Unloading nv
[    14.303] (EE) Failed to load module "nv" (module does not exist, 0)
[    14.303] (II) LoadModule: "vesa"
[    14.303] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.304] (II) Module vesa: vendor="X.Org Foundation"
[    14.304]     compiled for 1.11.3, module version = 2.3.0
[    14.304]     Module class: X.Org Video Driver
[    14.304]     ABI class: X.Org Video Driver, version 11.0
[    14.304] (II) LoadModule: "fbdev"
[    14.304] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.304] (II) Module fbdev: vendor="X.Org Foundation"
[    14.304]     compiled for 1.11.3, module version = 0.4.2
[    14.304]     ABI class: X.Org Video Driver, version 11.0
[    14.304] (==) Matched nvidia as autoconfigured driver 0
[    14.304] (==) Matched nouveau as autoconfigured driver 1
[    14.304] (==) Matched nv as autoconfigured driver 2
[    14.304] (==) Matched vesa as autoconfigured driver 3
[    14.304] (==) Matched fbdev as autoconfigured driver 4
[    14.304] (==) Assigned the driver to the xf86ConfigLayout
[    14.304] (II) LoadModule: "nvidia"
[    14.304] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    14.304] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.304]     compiled for 4.0.2, module version = 1.0.0
[    14.304]     Module class: X.Org Video Driver
[    14.304] (II) UnloadModule: "nvidia"
[    14.304] (II) Unloading nvidia
[    14.304] (II) Failed to load module "nvidia" (already loaded, 32560)
[    14.304] (II) LoadModule: "nouveau"
[    14.304] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.304] (II) Module nouveau: vendor="X.Org Foundation"
[    14.304]     compiled for 1.11.3, module version = 0.0.16
[    14.304]     Module class: X.Org Video Driver
[    14.304]     ABI class: X.Org Video Driver, version 11.0
[    14.304] (II) UnloadModule: "nouveau"
[    14.304] (II) Unloading nouveau
[    14.304] (II) Failed to load module "nouveau" (already loaded, 32560)
[    14.304] (II) LoadModule: "nv"
[    14.304] (WW) Warning, couldn't open module nv
[    14.304] (II) UnloadModule: "nv"
[    14.304] (II) Unloading nv
[    14.304] (EE) Failed to load module "nv" (module does not exist, 0)
[    14.304] (II) LoadModule: "vesa"
[    14.305] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.305] (II) Module vesa: vendor="X.Org Foundation"
[    14.305]     compiled for 1.11.3, module version = 2.3.0
[    14.305]     Module class: X.Org Video Driver
[    14.305]     ABI class: X.Org Video Driver, version 11.0
[    14.305] (II) UnloadModule: "vesa"
[    14.305] (II) Unloading vesa
[    14.305] (II) Failed to load module "vesa" (already loaded, 0)
[    14.305] (II) LoadModule: "fbdev"
[    14.305] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.305] (II) Module fbdev: vendor="X.Org Foundation"
[    14.305]     compiled for 1.11.3, module version = 0.4.2
[    14.305]     ABI class: X.Org Video Driver, version 11.0
[    14.305] (II) UnloadModule: "fbdev"
[    14.305] (II) Unloading fbdev
[    14.305] (II) Failed to load module "fbdev" (already loaded, 0)
[    14.305] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[    14.305] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.305] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    14.305] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.305]     RIVA TNT        (NV04)
[    14.305]     RIVA TNT2       (NV05)
[    14.305]     GeForce 256     (NV10)
[    14.305]     GeForce 2       (NV11, NV15)
[    14.305]     GeForce 4MX     (NV17, NV18)
[    14.305]     GeForce 3       (NV20)
[    14.305]     GeForce 4Ti     (NV25, NV28)
[    14.305]     GeForce FX      (NV3x)
[    14.305]     GeForce 6       (NV4x)
[    14.305]     GeForce 7       (G7x)
[    14.305]     GeForce 8       (G8x)
[    14.305]     GeForce GTX 200 (NVA0)
[    14.305]     GeForce GTX 400 (NVC0)
[    14.305] (II) VESA: driver for VESA chipsets: vesa
[    14.305] (II) FBDEV: driver for framebuffer: fbdev
[    14.305] (++) using VT number 7

[    14.305] (II) Loading sub module "fb"
[    14.305] (II) LoadModule: "fb"
[    14.305] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.305] (II) Module fb: vendor="X.Org Foundation"
[    14.305]     compiled for 1.11.3, module version = 1.0.0
[    14.305]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.305] (II) Loading sub module "wfb"
[    14.305] (II) LoadModule: "wfb"
[    14.306] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.306] (II) Module wfb: vendor="X.Org Foundation"
[    14.306]     compiled for 1.11.3, module version = 1.0.0
[    14.306]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.306] (II) Loading sub module "ramdac"
[    14.306] (II) LoadModule: "ramdac"
[    14.306] (II) Module "ramdac" already built-in
[    14.306] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    14.306] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.306] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.306] (WW) Falling back to old probe method for vesa
[    14.306] (WW) Falling back to old probe method for fbdev
[    14.306] (II) Loading sub module "fbdevhw"
[    14.306] (II) LoadModule: "fbdevhw"
[    14.306] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.306] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.306]     compiled for 1.11.3, module version = 0.0.2
[    14.306]     ABI class: X.Org Video Driver, version 11.0
[    14.306] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    14.306] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    14.306] (==) NVIDIA(0): RGB weight 888
[    14.306] (==) NVIDIA(0): Default visual is TrueColor
[    14.306] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.306] (**) NVIDIA(0): Option "NoLogo" "True"
[    14.306] (**) NVIDIA(0): Enabling 2D acceleration
[    14.795] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (CRT-0)) does not support NVIDIA
[    14.795] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    14.796] (II) NVIDIA(0): NVIDIA GPU GeForce 8200 (C77) at PCI:2:0:0 (GPU-0)
[    14.796] (--) NVIDIA(0): Memory: 524288 kBytes
[    14.796] (--) NVIDIA(0): VideoBIOS: 62.77.29.00.01
[    14.796] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    14.797] (--) NVIDIA(0): Connected display device(s) on GeForce 8200 at PCI:2:0:0
[    14.797] (--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
[    14.797] (--) NVIDIA(0): Samsung SyncMaster (CRT-0): 300.0 MHz maximum pixel clock
[    14.825] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    14.825] (**) NVIDIA(0):     device Samsung SyncMaster (CRT-0) (Using EDID frequencies
[    14.825] (**) NVIDIA(0):     has been enabled on all display devices.)
[    14.829] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    14.829] (==) NVIDIA(0): 
[    14.829] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    14.829] (==) NVIDIA(0):     will be used as the requested mode.
[    14.829] (==) NVIDIA(0): 
[    14.829] (II) NVIDIA(0): Validated modes:
[    14.830] (II) NVIDIA(0):     "nvidia-auto-select"
[    14.830] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    14.863] (--) NVIDIA(0): DPI set to (95, 94); computed from "UseEdidDpi" X config
[    14.863] (--) NVIDIA(0):     option
[    14.863] (II) UnloadModule: "nouveau"
[    14.863] (II) Unloading nouveau
[    14.863] (II) UnloadModule: "vesa"
[    14.863] (II) Unloading vesa
[    14.863] (II) UnloadModule: "fbdev"
[    14.863] (II) Unloading fbdev
[    14.863] (II) UnloadModule: "fbdevhw"
[    14.863] (II) Unloading fbdevhw
[    14.863] (--) Depth 24 pixmap format is 32 bpp
[    14.863] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    14.866] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    14.891] (II) Loading extension NV-GLX
[    14.914] (==) NVIDIA(0): Disabling shared memory pixmaps
[    14.914] (==) NVIDIA(0): Backing store disabled
[    14.914] (==) NVIDIA(0): Silken mouse enabled
[    14.914] (==) NVIDIA(0): DPMS enabled
[    14.914] (II) Loading extension NV-CONTROL
[    14.915] (II) Loading extension XINERAMA
[    14.915] (II) Loading sub module "dri2"
[    14.915] (II) LoadModule: "dri2"
[    14.915] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.915] (II) Module dri2: vendor="X.Org Foundation"
[    14.915]     compiled for 1.11.3, module version = 1.2.0
[    14.915]     ABI class: X.Org Server Extension, version 6.0
[    14.915] (II) NVIDIA(0): [DRI2] Setup complete
[    14.915] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    14.915] (==) RandR enabled
[    14.915] (II) Initializing built-in extension Generic Event Extension
[    14.915] (II) Initializing built-in extension SHAPE
[    14.915] (II) Initializing built-in extension MIT-SHM
[    14.915] (II) Initializing built-in extension XInputExtension
[    14.915] (II) Initializing built-in extension XTEST
[    14.915] (II) Initializing built-in extension BIG-REQUESTS
[    14.915] (II) Initializing built-in extension SYNC
[    14.915] (II) Initializing built-in extension XKEYBOARD
[    14.915] (II) Initializing built-in extension XC-MISC
[    14.915] (II) Initializing built-in extension SECURITY
[    14.915] (II) Initializing built-in extension XINERAMA
[    14.915] (II) Initializing built-in extension XFIXES
[    14.915] (II) Initializing built-in extension RENDER
[    14.915] (II) Initializing built-in extension RANDR
[    14.915] (II) Initializing built-in extension COMPOSITE
[    14.915] (II) Initializing built-in extension DAMAGE
[    14.917] (II) Initializing extension GLX
[    14.931] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.933] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.933] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.933] (II) LoadModule: "evdev"
[    14.934] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.934] (II) Module evdev: vendor="X.Org Foundation"
[    14.934]     compiled for 1.11.3, module version = 2.7.0
[    14.934]     Module class: X.Org XInput Driver
[    14.934]     ABI class: X.Org XInput driver, version 16.0
[    14.934] (II) Using input driver 'evdev' for 'Power Button'
[    14.934] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.934] (**) Power Button: always reports core events
[    14.934] (**) evdev: Power Button: Device: "/dev/input/event1"
[    14.934] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.934] (--) evdev: Power Button: Found keys
[    14.934] (II) evdev: Power Button: Configuring as keyboard
[    14.934] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.934] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    14.934] (**) Option "xkb_rules" "evdev"
[    14.934] (**) Option "xkb_model" "pc105"
[    14.934] (**) Option "xkb_layout" "es"
[    14.935] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    14.936] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    14.936] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    14.936] (II) Using input driver 'evdev' for 'Video Bus'
[    14.936] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.936] (**) Video Bus: always reports core events
[    14.936] (**) evdev: Video Bus: Device: "/dev/input/event3"
[    14.936] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    14.936] (--) evdev: Video Bus: Found keys
[    14.936] (II) evdev: Video Bus: Configuring as keyboard
[    14.936] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/LNXVIDEO:00/input/input3/event3"
[    14.936] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    14.936] (**) Option "xkb_rules" "evdev"
[    14.936] (**) Option "xkb_model" "pc105"
[    14.936] (**) Option "xkb_layout" "es"
[    14.937] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.937] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.937] (II) Using input driver 'evdev' for 'Power Button'
[    14.937] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.937] (**) Power Button: always reports core events
[    14.937] (**) evdev: Power Button: Device: "/dev/input/event0"
[    14.937] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.937] (--) evdev: Power Button: Found keys
[    14.937] (II) evdev: Power Button: Configuring as keyboard
[    14.937] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    14.937] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    14.937] (**) Option "xkb_rules" "evdev"
[    14.937] (**) Option "xkb_model" "pc105"
[    14.937] (**) Option "xkb_layout" "es"
[    14.937] (II) config/udev: Adding input device zc3xx (/dev/input/event13)
[    14.937] (**) zc3xx: Applying InputClass "evdev keyboard catchall"
[    14.937] (II) Using input driver 'evdev' for 'zc3xx'
[    14.937] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.937] (**) zc3xx: always reports core events
[    14.937] (**) evdev: zc3xx: Device: "/dev/input/event13"
[    14.937] (--) evdev: zc3xx: Vendor 0xac8 Product 0x307b
[    14.937] (--) evdev: zc3xx: Found keys
[    14.937] (II) evdev: zc3xx: Configuring as keyboard
[    14.937] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-3/input/input13/event13"
[    14.937] (II) XINPUT: Adding extended input device "zc3xx" (type: KEYBOARD, id 9)
[    14.937] (**) Option "xkb_rules" "evdev"
[    14.937] (**) Option "xkb_model" "pc105"
[    14.937] (**) Option "xkb_layout" "es"
[    14.938] (II) config/udev: Adding input device HDA NVidia Speaker CLFE (/dev/input/event10)
[    14.938] (II) No input driver specified, ignoring this device.
[    14.938] (II) This device may have been added with another device file.
[    14.938] (II) config/udev: Adding input device HDA NVidia Speaker Surround (/dev/input/event11)
[    14.938] (II) No input driver specified, ignoring this device.
[    14.938] (II) This device may have been added with another device file.
[    14.938] (II) config/udev: Adding input device HDA NVidia Speaker Front (/dev/input/event12)
[    14.938] (II) No input driver specified, ignoring this device.
[    14.938] (II) This device may have been added with another device file.
[    14.938] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event5)
[    14.938] (II) No input driver specified, ignoring this device.
[    14.938] (II) This device may have been added with another device file.
[    14.938] (II) config/udev: Adding input device HDA NVidia Mic (/dev/input/event6)
[    14.938] (II) No input driver specified, ignoring this device.
[    14.938] (II) This device may have been added with another device file.
[    14.939] (II) config/udev: Adding input device HDA NVidia Dock Mic (/dev/input/event7)
[    14.939] (II) No input driver specified, ignoring this device.
[    14.939] (II) This device may have been added with another device file.
[    14.939] (II) config/udev: Adding input device HDA NVidia Dock Headphone (/dev/input/event8)
[    14.939] (II) No input driver specified, ignoring this device.
[    14.939] (II) This device may have been added with another device file.
[    14.939] (II) config/udev: Adding input device HDA NVidia Speaker Side (/dev/input/event9)
[    14.939] (II) No input driver specified, ignoring this device.
[    14.939] (II) This device may have been added with another device file.
[    14.939] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    14.939] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    14.939] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    14.939] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.939] (**) AT Translated Set 2 keyboard: always reports core events
[    14.939] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    14.939] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    14.939] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    14.939] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    14.939] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    14.939] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    14.939] (**) Option "xkb_rules" "evdev"
[    14.939] (**) Option "xkb_model" "pc105"
[    14.939] (**) Option "xkb_layout" "es"
[    14.940] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
[    14.940] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    14.940] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    14.940] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.940] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    14.940] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
[    14.940] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[    14.940] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    14.940] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    14.940] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[    14.940] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    14.940] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    14.940] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    14.940] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    14.940] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.940] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    14.940] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 11)
[    14.940] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    14.940] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    14.940] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    14.940] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    14.940] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    14.941] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    14.941] (II) No input driver specified, ignoring this device.
[    14.941] (II) This device may have been added with another device file.
[    15.617] (II) NVIDIA(0): Setting mode "1920x1080_60_0"
[    41.703] (II) NVIDIA(0): Setting mode "1280x800"
[    43.418] (II) XKB: reuse xkmfile /var/lib/xkb/server-718511B28EE83035776F86B5B8BD8C9A5D1FC433.xkm
[  6843.358] (II) XKB: reuse xkmfile /var/lib/xkb/server-718511B28EE83035776F86B5B8BD8C9A5D1FC433.xkm
[  9204.065] (II) XKB: reuse xkmfile /var/lib/xkb/server-718511B28EE83035776F86B5B8BD8C9A5D1FC433.xkm
[ 20321.247] (II) NVIDIA(0): Setting mode "960x600"
[ 20330.299] (II) NVIDIA(0): Setting mode "1280x800"
[ 21119.636] (II) XKB: reuse xkmfile /var/lib/xkb/server-718511B28EE83035776F86B5B8BD8C9A5D1FC433.xkm
[/HTML]

---

### Post by guillermolisi on 2012-05-10
Hay algun problema con el driver nVidia que esta o deberias estar utilizando. Por eso dice que no puede abrir correctamente el driver nv (da error indicado con EE en el log de Xorg).

Como este driver no funciono, el sistema intenta con el driver Noveau que, por ahora, ande bien pero sin aceleracion grafica para estas placas de video.

Una alternativa seria bajar el ultimo driver de nVidia, desinstalar el Noveau, instalar el descargado y volver a probar para ver que resultado se obtiene.

Si vas a la opcion de Drivers Privativos en la Configuracion del Sistema, que te dice ?

---

### Post by Lio56 on 2012-05-11
:( y yo que pense que se había instalado bien...
Bueno ahora cuando llego a casa te digo bien que hace...

Gracias por la paciencia
Saludos
Lio

---

### Post by Lio56 on 2012-05-30
Antes que nada pido disculpas por la demora de mi respuesta.

Me mude, en el trabajo me estan matando y encima tengo como 2 horas de viaje.

Hoy deberia tener algo de tiempo libre y voy a ver si avanzo con la instalación.

Saludos gracias

---

