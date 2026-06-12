---
title: "How to install intel 2.8 on Jaunty?"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by chanyunkwan on 2009-07-24
I'm using kernel 2.6.30 and intel 2.7 driver. Though the graphic performance is much better than the default kernel with the old driver, it still got some problems.
I would like to upgrade to intel 2.8 driver.
But it requires mesa 7.5 which I have no idea how to install. 
Do I need active any options when runing 'configure'?
Do anyone know how to upgrade to mesa 7.5?
Also can I make a deb package, in case I wanna uninstall it?

Thanks

---

### Post by kilowattradio on 2009-07-24
> **chanyunkwan said:**
> I'm using kernel 2.6.30 and intel 2.7 driver. Though the graphic performance is much better than the default kernel with the old driver, it still got some problems.
I would like to upgrade to intel 2.8 driver.
But it requires mesa 7.5 which I have no idea how to install. 
Do I need active any options when runing 'configure'?
Do anyone know how to upgrade to mesa 7.5?
Also can I make a deb package, in case I wanna uninstall it?

Thanks

Make sure that **checkinstall** is on your system and after you use ./configure & make use the command checkinstall. 
 As far as building the software you will have to read the instructions. There may be a help forum or email list for intel drivers and/or mesa. Do a google search and you may find someone that has already asked the same questions and obtained the answers.

HTH,

---

### Post by chanyunkwan on 2009-07-24
> **kilowattradio said:**
> Make sure that **checkinstall** is on your system and after you use ./configure & make use the command checkinstall. 
 As far as building the software you will have to read the instructions. There may be a help forum or email list for intel drivers and/or mesa. Do a google search and you may find someone that has already asked the same questions and obtained the answers.

HTH,

check install complaints about error.
I think I can just switch to Karmic Alpha3

---

