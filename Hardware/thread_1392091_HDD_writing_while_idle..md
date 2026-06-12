---
title: "HDD writing while idle."
date: 2010-01-27
forum: Hardware
---

### Post by jonazzz on 2010-01-27
Hello, Im new to this forum and Ubuntu. I finally took the step to get rid of windows.
 
I got everything working as it should. But I have a question, i recently bought a new HDD its a Hitachi 1TB SATA2. (Im using a desktop computer)
 
Is it normal that ubuntu write to the drive while idle? It sounds like its writing for about 5-10 sec... then it stops for about 5 sec... and resumes again, and after about 30 minutes of that its silent. After about 30 minutes it starts again.
 
Its formatted in ext3 with one giant partition and ofc one for swap.

---

### Post by MaindotC on 2010-01-27
I wouldn't say this is normal.  I don't know much about SATA2 and any modules that are available for it so i'll just ask some basic questions.  How much memory do you have?  Also post the output of:
```

lshw -c storage

```

---

### Post by AlexZaim on 2010-01-27
It's a normal thing to have it do some activities once in a while. Try seeing from the system monitor which processes are actvie when you hear the sound.

When do you hear that its working? Is it on startup?

If yes, it may be the update notifier . And if it bothers you a lot: 
go to System>preferences>startup applications and uncheck the update notifier. You'll have to do your updates manualy after this.

---

### Post by jonazzz on 2010-01-27
I have 2GB of RAM. I dont hear the sound on startup its only when the computer has been idle for a while. Ah... I will check processes next time, why didnt I think of that :P.


This is the output:

   ```
*-ide:0                 
       description: IDE interface
       product: CK804 IDE
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: scsi5
       version: f2
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
       resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e000(size=16)
  *-ide:1
       description: IDE interface
       product: CK804 Serial ATA Controller
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: scsi0
       logical name: scsi1
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
       resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:cc00(size=16) memory:fe02b000-fe02bfff
  *-ide:2
       description: IDE interface
       product: CK804 Serial ATA Controller
       vendor: nVidia Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: scsi3
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
       resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:b800(size=16) memory:fe02a000-fe02afff
  *-scsi
       physical id: 10
       bus info: usb@1:5
       logical name: scsi6
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
```

---

### Post by MaindotC on 2010-01-28
> **jonazzz said:**
> 
   ```
*-ide:0                 
       description: IDE interface
       product: CK804 IDE
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: scsi5
       version: f2
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: **driver=pata_amd** latency=0 maxlatency=1 mingnt=3
       resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e000(size=16)
  *-ide:1
       description: IDE interface
       product: CK804 Serial ATA Controller
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: scsi0
       logical name: scsi1
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: **driver=sata_nv** latency=0 maxlatency=1 mingnt=3
       resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:cc00(size=16) memory:fe02b000-fe02bfff
  *-ide:2
       description: IDE interface
       product: CK804 Serial ATA Controller
       vendor: nVidia Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: scsi3
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: **driver=sata_nv** latency=0 maxlatency=1 mingnt=3
       resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:b800(size=16) memory:fe02a000-fe02afff
  *-scsi
       physical id: 10
       bus info: usb@1:5
       logical name: scsi6
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
```

You'll need to search for information on these modules to see if they support SATA2.

---

### Post by jonazzz on 2010-01-28
> **strAlan said:**
> You'll need to search for information on these modules to see if they support SATA2.
 
 
I think they support SATA 2, but now im unsure if my motherboard support SATA 2. It doesnt matter though, caus SATA Gen 1 is compatible with SATA 2. Its just the data transfer rate thats higher on SATA 2. I will set this thread to solved now. I dont think its really a problem. But thanks for your time. 
 
Btw... How do i set this thread to solved? :)

---

### Post by MaindotC on 2010-01-28
If you think the data transfer rate is a problem there should be some jumpers on the HD that allow you reduce the transfer rate.

---

### Post by jonazzz on 2010-01-28
> **strAlan said:**
> If you think the data transfer rate is a problem there should be some jumpers on the HD that allow you reduce the transfer rate.

It seems like my problem has somehow resolved itself. The HDD does not write anymore while in idle mode. Strange... :P

---

### Post by efflandt on 2010-01-29
Drive activity could be anything from logging, delayed disk writes, or locatedb updating its index of all of your files (for locate command).  At least it does not bog your system like file indexing can in Windows.

---

