---
title: "A big fat mess"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by comforteagle on 2006-01-30
I have a big fat mess on my hands.

I installed win xp on the first part of my hd.  Then Ubuntu.  

I could no longer boot into windows, but could ubuntu fine.  Naturally, I needed xp, otherwise a dual boot would have been out the window.

XP would begin to boot then cease complaining about an unmountable volume.  

I thought it may have been a grub issue so I booted the rescue cd, reinstalled grub, tried to reboot into windows. Same problem.  Tried rebooting into ubuntu.  That still worked fine.

Now, here's where my day goes bad: I booted into the xp cd, chose to 'setup' xp. It only saw 130 of 160G of diskspace so I figured it wanted to only format the first partition.  I hit OK... then as it began reformatting I came to my senses realizing XP isn't that smart.... reaching for the power button.. "shit, shit, shit!".  It only made it to a 20% of the reformatting, but I can't boot anything (which I realized was likely).

I'm thinking I may be lucky enough to recover those files, but have no idea how.

Can anyone help a poor, stupid soul????? I have a livecd here ready to go if that will help somehow.

---

### Post by az on 2006-01-30
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Good luck.


You can boot a live cd, compile foremost and use your ubuntu partition to store the files you can recover from it.

install build-essential
wget [http://foremost.sourceforge.net/pkg/foremost-1.1.tar.gz](http://foremost.sourceforge.net/pkg/foremost-1.1.tar.gz)
tar xvzf foremost*
cd foremost*
make
mkdir /mnt
sudo mount /dev/hda3 /mnt
make a storage directory somewhere.
sudo dd if=/dev/hda1|sudo ./foremost -o /mnt/home/me/storage/

(never did this and am not in front of my computer right now, but I guess it would work.  I probably made a typo or two, though....)

Yeeesh!

---

### Post by comforteagle on 2006-01-30
The partition is gone  Rats! 

So I've reinstalled... Win xp first then Ubuntu.  Now I get the dreaded missing hal.dll error msg when trying to boot into windows.  The forum topic on this appear to insist that windows should be installed first to avoid this, but alas, that's what I did.

---

### Post by DJeX on 2006-01-30
Hello comforteagle, I had the exact same problem you had, but it seems I'm too late in replying to help you.

It took me 3 days to fix mine. I had to change my XP hard drive partition back to 07 (NTFS file system) and make a new MBR. Then XP booted fine. But then I had to end up useing a data recovery program to salvage my files off my other hard drives that got lost in the process.

If this ever happends again I recommend using Winternals ERD Commander 2005. You burn it to CD and boot with it. Its almost like an XP operating system but its made for recovery and repair of messed up hard drives and unbootable Windows OSs.

I'm still trying to figure out how to dule boot Uduntu with XP but so far I've had no luck.

---

### Post by ddtmsa on 2006-01-30
[QUOTE=DJeX]
I'm still trying to figure out how to dule boot Uduntu with XP but so far I've had no luck.[/QUOTE]

I started off with an XP system and, as a complete newbie, followed step by step the instructions for installing Ubuntu + NTFS from 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It turned out to be the work of less than an hour and has produced no regrets.

---

### Post by comforteagle on 2006-01-31
[QUOTE=ddtmsa]I started off with an XP system and, as a complete newbie, followed step by step the instructions for installing Ubuntu + NTFS from 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It turned out to be the work of less than an hour and has produced no regrets.[/QUOTE]

I've read that & really don't see any difference between what he did & I except for the fat32 partition for writing files between win & linux.

I just reinstalled everything trying hoary instead & cannot boot windows again. The computer just reboots itself this time when trying to load windows.  I'm at a loss for a logical explanation.

---

### Post by Elvish Legion on 2006-01-31
Can I ask why you NEED windows?

---

### Post by DJeX on 2006-01-31
[QUOTE=Elvish Legion]Can I ask why you NEED windows?[/QUOTE]

Because almost every program and hardware is made for Windows.

---

### Post by aysiu on 2006-01-31
[QUOTE=DJeX]Because almost every program and hardware is made for Windows.[/QUOTE] Like K3B and PowerPC. No, it really depends on what you use.

If you have certain needs, it really doesn't matter if almost every program and hardware is made for Windows. Look at Mac users, for example. My wife just needs iTunes, Mail, Adobe Creative Suite, and Firefox. Sure, she's sad that more computer games aren't ported to Mac, but she hates Windows, and that's just what you deal with.

Same thing with Linux.

To Elvish Legion, believe it or not, there are programs that run only in Windows that even Wine and Crossover Office and Cedega can't handle.

---

