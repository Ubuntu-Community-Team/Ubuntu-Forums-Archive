---
title: "Good News For People With VFS101 Fingerprint Reader"
date: 2010-09-30
forum: Hardware
---

### Post by gallifrey on 2010-09-30
Note to mods: Apologies if this information s already available. I did do a search and saw no mention. Likewise, if I have posted in the wrong section, please move. Thank you.

Hello all, 
            having recently installed Ubuntu on an Acer Aspire 6935G, I quickly became aware of a problem with availability of drivers for the VFS101 Fingerprint reader (which Ubuntu detects as a DigitalPersona 138a:0001). It seems that development of an Open Source driver is not currently progressing, and my knowledge of programming is too far out of date for me to pick up where the previous developers have left off. In light of that, I contacted Validity Inc. And, with a little persistence, I got this reply:

>  
Thank you for your interest in Validity Sensors.
 
 We plan to release Ubuntu support package by the end of the year. It
 will include proprietary sensor daemon with sample for fprint. We do not
 have plans for Fedora, but the same package might work (no guarantee).
 
 Please check back in mid October if you are willing to be a beta tester.


It may not be FOSS, but it's a start. At least we will be able to make use of this hardware. :D

---

### Post by Grenage on 2010-09-30
That's good news, the hardware support is always a bonus.  Open source is preferable, but there's nothing wrong with proprietary.

---

### Post by stryker88 on 2010-12-25
I think this is not solved as anywhere I look online, so far, I can't find this release or place to enroll for beta testing.

---

### Post by fantasm!c on 2011-01-14
Hmm still nothing. fprint demo doesn't find anyting on my hp dv3-2350ed

---

### Post by fantasm!c on 2011-01-18
I have mailed to validity support and they say "There is just a short delay." So it will be here soon :)

---

### Post by fabrixx on 2011-01-27
With vfs101 driver i've get my fingerprint with VFS101 of mu HP Dv51170, i write apost in my blog with a fingerprint output image:

[http://www.osside.net/?p=5274](http://www.osside.net/?p=5274)

---

### Post by BHEJU on 2011-02-07
Please translate this in English.
Also, kindly provide the link to drivers site.

Bheju

---

### Post by fabrixx on 2011-02-07
I try to reassume in my bad english.

This sistem generate only fingerprint image without an useful sistem to use it in the sistem.

This is the driver page:
[https://github.com/rayl/vfs101driver/tree/master]("http://ubuntuforums.org/libusb-1.0-0-dev")

You have to download source at this link:
[https://github.com/rayl/vfs101driver/tarball/master](https://github.com/rayl/vfs101driver/tarball/master)

Uncompress & from driver dir:

```
$ mkdir -p img/X img/Y $ make 
$ sudo ./src/proto woot personal
```When you see scrolling text enroll your finger.

The images are saved in /rayl-vfs101driver-73a803b/img/X (or Y) folderIs necessary libusb-1.0-0-dev package build-essential & see make output for more.
I used Debian.

To translate you may use [google]("http://translate.google.it/translate?js=n&prev=_t&hl=it&ie=UTF-8&layout=2&eotf=1&sl=it&tl=en&u=http%3A%2F%2Fwww.osside.net%2F%3Fp%3D5274")

---

### Post by fantasm!c on 2011-02-09
I get a "command not found" when i try to execute proto

---

### Post by fabrixx on 2011-02-10
> **fantasm!c said:**
> I get a "command not found" when i try to execute proto

You have extecute it from source folder (cd  home/..desktop/rayl-vfs101driver-73a803b) ?

---

### Post by fabrixx on 2011-03-22
Patched:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089)

Post #78

---

### Post by Dngrsone on 2011-05-18
[This](https://launchpad.net/~fingerprint/+archive/fprint) seems to work for me, to a point... I can't seem to get a consistent scan for my finger. That is, I can consistently scan three times, but then I can't do it right later when I am trying to log back in.

My device is:  ID 138a:0001 Validity Sensors, Inc. VFS101 Fingeprint Reader

I am running 11.04-desktop-amd64 on a Pavilion DV4-1200us.

---

### Post by Alien.col on 2012-02-05
You are right the sensor fails to identify fingers consistently.

---

### Post by Druckin on 2012-06-23
Wow that release went back to 2010 and I have checked Validity website and many other places. It appears that they never did release the drivers for any flavor of linux, in addition they never even provided generic drivers for the Hardware vendors. I use Ubuntu exclusively and I would love to be able to use the fingerprint reader on my HP dv7. Has anyone heard of any solution that would allow me to do this? Also I am not a rocket scientist I have used Linux for about 18 months so I am a noob. If I have to do advanced tasks to make it work I will definitely require step by step directions. lol Thanks.

---

### Post by fabrixx on 2012-09-17
Supported in [Debian]("http://www.osside.net/?p=9847")

---

