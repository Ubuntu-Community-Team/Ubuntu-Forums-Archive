---
title: "Problem with printer HP LaserJet 1022"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by tirog on 2005-05-06
Hello.

I'm having problem with printer HP LaserJet 1022. I use Menu System > Administration > Printing and I add my printer (local printer, usb #1, driver from linuxprinting.org: HP-LaserJet_1022-hpijs.ppd), but printer doesn't print. It has status: Ready: Media tray empty!  :| 

Any ideas?
Thanks.
tirog

---

### Post by lorap on 2005-05-06
hi friend.
you'll need to add your printer via cups printing services in terminal window.
all things related to this topic are explained at this site:

[http://www.cups.org/doc-1.1/sum.html](http://www.cups.org/doc-1.1/sum.html)

---

### Post by tirog on 2005-05-07
Ok, but I didn't found a solution my problem  :cry: 

Module usblp is loaded. Now, printer has status "Ready: Printer not connected; will retry in 30 seconds..." lsusb show:
```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```
so Ubuntu doesn't see my printer and I don't have /dev/usb. 

Any ideas?
tirog
PS. How unlock configure by localhost:631?

---

### Post by meles² on 2005-12-10
Hi tirog,

i will work on your problem- because it's *exactly* mine now ;) 

I will let you know when i got my HPLJ1022 work. 
Or.. did you find a solution by now?

Greetings
meles²

---

### Post by David Haas on 2005-12-10
tirog--I see that Ubuntu Hoary does not have in its distribution the driver (PPD file) for the HP Laserjet 1022, but it has PPD files for printers that may work on the same driver. I'd next try the PPD file for the HP Laserjet 1100. I'd first select your printer--the 1022--in the Gnome printing GUI and then after clicking on select driver, click your way to the two PPD files in the HP directory at /usr/share/cups/model/foomatic-ppds/HP. The two files there are:
1) HP-LaserJet_1100-hpijs.ppd.gz
2) HP-LaserJet_1100-ljet4.ppd.gz

If one didn't work, I'd try the other.

David

---

### Post by neonux on 2006-02-28
Hello!
I had the same problem. When I added the printer with gnome printing tool, i was unable to print (ever using HP-LaserJet_1022-hpijs.ppd from linuxprint.org!!) but reading in other posts, it seems that that printer only works with usb2.0. I've the two versions of usb and then plugged in the version 2.0. I had reinstalled the printer and then, it printed.

I dont know if this solve your problem. I hope it help you.

I'm using ubuntu 6.04 (dapper) (because i can't wait to probe xgl ;) ) and it is ok. 

Bye!

PS: Please, forgive my english, i'm spanish and my english speech is very bad! [-(

---

### Post by linuxican on 2008-01-07
Hey,
I got a HP laserjet 1022 on mu gusty ubuntu machine. it worked out of the box without any problem.
Go for it. it's a fast and sweet printer.
Saeed

---

