---
title: "[SOLVED] Live CD not willing to co-operate"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by UltimateSephiroth on 2009-01-09
Hi everybody. I have a problem with the live CD of Kubuntu 8.10, so sit down and read, maybe you're able to help me.

I've had a Wubi installation of Kubuntu for some time now. I decided, though, that I want to install it on its own partition (instead of the Wubi disk image way). So, I downloaded the image file kubuntu-desktop-8.10-i386.iso as a torrent download. I checked the file's MD5 and it was OK. Then I burned the ISO on a CD-RW disc with InfraRecorder's image burning tool.

Once it was finished, I rebooted the computer with the newly burned CD in the CD-DVD-etc. drive. I got into the main menu, the one with the selections to either go testing, install, check the CD, check the memory or boot from HD. I tried the first one, but the CD drive just read the CD for a brief moment and then froze (CD drive's light was left lit, and it wouldn't open with the eject button).

So, I rebooted and tried to just install the OS. Same thing, it froze again. Then I tried to check the CD for defects; same fricking thing, it froze up. Angered by this, I formatted the disc and burned it with another software, but it still didn't work.

Today I took the CD with me to the school. I booted one of the school's computers on the CD and tried to start the system. This time, shortly after freezing up, a message popped up: "I/O Error: Error reading boot CD".

I'd really like to install Kubuntu, but it just doesn't want to work. What is the problem? Please help! (If you need extra information, I'll provide as much information as I can.)

E: Yeah, by 'freezing' I really mean freezing: the main menu stays on the screen, but no keyboard keys work, or if they do, the computer just beeps loudly.

---

### Post by frost151n on 2009-01-09
Try a CD-R instead of RW.

---

### Post by UltimateSephiroth on 2009-01-09
Oh... I thought it doesn't matter whether it's a CD-RW, so I burned it on a CD-RW because after installation I may not need the disc anymore. Well, then I'll go and buy a CD-R. I'll post here later today if that helped. Thanks!

---

### Post by UltimateSephiroth on 2009-01-09
Hey, it worked! That's excellent! Now I have finally installed Kubuntu! I'd have another, minor question: is there a driver for Vista that supports ext3 drives with 256 byte inode (no idea what that means, but I know that's my problem)? I tried one driver and it seemed to be OK... except that it would've needed 128 byte inode and I'd not like to install Kubuntu all over again just to change that. (I want to have access to all files on all drives on both OSes.)

---

### Post by frost151n on 2009-01-09
Kool. Keep the CD, it's always a good idea to have a Live CD around.
I don't know man. I've just got two Brown Beans.
Format you /home as FAT32. That's what i did.

---

### Post by UltimateSephiroth on 2009-01-09
Luckily I found a solution in which I didn't need to format the disk :) I installed a tool called Ext2Fsd, which lets me access the disk :P

---

