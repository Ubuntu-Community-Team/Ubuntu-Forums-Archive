---
title: "ATI Radeon X1400 drivers / gaming"
date: 2009-06-25
forum: Hardware
---

### Post by m0nkeyk0ng on 2009-06-25
Hey. Vista died on me so I formatted and installed Ubuntu on my reincarnated laptop. It is a Dell Inspiron E1705.

I am running into trouble running games on wine. I run into strange display problems that are usually not listed in the "common bugs" section, so I am guessing it has to do with my video card, which is an ATI Radeon X1400. So I'm trying to update the drivers.

A game I'm trying to test is Counter Strike: Source, which worked perfectly on Vista. The game loads all right, but the screen goes black after the menu finishes loading. To fix this issue, I tried updating the video card, but ran into problems in each attempt:

Apparently the device should be listed in System -> Hardware Drivers - but it is not.

So I tried installing the ATI drivers using envyng, that just screwed up my display completely and I had to revert to the previous configuration.

I tried following the steps on this link: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) (Install from Ubuntu repositories (easier)), but received the following prompt:

sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: can't read '/lib/modules/2.6.28-13-generic/volatile/fglrx.ko': No such file or directory

So basically I'm out of ideas. I would greatly appreciate any help!
Thanks!

---

### Post by kalbee on 2009-12-24
I'm in a similar perdicament.  Did you find a solution ?

---

