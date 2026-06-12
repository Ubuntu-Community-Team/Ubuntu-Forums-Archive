---
title: "newbie networking problems"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by joeroot on 2006-02-03
ive just got ubuntu installed, however i have come across problems when installing my netgear wg111t usb dongle.

i have installed both drivers, and for the athfmwdl.inf driver, it says that the driver is installed and hardware has been detected, however for the netwg11t.inf drier, it says the driver is installed but hardware is not found. when i go to system>networking, the wireless networking option is not there.

i have followed countless tutorials but none work, please help me.

---

### Post by joeroot on 2006-02-04
nebody?

---

### Post by ORF1000 on 2006-02-13
I'm having the same problem.  I can get my Linksys PCMCIA card (WPC54GS) to work fine, but not the Netgear USB.  

My laptop has a USB 1.1 port, and the Netgear dongle is designed for USB 2.0.  Could that be my problem?

Dave

---

### Post by ORF1000 on 2006-07-29
The trick to getting the WG111T to work is downloading  and installing the latest ndiswrapper.  Worked for me.  [Instructions are here; go to section 4]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  Unfortunatly, you may not be able to use the gtk graphical interface, but the instructions will get you through just fine.  Also, you need to install both Windows drivers, athfmwdl.inf and netwg11t.inf.

I like this adapter -- the effort was worth it.

---

### Post by northyj0e on 2007-10-17
I had the same problem!
ndisgtk reported that the device was not present for netwg111t but was for athfmwdl!
however the wireless interface is not recognised by any program and i don't get wireless netowrk options from ubunutu. 

I am using 7.04 (Fiesty).

any help would be very much appreciated

---

