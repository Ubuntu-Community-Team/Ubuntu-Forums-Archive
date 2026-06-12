---
title: "ASUS Prime X370 Pro Motherboard"
date: 2017-03-15
forum: Hardware
---

### Post by davaweb on 2017-03-15
Does anybody know of any problems using Ubuntu with the ASUS Prime X370 Pro Motherboard?

Looking to buy eith that or the ASUS Prime B350-Plus Motherboard (but the latter only has 6 sata ports).

Many thanks

---

### Post by QIII on 2017-03-16
Hello!

There are a number of posts on the Forums indicating that some people are having problems with the Socket AM4 Ryzen CPUs.  I can't tell you if there is a solution for Ubuntu, but apparently the problems do not exist for Fedora.

---

### Post by Delvien on 2017-03-16
Kernel 4.10 adds support for am4 CPUs, as Ubuntu 16.10 currently runs 4.8, and I do not believe 4.10 has been added yet (or im really behind on my updates!)

You can always compile the kernel yourself and run it.

---

### Post by QIII on 2017-03-16
Others on the forum have tried 4.10 and even 4.11 without success.

Phoronix has been able to do testing, but there seems to be some practical problem for normal end users.

---

### Post by davaweb on 2017-03-16
Thanks for the replies.
> Phoronix has been able to do testing, but there seems to be some practical problem for normal end users.
I saw they referred to having tested Ubuntu on the Prime X370 but could not find any info about their results.

Do you know of any test results? I have searched (including google) but found nothing.

Is this a case of 'in time' it or do some motherboards never get supported?

---

### Post by hedeon79 on 2017-03-17
I can confirm I had no problems with Arch Linux....

---

### Post by slickymaster on 2017-03-17
*Thread moved to **Hardware**.* for a better fit

---

### Post by gordonmoore on 2017-03-18
You mentioned you also were looking at the ASUS Prime B350-Plus.  I have this motherboard and have been attempting to install ubuntu server 16.04 and 16.10.  

During the install, I was unable to get the installer to get networking working.  The link state appears to be ok, but never is able to get a DHCP address.  No luck static IP either.  I had a spare intel PCI network card available, and after installing, I was able to successfully complete the installation process.... Which I think indicates that the motherboard is fine beyond the network driver.

However, after the install, I am still running into problems (am unable to get through initial boot) but I believe this is due to Ryzen and Kernal 4.10, 4.11 stuff.... not likely due to the motherboard.

Hope this helps.

---

### Post by davaweb on 2017-04-16
In case anybody isinterested, I used the ASUS Prime B350-Plus, Ryzen 1700X and 16GB G.Skill Flare-X F4-2400C15D-16GFXR (2x8GB) Ryzen DDR4.
Initially I tried Kingston HyperX Fury HX426C15FBK2/16 16GB (2x8GB) DDR4 Black but no response on boot - blank screen, nothing. Changed to the G.Skill and voilá, system worked!
Loaded Ubuntu with kernel 4.8.x and after extensive tests no hint of failure. However I did end up using kernel 4.10.10 stable because of the reported need for it and it is working very well - and fast.
I haven't tried installing Ubuntu in UEFI mode but cannot see that would be a problem (I don't use Windows). I'm no fan of UEFI have watched some of the conferences on it.
DOWNSIDE:
1. Ryzen 7 has no graphics processing so the rear panel sockets don't wok - a separate graphics card is needed.
(The AMD Athlon fits the AM4 socket so that is an alternative)
2. New technology so I can't find any sensor software for temps, voltages, fan speeds. lm-sensors and psensors give usage, temp1, cpu fan

Hope this helps those trying to make a decision.

---

### Post by paulisdead on 2017-04-17
I got the crosshair hero vi, which is pretty close, but has an intel NIC.  It's working fine with 17.04, although I brought over my Xonar DX2 sound card I had been using.  If the board in question uses an ALC1220 sound chip, you'll need a 4.11 kernel, too.

You can find an updated it87 driver that you can build manually to get temp sensors working [https://github.com/groeck/it87](https://github.com/groeck/it87)

Ubuntu 17.04 includes the 4.10 kernel, so probably the preferred version for Ryzen.

---

### Post by MIckaldo on 2017-04-27
I've had an asus prime x370-pro for about 2 weeks with Ryzen 7 and a couple SSDs.

I'm dual-booting Win 10 pro 64 and Ubuntu 16.04 64. 

So far, I've not had any unsolvable problems with anything in either system, so apparently it can work.

Other Info: 16 G DRAM; Bios 0504 (it came with, works OK); OC'd to 3500 stock fan; 

And: I did have problems on my first install with some device recognition in ubuntu, so I read about the latest kernel, at that time; 4.10.10 and installed it. That made a fair difference in terms of performance and recognition of sound device and some others. 

> $ uname -a Linux mingus 4.10.10-041010-generic #201704120813 SMP Wed Apr 12 12:15:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Good luck. I've not tried the latest bios 0604 and won't until there's good reports about the next bios.  --cheers

Update: My audio problem was just a dumb mistake by me. I had plugged my mike into the line in jack on the front of the box. Just unplugged it, put it in mike, and sound is fine again.

---

### Post by ruvapost on 2017-06-04
**ASUS Prime X370 Pro Motherboard and this soundcard works on Ubuntu 17.04**

---

