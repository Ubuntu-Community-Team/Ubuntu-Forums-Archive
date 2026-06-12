---
title: "Dell 1525 with WLAN 1395 in Europe or Japan"
date: 2009-06-09
forum: Hardware
---

### Post by csy33delight on 2009-06-09
I have tried for months to find a way to get my Dell 1525 with the 1395 WLAN card to recognize European or Japanese wireless channels. Channels 12-14. Dell support provided no help.

I finally found a Japanese version of r169066.exe and installed it under XP (I have a dual boot setup with Windows XP and Ubuntu 8.04) There is a directory /dell/drivers/r169066/driver_jpn. When I installed the wireless driver under this directory, I was able to see channels 12, 13, and 14 under Windows XP.

I then used the ndiswrapper tool to make a wireless driver for Ubuntu. I can now use all 14 channels under Ubuntu Hardy.

---

