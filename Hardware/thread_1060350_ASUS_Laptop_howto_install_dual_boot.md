---
title: "ASUS Laptop howto install dual boot?"
date: 2009-02-04
forum: Hardware
---

### Post by kazuya on 2009-02-04
Hi all. I got a ASUS X83A laptop which comes with 250 GB Hard drive., a certain partition of it has been used as Backup OS., and it comes with a recovery CD or dvd. for Vista 64.
 
I want to keep the Vista 64 that comes with the laptop, but resize and recreate about four primary partitions with an extra for swap .
 
Problem is i accidentally wiped out the recovery HD partition and the OS, and do not know if anyone has experience with installing linux on these laptops while not losing that backup HD partition?
 
Any ideas?
 
Is there a howto for installing linux on an ASUS notebook such that you still have the recovery partition. I would say just dont do a zero write on hard drive.. Too late now for me. lol

---

### Post by zapme on 2009-02-04
try this: get a ubuntu 8.10 cd,put it in the cdrom drive and boot from it. Then goto Administration and System and look for the Partitioner. Invoke the partitioner and goto Manual where you may be able to set up the partitions as you like them. This way you can ensure your backup partition remains untouched and set things up for installing Ubuntu. The partition manager gives you the before and after configuration before you commit to writing your drive. Check it carefully as the changes once written are irreversible.
Good Luck.

---

### Post by WannabeFantasma on 2009-02-05
You can make a partition in vista too

[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

I did it that way

than inserted disk->booted up->clicked install and when they asked about partition i picked "Manually" and resized that empty partition into the the sizes needed for ubuntu :)
maybe you can allready do that in vista too like 4GBand 10GB(probably you can) 
I only have "\Swap" and "\" but you might make a "\home" partition where you store all your files and when you reinstall you still have the data :)
__
Ow lol didn't read the thing good enough :D i have my vista partition and Back up partition and ubuntu :) (installed it again yesterday)
so: you can install vista again with the back up os partition
and when you resize the partition in vista you select the "OS partition"(probably the biggest partition on the hard drive) and than make it smaller(like in the link only with as much GB as you want for ubuntu)....
and than apply the things said above.

(hope this post still makes sense :D)

---

### Post by kazuya on 2009-02-09
problem solved. Thanks all. now i have problems with my realtek sound card. it is detected but does not work. I hear no sound. Mark this as solved please.

---

