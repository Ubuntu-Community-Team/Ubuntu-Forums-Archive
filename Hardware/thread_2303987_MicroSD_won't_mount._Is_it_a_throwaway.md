---
title: "MicroSD won't mount. Is it a throwaway?"
date: 2015-11-23
forum: Hardware
---

### Post by cdysthe on 2015-11-23
Hi,

I bought two 64GB micro SD cards. They both worked well for a little while, then one of them stopped working. This is what I get in syslog when I insert it for use on my Ubuntu 15.10 x64 latpop (I have tried in two other laptops as well with very similar result):

Nov 23 09:22:01 ThinkPad-X1Carbon kernel: [ 1494.467407] usb 1-1: new high-speed USB device number 5 using xhci_hcd
Nov 23 09:22:01 ThinkPad-X1Carbon kernel: [ 1494.661477] usb 1-1: New USB device found, idVendor=5453, idProduct=5038
Nov 23 09:22:01 ThinkPad-X1Carbon kernel: [ 1494.661481] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 23 09:22:01 ThinkPad-X1Carbon kernel: [ 1494.661483] usb 1-1: Product: TS-RDP8
Nov 23 09:22:01 ThinkPad-X1Carbon kernel: [ 1494.661484] usb 1-1: Manufacturer: Transcend
Nov 23 09:22:01 ThinkPad-X1Carbon kernel: [ 1494.661486] usb 1-1: SerialNumber: RDP800000000
Nov 23 09:22:01 ThinkPad-X1Carbon kernel: [ 1494.662473] usb-storage 1-1:1.0: USB Mass Storage device detected
Nov 23 09:22:01 ThinkPad-X1Carbon kernel: [ 1494.662915] scsi host4: usb-storage 1-1:1.0
Nov 23 09:22:01 ThinkPad-X1Carbon mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1"
Nov 23 09:22:01 ThinkPad-X1Carbon mtp-probe: bus: 1, device: 5 was not an MTP device
Nov 23 09:22:02 ThinkPad-X1Carbon kernel: [ 1495.661650] scsi 4:0:0:0: Direct-Access     RDP8     SD/microSD       1.00 PQ: 0 ANSI: 0
Nov 23 09:22:02 ThinkPad-X1Carbon kernel: [ 1495.664283] scsi 4:0:0:1: Direct-Access     RDP8     MS/M2            1.00 PQ: 0 ANSI: 0
Nov 23 09:22:02 ThinkPad-X1Carbon kernel: [ 1495.666953] scsi 4:0:0:2: Direct-Access     RDP8     CF               1.00 PQ: 0 ANSI: 0
Nov 23 09:22:02 ThinkPad-X1Carbon kernel: [ 1495.667285] sd 4:0:0:0: Attached scsi generic sg1 type 0
Nov 23 09:22:02 ThinkPad-X1Carbon kernel: [ 1495.667475] sd 4:0:0:1: Attached scsi generic sg2 type 0
Nov 23 09:22:02 ThinkPad-X1Carbon kernel: [ 1495.667643] sd 4:0:0:2: Attached scsi generic sg3 type 0
Nov 23 09:22:02 ThinkPad-X1Carbon kernel: [ 1496.019164] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Nov 23 09:22:02 ThinkPad-X1Carbon kernel: [ 1496.019746] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Nov 23 09:22:02 ThinkPad-X1Carbon kernel: [ 1496.020036] sd 4:0:0:0: [sdb] Attached SCSI removable disk

I see that the card gets detected for what it is, but the rest of the messages doesn't tell me anything (I'm pretty ignorant when it comes to these things). There's no data on the card that I need to save so if there's anything drastic I could do to try and save it I'll do that. So if someone could tell me whether this is one for the bin or if I can do something to save it I would greatly appreciate it.

---

### Post by sudodus on 2015-11-23
If the card does not mount in a card reader, where the other card mounts, you can check the following:

***When you 'see it' as a mass storage device there is hope.*** You can repair the file system, or create a new file system.

When no partition is found on the micro-sd card
```

sudo lsblk -fm
NAME FSTYPE LABEL MOUNTPOINT NAME   SIZE OWNER GROUP MODE
... [COLOR="#696969"](the other mass storage devices are shown)[/COLOR]
sdd                          sdd    958M root  disk  brw-rw----

```
When there is a normal FAT32 file system:
```

sudo lsblk -fm
NAME   FSTYPE LABEL   MOUNTPOINT NAME     SIZE OWNER GROUP MODE
...
sdd                              sdd      958M root  disk  brw-rw----
&#9492;&#9472;sdd1 vfat   TESTING            &#9492;&#9472;sdd1   957M root  disk  brw-rw----

```
When Lubuntu is copied/flashed/cloned/burned/restored onto it (so that it is a USB boot drive).
```

sudo lsblk -fm
NAME   FSTYPE  LABEL                     MOUNTPOINT                  NAME     SIZE OWNER GROUP MODE
...
sdd    iso9660 Lubuntu 14.04.3 LTS amd64                             sdd      958M root  disk  brw-rw----
&#9500;&#9472;sdd1 iso9660 Lubuntu 14.04.3 LTS amd64 /media/Lubuntu 14.04.3 LTS  &#9500;&#9472;sdd1   727M root  disk  brw-rw----
&#9492;&#9472;sdd2 vfat                                                          &#9492;&#9472;sdd2   2,2M root  disk  brw-rw----

```

If you had a FAT32 or other Windows file system, you can try to repair it in Windows with 

```
chkdsk /f X:
```

You can try to wipe the first megabyte, create a fresh partition table and file system with [mkusb](https://help.ubuntu.com/community/mkusb).

***When you cannot 'see it' as a mass storage device it is probably damaged beyond repair. ***

See also the following link: [Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by Holger_Gehrke on 2015-11-23
If I read this right, its a multicard reader for Memory Stick, Compact Flash and SD/micro SD that gets detected, not the card. If a card was detected, there would be something *like* this
```

Nov 23 16:20:32 _redacted_ kernel: [24068.024302] sd 5:0:0:0: [sdb] 7759872 512-byte logical blocks: (3.97 GB/3.70 GiB)
Nov 23 16:20:32 _redacted_ kernel: [24068.025152] sd 5:0:0:0: [sdb] Write Protect is off
Nov 23 16:20:32 _redacted_ kernel: [24068.025167] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
Nov 23 16:20:32 _redacted_ kernel: [24068.026027] sd 5:0:0:0: [sdb] No Caching mode page found
Nov 23 16:20:32 _redacted_ kernel: [24068.026040] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Nov 23 16:20:32 _redacted_ kernel: [24068.033183] sd 5:0:0:0: [sdb] No Caching mode page found
Nov 23 16:20:32 _redacted_ kernel: [24068.033204] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Nov 23 16:20:32 _redacted_ kernel: [24068.035463]  sdb: sdb1
Nov 23 16:20:32 _redacted_ kernel: [24068.040539] sd 5:0:0:0: [sdb] No Caching mode page found
Nov 23 16:20:32 _redacted_ kernel: [24068.040558] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Nov 23 16:20:32 _redacted_ kernel: [24068.040576] sd 5:0:0:0: [sdb] Attached SCSI removable disk

``` 
in the log (these lines are from syslog on my machine after connecting a reader with a 4GB micro SD card and appear after lines looking a lot like the ones in your post). Can your reader use micro SD directly or do you use some kind of adapter ? Those adapters are in my experience usually not too well made, I've got 4  of which only two work; two broke within days, either bad contacts or dust or corrosion ... So you might want to try different adapters and different readers. You could also clean the contacts of the 'defective' card, a tissue and some alcohol usually do the trick whenever I encounter this problem.

Holger

---

### Post by cdysthe on 2015-11-23
Hi,

Thanks guys! After reading the two responses above I've come to the conclusion that this card is toast. There's no output for the card doing 'sudo lsblk -fm'. All I see is the internal drive. Also, the output shown in the post above is missing for this card but I have it for the working one. So it's pretty obvious that something is seriously wrong with the card.

---

### Post by sudodus on 2015-11-23
I think so too. I'm glad that there's no data on the card that you need to save.

---

### Post by cdysthe on 2015-11-23
I'm one of those who notoriously back up everything, these days to Google Drive (except for sensitive data), that being my phone, my laptops or home computers. It always pays off in the end! :)

---

### Post by kurt18947 on 2015-11-23
There's no possibility those cards are formatted to exFAT, is there? I believe that for flash devices 64GB. and up exFAT is the default. You said they were working on *nix which they wouldn't - unless the package(s) for reading & writing exFAT were installed and now aren't for some reason.

---

### Post by cdysthe on 2015-11-23
> **kurt18947 said:**
> There's no possibility those cards are formatted to exFAT, is there? I believe that for flash devices 64GB. and up exFAT is the default. You said they were working on *nix which they wouldn't - unless the package(s) for reading & writing exFAT were installed and now aren't for some reason.

Yes, they were formatted exFAT but I've installed the exfat stuff on my computers and even partitioned and formatted SD cards exFAT. Gparted can't be used though. So that is not the reason I can not read this particular card.

---

### Post by ic3man5 on 2015-11-24
I format / use over 1000 microSD cards annually. When a card completely dies it won't show up in dmesg like you are seeing. I'd say about 5-10 in 1000 fail this way; maybe 1 or 2 will take out the card reader with it - stop using that card if you value your reader.

edit: A lot of the firmware on these cards are aweful and when it can't read a specific sector it locks up and becomes unusable; if it actually gets damaged (from ESD?) and draws current it will take out your reader with it.

---

### Post by cdysthe on 2015-11-25
> **ic3man5 said:**
> I format / use over 1000 microSD cards annually. When a card completely dies it won't show up in dmesg like you are seeing. I'd say about 5-10 in 1000 fail this way; maybe 1 or 2 will take out the card reader with it - stop using that card if you value your reader.

edit: A lot of the firmware on these cards are aweful and when it can't read a specific sector it locks up and becomes unusable; if it actually gets damaged (from ESD?) and draws current it will take out your reader with it.

Thank you. This is valuable information. The card reader is still working well and it turned out this card was within the return window with Amazon.com so it's going back for a refund. I'm not going to ask you why you use all those cards, but I will ask this: If you had to buy all those cards today assuming they are all going to be 64GB which card brand would you get? The card I returned was a Patriot Extreme Performance Series 64 GB MicroSDXC. I got a couple of them and the other one works well.

---

### Post by sudodus on 2015-11-25
> **cdysthe said:**
> [QUOTE=ic3man5;13396440]I format / use over 1000 microSD cards annually. When a card completely dies it won't show up in dmesg like you are seeing. I'd say about 5-10 in 1000 fail this way; maybe 1 or 2 will take out the card reader with it - stop using that card if you value your reader.

edit: A lot of the firmware on these cards are aweful and when it can't read a specific sector it locks up and becomes unusable; if it actually gets damaged (from ESD?) and draws current it will take out your reader with it.

Thank you. This is valuable information. The card reader is still working well and it turned out this card was within the return window with Amazon.com so it's going back for a refund. I'm not going to ask you why you use all those cards, but I will ask this: If you had to buy all those cards today assuming they are all going to be 64GB which card brand would you get? The card I returned was a Patriot Extreme Performance Series 64 GB MicroSDXC. I got a couple of them and the other one works well.[/QUOTE]

+1

This is interesting for me too :-)

---

