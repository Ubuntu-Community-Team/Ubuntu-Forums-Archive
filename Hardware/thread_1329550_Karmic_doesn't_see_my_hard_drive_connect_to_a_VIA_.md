---
title: "Karmic doesn't see my hard drive connect to a VIA VT6421 pci card"
date: 2009-11-17
forum: Hardware
---

### Post by slimscraggle on 2009-11-17
I've been lucky with Linux up until recently.  I previously had Hardy on my box but decided I wanted to use Karmic.  I installed Karmic but it doesn't see one of my SATA hard drives which is connected to a VIA VT6421 pci card.  Karmic also takes much much longer to boot than Hardy did and it appears to be related to this same card/HD issue.  Hardy had no trouble accessing this drive.  Can someone help me get karmic to find the drive?

---

### Post by slimscraggle on 2009-11-18
bump

---

### Post by slimscraggle on 2009-11-20
bump

---

### Post by slimscraggle on 2009-11-21
bump bump bump

---

### Post by slimscraggle on 2009-11-22
can someone please help me with this, I'd really like to make the move to Karmic as I'd like to use UbuntuOne, but I don't want to do it if it means losing a hard drive.  I'm guessing this is a kernel regression but I don't know how to deal with that.

---

### Post by valentt on 2009-11-29
I found the answer on how to make this VIA VT6421 card work on Ubuntu:

sudo modprobe sata_via

more details on my blog:
[http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/](http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/)

---

### Post by slimscraggle on 2009-11-30
Thanks so much for your response!  Sadly, it doesn't seem to be making any difference.  I really don't understand what's going on.  The drive doesn't show up in the disk utility or gparted or fdisk but it does show up when I issue the lspci -vv command (I'm not exactly sure what this is I found it in another post).

I tried adding nomraid to the kernel parameters in grub2 but that doesn't seem to have made any difference.

Another weird thing is that Hardy calls the drive I'm looking for /dev/sda but Karmic doesn't see it.

Any more ideas would be greatly appreciated.

---

### Post by slimscraggle on 2009-12-02
bump

---

