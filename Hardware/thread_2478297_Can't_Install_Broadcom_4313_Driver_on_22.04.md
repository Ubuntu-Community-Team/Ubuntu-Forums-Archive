---
title: "Can't Install Broadcom 4313 Driver on 22.04"
date: 2022-08-22
forum: Hardware
---

### Post by wmichaelb2 on 2022-08-22
I just installed and updated lubuntu 22.04 on my old Dell E6410. It uses the Broadcom 4313 chip:

lspci
,,,
02:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4313 802.11bgn 

When I was running xubuntu before, I had problems with slow wifi, but was able to solve them by installing the proprietary driver. This time, if I go to Preferences/Additional Drivers, the dialog box shows 

Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source

which is unchecked, and 

Do not use this device

which is checked. And the dialog box specifically states that "No proprietary drivers are in use". But the dialog box will not let me install that proprietary driver, which IIRC is what I did before. 
If I run 

lsmod | grep cfg80211

I get

cfg80211              974848  3 b43,mac80211,brcmsmac


Is there another way to install the proprietary driver? Thanks in advance.

---

### Post by tea for one on 2022-08-22
Here is the info [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

