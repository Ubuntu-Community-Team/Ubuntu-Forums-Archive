---
title: "Wireless printing an inconsistency recognising a HP laserjet printer"
date: 2012-04-26
forum: Hardware
---

### Post by oropeza on 2012-04-26
Really stuck with this and requesting help here as my last resort and after a few days of reading forums, tutorials and reading manuals and doing everything from scratch each time.

I bought a HP Laserjet p1102w wireless monochrome printer which supposedly was going to be really easy to get it working on Ubuntu but this hasn't been the case.

I run Ubuntu 11.10 Netbook Edition on a Samsung N145 netbookand so far tried setting the printer using Cupps and HPLIPS, I get to the point where the printer gets recognised when plugged in via USB however I have to reset the printer each time it goes to sleep as I get a Device Communication Error in HP LIPS each time this happens.

The other problem is getting the wireless connection to work, HP Lips gives me the following error when I do a HP-Wificonfig:

error: Channel write error
error:  An I/O error occurred.  Please check the USB connection to your printer and try again. (Device I/O error)

I must point out that when I print a self-test page directly from the printer I don't get any ip address.

To summarise I need help with the following two:

1. How can I get the USB connection to the printer to work consistently so I don't have to reset (unplug and replug) each time.
2. What is the best way to get the printer to work wirelessly forever?


A huge great amount of respect and gratitude will go to whoever puts me in the right path to solve this.

Thanks

Daniel

---

### Post by oropeza on 2012-04-26
Bumping with the hope that someone give us a hand... :p

---

### Post by kurt18947 on 2012-04-26
> **oropeza said:**
> Bumping with the hope that someone give us a hand... :p

What I'm about to suggest has worked pretty well for me using Brother networked printers.  I've used this same technique with an HP inkjet using a print server.  I don't see what version of Ubuntu you're using but it may not matter.  You want to be able to open printer properties.  You're looking for a line called "device URI".  It may start out with **usb://something** if the printer has a USB connection or something like **dnssd://something** if a network connection.  I assign a static I.P. address to the printer if I can then in the device URI line I put
```
socket://xxx.xxx.xxx.xxx:9100 
```
 where x=i.p address.  This has proven quite reliable for me.  It wouldn't work if the printer's i.p. address changed though hence the preference for a static address.

---

### Post by oropeza on 2012-05-04
Thanks for your reply, but I keep having the same problem and the error message:

An I/O error occurred.
Please check the USB connection to your printer and try again.
(Device I/O error)

not sure why since I have got the drivers

---

### Post by oropeza on 2012-05-04
I would say it is nessesary to add an IP address to the printer, when I print a self-test page from the printer the ip address comes as 000.000.000.000 which makes me think the printer is not accessible outside a USB connection.

Does anyone knows how a reliable method to assign an ip address?

---

