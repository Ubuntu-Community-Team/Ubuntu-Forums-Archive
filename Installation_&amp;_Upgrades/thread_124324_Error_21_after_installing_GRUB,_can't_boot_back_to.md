---
title: "Error 21 after installing GRUB, can't boot back to XP :-("
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by Kaustav on 2006-02-01
Hi all,
Total beginner to Ununtu. I have installed Ubuntu on an external Lacie BigBig (400Gb) which is hooked up to my desktop PC (Intel P3.4GHz, 2Gb RAM) via firewire 800. I have reached the installation phase where GRUB is installed and the system reboots. I now see the following error message:

GRUB loading stage 1.5
GRUB loading, please wait
Error 21

I've read that sometimes Ubuntu cannot recognise drives if they are not listed in the BIOS, so I checked this and indeed the only disk that's mentioned in the devices list in BIOS is the internal system drive on the PC. The main system drive has Windows XP installed on it which is why I installed Ubuntu on the external drive. 

Does anyone knows if :

a) I can fix the above problem, if so how? 
b) Can I still book in to XP or do I simply have to erase and reinstall XP?

If I did fdisk c: /mbr would this allow me to boot back to XP on the C drive? 

Also, I was considering mounting the external drive internally on the PC itself using a standard ATA cable. The primary hard disk is an SATA drive and the external disk in a standard ATA.  I've noticed the motherboard on my PC has two ATA plugs so all I'd have to do is buy the IDE cables and set the jumpers correctly on the second drive before I install it.

Kaustav

---

### Post by lha on 2006-02-01
Without any further information I can't say anything for sure, but most likely your problem is the fact that you installed Ubuntu on a drive which doesn't show up in bios. Grub error 21 means 'Selected disk does not exist' and as grub uses bios info to access drives (AFAIK), so no wonder you are having problems.

a) Putting that extra drive on an internal channel might be a good idea. Also, try to reinstall grub on the very disk you have Ubuntu on and use bios to select it as the boot device.

b) If you haven't done anything terribly wrong during installation, your XP is (almost) unharmed. Usually that fixmbr trick fixes this kind of issues.

---

### Post by Kaustav on 2006-02-01
Thanks for the infio. I have been advised to either :

1) burn a ubunto live CD and use it to defrag my HD, shrink my windows patition and then create a 50Mb partition at the end to boot Ubuntu from or

2) just put the Ubuntu install disk back in, reboot, go up to the patition phase and then get Ubuntu installer to create a 50Mb partition for me.  

Do you know if I use method 2 if I still need to defrag and shrink the windows partition? The internal C drive which houses Windows XP is a 250GB SATA drive and the whole thing is formatted to NTFS.

---

### Post by lha on 2006-02-01
There another thread [here]("http://ubuntuforums.org/showthread.php?t=124315") with good info on your problem... Have you noticed?

---

### Post by BenWilson on 2006-02-01
I am *really* new to Ubuntu, having not actually installed it yet. I'm a Gentoo fan who is looking to change because I have less time for being a geek now. :-( However, I noticed this thread and remember when I turned my laptop into a brick one business trip a few years ago.

Basically, I had it running with Grub on the MBR, and XP went into hybernation, or lost charge. I can't remember. Regardless, when it rebooted it could not do anything in Windows b/c of the hybernation problem. This was a problem because I had a reason for having *one* computer in my house run windows.
Anyway, so I had to emergency disk wipe my system, to much frustration. I could not just "repair" the problem because the restore disk did not like the MBR not being Windows.

The next time around, I found a way to get dual boot in a way that left Windows thinking it was in charge. I found it on another site, but becuase I hate having to hunt for things I mirrored on my site:

[http://dausha.net/Technical/WindowsDualBoot](http://dausha.net/Technical/WindowsDualBoot)

It's a bit more involved than the standard approach, but it works like a charm.

This may not solve your problem, unless you can get an MBR from a working windows box that you can overwrite, in the event the restore will not work for you. Mine was a total loss as the Gentoo install I was working on was not ready for use, and I needed the laptop operational in a hurry.

---

