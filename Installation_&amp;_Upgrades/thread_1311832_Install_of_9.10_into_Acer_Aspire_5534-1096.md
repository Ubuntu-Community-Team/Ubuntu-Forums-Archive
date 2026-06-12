---
title: "Install of 9.10 into Acer Aspire 5534-1096"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Wix on 2009-11-02
Just purchased this laptop and trying to prepare for install of Ubuntu 9.10 as a second OS on this PC. Will set as a dual boot into Win 7 and Ubuntu.  Have researched some Aspire installs and found one problem so far.   The PC comes with a ATI Radeon HD 3200 graphics and will have to load ATI driver for that.  So, after install and reboot, if I get a blank screen, how do I get workable screen so that I can select Synaptic Package Manager and install the ATI driver?  Any setup for sound with 9.10?  Any issue with WiFi for the Acer InviLink 802.11b/g.  Any other gotchas????    Would appreciate anyones knowledge/experience in bringing this system alive.   THX ....   Wix


= = = = =
Added 2013-11-28: 
Using Lubuntu 13.10 everything works (but the network card is Broadcom BCM43225)

---

### Post by eolson on 2009-11-02
I just did what you are about to do.   The graphics driver was not an issue.  It loaded as a proprietary driver after the system was up and running.  Sound worked with no additional work at all; came on as soon as the system booted.  Still wrestling with the wifi.  Wired works fine as does my Belkin USB wireless adapter so in a pinch can use it.  No big deal as it's very small, so no hassle to carry along if need be.

---

### Post by Wix on 2009-11-03
EOLSON:  Sure appreciate your response!!!  If you come up with a fix for the onboard WiFi let me know and I will do as well.   Which version of Ubuntu did you load in Acer,
9.10-desktop-i386 (for 32 bit) or  9.10-desktop-amd64 ?    Thx....

---

### Post by scoon on 2009-11-29
Hey there, 

I am considering one of these.  Any word on the WI-FI working?

Thanks.

---

### Post by Whiterin on 2009-12-03
I have this laptop, using it at the moment as we speak. The WiFi does work, sorta....sometimes...lol. It doesn't work very well... I always just use a use wireless receiver... since the on board is a pretty unstable with Ubuntu. When it does pick up the connection, it is usually low signal quality even when right next to the router, slow speeds, and drops a lot. Other then the WiFi, nothing else caused an issue. Runs fine, everything works...good times. An updated driver for the on board WiFi will probably come out soon too, most likely just doesn't work because it is a bit too new. If it helps anyone, the on board WiFi comes up as "Atheros AR928X". I tried a work around for it I found on the internet, and all it did was kill the ability to use wireless entirely... so I would say just go buy a dirt cheap use wireless adapter and use it until they release a better driver. I am using a Trendnet TEW-424UB personally. Costs like $18-20 I think.

---

### Post by Statik on 2009-12-07
I have an acer 4530 which has basically the same issue with wireless. I fixed the issue by downloading,compiling and installing the new compat version of the driver. Search for 4530 wireless and I'm sure you'll find the thread. 

I just bought a 5534 today and I'll be trying to get the wireless working tonight. I'll let you know how it goes.

Statik

---

### Post by darkod on 2009-12-07
I don't have this laptop and this integrated wireless but just to add.
Compiling a driver on your own might be a good way to go. It's as easy as running two commands in terminal. Of course, you need to download the appropriate driver depending what your chipset (wireless) is.
I had this situation with usb wi-fi I just bought. Karmic was trying to load wrong driver unfortunately and as soon as I compiled my own and blacklisted the wrong one, stable 150Mb connection which is the max for the adapter.

---

### Post by Statik on 2009-12-07
OK, as expected, I had trouble with the wireless. It showed up as functioning but didn't detect any networks. Here is the procedure that worked, flawlessly, based on [this]("http://ubuntuforums.org/showthread.php?t=882003&page=10") thread.

Downloaded [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2009-12-07.tar.bz2]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2009-12-07.tar.bz2") to the desktop. Its the latest compat wireless version.
Then:
```

cd ~/Desktop
sudo apt-get install build-essential
tar -xjvf compat-wireless-2009-12-07.tar.bz2
cd compat-wireless*
make
sudo make install
sudo make unload
sudo make load

```

Then reboot.

Hope this helps!

Statik

---

