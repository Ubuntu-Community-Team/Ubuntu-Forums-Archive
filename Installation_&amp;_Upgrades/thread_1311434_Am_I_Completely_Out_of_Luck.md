---
title: "Am I Completely Out of Luck?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by dsyskowski on 2009-11-02
Last night I decided to upgrade to 9.10 and so I started the process off. My Ubuntu computer is on a KVM switch. Since the upgrade takes a while, I was switching between computers and checking progress.
 
I got to about eight minutes left in the install process, when a dialog asking for a decision on keeping my fstab file appeared. (I have a second hard drive in the computer with custom mount points.) Unfortunately, at some point the computer lost its recognition that it had a keyboard and mouse and there was no way of responding to the dialog. Making matters even worse, after a while it decided that I wasn't active and shut down the monitor display so now I couldn't even look at the screen. I tried several ways to get a keyboard and mouse active, but nothing worked.
It seemed like the only choice was the big red switch with a hope that some re-entry into the process would occur. No such luck. The start-up stopped waiting for a device after displaying my drives on the screen. I tried to use several of the recovery points in GRUB, but the same thing happened.
 
My question is: am I completely hosed here, or do I have a chance if I can get to the drive to look at and edit fstab? There were still eight minutes of the install left with additional work, plus the cleanup, plus the reboot and whatever else happens when the computer first starts up with the new version. Is it worth pursuing this or should I just start from scratch? Is there any way, using a live CD, to back out of a partial install?

---

### Post by Dragonbite on 2009-11-02
I would first try plugging in a mouse or keyboard directly to the machine and not via the KVM.  See if it is responsive.  My KVM doesn't allow the mouse to work on one system, but only one system for some reason.

Otherwise, it may be easier to try re-installing it, rather then poking and prodding to get it working and risk not quite noticing something.

Just my opinion.

---

### Post by dsyskowski on 2009-11-02
I did try to put a physically connected monitor and keyboard an mouse on last night, but that did not work.  I guess it will probably be the fresh install tonight.

---

### Post by Dragonbite on 2009-11-03
Are you going to go with 9.10 or another version you know works well?  Just wondering about introducing a new version with its collection of unknown issues (since it's so fresh).

---

### Post by dsyskowski on 2009-11-03
I had 9.04 running successfully, and I was upgrading to 9.10 so I will continue with 9.10.  I will give it a try to see how it works.  I am running on the new 9.10 install as I type this and so far all is OK.  Trying to get things back to the way they were right now.

---

