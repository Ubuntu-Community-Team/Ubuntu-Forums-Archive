---
title: "probs installing Unbuntu on an Inspiron 8600"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by ianv01 on 2007-10-05
My 8600 has installed Unbuntu 7.04 but there are 2 issues.

1. The wifi card doesnt work (Intel Pro wireless 2200BG). I see people have made a few comments to other cards, but not this one. And some people are very technical explaining how to cut stuff from the WinXP driver - thats beyond me. Im a newbie.

2. The screen is very soft and quite large. There are 10cm 1 pixel high lines flashing on the screen. A driver issue here, but I cant install a linux driver. There is one on AMD website, but how do I install it? Its not simply double click like Windows! My card is the ATi Mobility Radeon 9600 turbo (128mb)

Sorry if Ive repeated my questions. I searched the site thoroughly, but found nothing the same.

If anyone can help, I would appreciate it.

---

### Post by yetanothernick on 2007-10-24
Hi,

I also have an Inspiron 8600, with ATI 9600, but Broadcom-Wireless, not Intel.
I was running ubuntu 7.04 on it, but just upgraded to ubuntu 7.10.
I can only recommend using the new 7.10, for me the upgrade worked perfect.

I used the following download link for the ATI driver:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.40.4-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.40.4-x86.x86_64.run")

Installation is rather simple: 
-open a terminal window
-cd to where you downloaded the driver
-type: sudo sh ati-driver-installer-8.40.4-x86.x86_64.run
 sudo will need your password, so give it when prompted.

Then follow instructions.

This gave me a stable X, just that resolution was only 1024x768.
There are ways to change this with ubuntu provided utilities (Menu System -  Preferences - Screen and Resolution) or also with an ATI tool installed along with the driver, but I changed this just directly in my xorg.conf.
If you need help there, just ask again.

Hope that helps!

---

