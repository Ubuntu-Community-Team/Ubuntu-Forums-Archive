---
title: "32 Bit or 64 Bit"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by linuxonbute on 2007-11-23
I am waiting for delivery of a Zepto Znote 3215W

spec chosen :
```

1.50 GHz Intel Core 2 Duo T5250 667MHz 
Intel® GMA X3100 graphics
15.4" WXGA Screen 1280x800 
2GB (2x1024) DDR2 667/PC5300 SODIMM, Zepto 
160GB 5400rpm SATA Harddisk Samsung 
Intel Pro/Wireless 4965AGN 
SAMSUNG DVD-RW DL
plus USB 2.0 Firewire, Bluetooth etc

```

While I have been using Linux for years and have Feisty on my Sempron desktop PC

I do not know whether it would be better to run 32Bit Gutsy or 64Bit Gutsy on the laptop.

Are all apps available for 64Bit?
I believe  I can  run 32Bit apps under 64Bit O/S eg Virtualbox or might there be problems?

Should I go 32Bit for now? (I have a 200 Gig drive in a USB box so I could always bump everything onto that if I went to 64Bit later)
tia

---

### Post by PmDematagoda on 2007-11-23
I would recommend you to go for Ubuntu 7.10 x64, everything has been more simplified on it including the installation of the Flash and Java plugins for Firefox, the repositories of both 32 bit and 64 bit are pretty much the same and you can install 32 bit packages on it by simply using the ```
sudo dpkg -i --force-architecture nameofpackage.deb
```
command.

---

### Post by atlfalcons866 on 2007-11-23
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

[http://ubuntuforums.org/showthread.php?t=185303](http://ubuntuforums.org/showthread.php?t=185303)

---

### Post by linuxonbute on 2007-11-23
Thanks for the info guys.


PmDematagoda

```
sudo dpkg -i --force-architecture nameofpackage.deb
```

I have normally used synaptic to install or remove packages.  Is there an option to force installs of 32 Bit apps in the 64 Bit version.

---

### Post by PmDematagoda on 2007-11-23
You can use the command I gave previously to install 32 bit .debs on Ubuntu x64, for installation methods concerning source code, you should be able to install the application simply by compiling it as normal like on 32 bit Ubuntu.

---

### Post by 0micron on 2007-11-23
I'd go for the 32-bit version. I recently got an AMD64 laptop and was quite enthusiastic about trying the 64-bit Gutsy, but after I a few days I switched back to the 32-bit one. It just works better.

---

