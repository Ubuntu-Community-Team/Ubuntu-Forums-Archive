---
title: "HELP! Install HP Officejet 4610/4620"
date: 2012-06-13
forum: Hardware
---

### Post by Alcidious on 2012-06-13
Howdy,

So, still a new linux user, and am attempting to install/configure my new printer... an HP Officejet 4610/4620.  I am running Ubuntu 11.10 32-bit on a laptop.  I tried to use the add printer utility, but the 4610/4620 series is not in the database.  I tried to search the given installation cd for the PPD file/files, but had no success.  

What should I do?  Should I use Wine, or some emulator, to run the installation of Windows software? And then run my printer through that (sounds like a pain in the ***)?  

I don't really care if the HP software works, I only care the proper drivers get installed and I can print, scan and copy.  Thanks for any help!

---

### Post by hansdown on 2012-06-13
Hi Alcidious.

Every hp printer I've used works by simply turning it on, and ubuntu gives a popup for "new printer found".

Does this work for you?

---

### Post by Alcidious on 2012-06-13
hansdown,

no, the utility began the configuration process, but my model was not recognized.  It is my guess that the printer is a new model whose drivers have not been added to any ubuntu-related repositories.  I thought about using a different model, such as 5610, but thought better of it.  I doubt the drivers are the same.

---

### Post by mastablasta on 2012-06-14
sometimes to use a similar model is just fine. especially if you find on some review site that important components are the same.
 
anyway.... you can try to do a manual install of hplip.: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
 
 
i can't find your printer on the site but there should be a similar one (from the series) you can use.

---

### Post by Alcidious on 2012-06-14
mastablasta,

how do you check to find out a similar series with the necessary drivers? Should I just perform a general search on the net, or should the hplip site have that info? thanks

---

### Post by Alcidious on 2012-06-15
So I went on the HPLIP troubleshooting forum, and I was told that my model will be supported in the next release, version 3.12.16, which will be out in a few days! Thanks everyone

---

