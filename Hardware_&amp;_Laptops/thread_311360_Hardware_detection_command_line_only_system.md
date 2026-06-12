---
title: "Hardware detection command line only system"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by uopjohnson on 2006-12-02
I installed the command line only system off of the Alternate 6.10 CD.  Unfortunately it appears that that installer detects hardware and then no hardware detection is installed as part of the actual system.  This is a problem because I need to be able to create an image of this partition and move it to another identical machine.  Unfortunately when I install the image on the new machine it is unable to detect the NIC as well as some other assorted stuff.  
I promise that I have a good reason for doing everything I'm doing, I just don't have a moment to explain it all.
What packages do I need to install to get hardware detection in the command line only installation?

Thanks for your help,

---

### Post by K.Mandla on 2006-12-02
The only thing I can think of is that the automatic detection that runs with the installer probably plucked the MAC address off your NIC and wrote it to /etc/iftable.

I think, but I'm not sure, that if you know the MAC on your NIC you can write it into that file and maybe it will pick it up on boot. No promises, though. ;)

---

