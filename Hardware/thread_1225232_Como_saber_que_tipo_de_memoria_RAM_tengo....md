---
title: "Como saber que tipo de memoria RAM tengo...???"
date: 2009-07-28
forum: Hardware
---

### Post by dcorrea on 2009-07-28
hola a todos!!!
Necesito "ampliar" mi memoria RAM y necesito saber de que tipo es...DDR2, DD"3 y su velocidad...existe algun modo de saberlo sin tener que abrir el PC?

Saludos!!!

---

### Post by docetrago on 2009-07-28
Hi, dcorrea !

You should key the following command on the terminal :

sudo lshw

It asks for your password.

Then, copy and paste the results here.

Thanks !

---

### Post by dcorrea on 2009-07-28
aqui esta lo solicitado....
es un poco largo...lo estoy revisando en estos momentos...
me interesa saber que tipo de memoria ram utiliza....y hasta que velocidad puedo hacer un upgrade. 
Es posible saberlo?

muchas gracias

```
 description: Desktop Computer
    product: ISTART 7095
    vendor: PACKARD BELL BV
    version: PB49304120
    serial: 126535420301
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=3C621914-3C48-DB11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: GA-8TRC410M-NF
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 20Q (07/19/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D  CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          slot: Socket 775
          size: 2666MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          description: CPU
          vendor: Intel
          physical id: 5
          bus info: cpu@1
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          slot: Socket 775
          size: 2666MHz
          capacity: 4GHz
          clock: 133MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci agp agp-2.0 bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=64 mingnt=8
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: ATA Disk
                product: ST3250820AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 4QE03S2M
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=63fb63fb
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: cc82-422b
                   size: 5130MiB
                   capacity: 5130MiB
                   capabilities: primary hidden fat initialized
                   configuration: FATs=2 filesystem=fat label=BACKUP
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 2261b3fe-1752-1c44-9aaa-362f21656cea
                   size: 113GiB
                   capacity: 113GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-08-21 08:17:08 filesystem=ntfs label=Disco C: state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   size: 113GiB
                   capacity: 113GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 88GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 19GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 2023MiB
                      capabilities: nofs
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 4879MiB
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ohci_hcd latency=64
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ohci_hcd latency=64
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 82
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GSA-H22N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [HL-DT-STDVD-RAM GSA-H22N1.0006/08/05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
           *-communication
                description: Modem
                product: SM56 Data Fax Modem
                vendor: Motorola
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
           *-multimedia
                description: Multimedia controller
                product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 1
                bus info: pci@0000:02:01.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=64 maxlatency=38 mingnt=15 module=saa7134
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:16:e6:92:8a:7f
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
     *-scsi
          physical id: 1
          bus info: usb@2:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:41:53:4b:14:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by aledruetta on 2009-07-28
Existen dos herramientas gráficas en Ubuntu que son: Hardinfo y Sysinfo. Podrías probar si alguna de ellas te da la información que estás buscando.
```
sudo aptitude install hardinfo sysinfo
```
Sysinfo aparece en el menú Aplicaciones-->Herramientas del Sistema.
A Hardinfo hay que llamarlo por consola:
```
sudo hardinfo
```

Suerte,
Alejandro.

---

### Post by docetrago on 2009-07-28
I googled for your motherboard specs in order to find its user's manual, but I'm not sure if it's correct, once the link states a slightly different model ( Rio ).

It seems your motherboard has a DDR2 memory bank, but I recommend to check this link and confirm by yourself :

[http://support.packardbell.com/uk/item/index.php?i=spec_Rio&ppn=PB34305801](http://support.packardbell.com/uk/item/index.php?i=spec_Rio&ppn=PB34305801)

In order to protect your private data, I recommend to use the command lshw as follows :

sudo lshw -sanitize

This option "-sanitize" removes all the serial info on output, if you prefer.

---

### Post by Carlos C on 2009-08-01
> **docetrago said:**
> 

In order to protect your private data, I recommend to use the command lshw as follows :

sudo lshw -sanitize

This option "-sanitize" removes all the serial info on output, if you prefer.

Buenísimo. Gracias por el dato! :)

---

### Post by euteliamartinez on 2010-10-22
dmidecode --type 17

Y obtendrás una salida similar a la siguiente:

SMBIOS 2.5 present.

Handle 0x000C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    ***[COLOR=Blue]Type: DDR2[/COLOR]***
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x000E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

> **dcorrea said:**
> hola a todos!!!
Necesito "ampliar" mi memoria RAM y necesito saber de que tipo es...DDR2, DD"3 y su velocidad...existe algun modo de saberlo sin tener que abrir el PC?

Saludos!!!

---

