---
title: "How do I enable DMA on my HDD? Ancient hardware EIDE"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by makkan77 on 2008-03-18
Recently I've come aware of what enabling DMA can do for your harddrive speed. I was really trying to disable DMA for a Compact Flash device when I returned to using the HDD I realized I wasn't using DMA in hdparm. 

Although hdparm /dev/hda gives me info that mdma2 is being used (marked with an asterisk) I get the following error message when I issue hdparm -d1 /dev/hda

HDIO_SET_DMA failed: Operation not permitted

So I googled and searched this forum and from what I've read one needs to either compile in some driver in the kernel or load the module at boot. Fair enough, I can do that. But then where do I get the information on what module I need to load? 

I read somewhere that I should lspci -v and look for the IDE part, but I have no such part. The computer I'm trying to do this on is an OLD Toshiba Laptop 233 MHz, 96MB RAM, EIDE 4GB HDD, built in CD-ROM/FLOPPY and so forth.

---

### Post by logos34 on 2008-03-18
try

**sudo** hdparm -d1 /dev/hda

it's probably an old dma/66 you have, not sure about module

---

### Post by makkan77 on 2008-03-18
That's what I have been trying, I just left out the sudo-part in my examples.

---

### Post by logos34 on 2008-03-18
check the Bios settings.

here are some commands that may help:

sudo lshw -C disk

sudo hdparm -v -i /dev/hda

lsmod | grep ata  (and/or ide)

---

### Post by makkan77 on 2008-03-18
```

sudo lshw -C disk

*-disk                  
       description: ATA Disk
       product: TOSHIBA MK4006MAV
       vendor: Toshiba
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: F2.03 A
       serial: 68Q31220
       size: 3909MB
       capacity: 3909MB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: smart=on
  *-cdrom
       description: IDE CD-ROM
       product: CD-220EA
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 7.1B
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
       configuration: status=nodisc

``` 

```

sudo hdparm -v -i /dev/hda

/dev/hda:
 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 unmaskirq     =  0 (off)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 7944/16/63, sectors = 8007552, start = 0

 Model=TOSHIBA MK4006MAV, FwRev=F2.03 A, SerialNo=68Q31220
 Config={ Fixed }
 RawCHS=7944/16/63, TrkSize=0, SectSize=0, ECCbytes=24
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=16
 CurCHS=7944/16/63, CurSects=8007552, LBA=yes, LBAsects=8007552
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 *mdma2 
 UDMA modes: udma0 udma1 udma2 
 AdvancedPM=no WriteCache=enabled

 * signifies the current active mode


```

```

lsmod | grep ide
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_generic             2176  0 [permanent]
ide_disk               18560  3 
ide_core              116804  3 ide_cd,ide_generic,ide_disk

```

(lsmod | grep ata yields nothing)

So there are my outputs but I'm still not sure what driver I might be missing or what I can do to turn on dma in hdparm.

---

### Post by logos34 on 2008-03-18
[http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance#I_get_.22Operation_not_permitted.22_errors_on_setting_DMA_.28-d1.29](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance#I_get_.22Operation_not_permitted.22_errors_on_setting_DMA_.28-d1.29)

Again, see if you can tweak your bios settings.  

But from your hdparm output, it looks as though ata33/udma2 is your limit.

---

