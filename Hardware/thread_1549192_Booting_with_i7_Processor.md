---
title: "Booting with i7 Processor"
date: 2010-08-09
forum: Hardware
---

### Post by xTLx on 2010-08-09
Has anyone one with the new i7 processor had trouble booting Ubuntu? What about with the liveCD? I can't seem to boot either way...

[http://ubuntuforums.org/showthread.php?t=1548861](http://ubuntuforums.org/showthread.php?t=1548861)

---

### Post by howefield on 2010-08-09
Doubt it is an issue with the i7 processor. 

Is this a "real" dual boot or a Wubi install of Ubuntu ?

---

### Post by xTLx on 2010-08-09
I've tried both. I'm unable to boot with either.

---

### Post by xTLx on 2010-08-09
bump

---

### Post by efflandt on 2010-08-09
I have a new Dell Studio XPS 8100 with i5 and nVidia GT220.  Everything worked out of the box, even its wireless.  I just enabled the nvidia driver for faster video.

But something strange that I have not figured out yet is that it boots 64-bit 10.04 fine from a 160 GB WD Passport, and it boots the same fine from the far end of its internal 1 TB drive (beyond 900 GB), but grub rescue says unknown filesystem for the same at the far end of a 500 GB WD Passport.  The filesystem in all cases was ext3 and the 500 GB USB drive boots fine on two different laptops from 2006.  So there is no problem with the system on the 500 GB USB drive (I use it for my work laptop when on the road).

Turbo mode may not work for i5 and i7 yet until a newer kernel, but there should not be other problems unless you end up with other cutting edge hardware that is not supported yet.

---

### Post by xTLx on 2010-08-09
Well right now I have a NVIDIA GeForce 310M... I dont know if thats very relevant to my problem, but I've never used Ubuntu before and know nothing about the command line... Thx anyways man.

                                  *    *    *

Right now I'm looking for some proper instruction on dual booting so anyones welcome to post suggestions, but I'm looking for some help from some one who is very experienced with boot-up related problems.

If you are interested with helping me thoroughly (step by step) please first read my other thread ([http://ubuntuforums.org/showthread.php?t=1548861](http://ubuntuforums.org/showthread.php?t=1548861)) and reply to me here. thx.

---

### Post by howefield on 2010-08-10
> **xTLx said:**
> If you are interested with helping me thoroughly (step by step) please first read my other thread ([http://ubuntuforums.org/showthread.php?t=1548861](http://ubuntuforums.org/showthread.php?t=1548861)) and reply to me here. thx.

Any one who wanted to help would have to start by asking you several questions as it isn't clear on exactly where you are stuck other than it is a boot problem. (could be why you had no responses on the other forum).

My advice would be to post another thread, cut out anything that isn't needed, stick to the problem and be precise about what that is.

Read the CoC if you like, "Section II - Technical Support Policies: When asking for technical support:" .

No offence, just saying.

---

### Post by xTLx on 2010-08-10
hey no problem sorry if I wasn't clear.

---

### Post by linux18 on 2010-08-10
I use an overclocked i7 @2.2GHz with turbo up to 3.2GHz and have never experienced a problem ever. 
i7 FTW!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Yellow Pasque on 2010-08-11
I would try the testing version of Ubuntu (10.10/Maverick). [http://cdimage.ubuntu.com/releases/maverick/alpha-3/](http://cdimage.ubuntu.com/releases/maverick/alpha-3/)

At least that would rule out issues due to Lucid's older kernel.

---

### Post by TBABill on 2010-08-11
Your other post states the "graphics are integrated with the CPU", which I believe means you are using the GPU integrated into the CPU "chip". I have a Core i3 and have the same scenario. I can boot mine with the CD, but it freezes. The problem is there is no support in kernels prior to 2.6.33 for the Intel Core i3/5/7 chips using the "on chip" GPU. If you had a separate graphics card I believe it would work, at least to a degree of performance.
 
Anyway, until 10.10 comes out you will not be able to use Ubuntu unless you are able to get a more current kernel to work with it. Since you are new to Ubuntu I wouldn't even recommend that route. If you want to try Linux anyway, [www.distrowatch.com]("http://www.distrowatch.com") has a search function where you can search by kernel to see what other distros use 2.6.33, 2.6.34 and 2.6.35 kernels. Those should provide the video support you need and the choice of distros is all yours. I personally use PCLinuxOS 2010 and it's incredibly easy (just like Mint), but you may find others to be friendly and to your liking.
 
Final recommendation: After trying so many different distros, I have some advice. When you find one using a kernel your machine requires, do some research on Google or another search engine and look for "distroname review" (distroname being whichever you want to research). See what blog authors or Linux journalists think of the distro, how easy it is to install and configure, hardware support, etc. There is a ton of info out there and it will help you not waste time with more advanced distros that may require a level of knowledge you have not yet obtained (for me that would be Arch or Gentoo....I am not yet at that level of knowledge yet).

---

### Post by tjktyler on 2010-08-11
I did a system rebuild this morning with an i7-930 (desktop) on a Gigabyte board. The board had some issues with USB not being enabled at boot, but Ubuntu booted fine. According to the box, the i7-9xx series needs a separate, dedicated graphics card. The only "issue" is that System Monitor shows 8 cores.

---

