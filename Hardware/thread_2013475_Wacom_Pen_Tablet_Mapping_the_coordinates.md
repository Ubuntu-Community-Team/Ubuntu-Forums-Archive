---
title: "Wacom Pen Tablet: Mapping the coordinates"
date: 2012-06-30
forum: Hardware
---

### Post by Raphial Hebert on 2012-06-30
Alright, I've got a slight problem with Ubuntu.

First off, I've used Ubuntu for years, and I love it. Only reason I've had to switch back to Windows so much is program incompatibility. Though I'm working on that as hard as I can when I got my hands on Ubuntu 10.10 64bit (I honestly do not like the 11 and 12 distros). So far my progress of making my computer faster, while making it more adaptable to Ubuntu, has worked out pretty smoothly until I missed a curve ball: Wacom tablets.

I was impressed enough that Ubuntu 10.10 64bit recognized my Wacom Bamboo Fun (CTE-650) at all. I realized how to map out the buttons and whatnot, but I cannot seem to map out the coordinates on my dual monitor setup to save my life. I've followed a lot of steps on other topics, and have gotten no where. The tablet works fine, except the mapped out coordinates for the tablet is literally split between both screens.

The pen jumps halfway on one screen to the halfway point on the other screen, as if there is a giant block in the middle where the pen skips over. It's so frustrating.

Is there a Wacom tool I could download that has a GUI? I'm a little flustered using the terminal for the past two days straight.

Opinions? I really need my pen tablet working.

---

### Post by Favux on 2012-06-30
Hi Raphial Hebert,

You don't say what video chipset you have:
```
lspci | grep VGA
```
or what video drivers you are using on it.  Or how you set the monitors up.

But with Maverick's X Server 1.9 you should be able to use MapToOutput provided you update your xf86-input-wacom.  Failing that use the appropriate CTM.  See:
[http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)
or
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up)

To compile a recent xf86-input-wacom see part II. of:
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
or
[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

The GNOME 3.4 Wacom tablet applet is in Precise in the System Settings and might do what you want.  Except I'm not sure your model Bamboo is in libwacom yet.  The first one in GNOME 3.2 that came with Oneiric probably doesn't have what you want.

---

### Post by Raphial Hebert on 2012-06-30
I have my primary monitor on an EVGA Nvidia Geforce 8800 GTX (1440x900), and my second monitor on a PNY Nvidia GeForce 8400 GS (1024x768).

I already followed these steps as best as I could, and there was no change. That is why I posted this topic.

---

### Post by Favux on 2012-07-01
Post the output of **xinput list** in a terminal and the same with **xrandr**.  Then check in the Nvidia control panel what the monitors are called and how you have them setup, TwinView or whatever.

Did you update your xf86-input-wacom?  That's the Wacom X driver and Ubuntu calls the package it is in xserver-xorg-input-wacom.

---

### Post by Raphial Hebert on 2012-07-01
> **Favux said:**
> Post the output of **xinput list** in a terminal and the same with **xrandr**.  Then check in the Nvidia control panel what the monitors are called and how you have them setup, TwinView or whatever.

Did you update your xf86-input-wacom?  That's the Wacom X driver and Ubuntu calls the package it is in xserver-xorg-input-wacom.

Xinput list:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Diamondback 3G              	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Lite-On Technology Corp. USB Multimedia Keyboard	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 6x8 eraser              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 6x8 cursor              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 6x8 pad                 	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 6x8 stylus              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Lite-On Technology Corp. USB Multimedia Keyboard	id=9	[slave  keyboard (3)]

```

Hm. Says RANDR is missing from my first display, and the extension isn't there.

I had no luck with xf86-input when I tried installing it. I kept getting dependency errors.

---

### Post by Raphial Hebert on 2012-07-02
Bump. I really need help with this.

---

### Post by Favux on 2012-07-02
Sorry, I got distracted.

I don't blame you for staying with Maverick.  That was my favorite release too.  But when they dropped support for it this April I finally bit the bullet and started transferring all my stuff to Precise.  It's starting to feel like home now.  I did set up Cairo dock vertically on the right and used it to supplement the launchbar on the left.  So pretty much have everything back.

Anyway I think your problem is that the support was dropped.  So the repository is dead and that's why you can't compile xf86-input-wacom.  I'd have to see the output in response to you trying to install the dependencies:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev
```
But I'm pretty sure that's the problem.  Somewhere in there it is telling you it can't access them.  I booted into my Maverick install and that seemed to be what was going on.

So you need to redirect your repository links in Software Sources if you want to keep Maverick.  I'm pretty sure you need to change the urls with the:
```
deb http://old-releases.ubuntu.com/ubuntu/
```
stuff.

While I haven't tested the switch over the following explains how to do it:
[http://askubuntu.com/questions/118674/are-ubuntu-10-10-maverick-meerkat-repositories-going-to-be-removed-or-deleted-af](http://askubuntu.com/questions/118674/are-ubuntu-10-10-maverick-meerkat-repositories-going-to-be-removed-or-deleted-af)
[http://askubuntu.com/questions/82291/installing-packages-to-end-of-lifed-ubuntu-editions](http://askubuntu.com/questions/82291/installing-packages-to-end-of-lifed-ubuntu-editions)
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Raphial Hebert on 2012-07-03
The main reason I stick with Maverick is because it's the last stable Gnome-based Ubuntu before Unity was pushed into the view. I think Unity is pretty cool for specific hardware like netbooks or tablets, but besides that, I honestly really dislike the new Ubuntu. I love the old Ubuntu I've been used to and familiar with for years. I love having the two horizontal taskbars, and being able to easily customize the appearance of my OS without much hassle. Unity though, that's a different ball-game.

Anywho, I can't check it out right now, because I'm taking a quick break from working on my car and am not near my rig, but I will see about giving you a straight-forward answer in a bit.

I remember that I couldn't finish the installation because, if I'm correct, the terminal informed me my Xserver was too old of a version to install it all. But I could be mistaken. And I already have my sources changed since I installed it lol It's one of the first things I do.

Disappointing they cut off support on that last Gnome-based desktop distro.

---

