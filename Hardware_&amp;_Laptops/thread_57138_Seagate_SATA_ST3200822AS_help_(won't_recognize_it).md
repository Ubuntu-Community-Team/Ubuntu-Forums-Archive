---
title: "Seagate SATA ST3200822AS help (won't recognize it)"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by alcak on 2005-08-15
hi there.

i tried to install Ubuntu 5.04 on my HP Pavillion ([specs.](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=c00415293#top) ) **AMD 64** 3500 machine and everything goes Ok untill it gets to the hard drive recognition part. when it gets there it simply says "**No partitionable media. Check is HD connected to the computer."**
My HD is **Seagate 200GB SATA Baracuda 7200.7 **(ST3200822AS).[(specs.)](http://www.seagate.com/docs/pdf/datasheet/disc/ds_barracuda7200.7.pdf) 

I also tried to boot from Ubuntu LiveCD, but same problem happens. it reports an error and offers me possibility to reboot my comp.

and i need to mention that i am using **genuine Ubuntu** installation cd's.

what should i do now???

help!!??

---

### Post by tseliot on 2005-08-16
I had the same problem with my SEAGATE SATA 160GB. I had to but an PATA harddisk to install Ubuntu (then you can use the SATA drive). However if you want to try (just for now and to keep you away from Windows) another distro if you can't buy a new harddisk now I suggest you to try PCLinux OS.

---

### Post by alcak on 2005-08-16
LOL

thanx for the reply. if there is no other solution i will get other HD cause i really do want to try Ubuntu. i have been using linux for several years now and i am a long time member of my hometown Linux User Group.
however i am still pretty much tied to Win OS simply cause i am 3D artist and so far there is no 3Ds Max for Linux. yes there is Maya, but not so powerfull as Max. and now recently there's Softimage XSi but i didnt try it so far so, yeah i gotta stay with windows for that. but for everything else, and I mean EVERYTHING else i have linux on my other machine.

anyway, thanx for your reply and wish you all the best.

cheers.

---

### Post by Kikoolol on 2005-08-19
Hi !

I've got the same problem with a Western Digital SATA II hard drive.

[QUOTE=tseliot]I had to but an PATA harddisk to install Ubuntu (then you can use the SATA drive).[/QUOTE]

Tseliot, could you give us a few more details about this ? I've got an old PATA drive (3.1GB) which could be useful, but what do you mean by saying "then you can use the SATA drive" ?

Thanks !

---

### Post by tseliot on 2005-08-19
I wanted to say that you have to install Ubuntu to another PATA harddisk. Then you have to set fstab properly in order to make it "recognisable" by Ubuntu.

Here is a HOWTO about using a SATA drive which has windows installed (so as to access windows partition)

[http://ubuntuforums.org/showthread.php?t=30233&highlight=SATA](http://ubuntuforums.org/showthread.php?t=30233&highlight=SATA) 

It's a great guide but perhaps it doesn't match all your needs (you could always ask for further information the author of the thread).

Let me know if it does. 

Otherwise would you interested in a HOWTO which explains how to put your "Home" folder in the SATA harddisk? You would still have to install Ubuntu on a PATA drive (which matches at least the minimum space requirements for the operative system)

In this case I would be glad to post a new HOWTO to help you.

EDIT: Actually I've almost completed the HOWTO, I need to take care of some important details. However I don't know how many days (I guess no more than a week) it will take, as I'm busy during the day (I need to study for an exam).

EDIT2: I'll be busy from now till september I've just found out I've got too much to study  :mad:

---

### Post by jeremy on 2005-08-19
I have Ubuntu 5.04 installed directly to a seagate 160GB SATA disk, I think it has to do with the BIOS settings for IDE/SATA.

---

### Post by tseliot on 2005-08-19
Yes, it depends on your motherboard (and bios).

---

### Post by jeremy on 2005-08-20
[QUOTE=tseliot]I had the same problem with my SEAGATE SATA 160GB. I had to but an PATA harddisk to install Ubuntu (then you can use the SATA drive). However if you want to try (just for now and to keep you away from Windows) another distro if you can't buy a new harddisk now I suggest you to try PCLinux OS.[/QUOTE]
 BTW, the FAQ for PCLOS states that SATA is not fully supported.

---

