---
title: "CPU speed low but temp low as well"
date: 2012-02-16
forum: Hardware
---

### Post by JumpStarter on 2012-02-16
Hi All,

I'm running Oneiric on a Sony Vaio VPCSA with an i5-2520M CPU and hybrid graphics which is set to use the on-board Intel chip (and SSD, in case that's relevant). After a fresh boot, everything is fine for a while, but then CPU speed goes down to 800 MHz (the lowest non-idle setting) with the consequence that CPU load goes up and everything slows to a crawl. I've installed lm-sensors, and in this state (or before), I never see temperatures > 78`C (although on the outside, the laptop does become quite warm).

What I find peculiar is that at no time does the fan go up. When I reboot into Windows (dual-boot), I immediately hear the fan go up. I've tried installing the Jupiter applet, but the only effect is that when I use the 'Maximum Performance' mode, the speed only drops to 1000 MHz instead of 800 after a while. I've also tried the other settings, with no change to speed or temperature.

My kernel is 3.0.0.16. 

This is the output from sensors when Jupiter is set to performance, and CPU is at 1000 MHz:
[FONT=Verdana][FONT=Courier New]acpitz-virtual-0
Adapter: Virtual device
temp1:        +77.0°C  (crit = +97.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +78.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +68.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +69.0°C  (high = +86.0°C, crit = +100.0°C)

[FONT=Verdana]Thanks for any help.[/FONT]
[/FONT]
[/FONT]

---

### Post by ahallubuntu on 2012-02-16
69C does not seem "low" to me for a laptop CPU - in fact that seems rather warm.  What is the temperature showing as in Windows?

It sounds like the CPU fan isn't coming on at all in Ubuntu.  Sometimes CPUs will automatically throttle (slow down) once they reach a certain temperature, to avoid getting too hot, and that can make everything crawl...

Have you poked around BIOS Setup for options related to fan control?

Have you updated the BIOS to latest available from Sony?  (You may need to do this update in Windows.)  Even though Windows may be fine with the fan and current BIOS, a BIOS update (if Sony has one) could help Ubuntu figure things out.

---

### Post by JumpStarter on 2012-02-16
Thanks for your suggestions. I checked how my system behaves in Windows. Even under full load, the core temp hardly ever exceeds 70`C, and the CPU clock adjusts fine to various levels of load.

In my BIOS, there are no options to do with power saving or clocking. I could not find any updates, but I presume it's pretty up-to-date since the computer is 2 months old and there's a Sony-proprietary update tool running under Windows.

In Ubuntu, I can hear the fan run and I know that a while ago, it would also go higher under load. I just don't know which changes might have affected this... I do assume what you were saying as well, that the CPU throttles to keep temperature down instead of ramping the fan up.

When I look at the output of cat /proc/cpuinfo (attachedt), there is no entry under power management. Is that normal?:

---

### Post by ahallubuntu on 2012-02-16
Not quite what I meant.  The CPU will idle to lower frequencies to keep it cooler and use less power, but when needed it runs at full speed.  The computer will increase fan speed to keep it cooler first before slowing the CPU.  But if the fan is at full speed and the CPU is getting too hot, then it CAN throttle the CPU to prevent overheating.

You seemed to say in the first post that the fan wasn't coming on at all in Ubuntu, which is why I suggested possible throttling.  But now you say it comes on just not as fast as in Windows.

Honestly, it seems Ubuntu's (or the kernel's) support for Sandy Bridge isn't quite there yet, based on lots of problem reports here on these newer laptop designs.  Let's hope in 12.04 LTS things are better.

70C (if that's an accurate reading) is alarmingly hot to me on a 3 month old laptop.  If that's normal for that thing, I would never want to own it.  Terrible design.  My Dell laptop CPU hits a tad over 50C when under load and I wouldn't want it getting much hotter than that - it's warm enough as it is.

---

### Post by 0011235813 on 2012-02-16
Sony and Linux... Well, let's just say it's not the best combination. Sony does not like Linux, and Linux distro's have always had trouble with Sony laptops.

I had an expensive Sony VAIO a couple of years ago, and I miss it. It's a real pity, because it was such a good laptop, but dear old Sony had misconfigured the motherboard with the AMD processor running on board, and it got hot. Very hot. So flippin' hot in fact, that the CPU itself got fried. Bye Bye.
(EDIT: I just remembered that Sony's first product was a rice cooker that failed because it always burned the rice! How appropriate!)

These Sony laptops are infamous for overheating, if I were you, I'd try to return it and get a System76 or ZaReason one instead.

PS: My old Compaq PC gets overheated when I do intensive activity as well, and while these CPU monitors help, it's always a good idea to let computers cool down, you'd be amazed at how much performance an overheated computer loses :(

---

### Post by JumpStarter on 2012-02-16
From my experience so far which is only a couple of months, I fully concur. I've had nothing but trouble trying to get Ubuntu running, starting with the installation on what turned out to be a fake-RAID made of 4 (!) SSDs, not being able to use my ATI graphics card, lack of or limited support for the touch pad and brightness sensor., and now this problem.

I can't return my laptop (customized...), so for me the alternative will be to end my flirt with Linux.

---

### Post by ahallubuntu on 2012-02-16
Some laptops do play well with Linux.  I've had great luck with Dell laptops.  I've had Ubuntu 10.04 LTS on my Dell Inspiron ("tri-boot" with XP and Windows 7) for over a year and use Ubuntu almost all the time these days.  I don't have any issues with overheating or slow performance.

So I think choosing hardware that works well with Linux is important.  It's a pity some manufacturers ignore it or do not support it.  I vote with my dollars for those who do.

As an alternative to dual boot, you could at least install Ubuntu as a virtual machine in Windows inside Virtualbox.  Then at least you could surf safely without worrying about hitting an infected site, etc.  While you lose some performance in a virtual machine vs. just running natively, it could be faster than what you are putting up with now.

---

### Post by 0011235813 on 2012-02-16
> **JumpStarter said:**
> From my experience so far which is only a couple of months, I fully concur. I've had nothing but trouble trying to get Ubuntu running, starting with the installation on what turned out to be a fake-RAID made of 4 (!) SSDs, not being able to use my ATI graphics card, lack of or limited support for the touch pad and brightness sensor., and now this problem.

I can't return my laptop (customized...), so for me the alternative will be to end my flirt with Linux.

I wouldn't leave Linux. I've used Ubuntu for about a couple of months, and now I positively can't stand Windows! It feels totally inferior. 

But I can think of a solution to your problem; a water cooler. Sure, they're not very cheap(see this: [http://www.technooutlet.com/dhcwch60.html?mr:trackingCode=A151524C-0CA5-E011-AC9E-001B2163195C&mr:referralID=NA](http://www.technooutlet.com/dhcwch60.html?mr:trackingCode=A151524C-0CA5-E011-AC9E-001B2163195C&mr:referralID=NA)) , and you might need help from a qualified technician to stick it in your PC, but darn it will keep your processor running so much cooler. 

@the other poster:
Nice idea, although security is more than just infected sites, and add-ons for Firefox and Chrome like WOT will warn you when trying to access them (or if you don't have that add-on in your browser [or you don't want to bloat it] you could always enable Google DNS {**D**omain **N**ame **S**ervice} which I found blocks them [{I can't even load them}]).

---

### Post by ahallubuntu on 2012-02-16
I personally can't imagine a water cooler is practical for a laptop - or a cooling pad for that manner. 

This laptop's CPU, an i5-2520M, is a fairly low power CPU (35 watt TDP) so should not get that hot.   Unfortunately, some laptops still have crappy designs that generate way too much heat or don't cool a CPU very well.  I simply try to avoid them.  I've never needed a cooling pad for any laptop I've ever owned - but I try to check how hot it will get before buying one.

My guess is that it really does not hit 70C even in Windows and that that is just a bogus reading.  The reason it's slow in Ubuntu may have nothing at all to do with heat - it may simply be due to poor support for Sandy Bridge in the 3.0 kernel so far (or at least in the kernel used in Ubuntu 11.10).

---

### Post by JumpStarter on 2012-02-17
It's not as simple. Yesterday I was running it for hours, even unloading and loading the battery, on the 'Performance on demand' setting of Jupiter, and it was fine scaling up the CPU clock. Then at one point, while I was using the same applications as before, the problem described above occurred again and stayed like that until I shut the computer down. It may be a mixture of several issues. Until I find out what causes it, my strategy will be to limit heat generation to avoid it occurring.

---

### Post by 0011235813 on 2012-02-17
> **JumpStarter said:**
> It's not as simple. Yesterday I was running it for hours, even unloading and loading the battery, on the 'Performance on demand' setting of Jupiter, and it was fine scaling up the CPU clock. Then at one point, while I was using the same applications as before, the problem described above occurred again and stayed like that until I shut the computer down. It may be a mixture of several issues. **Until I find out what causes it, my strategy will be to limit heat generation to avoid it occurring.**
So I'm guessing you're going to buy some sort of cooler then?

---

### Post by JumpStarter on 2012-02-17
No. This is a 13", 17mm thick chassis, I don't think there's a lot of space for extra stuff. I will just try to close all applications that are not necessary and switch to energy saving profile before the temp gets too high. And hope that in 12.04, things may improve...

---

### Post by 0011235813 on 2012-02-18
> **JumpStarter said:**
> No. This is a 13", 17mm thick chassis, I don't think there's a lot of space for extra stuff. I will just try to close all applications that are not necessary and switch to energy saving profile before the temp gets too high. And hope that in 12.04, things may improve...

Pity. Well, at least keep some liquid Nitrogen handy will ya?
But wait... 13" you say? 17mm chassis? That sounds like a small laptop. Almost netbook even. Are you sure you should have crammed so many specs in a laptop that size? Maybe that's why it's overheating...

---

### Post by JumpStarter on 2012-02-18
Positive. Plus a DVD burner and a 1600x900 display, That's why I wanted this little piece of metal, fine stats in a really handy form. And yeah, I guess they were pushing it with the thermal design, that's also what I read in some reviews.

---

### Post by JumpStarter on 2012-02-20
Problem solved: 
I thought I had switched off the dedicated graphics card of my hybrid setup. What I had done, following this enty: [http://ubuntuforums.org/archive/index.php/t-1752202.html](http://ubuntuforums.org/archive/index.php/t-1752202.html), was to use vgaswitcheroo to switch the inactive card off, and blacklist the radeon driver in /etc/modprobe.d/blacklist.conf. That did not work. I think the reason was that when radeon is blacklisted, there was no vgaswitcheroo, and so no powering off. NOT blacklisting radeon solved the problem.

Now the laptop uses 16W instead of 32W, the temperature is down to 57'C idle, and I'm happy!

---

