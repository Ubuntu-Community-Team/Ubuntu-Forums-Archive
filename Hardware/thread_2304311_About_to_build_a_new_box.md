---
title: "About to build a new box"
date: 2015-11-25
forum: Hardware
---

### Post by DigiAngel on 2015-11-25
So...here's what I'm looking at:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=9912896&CatId=11982](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=9912896&CatId=11982)
Intel Core i7-4790K 4.0GHz Quad Core Processor
MSI Z97-GAMING 5 ATX LGA1150 MB
HyperX Fury 8GB (2 x 8GB) DDR3-1866 Memory

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=9514803&Sku=EVG-102776324](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=9514803&Sku=EVG-102776324)
EVGA GeForce GTX 970 4GB FTW GAMING ACX 2.0 (04G-P4-2978-KR

Any surprises that people have experienced with Ubuntu?  Thanks....the wife's machine is fast dying, so this is sort of expedited.

---

### Post by oldfred on 2015-11-25
I have a Asus-AR z97 and I had to make many UEFI setting changes to correctly configure system. But 15.10 just installed, and SSD really makes system fast. I have small 120GB SSD for boot and larger HDD for data.
You also will have some settings and configurations to get nVidia working. Either from repository or the new Ubuntu ppa for video drivers.

 MSI-Z97/Intel's Core i7 5775C Broadwell Is Running Well On Ubuntu 15.10 Iris Pro 6200
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1)
Newer version but perhaps some of the same issues:

 MSI Z170A GAMING PRO motherboard
[http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1](http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

      
 NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

Just a while ago phoronix posted this:

 The GeForce GTX 970/980 new Maxwell GPUs also couldn't be tested since there isn't any hardware acceleration support with Nouveau and that's currently blocked by NVIDIA providing their new signed firmware images. Or only nVidia will work.

And generally you need newest kernel & newest video drivers.

---

### Post by Bucky Ball on 2015-11-26
*Thread moved to **Hardware**.*

---

### Post by DigiAngel on 2015-11-26
Beautiful...thanks so much...looks like the timing is good for getting a new box, Black Friday and all.  Thanks again.

---

### Post by Yellow Pasque on 2015-11-26
Keep this link handy for easy install of latest nvidia driver: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

I'd also be concerned with the LAN chipset - Atheros Killer E2205. I know folks were still having issues with it (needed to patch and build a custom kernel module) in Ubuntu 15.04. Maybe it works out of the box on Ubuntu 15.10, but don't count on it. Do some homework/research.

---

### Post by Yellow Pasque on 2015-11-26
On second look, support for the E2200 was supposedly added in kernel 3.10, so it should work on Ubuntu 14.04 or later.

---

### Post by MartyBuntu on 2015-11-26
Do NOT go cheap with a crappy power supply...
Power supplies are the base for any quality build.

---

### Post by Bucky Ball on 2015-11-26
> **MartyBuntu said:**
> Do NOT go cheap with a crappy power supply...
Power supplies are the base for any quality build.

This is also my soapbox. I'd swap the PSU to an 80%+ or 85% efficient if at all possible. This one is 78% and never heard of the brand (although that doesn't mean it is not a quality PSU, but you can definitely go better).

Further to MartyBuntu, the PSU is the heart of the machine. If it goes up in a sparky mess, some or all of the other components in the box will most certainly go with it. A good name-brand PSU will have the safety switches to ensure this doesn't happen. 

Good luck. :)

---

### Post by DigiAngel on 2015-11-27
Thank you....after doing more reading on the bundle I did a switch and went with:

[http://www.newegg.com/Product/ComboBundleDetails.aspx?ItemList=Combo.2442343]("http://www.newegg.com/Product/ComboBundleDetails.aspx?ItemList=Combo.2442343")

and

[http://www.amazon.com/BenQ-GW2765HT-27-Inch-LED-Lit-Monitor/dp/B00KYCSRSG/ref=cm_cr_pr_bdcrb_top?ie=UTF8]("http://www.amazon.com/BenQ-GW2765HT-27-Inch-LED-Lit-Monitor/dp/B00KYCSRSG/ref=cm_cr_pr_bdcrb_top?ie=UTF8")

Pretty stoked....been a while since I've built a box :)

---

