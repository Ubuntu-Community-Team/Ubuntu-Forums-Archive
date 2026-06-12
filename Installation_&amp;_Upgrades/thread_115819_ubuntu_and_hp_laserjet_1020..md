---
title: "ubuntu and hp laserjet 1020."
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by Fredde Mannen on 2006-01-11
Hi!
I've read that a lot people on internet has problems with the HP Laserjet 1020 printer. 

So do I! :???: 

Though my problem is not installing the printer, that was no problem for me. Though the foo2zjs driver had a little bug for the udev. Anyway, I can print nice and fine text uptil 21 pages or so, and then the printer just dies. 

Its like the usb or something hangs up, because if I restart the printer, it can print again for up to 21 pages, if im lucky! 

When i do the usb_printerid command on the /dev/usb/lp0 , i get something in style with: Device or resource is busy!

When i check the /var/log/message , i see something in style with for a 100 lines or so: ... error -110 reading printer status  

this is makeing me crazy... didnt work either with debian, got the same error after a while. 

Any good ideas?

---

### Post by KingBahamut on 2006-01-11
[http://doc.gwos.org/index.php/HPLJ1020](http://doc.gwos.org/index.php/HPLJ1020) 

This is the our process, does it differ from what you did to get the Printer to work?

---

### Post by Fredde Mannen on 2006-01-11
[QUOTE=KingBahamut][http://doc.gwos.org/index.php/HPLJ1020](http://doc.gwos.org/index.php/HPLJ1020) 

This is the our process, does it differ from what you did to get the Printer to work?[/QUOTE]

Well the only thing that differ is that i haven't installed the cupsys-bsd, i'll have to check that tomorrow and see if it's there.

---

### Post by Fredde Mannen on 2006-01-12
[QUOTE=Fredde Mannen]Well the only thing that differ is that i haven't installed the cupsys-bsd, i'll have to check that tomorrow and see if it's there.[/QUOTE]
Yes cupsys-bsd is installed. 

hmm.. something else got to be wrong!

---

### Post by gasparov on 2006-02-26
same issue here,the printer dies after a while and its a mess if you want to print a big document

---

### Post by earth_walker on 2006-04-05
[QUOTE=Fredde Mannen]Hi!
Though my problem is not installing the printer, that was no problem for me. Though the foo2zjs driver had a little bug for the udev. [/QUOTE]

What was the little udev bug? 

My hp1020 prints perfectly except that I have to turn it off and on between every document. Is this the bug you refer to? If so, how did you fix it?

---

