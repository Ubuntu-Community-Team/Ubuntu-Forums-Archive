---
title: "speedtouch"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by sdd231163 on 2007-05-30
Hi. I've just installed a nice new ubuntu 7.04  on my computer. Everything seems to be running fine except my internet connection. I have an ADSL Speedtouch 330 revision 4 and it seems to work fine under the default kernel, but, having updated my system with the package manager, the new kernel will not connect to the internet. Can anyone help?

My connection is PPPoATM, set up using the instructions  [here]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

---

### Post by travsraven on 2007-05-30
Hiya there,

I could never get my speedtouch usb modem to work with the instructions on that page at all or a few other pages I looked at via google when I had just installed Edgy for the first time. After a few hit and misses in google I finally came to a link that actually did the business. Funny thing is that it actually comes from Ubuntu's community document page.

The link in order to get the modem to work properly is [here]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch"). Go through the instructions before you use the terminal and see if there are any files you need to download first. 

Once done follow it all and then reboot. Here's a tip, if when you reboot that your modem still isn't working, follow that set of instructions again in terminal and then reboot - it will definitely work then. I don't know why but sometimes it never used to work for me first time round in Edgy and am not sure if it's still the case in Fiesty as I have changed to using a linksys router.

Hope this helps - cause that is the only page/link - I could follow with ease and it enabled to get my speedtouch modem to work.

---

### Post by spaarks on 2007-05-30
The easiest way to get your Speedtouch USB modem to work is to use PCLINUXOS (PCLOS) instead of Ubuntu. It detects the modem and brings up a window asking you the ISP protocol (eg PPPoE), user ID and password.
I do not know why Ubuntu can't do this.

---

### Post by TheMadGeneral on 2007-10-19
I got the Speedtouch modem to work by downloading usbadslmodemmanager_0.5.4_i386 at [http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page]("http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page")

Thanks to [email]StevenHarperUK@gmail.com[/email] for making this possible and persuading me to persevere with Linux.

---

### Post by FreewheelinFrank on 2007-10-21
> I do not know why Ubuntu can't do this.

> Our philosophy is reflected in the software we produce and included in our distribution. As a result, the licensing terms of the software we distribute are measured against our philosophy, using the Ubuntu License Policy.

When you install Ubuntu almost all of the software installed already meets these ideals, and we are working to ensure that every single piece of software you need is available under a license that gives you those freedoms. 

Ubuntu would rather have Ubuntu live CD'd sitting unused on shelves and Ubuntu partitions sitting unused on HD's than have their distro sullied by proprietary software. My own Ubuntu partition is an example of this: pure in it's expression of the Ubuntu philosophy, as  the only way I can get an internet connection using my Speedtouch modem is to boot into Windows.

The reasons I haven't wiped off Ubuntu are 1) my soundcard doesn't work with PCLinuxOS (yet?) and 2) I actually like Ubuntu.

How many users have tried Ubuntu and given up because they weren't prepared to follow the advice from Ubuntu that a) they have the wrong modem, buy a new one or b) perform a series of hacks and edits that need a level of skill only possessed by highly experienced computer users, and difficult even for experienced users switching over from Windows.

Having a pure philosophy is one thing- turning away potential users to preserve this philosophy is another.

---

