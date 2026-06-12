---
title: "Any experience with Maxtor OneTouch II"
date: 2005-02-06
forum: Hardware &amp; Laptops
---

### Post by tronda on 2005-02-06
I'm considering buying a external harddisk such as Maxtor's OneTouch with 250 GB or 300 GB. Do anyone of you have experience with such a disk? After some googling I found that it seems to work fine when using USB. Showing up as a mass storage device, but I would also like to know if anyone have used such a disk over firewire. 

----- Trond

---

### Post by paul cooke on 2005-02-06
[QUOTE=tronda]I'm considering buying a external harddisk such as Maxtor's OneTouch with 250 GB or 300 GB. Do anyone of you have experience with such a disk? After some googling I found that it seems to work fine when using USB. Showing up as a mass storage device, but I would also like to know if anyone have used such a disk over firewire. 

----- Trond[/QUOTE]
 Sorry, can't help you with the firewire aspect. I bought one of the 160GB ones a couple of days ago and have only attached it to my Suse 9.1 box so far, where it was recognised and mounted automagically as an external drive. Sadly, transfer speed was only 850 KB per second and I'm not sure what I would need to do to get it working as USB2 yet... I will be attaching it shortly to my ubuntu box to restore my home drive from my suse box, then I'll know how fast it is with ubuntu and if I need to fix anything... I'm supposedly able to get something like 10 MB per second at USB2 speeds.

---

### Post by bigkahuna on 2005-02-06
Hi,

I've been trying to get my IOGear 160 gb external hard drive to work with it's firewire connection.  I've managed to get the first FAT32 partition to work by entering these commands in the shell manually:

modprobe ieee1394
modprobe ohci1394
modprobe raw1394
modprobe sbp2
mount -t proc none /proc

then running this script with bash which I think I found on the Knoppix site:

rescan-scsi-bus.sh

(if you can't find this script, let me know and I can post it)

Another source for info is here:

[http://www.linux1394.org/](http://www.linux1394.org/)

So far I haven't figured out how to get the other partitions mounted or why I have to enter all of this manually when it appears that the boot process scans for firewire already.

BTW, I'm using the Ubuntu 4.0 Live CD.  I thought I'd used the LiveCD until I've ironed out all the problems and then decide if I want to permanently install Ubuntu.  I'm also a newbie and didn't find much in the docs or past posts about mounting external firewire hard drives.

Paul

---

