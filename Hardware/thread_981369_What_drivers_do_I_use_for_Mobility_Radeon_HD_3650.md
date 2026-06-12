---
title: "What drivers do I use for Mobility Radeon HD 3650?"
date: 2008-11-13
forum: Hardware
---

### Post by -|Veni_Vidi_Vici*- on 2008-11-13
What drivers do I use for the ATI Mobility Radeon HD 3650? The flgrx driver does not say it supports the mobility HD series and ati has no official driver on their site. If anyone could point me in the right direction I would appreciate it.

---

### Post by talofo on 2008-12-18
2 days ago. all worked. Just click over the hardware icon, and let ubuntu make download and install after you click active. No. No way! 

I have no idea why, but I can't get my driver to work. 


+1 here.


Any Help?

---

### Post by zika on 2008-12-27
I have Radeon 3650 (Ubuntu recognizes it as: Mobility Radeon HD 3600 Series) on Ubuntu Interpid Ibex (8.10) and I've installed already twice (update) driver from (this is the latest version) [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-12-x86.x86_64.run)

Try.

---

### Post by cprofitt on 2009-01-05
So the restricted driver included in Intrepid did not work?

---

### Post by zika on 2009-01-05
> **PrivateVoid said:**
> So the restricted driver included in Intrepid did not work?

are You asking me?

---

### Post by dgrafenhofer on 2009-02-03
This thread is already some weeks old, nevertheless I have a question for those who use the Mobility Radeon HD 3650:

For me only the version of the catalyst driver shipped with Ubuntu 8.10 and older catalyst drivers (8.11) works. When I install newer drivers (8.12 or 9.1, under Ubuntu 8.10 or openSUSE 11.1) X crashes on startup. In the Xorg.0.log file I find (for 8.12):

```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x79) [0x80c0c19]
1: [0xffffe400]

Fatal server error:
Caught signal 11.  Server aborting

```

zika: For you the 8.12 version seems to work. How did you install it? I just ran the installer and executed the script aticonfig --initial. Anything else?

More details (tons of log files) are available under [http://phoronix.com/forums/showthread.php?t=15215]("http://phoronix.com/forums/showthread.php?t=15215").

Thanks for your help!

Dominik

---

### Post by zika on 2009-02-03
> **dgrafenhofer said:**
> zika: For you the 8.12 version seems to work. How did you install it? I just ran the installer and executed the script aticonfig --initial. Anything else?
no. when I installed 8.12 I just ran the *sudo sh installer...**.**run* and *aticonfig --initial f *, it seemed to clean everything and install itself but I later (read bellow) learned that it left some remnants of fglrx drivers ...
when I installed 9.1 I've already had problems with several kernel updates and I've cleaned my installation from all fglrx and ati drivers and was running on radeon (ati) driver from open-source. You can see log of that endeavor in [http://ubuntuforums.org/showpost.php?p=6631114&postcount=14](http://ubuntuforums.org/showpost.php?p=6631114&postcount=14). my usual way of installing it was:```
cd ~/Desktop
sudo chmode +x ati-driver-installer-8-12-x86.x86_64.run
sudo sh ati-driver-installer-8-12-x86.x86_64.run
aticonfig --initial -f
```after these kernel problems I've realized that the best way to deal with that and with possible update of drivers (even though new versions of drivers clean before they install themselves) is to make xorg.conf look like:```

Section "Device"
    Identifier    "Configured Video Device"
        Driver    "ati"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth  24
EndSection

Section "DRI"
    Mode          0666
EndSection
        
Section "Extensions"
    Option        "Composite" "Enable"
EndSection
```, i.e. to go back to open-source-driver for a while, clean previous fglrx drivers with ```
cd /usr/share/ati
sudo chmod +x .fglrx-uninstall
sudo sh fglrx-uninstall.sh
```, check in Synaptic for any occurrence of fglrx and then do ```
*switch to metacity*
sudo dpkg-reconfigure -phigh xserver-xorg *(this might be overkill)*
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-9-1-x86.x86_64.run
sudo chmode +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
```now I wait for a new kernel update to test my program ... ;)

---

### Post by dgrafenhofer on 2009-02-03
Thanks for your hints zika! Your "procedure" seems to be a bit more sophisticated compared to what I have tried before :)

I will try it out this evening and let you/the forum know if it worked!

---

### Post by zika on 2009-02-03
it is all but sophisticated ... ;)
just a collection of things gathered by experience ... ;)
note that I've edited it to add a switch to metacity ...

---

### Post by dgrafenhofer on 2009-02-03
The "sophisticated part" was to run sudo dpkg-reconfigure ;)

Unfortunately your procedure did not work either. I get the same crash on the startup of X.

Btw. I am running 8.10 32 bit.

---

### Post by zika on 2009-02-03
> **dgrafenhofer said:**
> The "sophisticated part" was to run sudo dpkg-reconfigure ;) Unfortunately your procedure did not work either. I get the same crash on the startup of X. Btw. I am running 8.10 32 bit.
sorry to hear that. I'm running 8.10 64 bit. did You clear all of "fglrx" in Synaptic and switch to metacity? could it be something in BIOS that's making it that hard ... ? I'll look in my install notebook and try to think of what might help You... but, I'm just an ordinary guy ... ;)

---

### Post by dgrafenhofer on 2009-02-03
> **zika said:**
> You clear all of "fglrx" in Synaptic and switch to metacity?
I removed all "fglrx" packages, but did not switch to metacity, because I already checked with KDE/KDM and gnome/GDM.

> **zika said:**
>  could it be something in BIOS that's making it that hard ... ? 
I have not thought about that. The laptop is quite new (December), so I did not think about bios-updates and the likes. I will have a look at it.

---

### Post by zika on 2009-02-03
> **dgrafenhofer said:**
> The laptop is quite new (December), so I did not think about bios-updates and the likes. I will have a look at it.
I did not mean that BIOS is old but if there were any issues that could come from settings in BIOS. especially on laptop ...

---

### Post by dgrafenhofer on 2009-02-04
My problem seems to be a driver bug:

[https://bugs.launchpad.net/fglrx/+bug/288620]("https://bugs.launchpad.net/fglrx/+bug/288620")
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/314600]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/314600")

The strange thing is that it works for you! :) Maybe it is related to you running the 64-bit version. I will probably try to install it as well to see if the 64-bit driver works.

---

