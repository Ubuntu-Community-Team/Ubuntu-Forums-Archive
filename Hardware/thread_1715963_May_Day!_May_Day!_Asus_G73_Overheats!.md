---
title: "May Day! May Day! Asus G73 Overheats!"
date: 2011-03-27
forum: Hardware
---

### Post by giddyup306 on 2011-03-27
Yesterday out of the blue my laptop just locked up.  I was transferring some files from one USB drive to another and watching a video, when all of a sudden both screens went black, and the audio sounded like a broken record.  I then had to do a hard restart, and when it restarted, I noticed that my fans were noiser than normal.  When the computer finally booted up, my little widgit said that my CPU was 165*F (i7)!  Normally it runs in the high 120s or mid 130s.  Then today I caught it as high as 185F/85C.  From what I've read this is too hot.  I did some google searching, and LM Sensors won't work on my laptop.   What other alternatives do I have, and what steps do I need to do to start the diagnostic process?  

I've included a picture of the exact way that it was.  Under the laptop is a cooling pad (which doesn't do anything).  The only thing that might cause it to overheat is the box of books behind it, but I don't think that should cause it to overheat.  

I will NEVER buy another Asus product again!  This is an $1,800 POS.  It doesn't have anything to do with Ubuntu, either.  The first one I had wouldn't boot off the hard drive out of the box, nor would it boot off a live CD.  On the very, very rare occasion that I boot into 7, half the time it locks up before Windows even loads (Geek Squad installed the OS BTW)!  Oh, and the Asus updater doesn't work...


Also I very seriously doubt that the fans or fins are blocked.  This laptop is less than 6 months old.  I have a feeling that this thing is going to get warrantied.  I've had numerous problems with it.  Luckily, I bought the 3 year extended warranty...  Also, my CPU load was around 30%.  It usually is only about 10% or so. 

Thanks in advance...

---

### Post by Yellow Pasque on 2011-03-28
First off, make sure you're not watching video using Flash plugin. That thing is a horrible CPU hog and you should use Flash-aid extension to replace Flash with a native video player on popular sites.

Second, make sure proprietary ATI driver is installed for best GPU power consumption. The open-source driver works too, but even with power management it's not quite as efficient as fglrx/Catalyst.

Third, if you're still having issues with overheating, try turning off Turbo mode in the BIOS.

---

### Post by giddyup306 on 2011-03-28
Today it hasn't been acting up.  The CPU is hovering around 127/128, and I'm basically doing the same things I was yesterday without any change.  What gives???

> **Temüjin said:**
> First off, make sure you're not watching video using Flash plugin. That thing is a horrible CPU hog and you should use Flash-aid extension to replace Flash with a native video player on popular sites.

I have a painfully slow internet connection, so I download flash videos, and play them in VLC.


> **Temüjin said:**
> 
Second, make sure proprietary ATI driver is installed for best GPU power  consumption. The open-source driver works too, but even with power  management it's not quite as efficient as fglrx/Catalyst.


Fgirx is installed, and is the current version.

> **Temüjin said:**
> 
Third, if you're still having issues with overheating, try turning off Turbo mode in the BIOS.

I guess if I have any other problems, I'll have to do this.  I'm not overclocking or anything, so I don't know why I'd have to do this. :/

---

### Post by dummy910 on 2011-04-08
I'm having the **same issue** of late on the **Windows7** side of this hard drive I type this from on my G73, and she locks in win-doze **just surfing the internet**, and worse yet, **nothing heavy duty** like gaming or watching a dvd causes the lock. No warning signs, just a solid press-the-power-button for a few seconds to bring the machine to a power-off state.

I have been **experimenting over in W7 of late, disabling services**, especially all those bandits that are allowed to hog resources for little reason, so I would guess not having looked at any logs yet, as i just reboot back over to Ubuntu and life is good again. Go figure.

**Not a single lock up on this machine in Ubuntu 10.10** and thee most annoying issue that arises it both OS's is the jumpy touch-pad issues that are resolved by plugging in the old reliable-external mouse.

---

