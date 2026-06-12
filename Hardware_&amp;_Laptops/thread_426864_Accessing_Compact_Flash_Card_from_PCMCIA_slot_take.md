---
title: "Accessing Compact Flash Card from PCMCIA slot takes forever!"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by kevdog on 2007-04-28
Wow - I thought this was going to be a lot easier than this!

Currently using Kubuntu Feisty on Dell 5000e Laptop and trying to access Lexar CF card via PCMCIA slot with CF card adapter

What I did:

sudo mkdir /media/cf
Inserted CF Card
sudo fdisk -l
   After about 5 minutes the CF card was finally listed as /dev/sda1 with the following:

sk /dev/sda: 2052 MB, 2052513792 bytes
64 heads, 63 sectors/track, 994 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         994     2003872+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(903, 63, 63) logical=(993, 63, 63)

I then went to mount the device:
sudo mount /dev/sda1 /media/cf
This process took like 5 minutes

I am now able to read via command line from the card although it is extremely slow
Konqueror however crashes when trying to access the device.  What I want to do is to see the thumbnail pictures on the card similar to Windows Explorer.

Any ideas on why the card is so slow????

---

### Post by kevdog on 2007-04-28
Yet another problem, when booting with the card in the adapter the computer hangs during the boot process.  Im not sure if the system is trying to automount the compact flash card but something is wrong!

In additon after taking the card/with adapter out of the slot, the  computer will boot.  Inserting the card it is recognized with the fdisk -l command, and the computer tries to automount it with under /media/Lexar\ Media.  
The problem however is that I can not enter the directory. 

sudo cd Lexar\ Media -> returns command not found.

Is there a bug with Feisty or is this typical???

---

### Post by kevdog on 2007-04-29
Does anyone know if there has been any progress made with this PCMCIA bug??

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg300693.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg300693.html)

---

### Post by kevdog on 2007-05-03
Well I guess I will give up on this for now.  It seems like others may be having this problem too from perusal of the forums.  Google doesnt give any help.

If anyone could just confirm if there are problems accessing a compact flash drive via a compact flash adapter that plugs into the PCMCIA slot it would ease my mind.

Thanks

---

### Post by scottpreston on 2007-05-08
I was able to install using the Alternate Version of the distro. You can checkout the steps I used here

[http://www.scottsbots.com/articles/17.php]("http://www.scottsbots.com/articles/17.php")

Good Luck.

---

### Post by kevdog on 2007-05-09
More details since I cant seem to find a lot of other people with the same problem!

My PCMCIA card bus is made by Texas Instrument (TI). Its not that the drive wont mount manually or it cant be accessed after mounting, its just that it is terribly slow -- access time takes like 10 minutes to bring up 15 thumbnails.

I have a USB CF reader, this works normally -- the Lexar compact flash card is mounted automatically and directory access is just a few seconds.

Dmesg gives no indication why the access time on the PCMCIA card bus is so slow.

I have a feeling its a bug with the PCMCIA utils module but can not prove this. There are just a small scattered posts in this forum and on the web giving hints of this problem.

What else can I do at this stage???:confused:

---

### Post by yottabit on 2008-01-20
I'm using an IBM/Lenovo Thinkpad T60 with Ubuntu 7.10. I have a Sandisk Ultra II 1 GB CF inserted into a Sandisk CF-to-PCMCIA adapter sled. When copying files from the flash disk to the hard disk both CPU cores go to 100%, IOWait goes to 90%+, and the entire system slows to a crawl. Transfers take FOREVER. (In Windows XP none of this behavior is exhibited and the transfer speed is very fast.)

I tried setting DMA enable on the device:
```
# hdparm -d1 /dev/sdb

/dev/sdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

More pertinent information:
```
# lspci
...
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
```
```
# dmesg
...
[153822.604000] pcmcia: registering new device pcmcia0.0
[153822.972000] scsi6 : pata_pcmcia
[153822.972000] ata7: PATA max PIO0 cmd 0x00019100 ctl 0x0001910e bmdma 0x00000000 irq 3
[153823.136000] ata7.00: CFA: SanDisk SDCFH-1024, HDX 2.18, max PIO4
[153823.136000] ata7.00: 2001888 sectors, multi 0: LBA 
[153823.144000] ata7.00: configured for PIO0
[153823.144000] scsi 6:0:0:0: Direct-Access     ATA      SanDisk SDCFH-10 HDX  PQ: 0 ANSI: 5
[153823.144000] sd 6:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[153823.144000] sd 6:0:0:0: [sdb] Write Protect is off
[153823.144000] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[153823.144000] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[153823.144000] sd 6:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[153823.144000] sd 6:0:0:0: [sdb] Write Protect is off
[153823.144000] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[153823.144000] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[153823.144000]  sdb: sdb1
[153823.168000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[153823.168000] sd 6:0:0:0: Attached scsi generic sg2 type 0
```
```
# pccardctrl ls
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:15:00.0)
Socket 0 Device 0:      [pata_pcmcia]           (bus ID: 0.0)
```
```
# pccardctl info
PRODID_1="SanDisk"
PRODID_2="SDP"
PRODID_3="5/3 0.6"
PRODID_4=""
MANFID=0045,0401
FUNCID=4
```
```
# pccardctl status
Socket 0:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "pata_pcmcia"
```
```
# pccardctl ident
Socket 0:
  product info: "SanDisk", "SDP", "5/3 0.6", ""
  manfid: 0x0045, 0x0401
  function: 4 (fixed disk)
```

Obviously the problem is that the driver says the disk is only capable of PIO1 mode, instead of DMA... Any ideas how to get it to properly switch to DMA transfers?

J

---

### Post by pfps on 2008-03-22
This is a known long-standing problem.  I'm experiencing it on my T60p running Fedora 8.

It may be a BIOS problem.  I'm communicating with some kernel people to find out how to report it to Lenovo, see the thread [http://lkml.org/lkml/2008/3/20/304](http://lkml.org/lkml/2008/3/20/304)

Peter F. Patel-Schneider

---

### Post by kevdog on 2008-03-22
Thanks for the update -- I gave up after a while and bought a USB device to transfer the info!

---

### Post by yottabit on 2008-03-22
> **pfps said:**
> This is a known long-standing problem.  I'm experiencing it on my T60p running Fedora 8.

It may be a BIOS problem.  I'm communicating with some kernel people to find out how to report it to Lenovo, see the thread [http://lkml.org/lkml/2008/3/20/304](http://lkml.org/lkml/2008/3/20/304)

Peter F. Patel-Schneider

It's a kernel problem... I read a thread that even 2.6.24 is affected and the fixes haven't made it into even the most recent minors yet... but at least Linus has acknowledged the problem. It all goes back to the old PCMCIA (not even CardBus) Type III HDDs... PIO0 or PIO1... ;)

Sooner or later it will work!

---

### Post by kevdog on 2008-03-22
Thanks for the updates guys.  I thought I might have been the only one with the problem.  Hopefully someone is working on it.  Its rather annoying.

---

