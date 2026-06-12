---
title: "Hard drive not detected on warm boot"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by Peepsalot on 2006-06-04
I wrote this in a post in an [old thread](http://ubuntuforums.org/showthread.php?t=165028&page=2), but since that forum is now closed and I haven't figured this out yet, I'm making it a new thread.
> 
For some reason Linux cannot detect my drive from a warm boot. If I turn the computer off for 10 secs and then start up, it works fine every time. Windows on the other hand will load from the same hard drive no matter how it is booted.

So I can boot ubuntu off my hard drive from a cold boot, but on a warm boot this happens:
at the Ubuntu loading screen,
Mounting root file system...
Waiting for root file system...
(the computer sits here for a couple minutes, then)
ALERT! /dev/sda2 does not exist. Dropping to a shell!

I don't know what the shell is running off of. I tried to fdisk from there but I guess the fdisk executable is not there. When I boot my LiveCD from a warm boot and try sudo fdisk -l, there is absolutely no output. I just get another command prompt on the next line, as if I had pressed enter with no command at all.

It is such a strange problem. Does anyone have an idea why this would happen?

The only thing I can think of that might be causing this behavior is that I used a Windows program called ATItool to enable SMART settings on the hard drive for reduced noise("acoustic management" they call it). I try to turn it off, but running ATItool now causes my system to spontaneously reboot now. I think I'll try reinstalling it and trying to turn off this acoustic management option if I can. Does anyone know if this is some issue with Linux being incompatible with these settings?


Some hardware info:
Asus Pundit P2-AE2 ([specs](http://www.newegg.com/Product/Product.asp?Item=N82E16856110040))
AMD Sempron 3000
Western Digital WD3200KS 320 GB SATA hard drive

I saw read a post about these computers being unstable with "Cool and Quiet" enabled in BIOS, so I disabled that, but my problem persists.

---

### Post by Peepsalot on 2006-06-21
Any help?  Ubuntu Dapper on this hardware is the most unstable system I've ever used :(

---

### Post by Joenewbie on 2006-06-21
This is all I can tell you. For some reason the Pundit's VIA SATA controller will not recognize the SATA on a re-start or warm boot (with ubuntu installed) and will instead pull up 4 ide drives (all of which obviously are not there!!!) causing the software to hang at the log on screen because it can't mount the sata drive, nor the missing ide drives. Then it will go to terminal mode something or other.
But...if you will shut down completely after upgrades and installs. Then re-boot i.e. completely cold start.....then it works great. 
I bought my Pundit P2-AE2 to use as a server. I have grown to dislike XP prof and wanted a change. The ASUS Pundit works great with ubuntu and I am learning more daily. Huge learning curve, but lot's o' fun.

P2-AE2
WD SATA 250gig
1gig mem
Sempron
(mostly old left over parts) 

Good luck with yours.

---

### Post by Peepsalot on 2006-06-21
Cool, there is actually someone else on the same hardware.   Good to know I'm not the only one.  Yeah this SATA thing is pretty annoying.  I wonder what Windows knows that linux doesn't.  It's not just Ubuntu, it seems that even any Linux LiveCD will not detect the drive on restart.  But my windows partition still boots fine.

By the way, how is your onboard video treating you?  My computer was constantly crashing until I completely disabled screensavers.  I use xfce for my desktop, and the display is hardly responsive at times.  I wish it just had a little more acceleration(is there any?)

---

### Post by sternael on 2006-06-23
As far as I know, a number of controllers have some kind of warm boot problem in Linux. I used to have a IT8212 (the feared one!) and it never rebooted even from Ubuntu to Windows (Windows to Windows was OK). It just blank screened in the POST if the last OS was Ubuntu.

---

### Post by Joenewbie on 2006-06-25
[QUOTE=Peepsalot]Cool, there is actually someone else on the same hardware.   Good to know I'm not the only one.  Yeah this SATA thing is pretty annoying.  I wonder what Windows knows that linux doesn't.  It's not just Ubuntu, it seems that even any Linux LiveCD will not detect the drive on restart.  But my windows partition still boots fine.

By the way, how is your onboard video treating you?  My computer was constantly crashing until I completely disabled screensavers.  I use xfce for my desktop, and the display is hardly responsive at times.  I wish it just had a little more acceleration(is there any?)[/QUOTE]

The max video refresh rate is slower than I like. It's 65mh where I am used to 85 (less eyestrain /headache) but no I have not tweaked the video and it has never crashed on me. I am meerly surfing, reading mail and learning ubuntu. DId not build for gaming or high res stuff. Took XP off completely, reformated and installed ubuntu which has proven very stable for this machine.

---

### Post by mkp on 2006-07-29
The 160GB Hitachi SATA drive in my P2-AE2 has the same exact warm start symptoms as everyone else.  Other hardware: Sempron 2800+ and 1GB of memory.  It's a good little web browser/email/general purpose box, rock solid other than this stupid warm start problem.

---

