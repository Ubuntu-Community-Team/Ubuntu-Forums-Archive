---
title: "Grub harddisk boot order"
date: 2009-09-17
forum: Hardware
---

### Post by JoSSte on 2009-09-17
I just installed Ubuntu 9.04 on my Via EPIA machine after updating it with a PCI SATA controller.

I have purchased an eSATA HDD enclosure, to enable me to add another harddisk. 

when I installed Ubuntu, the installation finds /dev/sda1, my IDE internal drive's first partition, mounted as /boot, which GRUB designated HD(0,0). 

After the completed installation I attached the eSATA drive to the controller and boot the PC, and GRUB halts with the "loading the menu" message and doesn't get anywhere.

If I disconnect the external box, and conenct and mount the partition after GRUB boots it works fine.

I presume that it has something to do with the sd driver loading SATA drives before IDE drives, and I know that I could just alter hd(0,0) to hd(1,0) - but if the external drive should fail, I'd have a problem again.

I'd like to have GRUB always boot  from the first IDE drive - any bids?

---

### Post by oldfred on 2009-09-18
First choice - does your BIOS allow you to set boot priority? My old motherboard did not but my new one does.

Little more complicated but workable - Install a tiny grub only partition at the beginning of your sata drive and in a menu.lst put a chainboot entry back to your pata drive.
Grub only info from Herman:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")

Grub only is more for chainbooting many alternates where you have different operating systems, but will work for just about any boot.

---

