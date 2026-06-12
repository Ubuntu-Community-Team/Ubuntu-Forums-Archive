---
title: "Toshiba A135 S4527 Compatibility"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by gubemton on 2007-11-05
Hi.  I am a bit of a newbie to linux (still have no idea of how to compile).

Recently I installed Ubuntu Ubuntu 7.10 on my new Toshiba A135-S4527 (tired of Vista slowness).

I have the following issues:

1) The sound does not works at all.  I have seen many solutions but they seem way too complex as they require comiling the kernel :(

2) My WiFi network is seen but when I enter the Security Encryption (WEP) Key it does not connect.

3) 3D effects are not working.  My laptop has an intel 945 integrated 3D graphics, how can I install the driver for this.  I only saw driver for nVidia and ATi Cards.

I previously tried ubuntu 6 on an M35X and it installed and worked perfectly.  I am frustrated now with this laptop and Ubuntu.


Thanks for you help and patience.   If I get this working I will be a Linux convert!

PS:

One thread pointed out that there was a bug report for this isue, but the report says it was fixed.  It does not work
[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88400](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88400)

---

### Post by xcat442 on 2007-11-12
Open up the terminal and type: sudo gedit /etc/modprobe.d/alsa-base

Scroll down through the alsa-base file til you find the line: # Ubuntu #62691, enable MPU for snd-cmipci

Now paste this line just above it: options snd-hda-intel model=3stack

Save the file and reboot your laptop. This has worked for me, I hope it works for you.

Peace

P.S. Try changing the network settings around and select HEX or ASCII and re-enter your password. The WiFi does work with Ubuntu.

---

### Post by PRDS on 2008-04-18
Your suggestion for the sound problem fix worked like a charm for my Toshiba Satellite A135-S2745. **Thank you very much!**

---

