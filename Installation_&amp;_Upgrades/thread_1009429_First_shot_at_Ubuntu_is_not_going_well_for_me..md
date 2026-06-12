---
title: "First shot at Ubuntu is not going well for me."
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by timp4jc on 2008-12-12
I am giving Ubuntu my first serious attempt and I am having fits getting the video working on the old laptop that I have to test it on (Sony Viao vgn-s150).  I can install the OS in safe graphics mode and it will go through and appears to work fine, but I cannot change the resolution to be above 800x600.  I have read for hours online about how to get this working and have tried many suggestions and each time I get the privelege of reinstalling the OS.  I know the laptop has a ATI Mobility Radeon 9200 video card in it, but I just can't get it working.  I am sorry if I am missing something or if I am posting this in the wrong place but I would appreciate any detailed help that someone could offer me as I at my limit with this and I don't want to give up.

---

### Post by donkyhotay on 2008-12-12
It might help to know what you've done already. First thing I would do is to check the drivers. How did you install them? Did you install them from 
system > administration > hardware drivers
or from the linux driver installer available on the ATI website?

---

### Post by 2hot6ft2 on 2008-12-12
System>Administration>Hardware Drivers to install graphics drivers

---

### Post by timp4jc on 2008-12-12
I have go to the system->Admin->Hardware Drivers area, but it shows no Proprietary drivers are in use on this system.  The only thing I see is the help and close button.  I did try the ati drivers from their site, butI really screwed it up somehow and had to do a full reload.

---

### Post by timp4jc on 2008-12-12
I have been reading around the internet and it appears that I need to install the ATI 8.28.8 driver version.  Could someone give me a step by step on how to do this.  I can't find good instructions anywhere.  Thanks.

---

### Post by 2hot6ft2 on 2008-12-12
First refresh your sources in a terminal Applications>Accessories>Terminal
```
sudo apt-get update
```
Check for updates System>Administration>Synaptic Package Manager then "Reload" then "Mark All Upgrades" and install them you could even install envyng while you're in there.
Close Synaptic and try System>Administration>Hardware Drivers again and see if it found a driver.

If not try Applications>System Tools>EnvyNG and see if it has one for you.

Hopefully it will get one to show up.

You may not even need one as this says that card is supported by linux and doesn't need the restricted drivers look here. [http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200)

---

