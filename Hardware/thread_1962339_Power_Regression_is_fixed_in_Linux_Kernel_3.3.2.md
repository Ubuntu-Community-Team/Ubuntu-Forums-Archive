---
title: "Power Regression is fixed in Linux Kernel 3.3.2?"
date: 2012-04-20
forum: Hardware
---

### Post by suryak on 2012-04-20
I just opened linux kernel site and found that a stable version 3.3.2 is already released..

so, does the power regression in laptops (especially intel, with graphic cards..) is fixed or not???

I use Lenovo G570 with Intel i5, ATI Radeon Graphics.
What's the status of the bug??

---

### Post by mastablasta on 2012-04-21
> **suryak said:**
> I just opened linux kernel site and found that a stable version 3.3.2 is already released..

so, does the power regression in laptops (especially intel, with graphic cards..) is fixed or not???

I use Lenovo G570 with Intel i5, ATI Radeon Graphics.
What's the status of the bug??

what buG? AMD radeon in your maschine use proprietary drivers not kernel drivers. and AMD proprietary drivers now support hybrid graphics (intel/ati).

---

### Post by jocko on 2012-04-21
> **mastablasta said:**
> what buG? AMD radeon in your maschine use proprietary drivers not kernel drivers. and AMD proprietary drivers now support hybrid graphics (intel/ati).
How do you know that suryak uses the proprietary driver? Are you sure it really support the type of hybrid graphics in his laptop?

As far as I know, amd's support for intel/ati hybrid graphics only work for some laptops.
There are two types of hybrid graphics: Muxed and muxless (don't ask me what that means, I have no idea). Muxed hybrid graphics have a bios switch where you can choose between switchable or only dedicated graphics. Amd's driver does NOT support this type. Trying to activate it with jockey will fail. Installing it manually and setting up a xorg.conf yourself will result in failsafe X. But it should work on muxless laptops. I have no idea which type suryak's laptop is.

The only option to save power on a laptop with muxed hybrid graphics is using only open source drivers and turning off the ati card with vgaswitheroo. Turns my acer timelinex 3820tg from a >35 watt hot and noisy powerdrain that empties the battery in less than two hours to a ~11 watt, cool and quiet laptop that runs for almost six hours...

---

### Post by suryak on 2012-04-21
Let me make it clear about my laptop config:

Lenovo G570
Intel 2nd Gen i5; 4GB DDR3 RAM ;
Intel build-in Graphics + ATI Radeon Dedicated graphics.

When I first brought my laptop, I used Windows 7 for sometime and switched to Ubuntu. So, when I installed it, I found a hell of difference in the laptop's temperature.

(Its was burning...!)

I searched google and found that its not just my problem. There is power regression issues in the kernel to be fixed.


This is what I know.

More over, I had to install AMD drivers explicitly. Ubuntu's software center recognized some drives but they failed to install. There was some fix for that even.. this story goes..

The bottom line is, when I used Ubuntu, Laptop's temperature was very high. 

Now, I am using Win7, it really manages it well..

As I recently found that Linux Kernel released 3.3 (stable), thought "the power regression" bug might have been fixed.

So, is it fixed or not ?????

---

### Post by jocko on 2012-04-21
Not sure about what power regression bug you are talking about. On [phoronix]("http://www.phoronix.com/scan.php?page=article&item=linux_31_power_regress&num=1") there are a few articles about a power regression in the recent linux kernels, but it [seems to have been fixed in the 3.3 kernel]("http://www.phoronix.com/scan.php?page=news_item&px=MTA0MTM").
Not sure if that's what's causing your laptop to run hot.
Did I understand you correctly that you managed to get amd's proprietary driver working?
In that case your laptop must have the type of hybrid graphics that is actually supported by the driver. Then you should be able to switch to using the intel graphics (to save power and let the laptop run cooler) through the catalyst control center.

---

### Post by suryak on 2012-04-22
> Not sure about what power regression bug you are talking about. On phoronix there are a few articles about a power regression in the recent linux kernels, but it seems to have been fixed in the 3.3 kernel.
Not sure if that's what's causing your laptop to run hot

Yeah, that's what I am talking about.


> Did I understand you correctly that you managed to get amd's proprietary driver working?
In that case your laptop must have the type of hybrid graphics that is actually supported by the driver. Then you should be able to switch to using the intel graphics (to save power and let the laptop run cooler) through the catalyst control center.

Well, to be exact: I didn't install them correctly. Ubuntu Software center showed some drivers but they failed to install. 

So, I had to install explicitly which I didn't do...

---

### Post by mastablasta on 2012-04-22
and again it doesn't have to do with the kernel but with the graphics drivers.

have you seen/read this?:
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=amd+hybrid](http://ubuntuforums.org/showthread.php?t=1930450&highlight=amd+hybrid)

---

