---
title: "[SOLVED] Installing Ubuntu 8.10 to USB thumb drive..."
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by ragtag on 2008-12-13
I'm trying to install Ubuntu 8.10 to a thumb drive on my HP TC4400 and am having problems with it. I've been running Ubuntu on my workstation for a few years, but have some srange issues on my laptop.

The reason I'm not installing it to the disk is that I would rather not mess with the Windows XP install on it. TabletPCs with WinXP don't come with the install cd. Why on earth someone at Microsoft thought that was a good idea I have no idea!

Anyways. I install from the boot screen (not using the desktop icon, as the installer there doesn't find the thumb drive). The first attempt at installing the install was running for a while and then just stopped with the desktop image and nothing else. The second time, it stopped at 82% and Configuring apt-get. The second time I also partioned the USB drive manually just in case.

I know people run Ubuntu on the TC4400, so I'm not sure what the problem is. Any ideas?

---

### Post by 1467 on 2008-12-13
have you tryed booting a usb device on this computer be for ? 

how old do you think the computer is?

---

### Post by 1467 on 2008-12-13
i had this problem for a long time on this computer i gust had th edit my BIOS a bit

---

### Post by ragtag on 2008-12-13
I got it working the third time around without really doing anything different. Just a dog standard install. Though I've no idea why it failed the first couple of times, maybe there are faulty blocks on the thumb drive. I just bought it today and haven't tested it before.

It is a bit slow though. hdparm -t gives me 18 MB/sec, while the built in drive gets 40 MB/sec (probably a 4500rpm drive). Now I just have to play around with getting the Tablet functionality working. :)

---

### Post by miniyak on 2009-12-14
hmm good info to keep in mind, i just picked up one of these for free and it has been dropped

The hard drive bay cover is cracked and the hard drive is reported as having many bad sectors so i dont expect the drive to last for too long, i was thinking usb might be the way to go. I just tried a 250 gig sata and it dosn't seem to want to boot with it. Though it installed just fine and mounts from the live cd. Is it really only compatible with certain sata drives? .. maybe i should start my own thread

---

