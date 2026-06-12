---
title: "Intel(R) PRO/Wireless 2200/2915 in Lucid"
date: 2010-06-05
forum: Hardware
---

### Post by jeremiah.bloggs on 2010-06-05
My laptop drops the wireless network connection when transferring a lot of data. I have tried setting hwcrypto=0 and associate=0. I am aware of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352150) , which seems to be the cause. I am using WPA2 and have tried two different access points. I am not fussed about the resets, but every few times the networking freezes and I have to do rmmod ipw2200; modprobe ipw2200 before I can connect again. This may be required more than once a minute (but it will also work fine for hours at a time when used lightly).

I wondered if anyone had any suggestions, and what other mini-PCI card to buy instead that would definitely work. Many thanks.

---

