---
title: "[SOLVED] SATA devices (HDD &amp;amp; DVD drives) are not detected"
date: 2008-07-13
forum: Hardware
---

### Post by delirium83 on 2008-07-13
Hi,

I have a problem with SATA devices. I have a SATA HDD and a SATA DVD-Burner which both work fine in Windows Vista. Unfortunately both don't have an entry in /dev so I am unable to mount & use them. I run Kubuntu from an IDE HDD, a second IDE HDD is detected as well.

I recently exchanged my mainboard, CPU, memory and Graphics ( reinstalled Kubuntu afterwards ). With the old hardware the HDD worked fine in Kubuntu so it's in general possible to get it to work ( the HDD worked out of the box and I didn't have the DVD-Burner hence couldn't test it back then ). See the end of the post for hardware details!

The following command outputs show the Windows Vista ( IDE-HDD, sda ) and Kubuntu ( IDE-HDD, sdb ) drives only, but no sign of the SATA devices:

```

$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba378777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5221    41937651    7  HPFS/NTFS
/dev/sda2            5222       19458   114344960    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb83c8062

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris
```
```

$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb5
```

dmesg does not show any activity when hot plugging the SATA-HDD either.


Do you guys have any ideas about what's wrong here?


I am using the 32 Bit Version of Kubuntu 8.04.1, kernel 2.6.24-19-generic, everything is updated.
My hardware is:
Mainboard: MSI P43 Neo-f
Processor: Core2Duo E8400
Memory: 4GB 800Mhz
Graphics: ATI HD4850, using proprietary driver

If further info is necessary please ask for it (please post the commands necessary to obtain the info as I am not completely used to linux yet)

---

### Post by tech0007 on 2008-07-13
Run 'dmesg | grep ata'.  It should show info about your sata devices. My optical drives show up as /dev/scd*.

---

### Post by delirium83 on 2008-07-13
First of all thank you for your fast reply tech0007!

Another detail about my hardware: I have six SATA connectors on my mainboard and use the ones labeled 5 and 6 for the two mentioned drives... but that hopefully does not matter as I want to be able to use all connectors anyway!


just to make sure I checked
```
$ ls /dev/s*
/dev/sda   /dev/sda2  /dev/sdb1  /dev/sdb5       /dev/sequencer2  /dev/sg1       /dev/sndstat  /dev/stdin
/dev/sda1  /dev/sdb   /dev/sdb2  /dev/sequencer  /dev/sg0         /dev/snapshot  /dev/stderr   /dev/stdout
```

so there are no devices named like yours.

```

$ dmesg | grep ata -i
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[   19.148678] Memory: 3098212k/4194304k available (2177k kernel code, 45764k reserved, 1006k data, 368k init, 2227776k highmem)
[   19.148686]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   19.741924] Error attaching device data
[   19.741948] Error attaching device data
[   19.741969] Error attaching device data
[   19.741991] Error attaching device data
[   22.014193] libata version 3.00 loaded.
[   22.117959] scsi0 : pata_jmicron
[   22.118134] scsi1 : pata_jmicron
[   22.118415] ata1: PATA max UDMA/100 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 16
[   22.118418] ata2: PATA max UDMA/100 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 16
[   22.293329] ata1.00: ATA-7: SAMSUNG SP1614N, TM100-31, max UDMA/100
[   22.293332] ata1.00: 312581808 sectors, multi 16: LBA48
[   22.294258] ata1.01: ATA-5: WDC WD400EB-00CPF0, 06.04G06, max UDMA/100
[   22.294260] ata1.01: 78165360 sectors, multi 16: LBA
[   22.302324] ata1.00: configured for UDMA/100
[   22.319072] ata1.01: configured for UDMA/100
[   22.472596] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP1614N  TM10 PQ: 0 ANSI: 5
[   22.472659] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5
[   32.845447] EXT3-fs: mounted filesystem with ordered data mode.
```

mainly shows the two IDE devices I guess. The lines around the "Error attaching device data" are
```

$ dmesg | grep 'Error attaching device' -B 7 -A 20
[   19.736558] ACPI: bus type pci registered
[   19.736654] PCI: Using configuration type 1
[   19.736670] Setting up standard PCI resources
[   19.739153] ACPI: EC: Look up EC in DSDT
[   19.741809] ACPI: Interpreter enabled
[   19.741810] ACPI: (supports S0 S1 S3 S4 S5)
[   19.741819] ACPI: Using IOAPIC for interrupt routing
[   19.741924] Error attaching device data
[   19.741948] Error attaching device data
[   19.741969] Error attaching device data
[   19.741991] Error attaching device data
[   19.746041] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.747274] PCI: Transparent bridge - 0000:00:1e.0
[   19.747297] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.747390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   19.747469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   19.747522] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   19.747576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   19.749898] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[   19.749973] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[   19.750047] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 *14 15)
[   19.750121] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 14 *15)
[   19.750195] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[   19.750269] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 *11 12 14 15)
[   19.750342] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[   19.750415] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *6 7 10 11 12 14 15)
[   19.750487] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  69, should be 64 [20070126]
[   19.750492] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.750507] pnp: PnP ACPI init
[   19.750512] ACPI: bus type pnp registered
[   19.752840] pnp: PnP ACPI: found 16 devices
```


I'm not sure whether it's of any use, but some more outputs:
```

$ sudo lshw -C disk -C storage
  *-ide
       description: IDE interface
       product: JMB368 IDE controller
       vendor: JMicron Technologies, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: scsi0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm pciexpress bus_master cap_list emulated
       configuration: driver=pata_jmicron latency=0 module=pata_jmicron
     *-disk:0
          description: ATA Disk
          product: SAMSUNG SP1614N
          physical id: 0.0.0
          bus info: scsi@0:0.0.0
          logical name: /dev/sda
          version: TM10
          serial: S016JR0P300189
          size: 149GiB (160GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=ba378777
     *-disk:1
          description: ATA Disk
          product: WDC WD400EB-00CP
          vendor: Western Digital
          physical id: 0.1.0
          bus info: scsi@0:0.1.0
          logical name: /dev/sdb
          version: 06.0
          serial: WD-WCAAT6637408
          size: 37GiB (40GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=b83c8062
  *-ide:0 UNCLAIMED
       description: IDE interface
       product: ICH10 4 port SATA IDE Controller
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm cap_list
       configuration: latency=0
  *-ide:1 UNCLAIMED
       description: IDE interface
       product: ICH10 2 port SATA IDE Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm cap_list
       configuration: latency=0
```
maybe the '*-ide:0 UNCLAIMED' (ide:1 respectively) are the controllers for my SATA ports? I'm not sure what UNCLAIMED means in this context...

```

$ lspci -vvv | grep ata -iA12
00:1f.2 IDE interface: Intel Corporation ICH10 4 port SATA IDE Controller (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7519
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 20
        Region 0: I/O ports at a000 [size=8]
        Region 1: I/O ports at 9c00 [size=4]
        Region 2: I/O ports at 9880 [size=8]
        Region 3: I/O ports at 9800 [size=4]
        Region 4: I/O ports at 9480 [size=16]
        Region 5: I/O ports at 9400 [size=16]
        Capabilities: <access denied>

--
00:1f.5 IDE interface: Intel Corporation ICH10 2 port SATA IDE Controller (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7519
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 20
        Region 0: I/O ports at 9000 [size=8]
        Region 1: I/O ports at 8c00 [size=4]
        Region 2: I/O ports at 8880 [size=8]
        Region 3: I/O ports at 8800 [size=4]
        Region 4: I/O ports at 8480 [size=16]
        Region 5: I/O ports at 8400 [size=16]
        Capabilities: <access denied>
```

---

### Post by delirium83 on 2008-07-14
any more ideas anyone (aka bump)

---

### Post by markbuntu on 2008-07-14
SATA drives are generally recognized as scsi devices and mounted as sda, sdb, etc.

[   22.472596] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP1614N  TM10 PQ: 0 ANSI: 5
[   22.472659] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400EB-00CP 06.0 PQ: 0 ANSI: 5

are these them?

---

### Post by delirium83 on 2008-07-15
no, these are the Windows and Kubunut IDE HDDs. Missing is a 500GB Samsung hd501lj HDD as well as a LG DVD-Burner.

It seems like SATA is somehow disabled a none of the SATA but all other drives are recognized

---

### Post by delirium83 on 2008-07-15
*sortof bumping*

I just replugged both devices to use SATA ports 1 & 2 instead of 5 & 6, but the picture stays the same... still no sign of the two drives. It is possible to switch SATA off and on in general? I mean apart from recompiling the kernel ( I assume the generic kernel comes with SATA support?)?

---

### Post by markbuntu on 2008-07-15
I read somewhere that there are some bios issues with a few of the newer mobos that cause linux to not recognize the lower SATA ports, only 5 and 6. There is a workaround. 

I'm sorry that I cannot remember where I saw that.

Try a google search.

---

### Post by jimv on 2008-07-15
It could be that Ubuntu doesn't have the correct drivers for SATA support on your motherboard.  If you go into your BIOS, there should be an spot where you can set your SATA mode to IDE, so Ubuntu will read them as IDE drives instead of SATA.

---

### Post by SeePU on 2008-07-15
How did you connect your drives including your SATA drives?  

I don't think it has to do with Ubuntu and support of SATA drivers.  Either the SATA drives can be used in AHCI mode (using SATA controllers of the motherboard) which is only an issue for very older distros with older kernels and XP (long story) or IDE-emulation mode.

I think the problem has to do with setup of using both IDE and SATA  but it will be helpful if you go check your BIOS settings.  Post what setting you have your HDDs using or set for.  s

I have one suggestion for you but it might be a bit of trouble for you.  I would disconnect my IDE drives and just connect one SATA drive and see if you can install Ubuntu on one.  That is, if you have nothing (i.e. no data) on the SATA drive.  If you know they are working properly, note the BIOS setting and add an IDE drive and so on.  

I think there is an issue when combining IDE and SATA drives in Linux but there is a definite workaround.

---

### Post by delirium83 on 2008-07-16
@markbuntu: I tested port 5&6 as well as 1&2 so this is probably not the problem.

@jimv: The only setting corresponding to what you said is called "Raid Mode" and is already set to IDE. I read somewhere that some people had to set a setting in their BIOS to AHCI to get it to work, but my BIOS does not give me any options there, IDE is the only choice (I already asked in the manufacturer's forums whether that is normal or a defect as it shows the AHCI option in the handbook... I am still waiting for an answer there ).

@SeePU: as mentioned above to jimv unfortunately I cannot set AHCI mode in my BIOS but only IDE. I tried disconnecting my IDE HDDs and boot a live CD but the behaviour was the same as with the IDEs attached. The LiveCD would not boot as it does not detect the SATA-DVD-Burner and sends me to busybox.

what exactly do you mean by how I connected them? The two working IDE HDDs are attached to the only IDE controller as master and slave and I tested the SATA drives on ports 1 & 2 respective 5 & 6.

---

### Post by SeePU on 2008-07-17
I will guess that you can use AHCI but not RAID.   The 'R' that is at the end of ICH Intel mobos means that the board is capable of supporting RAID and SATA hard drives in RAID configurations.   AHCI is just a mode that supports SATA2 hard drives.   Don't worry about that.   You just need to find where the BIOS setting is to enable it if you want to use it.   Windows is a different story there, though.   It's supported out of the box for Vista so if that is the Windows OS you use, you will have no problem there.  I would concentrate on using the SATA HDDs in IDE-emulation mode for now.  

As for your other problem of SATA DVD detection and your overall detection of the SATA drives in Kubuntu, I still am not sure.   I wonder if it is a mounting problem for seeing the drives.   Does Gparted and/or KwikDisk 'see' the SATA drives?  

If you cannot get the LiveDVD or LiveCD to boot up, do you know if you have the BIOS setting to detect the DVD device first?   Sorry if you already do.  I am just trying to cover every angle.   I would re-check the connection of the SATA drive.   Which DVD drive are you using?   Kubuntu shouldn't have any issues with SATA devices.   There might be a trick to combining IDE and SATA drives but you should be able to boot up a liveCD/DVD with a SATA DVD drive as long as the CD/DVD burn was good.  I hope I gave you a good idea of what to try.  If I think of anything else that might help, I'll repost.

---

### Post by delirium83 on 2008-07-17
OK, the problem is solved \\:D/. I updated the BIOS from version 1.1 to 1.3 and had the AHCI option afterwards. Switched "Raid Mode" setting from IDE to AHCI and everything is instantly recognized!

Thank you all for your ideas and help!
=D

PS: MSI's customer support is awesome! They answered both of my requests within only several hours giving detailed information on what to try in which order.

-------------------------------------------------------------------


The problem is that the BIOS setting to switch AHCI on does not exists ;) It's there, but I can only select IDE, nothing else... MSI customer support told me to update my BIOS which I will do today.

gparted does not see the SATA drives, kwikdisk crashed on start.

With "BIOS setting to detect the DVD device first?" I guess you mean the boot device order? Yes, I boot from DVD, then it loads a little and then sends me to a busybox command line.

Plug connection is fine for both devices.

The DVD burner is a LG GH-20NS, the not detected HDD a Samsung HD501LJ.

The DVD itself is OK, I already installed from it before switching to the new mainboard (with which the SATA DVD drive came) and I handle my DVDs very carefully so it has no scratches.

---

