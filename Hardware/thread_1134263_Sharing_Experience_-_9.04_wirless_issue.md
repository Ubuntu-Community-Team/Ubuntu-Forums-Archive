---
title: "Sharing Experience - 9.04 wirless issue"
date: 2009-04-23
forum: Hardware
---

### Post by gadgetman1 on 2009-04-23
I just tried a fresh install on two Dell Latitude Laptops. One is D600 and the other D800 (both using Broadcom BM43XX legacy driver). 
9.04 did not detect the wireless on either one and I could not spend any more time to resolve the issue. Also on D800, did not detect nVidia display driver. Versus I have been using 8.04 and later 8.10, and everything worked out of the box minus some Codecs that I installed myself.
For Now, going back to 8.10, unless I have time to spend resolving the issues.
Any quick fixes and suggestion appreciated.

Gadgetman1

---

### Post by SpyroViper on 2009-04-23
Broadcom do horrible hardware that isn't compatible with practically any distros out of the box for Linux.

I thought Dell's used Realtek?

---

### Post by gadgetman1 on 2009-04-23
I have been using these two laptops for almost a year. Ubuntu 8.04 and 8.10 did not have any problem on any of these two models.

May be the newer Latitude's using other wireless, but the older Latitudes are all using Broadcom wireless, even though under Windows they get installed under Dell Brand.

---

### Post by mcserags on 2009-04-24
I have been experiencing this exact same issue.  I too have a D800 trying out the new 9.04 Intrepid Ibex version.  The wireless card is a bcm4306.  I resolved this issue by downloading the firmware for the card. (Google for b43 firmware download).  You just download and extract both the b43 and b43legacy directories into the /lib/firmware/ directory.  Reboot and BAMM! it started working and detected nearby wlans.

Hope this helps!!  Hope you read this before reverting back to 8.04 good luck.

---

### Post by gadgetman1 on 2009-05-12
Thank you very much mcserags and sorry for the late reply. I will try your solution for firmware upgrade and will keep everyone posted specially since many people have issue with wireless on 9.04. Probably over the weekend. Thanks
 again

Gadgetman1

---

