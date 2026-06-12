---
title: "Switching Video Cards"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by Mr. Smiley on 2005-11-05
I have a 3dfx Voodoo 3 installed on my machine right now and was wondering how I would go about installing a Nvidia 5600. I went ahead and tried installing the card and booting up linux without changing any settings or anything but it gave me an error about my x server being not set up correctly. Could anyone explain to me how I do this? Thanks:razz:


Edit:Opps! Amazing what a little more searching can do! Anyway I ran the sudo dkpg-reconfigure xserver-xorg command and Im now configuring the xserver but I need help trying to find the right driver for the card. When it says select the desired x server driver: is the driver I want to select nv?
Thanks again!

---

### Post by Leif on 2005-11-06
choose nv for the moment, then follow these instructions : [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver) to install the official nvidia drivers.

---

