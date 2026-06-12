---
title: "USB drive prevent system from booting"
date: 2011-02-09
forum: Hardware
---

### Post by paolo.quaglino on 2011-02-09
Hi, I recently bought a WD "My Passport Essential SE" external drive..
It's a USB 2.0 self-powered 1TB 5400rpm external HD..

It's a nightmare..
When I plug it in (before powering on), the system boots regularly, I can use my disk,  shutdown and power on again 2-3 times without problems.
Then my pc HANGS during booting (after grub, before gnome), and there's no way to resume if not HARD power off (Ctrl-Alt-Del usually prints out a lot of things - segmentation fault etc etc - but does not work)
From then I cannot boot, since I disconnect the drive.
Then I got strange errors again for a couple of attemtps (drive disconnected), and at a certain point my pc boots regularly again..
If I plug it in while ubuntu is running everything looks ok, I can mount partitions and do everything, but I experienced strange freezes sometimes (mouse also, need to power off).

Some info that could help:
- the disk has 2 primary partitions, NTFS first then EXT4
- I tried both automount and manual, with or without sync, in fstab
- I tried removing entries from fstab for this disk
- I tried different usb ports
- when the boot fails I see strange error messages (segmentation fault, and a lot of hex codes)
- when the boot fails I see fsck errors.. it seems that root and /home filesystem (which are in different ext3 partitions) cannot be mounted - I did fsck later and everything is ok
- never had similar issues (I can't remember a freeze or a boot problem) - my system started as a 8.04 or 8.10, now is a 10.4..
- I've had for years a IDE disk in a usb box working flawlessly
- never had issues with usb pendrive or other devices
- I use this disk for backup purposes also, so I'd like to have it always connected - i've got scripts that mount and unmount and do backup during startups, etc...
- no issues with windows xp and seven (same pc)

So, I think I can say the disk is not broken, and it's not a mount/partition issue.. 
I've been running linux-ubuntu for a few years, but i'm definitely not an expert, any ideas? if there is a way to gather more information/logs please tell me what to type!

Thanks a lot..
Of course I'd prefer not to reinstall everything or change this drive.. also because I'm not sure it would solve!

---

### Post by slooksterpsv on 2011-02-09
> **paolo.quaglino said:**
> ...

When I plug it in (before powering on), the system boots regularly, I can use my disk,  shutdown and power on again 2-3 times without problems.


Ok

> 
Then my pc HANGS during booting (after grub, before gnome), and there's no way to resume if not HARD power off (Ctrl-Alt-Del usually prints out a lot of things - segmentation fault etc etc - but does not work)


If you go to grub (where you can select Linux <kernel version>, Linux <kernel version> (recovery mode). Highlight Linux <kernel version> and press e. Remove quiet and splash. (Go down to the line that contains it, go to the end of that line using the right-arrow key) then press Ctrl+X to boot. - This will help to see where it's failing at by not showing the splash screen and not holding back the errors. It could be fsck found errors and is fixing them, it could be something else.

> 
From then I cannot boot, since I disconnect the drive.
Then I got strange errors again for a couple of attemtps (drive disconnected), and at a certain point my pc boots regularly again..


No offense, but it sounds like it could be either a hard drive issue or OS. Almost sounds like the hard drive is going bad.

> 
If I plug it in while ubuntu is running everything looks ok, I can mount partitions and do everything, but I experienced strange freezes sometimes (mouse also, need to power off).


This suggests either memory or hard drive or OS issues.

> 
Some info that could help:
- the disk has 2 primary partitions, NTFS first then EXT4 **ok**
- I tried both automount and manual, with or without sync, in fstab [b]ok[/b[
- I tried removing entries from fstab for this disk **careful, want to make sure it's nothing the OS depends on**
- I tried different usb ports **good**
- when the boot fails I see strange error messages (segmentation fault, and a lot of hex codes) **if we could get more information where this is happening, sometimes dmesg will hold the information**
- when the boot fails I see fsck errors.. it seems that root and /home filesystem (which are in different ext3 partitions) cannot be mounted - I did fsck later and everything is ok **points towards a harddrive or OS issue. Hard drive seems more probably (could be bad cable, bad drive, etc.).**
- never had similar issues (I can't remember a freeze or a boot problem) - my system started as a 8.04 or 8.10, now is a 10.4.. **reformat would be best to see if it happens from a fresh clean state**
- I've had for years a IDE disk in a usb box working flawlessly **could be giving up now, disks go bad, my 160GB is dying :(**
- never had issues with usb pendrive or other devices **ok**
- I use this disk for backup purposes also, so I'd like to have it always connected - i've got scripts that mount and unmount and do backup during startups, etc... **I'd make sure to have another backup of your data just in case**
- no issues with windows xp and seven (same pc) **sounds more like OS needs a reformat for Ubuntu - inplace upgrades never work as well as they should - not for Mac not for Windows and not for Linux.**

I posted bold statements next to each.

> 
So, I think I can say the disk is not broken, and it's not a mount/partition issue.. 
I've been running linux-ubuntu for a few years, but i'm definitely not an expert, any ideas? if there is a way to gather more information/logs please tell me what to type!

Usually in /var/log you can look through dmesg logs. I'm on a Cr-48 using Chrome OS, so I'll try to find you more info.
> 
Thanks a lot..
Of course I'd prefer not to reinstall everything or change this drive.. also because I'm not sure it would solve!
A reinstall may be in order, unfortunately.

---

### Post by P4man on 2011-02-09
> **paolo.quaglino said:**
> Hi, I recently bought a WD "My Passport Essential SE" external drive..
**It's a USB 2.0 self-powered 1TB 5400rpm external HD**..

There is almost certainly your problem.
Many (most) USB ports do not provide enough power to reliably operate a harddrive. You will need to use a powered USB HUB, or use a power supply for that drive.

---

### Post by paolo.quaglino on 2011-02-09
Thank you for all your hints!
Let's see:

> **slooksterpsv said:**
> If you go to grub (where you can select Linux <kernel version>, Linux <kernel version> (recovery mode). Highlight Linux <kernel version> and press e. Remove quiet and splash. (Go down to the line that contains it, go to the end of that line using the right-arrow key) then press Ctrl+X to boot. - This will help to see where it's failing at by not showing the splash screen and not holding back the errors. It could be fsck found errors and is fixing them, it could be something else.

I installed startup-manager disabling "splash screen" and enabling "text during boot".. guess it's the same, right?

> 
No offense, but it sounds like it could be either a hard drive issue or OS. Almost sounds like the hard drive is going bad.Could be.. I'll try it more under windows (on same machine, but seldom used)

> Usually in /var/log you can look through dmesg logs. I'll search for something there.. never did it, it's time for me to learn something.. :)

> 
- I've had for years a IDE disk in a usb box working flawlessly **could be giving up now, disks go bad, my 160GB is dying**the hdd is brand new, it substituted the old boxed one.. just to say that I already had a working external usb drive..
If the new one is damaged, should show issues on other OSs and other machines.. I'll try it more before reinstalling.. 

Anyway, this ubuntu installation lasted more than any windoz ever had.. ;)
Thanks again!

---

### Post by paolo.quaglino on 2011-03-01
solved with a fresh install..

---

