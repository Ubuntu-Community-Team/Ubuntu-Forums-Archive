---
title: "Can my built in memory card reader be made to work?  (OZ711M1/MC1)"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by Nazosan on 2007-06-12
This laptop has a built in memory card reader that supports SD, so it would be a great help to me if I could use it.  I have an external reader, but due to the limited number of USB ports and power issues, using it is no easy task typically (plus it's just plain inconvenient as it's big and it doesn't plug in well to USB ports requiring a lot of force to get it in there.)  I'm wondering if anyone might know of drivers or settings that work with it?

I was feeling too lazy to type it all out, so here it is in an image:

[img]http://img156.imageshack.us/img156/234/cardreaderfd4.png[/img]

---

### Post by Xen2oo6 on 2007-06-13
MSI released driver for an O2Micro SD Card Reader, but i can´t build it :(

[http://global.msi.com.tw/html/popup/nb_linux/driver/CardReader_Linux.zip](http://global.msi.com.tw/html/popup/nb_linux/driver/CardReader_Linux.zip)

[http://global.msi.com.tw/html/popup/nb_linux/content.htm](http://global.msi.com.tw/html/popup/nb_linux/content.htm)

---

### Post by Nazosan on 2007-06-13
Yeah, I'm getting a ton of errors too.  Well, considering that it came packed as an RPM, it clearly wasn't meant to be a generic driver but was obviously for more RPM supporting systems -- likely one specific distro (and likely a few specific versions even.)

In my searching, I have found this:  [http://www.musclecard.com/drivers/readers/files/](http://www.musclecard.com/drivers/readers/files/)  It says PCMCIA, so I'm not sure if it would work or not though.

Unfortunately, I can't get it to build either...  Thing is, one of the first errors I see is it complaining about a missing linux/config.h which I saw earlier when trying to build another linux driver.  I suspect I'm missing some key thing that each of these wanted, but I don't know what.  My first thought would be the kernel source, but as nearly as I can determine every single kernel source related thing that I can find is installed...  So I don't really know what they are looking for.

---

### Post by Xen2oo6 on 2007-06-14
Great there are two drivers but we can´t build them :(

---

### Post by tgalati4 on 2007-06-14
Try the latest Fedora 7 Live.  Boot it and see if your SD card works out of the box.  Sometimes you need to find a distro that works with your hardware rather than try to tweak Ubuntu to get everything to work.

Let us know what you find.

---

### Post by Nazosan on 2007-06-14
Sometimes you don't want to change distros just for something like a card reader...  And even if you were willing, why should you have to, when really it's just about getting a working driver?

Besides, I'm pretty sure Fedora won't work in such an unusual setup.  Part of why I chose Ubuntu is its frindliness towards a live setup.  It's more able to handle unusual things such as this setup where I have the OS running off of an external USB harddrive (which isn't optional unfortunately.)  So really I couldn't run it if I didn't hate Fedora Core (I've tried every version -- well, except 7 -- and I just can't learn to like any single one of them no matter how I try.  Frankly I don't care how popular it is, that doesn't make it a good distro.)

However, Xen2oo6, if you can run it and want to do so, please report back if it works (I suspect it will not though as Fedora isn't really so much more likely to have more drivers like that, and Fedora 7 is probably way too new for those drivers to sucessfully build in without modifications.)

---

### Post by Xen2oo6 on 2007-06-15
It dosen´t work with Fedora, Mandriva. The only way to get it work is Suse Linux Enterprise Desktop 10, but this is only a 60day trial version :(

---

### Post by tgalati4 on 2007-06-16
It's like $60 for a year of support?  Perhaps it is worth it.  Or, while running SLED, figure out what modules are running (lsmod) and see if they are different from the other modules.  So there is at least one distro that will recognize your card reader.

Or, you might have to compile a version of the kernel (from kernel.org) that SLED uses, because it works whereas the other distros don't.  Either way, post what you finally ended up doing.  Now we are curious.

---

### Post by Masol on 2007-08-19
Have anyone managed to make this memory card reader work on Ubuntu? I tried driver form MSI above converted with alien, and [this](http://mmc.drzeus.cx/wiki/Controllers/O2/OZ711MP1/MS1?action=AttachFile), but they do not work (this second I couldn't compile, but I don't have experience at this).


If it would be useful, my [entry on hwdb](http://hwdb.ubuntu.com/?xml=79f31a305bcf24bce1c2afd2e553bea0).

---

### Post by matthijskooijman on 2007-12-29
Hey,

I have the same cardreader in my MSI S270 notebook (or so lspci says). I found out that it supports the "SDA" or "SDHCI" standard, or something like that. Anyway, linux kernels from 2.6.18 support the SD part of the cardreader natively. Look around in your kernel options or modules, if you are already using a newer version, or upgrade.

---

### Post by zipperback on 2007-12-29
> **matthijskooijman said:**
> Hey,

I have the same cardreader in my MSI S270 notebook (or so lspci says). I found out that it supports the "SDA" or "SDHCI" standard, or something like that. Anyway, linux kernels from 2.6.18 support the SD part of the cardreader natively. Look around in your kernel options or modules, if you are already using a newer version, or upgrade.


Gutsy works with my Acer 5050-3371 laptop that uses an ENE chipset for the card reader.

What chipset does your card reader use?

- zipperback
:popcorn:

---

