---
title: "Ati driver 9.3 Problem!"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by max246 on 2009-04-29
Hi,
I have a problem after upgrading to 9.04.
When I have finished the upgrade my video running without driver ati and I can install the new driver ati but while restart the computer on display look the message:
"(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)"


I have created the zip log error (  look the attachment ) but I can't resolved it!

My video board is Ati xpress 200  mobile
My laptop is Hp compaq nx 6325

Before the upgrade Ati 9.3 work!

---

### Post by alphacrucis2 on 2009-04-29
> **max246 said:**
> Hi,
I have a problem after upgrading to 9.04.
When I have finished the upgrade my video running without driver ati and I can install the new driver ati but while restart the computer on display look the message:
"(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)"


I have created the zip log error (  look the attachment ) but I can't resolved it!

My video board is Ati xpress 200  mobile
My laptop is Hp compaq nx 6325

Before the upgrade Ati 9.3 work!

Catalyst 9.3 driver doesn't work with x.org server 1.6 which is what Jaunty has. You would have to use Catalyst 9.4 but ATI dropped support for a lot of older cards in Catalyst 9.4. If you have one of the older cards you either have to use the open source ati driver (or radeonhd if applicable to your card) or otherwise stick with Intrepid or buy a new graphics card.

---

### Post by hockman5 on 2009-04-29
How can we tell which ATI cards are supported under 9.4? My ATI card isn't that old and it doesn't work either.

---

### Post by alphacrucis2 on 2009-04-29
> **hockman5 said:**
> How can we tell which ATI cards are supported under 9.4? My ATI card isn't that old and it doesn't work either.

I think if it is supported by 9.4 then it should offer the proprietary driver under System Administration Hardware Drivers. I don't know why ATI did this.

BTW they dropped the support in the Windows drivers too. Here's some info:

[http://www.techpowerup.com/index.php?87181]("http://www.techpowerup.com/index.php?87181")

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1")

---

### Post by StuartN on 2009-04-29
> **hockman5 said:**
> How can we tell which ATI cards are supported under 9.4? My ATI card isn't that old and it doesn't work either.

The Catalyst 9.3 release notes [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_93_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_93_linux.pdf) list all the cards recently moved to "legacy" status, i.e. those that worked with 9.3 but not 9.4.

The Catalyst 9.4 release notes [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37) list all currently supported cards.

---

### Post by max246 on 2009-04-29
My card is : 01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
 

I try to look in the release note but I can't found!

With driver ati open: 
$ sudo dpkg -l | grep video-ati
ii  xserver-xorg-video-ati                     1:6.12.1-0ubuntu2                                          X.Org X server -- ATI display driver wrapper

The encoder video flash, video, ecc is very SLOW!

What is the driver open raden?

---

### Post by max246 on 2009-04-29
I have install radeon but the xglinfo return:
"$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
"


xorg 
"Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        BusID           "PCI:1:5:0"
        Option          "XAANoOffscreenPixmaps"
        Option        "BusType" "PCI"
        Option         "AGPMode" "1"

EndSection
"

---

### Post by Mark Phelps on 2009-04-29
> **max246 said:**
> My card is : 01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
 

I try to look in the release note but I can't found!

With driver ati open: 
$ sudo dpkg -l | grep video-ati
ii  xserver-xorg-video-ati                     1:6.12.1-0ubuntu2                                          X.Org X server -- ATI display driver wrapper

The encoder video flash, video, ecc is very SLOW!

What is the driver open raden?
This is the open source ATI video driver.  If your card supported proprietary drivers, you would have seen a popup allowing you to select those drivers or you would see that option under Administration --> Hardware Drivers.  Since you evidently didn't get those, open source is your only option at this point.

As to the release notes, you didn't look far because the Xpress 200M is clearly listed in the 9.3 release notes and NOT in the 9.4 notes -- indicating that it's no longer supported.

---

### Post by hockman5 on 2009-04-29
So my card is supported but still doesn't work.....bummer

---

### Post by emarkay on 2009-04-29
I am trying to get all the ATI/AMD 9.04 issues here in this thread

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by max246 on 2009-04-30
I have read this [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) for install open driver

---

### Post by emarkay on 2009-05-01
never mind -wrong thread...  :)

---

### Post by max246 on 2009-05-04
Help!!!
I hate this situation!

glx driver not work!!!!

glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

I have try add the module radeon and insert in xorg.conf but when reboot I looking the screenblack!

---

### Post by Mark Phelps on 2009-05-05
Did you follow the instructions in the link in post #11? Or did you just read it?

---

