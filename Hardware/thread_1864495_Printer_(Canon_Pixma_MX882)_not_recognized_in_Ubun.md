---
title: "Printer (Canon Pixma: MX882) not recognized in Ubuntu 11.10"
date: 2011-10-19
forum: Hardware
---

### Post by Black_Sector on 2011-10-19
So, I HAVE installed the drivers for this in x64bit. I followed some instructions that people claimed to have worked in 10.10 and 11.04. I did everything I was supposed to do, but when I tried to add the printer it did not show up at all.

I previously got this printer working in a derivative of Xubuntu, the previous release. I might have been messing around with printer debs from Synaptic and just got lucky. I am trying to add it now, but no such luck.

I have no idea what to do next, but I would really rather not have to return this printer again. This has been a huge problem. Ive even considered switching to the first alternative distro that can get my printer working.

---

### Post by Black_Sector on 2011-10-19
Bump. Anyone know how to trouble shoot this issue?

---

### Post by Black_Sector on 2011-10-19
Please, one at a time....

---

### Post by jgrocha on 2011-10-19
Same here. My Canon Pixma MP 560 was working perfectly in Ubuntu 11.04 but no longer works after upgrading to 11.10. I'm looking for a solution...

Right now, I have an error message saying: 
File "/usr/lib/cups/filter/pstocanonij" not available: No such file or directory

Downloading and installing Canon .deb drivers (from Canon's web site) no longer works. I also tried to compile, but I was unable to do that.

---

### Post by Black_Sector on 2011-10-19
Did you "upgrade" or did you do a clean install? I wonder if you could add it in 11.04 then keep it working after upgrade, or if you just cant ADD it in 11.10

Are you sure it worked in 11.04?

---

### Post by Black_Sector on 2011-10-20
OK, I got it working in Mint Debian edition. It MIGHT also work in Ubuntu 11.10.


It would seem that the trick is to plug the USB cord into your wireless router instead of to your computer directly. That way you get wireless printing by default, and Ken's instructions work great.

[http://blog.kenweiner.com/2011/04/using-canon-pixma-mx882-all-in-one-with.html](http://blog.kenweiner.com/2011/04/using-canon-pixma-mx882-all-in-one-with.html)


Anyone want to confirm if they cant get it to working using this method, plugged into the router instead, when using Ubuntu 11.10?

---

### Post by Black_Sector on 2011-10-23
Working great in Ubuntu Studio, but ONLY through my router. I plugged my router in to my printer via the USB that my router has to avoid connecting it every time I want to print wirelessly. When I try to add it, it shows up no problem under Network. I add the second one with the serial attached, then use default options for the following steps.

Working great....I dont know what to tell you if you dont have a router. If you get one, get one with a USB connection just to avoid having to set it up.

---

### Post by pookieman123 on 2011-10-26
Hi I followed this too

[http://blog.kenweiner.com/2011/04/using-canon-pixma-mx882-all-in-one-with.html](http://blog.kenweiner.com/2011/04/using-canon-pixma-mx882-all-in-one-with.html)

and the printer and the scanner are both working perfectly wirelessly for me on 11.10

---

