---
title: "not recognizing cd burner"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by merlinus on 2007-04-28
My internal cd burner drive (PlexWriter 24/10/40A) is not being recognized.  

Although devices listed in /media include cdrom and cdrom0, they both point to the same device, i.e. the contents of the disk in the dvd-rom drive are listed on both in the file manager.

When I select Properties for cdrom it says Kind: link to folder and Link target: cdrom0.  Properties for cdrom0 only says Kind: folder.

I tried adding irqpoll to the /boot/grub/menu.lst as suggested in another thread, but all that did was kill my usb wireless mouse a few moments after bootup!

I know that the drive is working because I just burned a cd under Win2000 with my dual-boot system.

Here is my fstab:

# Entry for /dev/sda7 :
UUID=74ea0d79-f0a5-4381-a98d-08258758e696 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=143857E33857C302 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=18082DAD082D8B38 /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda6 :
UUID=D444F4A544F48B8C /media/sda6 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda8 :
UUID=8d0e34ce-515e-4595-b8d3-f04930ca0baa none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Notice that cdrom is not listed, but what might I add to this file so the burner is recognized?

AFAIK, cdrom should be the burner.

Thanks for any assistance.

-merlin

---

### Post by merlinus on 2007-04-28
I added to fstab:

/dev/scd1 /media/cdrom udf,iso9660 user,noauto 0 0

and restarted the computer, but nothing changed.

Assistance greatly appreciated!!!

-merlin

---

### Post by merlinus on 2007-04-29
Please -- can someone either help or point me in a direction to get assistance.

I have searched the forums and Ubuntu sites on this topic, but found no useful info.

I have checked and my hardware, including Plextor cd burner, is compatible with Feisty.

Many thanks!

-merlin

---

### Post by kenklay on 2007-04-30
Your problem maybe related to another thread.  See
[http://ubuntuforums.org/showthread.php?t=426068](http://ubuntuforums.org/showthread.php?t=426068)

---

