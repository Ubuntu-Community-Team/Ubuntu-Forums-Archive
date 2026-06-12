---
title: "Acer Aspire One 725 now fully supported in 12.04!"
date: 2012-12-04
forum: Hardware
---

### Post by NihilisticNabarlek on 2012-12-04
Hi Everyone,

Just wanna share a tutorial/good news,  if you own an Acer Aspire One 725, Ubuntu 12.04 is now fully support, I'll go over what you need to do to get it running fully.

First, _**you must install the 64 bit NOT the 32 bit Ubuntu desktop**_, the 32bit will not work properly, generate errors and cause laggy animations, etc, the AMD C60 is a dual core 64 bit CPU, not 32 bit, hell, if you've purchased a computer in the past 3 years you probably require the 64 bit version of Ubuntu.

Touchpad: You must hit Fn+F7 keys at the login screen to enable the touchpad, it's a weird bug but not a deal breaker.  Two finger scrolling can then be enabled in the Mouse/Touchpad settings in Ubuntu.

Screen dimming/3D: You must install the latest AMD Catalyst beta 12.11 Click [HERE]("http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.zip"), reboot after install and now dimming/brightening works with Fn+arrow keys left/right **_DO NOT INSTALL the 12.10 Stable driver it will break your install!!!!_**

After you install you'll want to get rid of the idiotic watermark AMD puts on their driver.  Do that by opening a terminal and running the following script in your Downloads/ directory, script is found [HERE]("http://ubuntuforums.org/showthread.php?t=2076381"):

sudo bash [COLOR=Black][amd_remove_unsupported.sh]("http://ubuntuforums.org/attachment.php?attachmentid=226113&d=1351215018")

Sleep/Wake/Wifi: all work out of the box.  

Enjoy your fully functioning ubuntu 11" Laptop
[/COLOR]

---

### Post by milkacow on 2012-12-18
thanks for the heads up about the beta driver, and watermark script.  solved a major annoyance with my 725. seemed to fix it on 32 bit xfce mint for me.

---

### Post by smalss on 2012-12-19
I just installed 12.04 64 bit and WiFi didn't work for me after i did an update. Any suggestions?

---

### Post by Xbastion on 2013-01-04
You  **NihilisticNabarlek** were completely right about x64. It's really works much better than x86. My acer is fully performance.
Almost everything works well. 

The last one which need to improve is HD playback with hardware decoding.
Still some x264 movies play slows, and Flash full screen I'm sure can be better.

Very grateful for your experience, and that has helped me! ;)

---

### Post by mangkokoo on 2013-03-03
> **NihilisticNabarlek said:**
> Hi Everyone, 

Just wanna share a tutorial/good news,  if you own an Acer Aspire One 725, Ubuntu 12.04 is now fully support, I'll go over what you need to do to get it running fully.

First, _**you must install the 64 bit NOT the 32 bit Ubuntu desktop**_, the 32bit will not work properly, generate errors and cause laggy animations, etc, the AMD C60 is a dual core 64 bit CPU, not 32 bit, hell, if you've purchased a computer in the past 3 years you probably require the 64 bit version of Ubuntu.

Touchpad: You must hit Fn+F7 keys at the login screen to enable the touchpad, it's a weird bug but not a deal breaker.  Two finger scrolling can then be enabled in the Mouse/Touchpad settings in Ubuntu.

Screen dimming/3D: You must install the latest AMD Catalyst beta 12.11 Click [HERE]("http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.zip"), reboot after install and now dimming/brightening works with Fn+arrow keys left/right **_DO NOT INSTALL the 12.10 Stable driver it will break your install!!!!_**

After you install you'll want to get rid of the idiotic watermark AMD puts on their driver.  Do that by opening a terminal and running the following script in your Downloads/ directory, script is found [HERE]("http://ubuntuforums.org/showthread.php?t=2076381"):

sudo bash [COLOR=Black][amd_remove_unsupported.sh]("http://ubuntuforums.org/attachment.php?attachmentid=226113&d=1351215018")

Sleep/Wake/Wifi: all work out of the box.  

Enjoy your fully functioning ubuntu 11" Laptop
[/COLOR]

When i install the driver, it says "your graphic adapter is not supported with this driver" 
Is there any solution?

---

### Post by jlh68 on 2013-08-25
I have the same problem with the WiFi.  It does not connect.

As for trhe touchpad [Ctrl] + [Fn] + [F7] works at anytime after boot.

---

### Post by jlh68 on 2013-08-25
**NihilisticNabarlek** Screen dimming/3D: You must install the latest AMD Catalyst beta 12.11, how did you install the AMD Catalyst?  Where did you extract it to or what ever?  I downloaded it and have the file on my desktop, but could not install.

---

