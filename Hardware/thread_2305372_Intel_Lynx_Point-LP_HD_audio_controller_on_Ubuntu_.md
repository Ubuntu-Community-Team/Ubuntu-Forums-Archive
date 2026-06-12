---
title: "Intel Lynx Point-LP HD audio controller on Ubuntu 14.04: no sound in subwoofer"
date: 2015-12-05
forum: Hardware
---

### Post by shersk on 2015-12-05
According to lspci and this page [http://www.ubuntu.com/certification/hardware/201307-14038/](http://www.ubuntu.com/certification/hardware/201307-14038/) my Vostro 5470 has two sound controllers, one for HDMI and the other for the built-in speakers, which includes one subwoofer.

I have problems getting the subwoofer to work in Ubuntu. There are some posts various pages relating to the Vostro 5470 subwoofer problem. For example:

[http://ubuntuforums.org/showthread.php?t=2249148](http://ubuntuforums.org/showthread.php?t=2249148)

This did not help in my case.

[https://askubuntu.com/questions/405408/subwoofer-not-working-in-13-10-on-asus-n56dp](https://askubuntu.com/questions/405408/subwoofer-not-working-in-13-10-on-asus-n56dp)

This made the subwoofer work, but the internal microphone, which had worked normally before, stopped working, I tried many different pin combinations using HDAJackRetask - a useful tool if you want to tinker - but none of them made my microphone work again. Tired of all this endless tinkering, I am looking for experiences others have had to fix this. I am surprised that this laptop doesn't already have a solution regarding the subwoofer, since it's certified for Ubuntu pre-install. (Does Ubuntu really allow a certified pre-install that leaves the subwoofer out? Hm..)

Using dmesg, it seems the codec Realtek ALC290 is used to control the internal speakers. My question is: Is it correct to use this codec to control the Intel Lynx Point-LP HD audio card?

---

