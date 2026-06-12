---
title: "Configuring Broadcom wifi w/o any internet connection"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by Andrew Shimmin on 2006-01-19
I'm a linux newbie who finally installed Ubuntu. The trouble is, my paid internet access is dial-up, and my only other access is through wifi hotspots. This wouldn't be a problem if I had a real modem, but I don't. My soft modem is conexant, which can only be made to work, I understand, with a third-party driver for sale. And my wifi can only by made to work with ndiswrapper, which, since I don't have internet access in Ubuntu has proven too difficult for me to configure without help. There must be a way to aquire and install ndiswrapper locally, right? Can I get it from the install disk? How?  If it helps, I'm using Ubuntu 5.10 32 bit (I have an AMD64 processor, but couldn't get the 64 bit install to work) on an Acer travelmate 4402. If I can get the wifi working, I'll be able to use it for all my other configuring.

Thanks to anyone who can help. I've been using open source software for about 18 months now (firefox, thunderbird, freepops) and am amazed that so many people are willing to do so much valuable work for free!

---

### Post by jag164 on 2006-01-19
Included? Nope. But you're not necessarily out of luck .   You most likely need to use ndiswrapper b/c you have a broadcom chip card.   Now, Ndiswrapper litterally 'wraps' windows wi-fi drivers and uses the unaltered. The problem is Ubuntu ( Mandrivia, RedHat, Suse, et al) are not really allowed to package those drivers for distribution.   So **A)** you must [identify (using lspci) and manually download]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") the driver from a friend's or library's pc onto a USB key (thumb drive). **B)**  If you have/had a window's partition and had the wireless workin on a hotspot, you had the correct drivers at one time on the hard driver and they still may be on a driver install CD.   Finding them in windows can be a pain b/c you don't know what they are called.
Use  **/bin/lcpci** and the links  above to possibly find the correct driver name.  Can't find it?   dump the output of lspci and lspci -n and some one may be be able to help with the name. for you to look for on a local haarddrive or install CDROM.

---

### Post by Andrew Shimmin on 2006-01-19
I'm dual booting. That was probably important to mention; sorry.  So, I've still got internet access, just not in linux, so synaptics/apt-get aren't getting the job done. Is ndiswrapper not necessary for configuring the windows driver in linux? I've got the driver (bcmwl5). I've copied it over to my linux desktop. It's just the next step that's got me tripped up.  Thanks for your help, jag164.

---

### Post by kojak75 on 2006-01-19
Where do I type these commands you mention? I have read several instructions to install ndis, but none tell me where I am supposed to do this. I have never used linux. So talk to me like I am a ignorant user, I won't be too offended. 




[QUOTE=jag164]Included? Nope. But you're not necessarily out of luck .   You most likely need to use ndiswrapper b/c you have a broadcom chip card.   Now, Ndiswrapper litterally 'wraps' windows wi-fi drivers and uses the unaltered. The problem is Ubuntu ( Mandrivia, RedHat, Suse, et al) are not really allowed to package those drivers for distribution.   So **A)** you must [identify (using lspci) and manually download]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") the driver from a friend's or library's pc onto a USB key (thumb drive). **B)**  If you have/had a window's partition and had the wireless workin on a hotspot, you had the correct drivers at one time on the hard driver and they still may be on a driver install CD.   Finding them in windows can be a pain b/c you don't know what they are called.
Use  **/bin/lcpci** and the links  above to possibly find the correct driver name.  Can't find it?   dump the output of lspci and lspci -n and some one may be be able to help with the name. for you to look for on a local haarddrive or install CDROM.[/QUOTE]

---

### Post by Andrew Shimmin on 2006-01-20
In the terminal. There are probably other ways to get to it, but if you click Applications (top left corner), then open Accessories, it should be in the list. It's like an MS command prompt.

---

### Post by pesz on 2006-01-21
I have installed the driver for my TravelMate 4401 a few days ago. The ndiswrapper installation page is quite helpful to follow step by step ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)). Then I found acer_acpi and enabled the wireless feature ([http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)). Now I can see my AP with iwconfig but ping results in Destination Host Unreachable. :???:

---

