---
title: "New laptop XPS 1210, new woes"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by xboxbman on 2006-10-19
I just got a new laptop from dell, the XPS M1210.  Naturally I instantly installed ubuntu 6.06 on it.  To my dismay, the wireless doesn't work.  Infact the wireless is completely abscent as far as I can tell.  I ran windows on it for about 5 minutes when it first arrived (to remind me why I use linux) and the wireless was working fine.  According to the ubuntu wiki, this thing uses the ipw3945, which the latest kernel is supposed to support.  But so far nothing. Any ideas?   I can't even find a reference to it in the device manager to see make make it is, and in the BIOS it simply says DELL wireless.  This is my university computer, and I need this thing up and running as soon as possible!  All help is greatly appreciated.

---

### Post by xboxbman on 2006-10-19
Just checked my bill, it says my wifi card is: Dell Wireless 1500 Draft 802.11n Dual-band Internal Wireless....doesn't help me yet though.

Edit:  I just found that it is Broadcom 4328 chipset.  lspci I get:

0000:0c:00.0 Network controller:  Broadcom Corporation:  Unkown device 4328 (rev 01)

I had a broadcom chipset in my old laptop and got it working after about 20 hours messing with ndiswrapper and bcm43xx drivers.  Should I try the same?

---

### Post by xboxbman on 2006-10-19
bump

---

### Post by xboxbman on 2006-10-20
so...that's then.  If I can't solve this, I'm afraid I may have to go back to Windows (booooo!!) if I can't solve this by the end of the weekend.  I will keep this thread going to keep all you readers posted on my progress (if any).  Hopefully I will find a solution and help anyone else in the same boat as me...

---

### Post by abarth on 2006-11-25
Too bad, you choose the Dell wireless card instead of the Intel wireless Pro card (ipw3945). According to [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), 
the Intel wilreless card works in Dapper out of the box. 

But you might not be entirely out of luck. The link above and especially the site [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) might help you to make this wireless card work.

The bcm43xx driver is also included in the Linux kernel since 2.6.17-rc2. Edgy uses the 2.6.17 kernel, so might want to try the LiveCD of Edgy.

Good luck,
Alex

---

### Post by didobuntu on 2006-11-25
> **xboxbman said:**
> bump

Try Edgy, ubuntu 6.10. Sure it will be better

---

### Post by HokkaidoHillbilly on 2007-04-15
Another thing is that you got a 802.11n card, which is technically still in draft, i.e. you might have problems w/ it even in some Windows apps.  Maybe it'll run under Feisty when it's released in a few days?

---

### Post by xboxbman on 2007-04-18
> **HokkaidoHillbilly said:**
> Another thing is that you got a 802.11n card, which is technically still in draft, i.e. you might have problems w/ it even in some Windows apps.  Maybe it'll run under Feisty when it's released in a few days?

I just tried the feisty beta disc and the wireless did not work.  Nor did the web cam, or the sdcard reader.....Silly me getting my hopes up.  I've got the wireless running now with ndiswrapper.  Still it would be nice if it orked out of the box, instead of having to fix it everytime I update the kernel.

---

### Post by hardyn on 2007-04-18
The cards are modular... if it really is causing you grief... you may be able to have it swapped at your expence at a dell repair outlet.

---

### Post by Alfdog on 2007-04-27
You can get a 3945abg card off of ebay for about $20, and it's quite easy to change yourself, almost like changing ram, but there a couple of antenna wires that attach to the card.  Keep looking though, because there probably is a solution somewhere for that card.

---

### Post by newtimes on 2007-06-08
I have the m1210 and ran 6.06 in disc mode and wifi card worked right away but ran 7.04 in disc mode and it did not work I have the Intel PRO/wireless 3945ABG. hope this is helpful.

---

### Post by truico on 2007-06-09
:(  I installed 7.04 on a brand new Ahtec M31EI7 and everything worked fine out of the box! 
But yesterday, after an internet session via a hotspot my WiFi disappeared from the network box. I have a Intel Corp Pro/Wireless 3954 ABG Network card (bus type PCI). I searched berlios.de, but no help found. It just broke.

Anything I can do with the terminal (is this newbe-talk?:redface:)

---

