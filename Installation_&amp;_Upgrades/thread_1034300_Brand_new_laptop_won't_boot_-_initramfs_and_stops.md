---
title: "Brand new laptop won't boot - initramfs and stops"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by dBuster on 2009-01-08
Okay my old laptop died so I bought this 64 bit compaq laptop with the AMD Athlon 64 X2 processor and when I try to boot from the CD, the 8.04 LTS disc I get to a terminal screen with the prompt <initramfs> and then nothing happens...

I can enter commands and have tried several different configurations to get it to boot but no luck.  I even tried to run the TRY WITHOUT INSTALL mode and same thing...  I have been through the laptop bios and nothing there would indicate it is preventing me.  The laptop was preloaded with ugh, vista home premium SP1...

Any ideas to get the install to work???

---

### Post by kranny on 2009-01-08
try to Install with the Alternate CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'
Follow this guide:
[https://help.ubuntu.com/community/Bu...8burn%29%7C%28](https://help.ubuntu.com/community/Bu...8burn%29%7C%28)
Do md5sum on iso, burn at 4x or less, as 'image' and not 'data', in good quality CD-R media, check CD integrity before installation.

---

### Post by dBuster on 2009-01-08
> **kranny said:**
> try to Install with the Alternate CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'
Follow this guide:
[https://help.ubuntu.com/community/Bu...8burn%29%7C%28](https://help.ubuntu.com/community/Bu...8burn%29%7C%28)
Do md5sum on iso, burn at 4x or less, as 'image' and not 'data', in good quality CD-R media, check CD integrity before installation.

So then you think the 8.04 LTS 64bit version I got from Canonical may have gone bad?  I will give it a try and burn a new cd.  Couldn't hurt...

---

### Post by kranny on 2009-01-08
Yes that happens sumtimes

---

### Post by avtolle on 2009-01-08
Have you tried booting in "safe graphics" mode? There could be a graphics card conflict causing the problem. It's been a long time since I've tried to install from a "live" CD, but I think the safe graphics option is accessed by pressing F4 or F6 at the initial menu and selecting the same from the drop down list that appears.

---

### Post by dBuster on 2009-01-08
> **avtolle said:**
> Have you tried booting in "safe graphics" mode? There could be a graphics card conflict causing the problem. It's been a long time since I've tried to install from a "live" CD, but I think the safe graphics option is accessed by pressing F4 or F6 at the initial menu and selecting the same from the drop down list that appears.

I have also tried that.  I have tried almost every possible boot configuration there is from the cd and each time I get to that <initramfs> and it just stops...  I even thought to let it sit for a while and 20 minutes later it was still at that point.  I think it has or was something to do with a ram file system for the install...  Not sure though hence my asking the guru's here.

Also in the bios setup of the laptop there is a setting for turning on virtual machine ability with the Athlon X2 64 bit processor.  Currently that state is set to disabled.  Anyone think enabling it might help?  Since the vista version shipped with the laptop was and is a 32 bit OS and I am trying to get a 64 bit OS installed.

---

### Post by dBuster on 2009-01-08
Update:

I have downloaded and burned the new iso 8.04.1 and I am now able to get a little bit further but the system still hangs and will not boot fully.

I get past the initial screen choosing to run from the cd without making changes to start out to make sure I can boot Ubuntu.  I get through the choices and yes I have tried the safe graphics mode, and then the progress bar comes up and it goes back and forth several times then it starts to load starting at the left of course and it makes it almost to the third block before it stops.  Now this time I notice that the caps lock light is flashing.  But it will not go any further.

Any help?

---

### Post by dBuster on 2009-01-08
Okay this is weird, but I tried to run the qemu with Ubuntu inside of Vista and it is telling me that I do not have a 64 bit processor!  I have an Athlon X2 64 bit processor!!!  What is going on?

this is a brand new Compaq Presario CQ60....

I was able to boot using the [ctrl][alt][F1] to see the verbose of the boot.  The following is what I ended up with.

```
[  113.978568]
[  113.978569] HARDWARE ERROR
[  113.978570] CPU 0: Machine check exception:  4 Bank  4: b600000000070f0f
[  113.978825] TSC 35134dc47c  ADDR 900000c2004001
[  113.978076] This is not a software problem!
[  113.979042] Run through mcelog --ascii to decode and contact your hardware vendor
[  113.979130] Kernel panic - not syncing: Machine check
```

---

