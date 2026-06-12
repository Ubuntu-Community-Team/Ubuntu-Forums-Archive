---
title: "How can I run fsck on a device that Ubuntu doesn't recognize?"
date: 2008-11-19
forum: General Help
---

### Post by Roasted on 2008-11-19
Ubuntu doesn't recognize my flash drive. Three weeks ago it did. But today it does not... and I know the drive is fine because it works on this computer in Vista.

In another thread somebody said they believed their's was working fine after a fsck... but I don't know how to do that and on top of that I'm unsure of how I'd do it if Ubuntu can't read my flash drive for whatever reason...

The flash drive is 8gb A-DATA FAT32. sudo fdisk -l and gparted won't pick it up, along with a Hardy LiveCD, which kind of surprised me.

Any help?

---

### Post by taurus on 2008-11-19
The last time you used it in windows, did you just unplug it or did you go through safely remove hardware option first before you unplugged the drive?  Maybe you can try to run a scandisk on it from windows to see if that fixes the problem with Ubuntu.

---

### Post by Roasted on 2008-11-19
No, in XP I always just yank it since that shouldn't be a problem in XP. I also formatted it again to FAT32 in XP and Ubuntu still didn't pick it up.

I'll boot to Vista on this computer and give it a shot.

---

### Post by taurus on 2008-11-19
Yanking it out without unmount it first even in windows is not a good idea.  Always a good idea to click the little icon at the bottom right, next to clock, to safely remove it.

---

### Post by Roasted on 2008-11-19
> **taurus said:**
> Yanking it out without unmount it first even in windows is not a good idea.  Always a good idea to click the little icon at the bottom right, next to clock, to safely remove it.

Are you saying that me yanking it out in XP, despite XP's ability to handle that better than 2k Pro and all previous versions of Windows, could have damaged the flash drive to the point that XP/Vista STILL recognize it yet Ubuntu doesn't? Really?

---

### Post by easoukenka on 2008-11-20
To start out with unmount your devices.  Windows puts an icon there for you to click and makes it really easy because it can cause damage it has been known people that can get drives to work in in Linux but not in windows.  Your answer is possibly yes it could have screwed it up in linux and may screw it up in windows also.  They are different OS's and read things in a different way.  

Now beyond that lets solve your problem!      
ok plug in your USB device type dmesg you will see somewhere something like /dev/sdb1 you can do sudu fsck /dev/sdb1 now

good luck might not be a bad idea to do mkfs which will format it.

---

### Post by Roasted on 2008-11-20
I did dmesg it. I also lsusb'd it. I have another thread going trying to truobleshoot this problem.

My system literally does NOTHING when this thing gets plugged in. Nothing.

2nd page of other thread with dmesg...

[http://ubuntuforums.org/showthread.php?t=984777&page=2](http://ubuntuforums.org/showthread.php?t=984777&page=2)

---

