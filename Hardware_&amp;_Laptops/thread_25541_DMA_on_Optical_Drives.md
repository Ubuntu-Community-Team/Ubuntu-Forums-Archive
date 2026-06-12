---
title: "DMA on Optical Drives"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by Leebobs on 2005-04-10
I'm currently trying to enable DMA in 5.04 on both of my optical drives. Here is the state of play so far:

Device 1's info:
> dev/hda:

ATAPI CD-ROM, with removable media
        Model Number:       _NEC DVD_RW ND-2500A
        Serial Number:
        Firmware Revision:  1.0A
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 3ms.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns

And Drive two:
> /dev/hdb:

ATAPI CD-ROM, with removable media
        Model Number:       SAMSUNG CD-R/RW SW-252B
        Serial Number:
        Firmware Revision:  R704
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(can be disabled)
        DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 *udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    NOP cmd
           *    DEVICE RESET cmd
           *    PACKET command feature set
           *    Power Management feature set
HW reset results:
        CBLID- above Vih
        Device num = 1

However, whenever I try the following command:
$sudo hdparm -d1 /dev/hda

I get the following reponse:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

I have searched the forums and am seeing that a number of people are experiencing similar issues.

My Motherboard is a Abit AV8-3rd Eye based around a VIA K8T800 Pro chipset. And I have noticed a number of devices in "Device Manager" are reported as being Unknown.

Thanks for any help you may be able to offer

Leebobs

---

### Post by darkaudit on 2005-04-10
What type hard drive(s) are you running? I tried to set up a new machine with a SATA drive as the sole hard drive. I couldn't change any hdparm settings on the DVD burner with that setup.

I fixed that by adding the IDE drive that housed linux on my old system. Now I can change settings on my DVD burner again.

Main board is an Abit NF7-S v.2 with onboard Silicon Image SATA controller.

---

### Post by Leebobs on 2005-04-10
[QUOTE=darkaudit]What type hard drive(s) are you running? I tried to set up a new machine with a SATA drive as the sole hard drive. I couldn't change any hdparm settings on the DVD burner with that setup.

I fixed that by adding the IDE drive that housed linux on my old system. Now I can change settings on my DVD burner again.

Main board is an Abit NF7-S v.2 with onboard Silicon Image SATA controller.[/QUOTE]

I have one SATA Hdd using the onboard Silicone Image SATA controler  ](*,)

---

### Post by spirilis on 2005-04-10
[QUOTE=Leebobs]I have one SATA Hdd using the onboard Silicone Image SATA controler  ](*,)[/QUOTE]
 I noticed this too.  I couldn't set DMA on my DVD burner.  Are there any kernel updates we could try?

---

### Post by darkaudit on 2005-04-10
Looks like the system wants an IDE hard drive connected before one can adjust settings on an optical drive. Once I installed one, problems with the DVD burner went away.

---

### Post by Leebobs on 2005-04-10
[QUOTE=darkaudit]Looks like the system wants an IDE hard drive connected before one can adjust settings on an optical drive. Once I installed one, problems with the DVD burner went away.[/QUOTE]

But if we don't have an IDE hard drive... or if we have one and we instaled it as a secondary master (with or DVD-RW & CD-RW being primary mater / slave)... How can we fix it?

---

### Post by mjr on 2005-07-01
[QUOTE=darkaudit]Looks like the system wants an IDE hard drive connected before one can adjust settings on an optical drive. Once I installed one, problems with the DVD burner went away.[/QUOTE]

Can confirm that for me, too, setting DMA on my PATA DVD burner doesn't work after I switched hds to SATA. (Bugger.)

Does anyone know if this fixed in more recent kernels?

---

### Post by bigcletus on 2005-07-01
I am also having this problem.  Just bought a Plextor DVD R/W drive today and have been trying to get dma turned on with hdparm.  My system is as follows:

1 sata 120gig HD with Linux (/dev/sda)
1 ide 60gig HD with WinXP (/dev/hda1, hda5)

1 ide Plextor dvd drive (/dev/hdc)

If I comment out the ide modules in /etc/modules and restart, I can nolonger access my windows drive but I CAN enable dma on the DVD drive and 32bit I/O support.  I would like to be able to retain access to my second hd though  (the winxp disk) and be able to change dma settings on my drive.  I also noticed that this dvd drive has a jumper position for ultra dma...I wonder if I put a jumper on there and reboot if this will help any.

Any one care to add there help/input on this?  Thanks for any suggestions.

---

### Post by mjr on 2005-07-07
[QUOTE=mjr]Can confirm that for me, too, setting DMA on my PATA DVD burner doesn't work after I switched hds to SATA. (Bugger.)
[/QUOTE]

Hmpf. Removing the autoloading of ide modules and loading the manually afterwards seems to do the trick for me, too. Wonder why the heck.

---

