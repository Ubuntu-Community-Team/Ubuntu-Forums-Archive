---
title: "Acer Aspir 5612 (Intel Core Duo) compatable?"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by abh83 on 2006-12-07
hey there,

does any one know if the Acer Aspire 5612WLMi series is compatible with Ubuntu 6.06 (dapper drake)? :confused: 

system specs:

-Processor: Intel Core Duo, T2300E 1,66GHz (2MB L2 Cache)
-Chipset: Mobile Intel 945PM Express Chipset
-Mem: 1x 512MB DDR2 533MHz (2nd slot free)
-Grfx: nvidia geforce go 7300, 128MB GDDR2 VRAM
-Display: 15,4" WXGA TFT LCD
-DVD drive: 8xDVD Smulti DL (DVD RW)
-HDD: 120 GB
-5-in-1 card reader
-Wireless: WLAN Acer InviLink Nplify
802.11a/b/g Wi-Fi
LAN: Fast Ethernet
-4x USB 2.0

thx
ABH

---

### Post by rpkehoe on 2006-12-07
The easiest thing to do is try everything out with a live cd, just down and burn it, and reboot into it.  But from the description, I don't see anything that should cause you any problems.  After you install you are going to want to get some drivers for your nvidia card, but it will still work without them (at a lower resolution).

---

### Post by GingerAlex on 2007-05-11
Hello,

I have the above laptop and can confirm that **it works!**

All hardware detected automatically except for the wireless card, which is a Broadcom 4318.

this took me a while to get to work, and as a noob I must confess I'm not entirely certain how I did it, but I can say:

1. the native driver (bcm43xx) is no good (by my experience and apparently others on the internet). You need to go down the 'ndiswrapper' route.

2. You need to install either or both of **acerpi** or **acerpk** . Again, I was being a bit unsystematic whilst trying to get this to work but I believe I now have both,

3. There is some excellent help if you search 'Broadcom 4318' on this forum.

I am using 7.04 Feisty Fawn.

Bon chance,
Alex.

---

### Post by Graphite on 2008-01-13
I've just installed Ubuntu 7.10 on my Aspire 5612, and t works almost flawlessly. My only gripes so far:

Bluetooth isn't detected and dosn't respond to the little switch on the front of the laptop
None of the media / special keys seem to work.

The wireless gave me a warning that proprieory drivers were being used, but worked completely automatically; I didn't have to install anything myself.

...Does anyone have ideas to fix my little gripes?

---

### Post by rpkehoe on 2008-01-13
Can't help you with the bluetooth (don't have it myself), but you should be able to easily setup the media keys using System > Preferences > Keyboard Shortcuts.  You have to set them up individually, but you can set them however you like.

As for the wirless drivers, that is only a matter of whether you have a philosophical aversion to proprietory drivers, I personally don't.  

Enjoy Ubuntu

---

