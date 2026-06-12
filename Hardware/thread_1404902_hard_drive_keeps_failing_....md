---
title: "hard drive keeps failing ..."
date: 2010-02-12
forum: Hardware
---

### Post by cscott5288 on 2010-02-12
So last year I bought a dv5-1000 hp laptop computer with an amd athlon x2 64 dual core processor, 256mb radeon video card and 2GB of ram. The laptop had Vista on it (unfortunately) and I hated it very much because everything was incredibly slow compared to XP. Then it failed one day and I had to re-install the OS using the recovery partition. Then it failed again so I decided to install Windows 7 (the trial version) on it (the hard drive wasn't destroyed). That was great for a few months but then the hard drive completely failed so I borrowed a friends hard drive and put ubuntu on it. That didn't fail but started to get bad sectors so I decided to buy a brand new 320GB 7400 RPM SATA hard drive. I installed ubuntu on that and everything was going fine until it started randomly shutting off. I decided that it must have been because of the heat and (after propping the computer up to keep it cooler) I no longer had it randomly shutting off on me. The battery had already failed so it wasn't mobile anyway but then I had another problem arise today. I turned it on and there was a disk error. I ran the diskcheck in GRUB and was able to repair whatever was preventing a start-up. Then I went into my palimpsest disk utility and looked at my hard drive and, low and behold, there are 24 bad sectors (3 sectors pending sector count and 21 remapped sectors. )... I also have the reading for Airflow temperature saying: failed in the past.

I just don't know what to do now because I am so frustrated and tired of spending money on this PC. I bought a new laptop battery and guess what? the guy I bought it from on ebay decided he wasn't going to ship it to me for whatever reason (and he has over 95% positive feedback for over 2000 sales). I am still working that out but I want to really make sure that my hard drive is not going to fail on me again ... It's a brand new hard drive with a 5 year warranty (you bet I made sure it had a warranty) but I really don't want to go through the trouble of AGAIN purchasing and installing a new hard drive and transferring the data... I am a student so having a working computer is vital to me. Unfortunately I have absolutely no support from HP whatsoever because the HD and battery failed one month after my warrant expired with them (talk to the hand). 

Just looking for some advice. Do I have to return the hard drive again? What is causing my bad sectors? Could it be the overheating which I thought I recently corrected ... thanks. pretty mad right now and amazed that I got through this whole post without using expletives.

---

### Post by cscott5288 on 2010-02-12
Anyone have any advice for me? I would really appreciate it and I know there are a lot of computer wizs' on this forum.

---

### Post by mhgsys on 2010-02-12
Well, The only experience I have with failing harddisks is that they will fail eventually.

Bad sectors are the beginning of the end. 

Sure you can work around them for a while (chkdsk,fsck etc) but eventually it will crash.

I recommend to return the hd, since you have 5 year warranty.

When you have enough money; buy a solid state drive

Wish I could tell you I knew a way to prevent disks from crashing, I have some bad hd's laying around here myself.

---

### Post by cscott5288 on 2010-02-12
> **mhgsys said:**
> Well, The only experience I have with failing harddisks is that they will fail eventually.

Bad sectors are the beginning of the end. 

Sure you can work around them for a while (chkdsk,fsck etc) but eventually it will crash.

I recommend to return the hd, since you have 5 year warranty.

When you have enough money; buy a solid state drive

Wish I could tell you I knew a way to prevent disks from crashing, I have some bad hd's laying around here myself.
My concern is that the my particular PC is causing them to crash. Is that possible?

---

### Post by mhgsys on 2010-02-12
Well, I can't state that it's not possible, but it seems pretty strange.

The only reason I can think of if when it's specifically that pc that "eats" drives is a bad power supply.

Drives will crash eventually when they are turned on and off quickly.

But I think you would have noticed that, since the system would be hanging then.

---

### Post by dabl on 2010-02-12
I concur with mhgsys.  I can only think of two ways your computer could damage your hard drive:

- if it runs hot all the time, and the hd isn't getting any ventilation

- if the power supply is shaky and the 12V power to the hd was not meeting spec

If the hd is not running excessively hot, and if the power is within tolerance, then whatever is going wrong with it is a defect in the hd itself.

All modern hard drives come with SMART self-diagnostics, which you can access with smartmontools.  Here's a how-to:

[http://kubuntuforums.net/forums/index.php?topic=3097029.0](http://kubuntuforums.net/forums/index.php?topic=3097029.0)

---

### Post by cscott5288 on 2010-02-12
> **dabl said:**
> I concur with mhgsys.  I can only think of two ways your computer could damage your hard drive:

- if it runs hot all the time, and the hd isn't getting any ventilation

- if the power supply is shaky and the 12V power to the hd was not meeting spec

If the hd is not running excessively hot, and if the power is within tolerance, then whatever is going wrong with it is a defect in the hd itself.

All modern hard drives come with SMART self-diagnostics, which you can access with smartmontools.  Here's a how-to:

[http://kubuntuforums.net/forums/index.php?topic=3097029.0](http://kubuntuforums.net/forums/index.php?topic=3097029.0)
Well, I will tell you what does happen.

- When I try to power on the computer, I have to hold down the power button for a few seconds (unlike when I first bought it), and it will only turn on if I hold it down for a few seconds.

- I took the battery out completely and am just using AC power because my battery failed and would not hold a charge. Like i said before, sometimes it randomly shuts off.

It seems to me like the above problems can be indicative that my computer has an overheating problem or a power supply problem .... what do you guys think?

---

### Post by mhgsys on 2010-02-12
> **cscott5288 said:**
> 

It seems to me like the above problems can be indicative that my computer has an overheating problem or a power supply problem .... what do you guys think?


It seems to me like the above problems can be indicative that your computer has an overheating problem or a power supply problem ....

You can monitor temperatures on ubuntu with the computertemp applet. 
```
sudo apt-get install computertemp
``` right click a panel>add to panel> computer temperature monitor. 

(if you don't get any output on the sensor, install libsensors4 & lm-sensors as well)
after that run
```


sudo sensors-detect

``` 
reboot and try again.


although it seems to late for that , it will perhaps be handy in the future.


(The "random" shutting down problem most likely is a overheating problem btw)

---

