---
title: "RIVA-TNT wrong resolution DISPLAY unknown"
date: 2013-03-19
forum: Hardware
---

### Post by kuifje09 on 2013-03-19
Because I want to upgrade to the release 12.04 LTS I searched the list for that release.

Currently I have problems with my video card Riva-TNT which always worked as a charm.
Even my monitor is no longer detected, but is a near perfeckt Samsung Syncmaster 910MP.
DISTRIB_RELEASE=11.10  kernel version : 3.0.0-32-generic.

So I decided to check the hardware compat list first as you should always.

When I view the hardware compat list, then I am a bit confused.
While a lot of people complain about things broken after an upgrade, I did a review of the hardware list.

This was the promise I could read and was very pleased with it:

"Canonical works closely with OEMs to certify Ubuntu on a range of their hardware. The following are all Certified. More and more devices are being  added with each release, so don't forget to check this page regularly."

But for the Riva-TNT  or riva-tnt I got:


  "Search results for "riva-tnt":

    No results found."

Why does the ubuntu devellopers break their promise.

---

### Post by kuifje09 on 2013-03-21
Alright, I did a last atempt to live upgrade my ubuntu from 11.10 to 12.04 hoping it would work.
Well, it didn´t .
I tried the 12.04 dvd to live-boot the system and it showed all in good condition. I am confused.

Now I took a 30Gb spare disk and tried to do a clean install 12.04 on that disk.
Choose the dutch language, would fit better. But... almost done, the installer crashed. Still confused, but such can happen.
Just maybe because of the language?

Reinstalled but now chosen the default english language.  It went smooth and fast.
This is what I just type from that instalation... 

Can someone confim and explain why my riva-tnt does work well now ?  All posible resolutions are shown in the systemsettings-display.


I think I have to do the same install again on a bigger disk, fitting all my tools and docs..  and restore my personal data after the clean install to the new instalation.

( What I just found,  my live update gave me kernel version 3.2.0-39   The dvd version gave me version 3.5.0-23  )

---

### Post by kuifje09 on 2013-03-21
Well, Stuck again.

Just installed the updates, with also a new kernel  : 3.5.0-26-generic , and the display is no longer recognized.
Also the resolution is wrong,  and xrandr -q which gave up to 2048x2048  now stops at :  maximum 1024 x 768.

So the system now thinks I have a laptop screen , 1024 x 768 pixs.

What to do next ?  any ideas ?      I am rather bored and sick now.

---

### Post by ManamiVixen on 2013-03-21
Riva-TNT is no longer supported under Ubuntu. That card is WAY to old... In fact, it's practically the first 3D card and does not fit Unity's requirements. I believe Ubuntu 10.04 supports the card, but 10.04 support ends next month. Either use a different distro or buy/build a new computer. Because yes, Linux runs on old hardware, but it doesn’t do it for you. There will be times you'll have to compile your own software and drivers or get source from projects and install that for a particular system, but seeing as you are an average user, you rely on the standard stuff given out. So your choices of Linux Distros is limited. Preferably to the 2.6 kernel or older.

---

### Post by mörgæs on 2013-03-21
There's no such thing as a broken promise here. Such accusation does not help you getting an answer.

Your graphics card is ancient, in fact many years older than the first Ubuntu release. This might explain why people show little interest in developing drivers for it.

It might work, though. Go for a fresh install of a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").

---

### Post by kuifje09 on 2013-03-21
Thanks for your answers. But there is a little strange behavior.
I do a fresh install of the ubuntu 12.04 and my card is perfectly detected also the monitor.
Even skype does work ( with the PRELOAD )

To be precise ..  Ubuntu with kernel 3.5.0-23 is a guinine ubuntu 12.04 ?

So an update breaks things !  If there is a driver already, you don't need to build.
If the smart gnome3 could not work with the RIVA-TNT , then why the fresh install does.
And then, I can choose for classic view/no effects. Whats the point.

I don't mean to start a fight here! But I dont understand which I realy want to.

Not maintained, but works, update and bye bye. 
Beeing just lucky it works on a fresh install cannot be true.


Edit : Maybe I see thing in the wrong way...

Does Lubuntu Xubuntu, or any other differ in kernel and drivers. For as far as I know has Ubuntu only another preinstalled desktop.
I mean this ,  the videocard is supported or plugged-in into the kernel... So what would the kernel has to do with the desktop.
So I expect the same problems for the graphics card with all the new distro's

---

### Post by mörgæs on 2013-03-22
> **kuifje09 said:**
> So I expect the same problems for the graphics card with all the new distro's

It's better to test than expect. 

No matter which version you select, don't upgrade a system. Go for a clean install.

---

### Post by Yellow Pasque on 2013-03-22
Apparently, there's some regression with newer kernels for you card.

1. Do a fresh 12.04.2 install
2. Run 'sudo apt-get update'
3. Install the the xserver-xorg-lts-precise package and a 3.2 kernel package (currently linux-image-3.2.0-40-generic package)
4. Boot into the 3.2 kernel
5. Now purge the xserver-xorg-lts-quantal package and any 3.5 kernel packages
6. Reboot for good measure
7. Now you can install the rest of the updates and use your system normally

> Ubuntu with kernel 3.5.0-23 is a guinine ubuntu 12.04 ?
Well, it depends what 'genuine' means to you. Ubuntu 12.04.2 = Ubuntu 12.04 with updated kernel/X. That is problematic for some hardware (like yours), which is why the xserver-xorg-lts-precise package exists to make it easy to use the original graphics stack.

---

### Post by kuifje09 on 2013-03-22
Hello Temüjin, that is a nice thing to try. I will see if I can do it today...
I Will testrun it on my "fresh" install. If it works for me I will try on my "working" box.
Many thanks for now.

---

### Post by kuifje09 on 2013-03-23
Well, that is not the solution.
The 3.2.* as suggested, did run already, in wrong detection/resolution.
The 3.5.* with 1:7.6 Xserver does work.  and so does 2.6.38 Linux with 1:7.6 Xserver
Other combination want work well. 

I must keep running on 2.6.38 Linux with 1:7.6 Xserver whith does the best for me.
On the newer kernel, 3.5.*linux, I got some artifacts, but was usable, until the update.

Thanks for all reactions, altough none solved the issue.

---

### Post by kuifje09 on 2013-03-30
Well, sorry but still not satisfied.

When reading the X.Org documentation it says Riva-TNT is still supported.

Snip:
**Xorg           Nouveau Driver-1.0.6**

                    **Introduction to Xorg Nouveau Driver**

                        The Xorg Nouveau Driver package             contains the X.Org Video Driver for NVidia Cards including RIVA             TNT, RIVA TNT2, GeForce 256, QUADRO, GeForce2, QUADRO2, GeForce3,             QUADRO DDC, nForce, nForce2, GeForce4, QUADRO4, GeForce FX,             QUADRO FX, GeForce 6XXX and GeForce 7xxx chipsets.           


So my question is still, why does it not work ? Did the ubuntu engeneers made a X.Org split-off ?  What version of the nouveau driver is ubuntu using  with the latest kernel?

Could I take the driver from X.Org and compile it myself, and should it work on the "ubuntu" kernel?

I found the info at [http://www.linuxfromscratch.org/blfs/view/svn/x/x7driver.html#xorg-fbdev-driver](http://www.linuxfromscratch.org/blfs/view/svn/x/x7driver.html#xorg-fbdev-driver)   , now don't tell they are smarter guys.

---

