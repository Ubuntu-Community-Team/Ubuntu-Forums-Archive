---
title: "Problema con WiFi, Notebook Bangho"
date: 2010-10-02
forum: Hardware
---

### Post by KistIndigo on 2010-10-02
Buenas, me compré hace poco una Notebook Banghó FUTURA, que vino con Windows 7 Professional sin activar. Enseguida le metí Ubuntu Lucid 10.04.
**Grave error** tendria que haberme fijado antes que drivers utiliza, ya que ahora** no puedo hacer andar el WiFi, ni el Bluetooth.**
Intenté entrar desde su pagina web a ver, ya que en la seccion Drivers/Descargas si uno introduce el numero de serie de la maquina, nos dice que drivers necesita. Me larga un error de SQL ¬¬.

Bueno aca les dejo los comandos que veo que siempre piden en este foro a la hora de diagnosticar un problema como este. Al momento de hacer los mismos, estaban activados el WiFi (Fn+F11), el Bluetooth (Fn+F12), la camarita Web (Fn+F10) y desactivado el Touchpad (Fn+F1), porque me molesta a la hora de escribir. Ademas, tenia conectados en los usb un Mouse Genius y el cable que le da energia a los parlantes. La placa Ethernet funciona perfectamente, es la conexion que estoy usando para escribir esto.

[B]lsusb:
[/B]```
root@pedro-laptop:~# lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 5986:0241 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```[B]
lspci:
[/B]```
root@pedro-laptop:~# lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
0f:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
15:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
15:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
15:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
15:00.5 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 02)

```[B]lswh:
[/B]```
root@pedro-laptop:~# lshw
pedro-laptop              
    description: Computer
    product: M7x0K
    vendor: Bangho
    version: Rev 1
    serial: None
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific cpus=1 uuid=0090F5A1-6B09-0000-0000-000000000000
  *-core
       description: Motherboard
       product: M7x0K
       vendor: Bangho
       physical id: 0
       version: Rev 1
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 4.06 (02/25/2010)
          size: 112KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor TF-20
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          slot: Socket M2/S1G1
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             physical id: 0
             slot: S1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 [empty]
             physical id: 1
             slot: S2
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:9000(size=4096) memory:f0000000-f01fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:18 memory:d0000000-dfffffff memory:f0100000-f010ffff ioport:9000(size=256) memory:f0000000-f00fffff
           *-multimedia
                description: Audio device
                product: Radeon X1200 Series Audio Controller
                vendor: ATI Technologies Inc
                physical id: 5.2
                bus info: pci@0000:01:05.2
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=64
                resources: irq:19 memory:f0110000-f0113fff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-pci:2
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:3
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26
        *-pci:4
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:a000(size=4096) memory:f0200000-f02fffff
           *-network UNCLAIMED
                description: Network controller
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0f:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: ioport:a000(size=256) memory:f0200000-f0203fff
        *-pci:5
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:b000(size=4096) memory:f0300000-f03fffff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:15:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f0300000-f03000ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:15:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f0300400-f03004ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:15:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:f0300800-f03008ff
           *-network
                description: Ethernet interface
                product: JMC260 PCI Express Fast Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0.5
                bus info: pci@0000:15:00.5
                logical name: eth0
                version: 02
                serial: 00:90:f5:a1:6b:09
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.6 duplex=full ip=192.168.160.33 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:29 memory:f0304000-f0307fff ioport:b400(size=128) ioport:b000(size=256)
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8440(size=8) ioport:8434(size=4) ioport:8438(size=8) ioport:8430(size=4) ioport:8400(size=16) memory:f0609000-f06093ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVT-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXM1A60Y2973
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00050a0f
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: f3a4779b-fda4-4267-a6a1-426d4513477c
                   size: 227GiB
                   capacity: 227GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-09-24 17:51:23 filesystem=ext4 lastmountpoint=/{&:&#65533;&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h &#65533;&#65533;h/&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]k modified=2010-10-02 09:38:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-10-02 12:41:38 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 5152MiB
                   capacity: 5152MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5152MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DS8A4S
                vendor: Slimtype
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: JX11
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f0404000-f0404fff
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f0405000-f0405fff
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0406000-f0406fff
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f0407000-f0407fff
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0408000-f0408fff
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f0609400-f06094ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f0400000-f0403fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:6
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
```[B]sudo uname -r:
[/B]```
2.6.34-020634-generic
```Bueno, eso es todo, despues de merodear por internet buscando una solucion recurro a ustedes. En este merodeo por internet descubrí que la notebook que me vendieron es CHINA, solo las ensamblan en Argentina. :( me sentí estafado...
En fin, espero me puedan ayudar. Saludos!
--------------------------
Editado 02-Oct-2010 18:05

Gente, pude hacer andar el Wi-fi :guitar:
Solo tuve que instalar los drivers de mi placa, que era una Realtek, a pesar de que yo creia que era la JMicron. Ademas, aparentemente, el kernel que instalé para que anduviera la camarita web, no tenia los drivers de la placa wi-fi.

Sin embargo **no puedo hacer andar el Bluetooth**. :(. A continuacion les dejo como hice andar el Wi-Fi:

Seguí los pasos de estos dos blogs:
[http://blog.zorinholdings.com/post/501557101/lenovo-thinkpad-edge-wifi-with-ubuntu-10-04](http://blog.zorinholdings.com/post/501557101/lenovo-thinkpad-edge-wifi-with-ubuntu-10-04)
[http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html](http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html)

Es asi:

1) Bajar los drivers de este link: [http://www.megaupload.com/?d=RRIB3XDA](http://www.megaupload.com/?d=RRIB3XDA)
1)a) Yo apenas lo descargué lo puse en mi carpeta personal /home/*mi_usuario*/ asi era mas facil de encontrar
2) En terminal convertirse en super usuario *# sudo su*
3) Descomprimir el archivo descargado *# tar zxvf /home/[I]mi_usuario*/rtl8192se_linux_2.6.0017.0705.2010.tar.gz[/I]
4) Me posicione en el directorio [I]# cd rtl8192se_linux_2.6.0017.0705.2010/
[/I]5) Compilar:
[I]# make
# make install
[/I]6) Reinicié la Notebook
7) Disfrutar el Wi-Fi :popcorn:

---

### Post by guillermolisi on 2010-10-02
Me parece que, de haber Blutooth en esa maquina, es JMicron ya que es la unica placa PCI que quedo UNCLAIMED despues de haber instalado los drivers de Realtek.

Podrias confirmar esto ?

PS: Practicamente no hay hardware en el mundo que no este hecho en China y practicamente todas las marcas ensamblan con las honrosas pocas excepciones de aquellas que diseñan algunas cositas que los chinos se encargan de implementar.

---

### Post by asterix77 on 2010-10-04
Con respecto al bluetooth, pega lo que te arroja los siguientes comandos:

#sudo bluetoothd -nd
#lsmod
#hciconfig -a                  ("hciconfig hci0 up" levanta la interfaz)

Puede dar esto una pista si tu dispositivo es reconocido, o si está cargado el módulo.

Saludos

---

### Post by sys.adm.og on 2010-10-05
Seguramente necesitaras cargar algún módulo.
Intenta cargar el módulo de la siguiente forma 
```
modprobe bluetooth
```

instala esto:
```
apt-get install gnome-bluetooth libbluetooth7
```

libgnome-bluetooth7                                                    - Herramientas Bluetooth de GNOME

Usualmente viene por defecto pero no esta demas verificar :guitar:

---

### Post by guillegauna on 2010-10-13
yoo lo pude solucionar, el problema es qee no están los drivers para todas las versiones de linux...

En mi casa, la netbook vino con un 3dsp, qe es un dispositivo qe tiene integrado wifi y bluetooth!!

buscalo en google, ii está en chino o japonés la pag..

por ahí te sirve...

Abraso che!

---

### Post by guillermolisi on 2010-10-14
3DSP es una interface distinta de JMicron y tambien distinta de la Realtek, distintos fabricantes, distintos drivers.

KistIndigo, seria clarificador ver la salida del comando "lsmod" (sin las comillas teniendo la maquina en red via el cable Ethernet. De esa forma podremos saber si la placa WiFi es Realtek o JMicron (por descarte).

---

### Post by sys.adm.og on 2010-10-14
Seria bueno que prepares un post o bien des la la forma en que solucionaste asi si a alguien le ocurre lo mismo o algo similar pueda encontrar o bien tener una guia para la solución!

Felicitaciones!

---

### Post by guillermolisi on 2010-10-14
> **sys.adm.og said:**
> Seria bueno que prepares un post o bien des la la forma en que solucionaste asi si a alguien le ocurre lo mismo o algo similar pueda encontrar o bien tener una guia para la solución!

Felicitaciones!
Con los drivers para 3DSP solo hay que descomprimir el tarball y correr el instalador con privilegios de superusuario (esto en una terminal/consola).

Si cambia el kernel es probable que el driver deje de funcionar, aun reinstalando, ya que cualquier modificacion en los headers del kernel hacen que la compilacion de error. Cuando esto sucede hay que esperar a que el fabricante libere una nueva version y reinstalar, mientras podes seguir usando el kernel anterior (si no se desinstalo) para que funcionen las interfaces WiFi y Bluetooth de 3DSP.

---

### Post by sys.adm.og on 2010-10-14
> **guillermolisi said:**
> Con los drivers para 3DSP solo hay que descomprimir el tarball y correr el instalador con privilegios de superusuario (esto en una terminal/consola).

Si cambia el kernel es probable que el driver deje de funcionar, aun reinstalando, ya que cualquier modificacion en los headers del kernel hacen que la compilacion de error. Cuando esto sucede hay que esperar a que el fabricante libere una nueva version y reinstalar, mientras podes seguir usando el kernel anterior (si no se desinstalo) para que funcionen las interfaces WiFi y Bluetooth de 3DSP.

Excelente explicación, mas queria el enfoque para usuario comun ya que lo del kernel y la compilacion no creo que sea un fuerte para ellos!!

Me gustaria consultarte algo Guillermo pero no puedo escribirte aun como puedo contactarte?

---

