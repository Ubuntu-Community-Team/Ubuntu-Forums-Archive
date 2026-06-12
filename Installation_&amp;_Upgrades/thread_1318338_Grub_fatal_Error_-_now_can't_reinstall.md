---
title: "Grub fatal Error - now can't reinstall"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Martin_sensei on 2009-11-07
I have been flogging a very dead eee pc for a few hours now, I hope someone can help as I have no idea what is happening.

First the machine set up:
Asus eee PC 900 1GB RAM
2 solid state hard drives:
sda1 - (windows 4gb)
sda2 - small utiities partition
sdb1 - (ubuntu 6gb)
sdb2 - swap

I created an Ubuntu 9.10 USB install disk
I ran the installer, installing Ubuntu 9.10 on sdb1 and keeping the swap as is.
The install seemed to go well but failed at 97% with a fatal Grub error.
I tried to restart but got stuck in grub.
I then booted windows, and deleted all partitions on sdb

Now I can not get the installer to run any more, when I choose install ubuntu, I always end up in a live session, but with no keyboard or mouse!

I suspect the boot sector on sdb may be in a strange state?

Can anyone help me out of this mess?  

Cheers

Martin

---

### Post by Martin_sensei on 2009-11-07
Just to add to this,

I have tried booting from hdb (the second hard disk) and I get a grub recovery prompt.

Can I use this to repair/remove the boot sector from this disk?

The mbr on this disk seems to be stopping me from instlling Ubuntu.

(I had Ubutu 9.04 running perfectly on the second disk before I attempted to install 9.10 - the phrase "if it's not broken... springs to mind)

---

### Post by Martin_sensei on 2009-11-08
Hello again,

I am in a slightly different situation now.  I have created a 9.10 netbook remix usb stick which now at least lets me into a live session with keyboard and mouse.

I can also install from this USB stick.  So I did...

The istall seemed to be going well, but at round 95-98%  The machine rebooted and ended up in a live session.  When I reboot without the usb stick I get a recovery:grub> prompt.

So I think I have Ubuntu 9.10 netbook remix installed, but the mbr on the 2nd hdd (sdb) seems very broken.  Is there a way to at least boot into ubuntu from this recovery thing?

Or repair it even?

Please, anyone help, I've been trying to install Ubuntu 9.10 all weekend.

---

### Post by Qwertinsky on 2009-11-08
I have ran into the same sort of situation here

[http://ubuntuforums.org/showthread.php?t=1318992]("http://ubuntuforums.org/showthread.php?t=1318992")

I tried installing Ubuntu 9.10 on my Asus EeePC 900 netbook yesterday.

Everything was going along fine up until about 95% when the grub installation crashed.

This left my main SSDD (solid state disk drive) in a state that is can not be read or written to.

Further installation attempts the partitioner in graphical installers return an I/O error, and text based installers just say "operation failed" when trying to do anything to this drive.

Gparted scans it then seems to ignore it as sdb (second drive) and sdc (usb drive) show up as devices but not sda?

When running a Windows XP installer, it sees the drive but says "Windows can not access this device"

This all kind of leads me to believe the drive is somehow locked.

Anyone recommend something that could fix this that also can be booted from a USB device?

---

### Post by Martin_sensei on 2009-11-08
Hmm that sounds quite a lot worse than my current situation...

I am pretty sure ubuntu exists on the disk, and the disk is healthy (I have managed to format the whole disk and re-partition it in windows, and using the ubuntu installer.

I just need a way to sort out the master boor record on the second hdd (I think/hope)

I was hoping to be able to manually boot into the disk to check ubuntu is actually installed, then repair the mbr.

Any ideas how to do a boot fom the grub prompt?

---

### Post by Qwertinsky on 2009-11-08
I fixed it by low level formatting the drive using

HDD Low Level Format Tool from HDDGURU.COM

[http://hddguru.com/content/en/softwa...l-Format-Tool/](http://hddguru.com/content/en/softwa...l-Format-Tool/)

You have to be able to boot to Windows to use this. I was lucky and still could boot my Windows partition from a USB drive.

I have seen places on the net with instruction on how to install Windows XP to a flash dive in a way that makes it bootable and usable.

I am back to 9.04 and holding.

---

### Post by Martin_sensei on 2009-11-08
Thanks for the link to that format tool, that (as you would expect) destroyed the mbr!

I had another go with 9.10 Netbook remix, this time the installer completed, the boot sector was correct, it actually started to boot...

but all I get is a desktop wallpaper, and a cursor!  I left it for 10 minutes or so, but nothing else.

So unless anyone knows of a way to actually install 9.10 on a eeePC I will have to go back to 9.04 as well (and be one of those people who just can't get it to work at all).

---

### Post by horacioh on 2009-11-10
you should follow this bug report:
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387272](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387272)
 
The problem is already known but it seams no one is still on the issue... The danger of complete disk data lost using ubuntu 9.10 with asus eee 900 is very real and everyone should be warned

---

