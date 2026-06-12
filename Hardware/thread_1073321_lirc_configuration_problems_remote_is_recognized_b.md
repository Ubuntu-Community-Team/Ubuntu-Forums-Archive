---
title: "lirc configuration problems: remote is recognized but not in mythtv"
date: 2009-02-18
forum: Hardware
---

### Post by Hefeweiz3n on 2009-02-18
Hello everyone,

I am having trouble with my Hauppauge Remote on my Mythbuntu 8.04 Box. The Remote is connected via the IR-Input of my Nova-S TV-Card. What i have done so far is got it to work in **irw**, but apart from that: nothing.

So here is how i got irw to work: I started lircd using
```
$ sudo /usr/sbin/lircd -H dev/input -d /dev/input/event5 -n
```
then started irw. This is what i got:
```
$ irw
000000008001006c 00 Down HVR-1100
0000000080010067 00 Up HVR-1100  
00000000800100cf 00 play HVR-1100
00000000800100d0 00 SKip HVR-1100
...
```
So apparently the lircd.conf is fine, but somehow i am not able to use any keys on the remote besides the up/down/left/right and number keys, but strangely enough they even work when lirc is NOT running. I am quite frankly at a loss, because the mappings between the lircd.conf and the .lircrc seem OK (Using the provided Mappings from Mythbuntu). I attached my hardware.conf, the lirc version used is the standard 8.04 "lirc 0.8.3~pre1". So if u have any idea, it would be most welcome, cause i am sick of navigating TV with my keyboard.
If u need anymore Information please ask!

Thanks in advance, hefeweiz3n

EDIT: What i just found: **/dev/lirc0** is not present, i don't know if that is important, but is seems that that is the default device for lirc. the only lirc's i have are **/dev/lircd** and **/dev/lircm**.

---

### Post by Hefeweiz3n on 2009-02-18
Ok, so now i have some more clues: In my PC-Case i have another IR-Receiver, a iMon/Soungraph device which i can't use with the hauppauge remote. it would seem that that is interfering with my other ir receiver. but i don't get what **dmesg | grep -i lirc** is telling me...
```
[   41.377956] lirc_dev: IR Remote Control driver registered, at major 61
[   41.439861] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3
[   41.439867] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[   41.439901] usbcore: registered new interface driver lirc_imon
```

---

