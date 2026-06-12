---
title: "Move Ubuntu to another computer"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by Levo on 2009-06-09
I want to install Ubuntu in an old computer, but it has no internet connection. I have tried many things, such as AptOnCD, Rematersys, but none of them really worked. Is it possible to boot the LiveCD, copy or compress the data of my linux partition and then extract them to a linux-formatted (ext3/4) partition on the old computer??

Levo

---

### Post by wpshooter on 2009-06-09
Does this "old" computer have exactly the same hardware as the computer you currently have Ubuntu installed on ?

---

### Post by Levo on 2009-06-09
> **wpshooter said:**
> Does this "old" computer have exactly the same hardware as the computer you currently have Ubuntu installed on ?

No, that's why I ask.

---

### Post by boof1988 on 2009-06-09
> **Levo said:**
> I want to install Ubuntu in an old computer, but it has no internet connection. I have tried many things, such as AptOnCD, Rematersys, but none of them really worked. Is it possible to boot the LiveCD, copy or compress the data of my linux partition and then extract them to a linux-formatted (ext3/4) partition on the old computer??

Levo

Ubuntu is pretty good at moving to other hardware (provided the new hardware doesn't have any linux-incompatibility problems).  If you have time, you should try it.  Make sure you have proper backups of your data in case of a problem.

I have moved a hard drive (which had Ubuntu installed on it) to another machine and it booted up just fine.

If you do try it, you may need to use recovery mode to fix something (video etc).

---

### Post by Levo on 2009-06-09
OS: Ubuntu 9.04 32bit

CPU
Current: AMD Athlon 64 3500+
Old: AMD Athlon 1.0GHz

Motherboard
Current: MSI K8N Diamond 7100
Old: QDI Kinetiz 7E

Video Graphichs
Current: ASUS EN8800GTS (G80)
Old: GeForce FX (I don't even know the manufacturer)

RAM
Current: 2GB DDR
Old: 512 or 768 SDRAM

There are big differences between the two computers.
As far as I remember there was no sound under Hardy/Intrepid. The old motherboard has an AC97 Audio chipset, which did't work. I haven't tried any updates, because there is no internet access there (there is a PCI 56K modem which works under other OSes, but I can't configure it to work under linux).

---

### Post by singalen on 2009-06-09
I did exactly the same with my two laptops and 9.04.
Copied a Linux partition with Ghost, created a new Linux type partition on a new laptop (and two more for /home and swap), and extracted the image there.

Afterwards I:
- Booted Ubuntu CD and installed Grub to MBR;
- From the same Ubuntu CD, mounted that partition and edited its /etc/fstab to point to new hard disk partitions.
(There were UIDs in old fstab, but I didn't know them for a new system, I used old-style names like /dev/sda3)
- edited /boot/grub/menu.lst to match the same partition names;
- from the same Ubuntu CD, remounted the partition read-only and ran a fsck on it (because the new partition was of bigger size).

That's it. Afterwards I had to install video drivers, but that's all the trouble.

Oh yes, you can see your partitions list with fdisk -l

(But you can try to go with just moving your home directory)

---

### Post by Levo on 2009-06-09
> **singalen said:**
> 
Afterwards I:
- Booted Ubuntu CD and installed Grub to MBR;
- From the same Ubuntu CD, mounted that partition and edited its /etc/fstab to point to new hard disk partitions.
(There were UIDs in old fstab, but I didn't know them for a new system, I used old-style names like /dev/sda3)
- edited /boot/grub/menu.lst to match the same partition names;
- from the same Ubuntu CD, remounted the partition read-only and ran a fsck on it (because the new partition was of bigger size).


Thanks singalen for your answer. Are these the only steps I need to do in order to configure the system?

---

### Post by singalen on 2009-06-09
> **Levo said:**
> Thanks singalen for your answer. Are these the only steps I need to do in order to configure the system?

Yep, it worked for me.
I'm not sure about video drivers, but open-source one should provide a decent fallback.
Note the fsck part.

---

### Post by Levo on 2009-06-09
> **singalen said:**
> Yep, it worked for me.
I'm not sure about video drivers, but open-source one should provide a decent fallback.
Note the fsck part.

I do not have access to that computer at the moment, but I'll try it and post a comment.
If anyone else knows another way, please post it.

---

### Post by Levo on 2009-06-10
> **singalen said:**
> I did exactly the same with my two laptops

Are these laptops of the same manufacturer?

---

### Post by fdbk on 2009-06-10
> **Levo said:**
> I want to install Ubuntu in an old computer, but it has no internet connection. I have tried many things, such as AptOnCD, Rematersys, but none of them really worked. Is it possible to boot the LiveCD, copy or compress the data of my linux partition and then extract them to a linux-formatted (ext3/4) partition on the old computer??

Levo

Sorry but I can't help asking: why can't you use your Live CD to install ubuntu directly on your old computer?

---

### Post by Levo on 2009-06-11
> **fdbk said:**
> Sorry but I can't help asking: why can't you use your Live CD to install ubuntu directly on your old computer?

Because, as I have already said, there is no Internet connection on that computer and I want to have all my packages. I also downloaded the Ubuntu DVD and some repository DVDs I found, but I prefer moving it.

---

