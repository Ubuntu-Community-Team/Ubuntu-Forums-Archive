---
title: "Promise TX4310 not recognized (Ubuntu 6.10, Linux 2.6.17)"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by kevin24 on 2006-08-08
Hi,


I'm trying to get my Promise TX4310 Hardware Raid Controller working (Raid 5 on 4 disks). I'm running a KUbuntu 6.10 i38 Edgy Eft Knot 1 System using Linux 2.6.17-5-386 (I also tried it under Debian Sid). In theory it should work out of the box, because this controller is officially supported by the Linux 2.6.17 kernel, but it doesn't. I can't find the controller in /proc/ide/* or at /proc/devices. I don't have a /dev/ataraid/* entry. I got four single blockdevices (sda, sdb, sdc, sdd), but I can't mount them. Probably they are my four raid disks, but I can only guess that.

I found a tutorial for setting up a hardware raid configuration at [http://www.faqs.org/docs/Linux-HOWTO/ATA-RAID-HOWTO.html#EXISTING]("http://www.faqs.org/docs/Linux-HOWTO/ATA-RAID-HOWTO.html#EXISTING") . But I don't know how to get the IRQ and the I/O-ports for my card - /proc/pci doesn't exist.

I also tried the official driver (partial open source) from the Promise website. I could compile it successfully and I could even load the driver with modprobe. But there is no change at all - still no additional devices in /dev.

I would appreciate any help or explanation, thanks.

kevin

---

### Post by kevin24 on 2006-08-17
Hi again,


Altough I managed to compile the Promise driver with their own instructions, I tried the solution at [http://ubuntuforums.org/showthread.php?t=126199](http://ubuntuforums.org/showthread.php?t=126199) (thanks to keebler411).

All instructions worked, but I still got no entries for my raid-partitions (I got sda, sda1, sda2 und sdb like before, but they aren't mountable).

I know that libata and ftsata2 (the Promise driver) are loaded. The controller got the IRQ #217 (/proc/irq/) - quite high I think. I also found it at /proc/devices, but not as a block device like I expected, but as a character device with the number 254 called "fasttrack". Any idea why it's recognized as a character device? What is the number for?

Can anyone tell me how to get the I/O-Ports of my PCI-cards? Then I could try the other method at least..

I really don't know what to do anymore. I would appreciate any reply, thanks.

kevin

---

### Post by tomane on 2007-11-20
Hi, did you manage to tacke the card?
I'm making some component choices for an office storage server with RAID5 and that controller was an option. Unfortunatelly I can't access ant 3ware models, which seem to be natively supported.
Is that controller working in your machine?

cheers,
--to

---

### Post by arell12 on 2008-02-14
Is 3ware generally better supported In Ubuntu?  I am looking at the Promise card but after reading this maybe i should get a 3ware ?

---

