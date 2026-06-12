---
title: "Unable to access BIOS - grub keeps booting"
date: 2008-06-22
forum: Hardware
---

### Post by smilingfrog on 2008-06-22
So I am having quite a bit of problem with my Toshiba Satellite M40 running feisty. The CD ROM stopped working sometime in February. It used to work. Now, it does not appear in the /dev folder. This has been a problem for others ([no cdrom in /dev]("http://ubuntuforums.org/showthread.php?t=412118")).

My problem is now trying to boot into the BIOS. This is supposed to be accessed by holding down ESC on boot, and then pressing F1 to get into the bios. Instead, grub loads up. Furthermore, the CDROM won't read bootable media, so I can't boot a recovery disk, or a bootable CD to upgrade to Hardy.

Can I make grub boot a CD?

---

### Post by devonharlan on 2008-06-22
If your cd rom drive isn't working than grub on a cd wouldn't do you any good.
I think there is a way to get grub on a usb key. Unfortunately the only way to boot from it requires you to access bios.

---

### Post by upchucky on 2008-06-22
google for Supergrub, it can boot u cdrom if u have the drive specs to set it up with.

otherwise keep trying to press the esc key multiple times on boot up, it should work.

You may be able to just take out the hard drive then boot the pc, it may be enough to let you into the bios cause the drive is not there and grub cant load.

Disconnecting the keyboard then booting will also get you into the bios.

when you try this watch the screen very carefully, it should briefly flash the key to press to access the bios. you may have to boot it several times to see the flash on the screen, i have seen them flash by very fast. 

Barring that you can force the bios to boot by unplugging the power, taking out the battery,  then taking out the cmos battery, then putting the cmos battery back in and the main battery back in, then powering up the laptop. this erases the time date, and the bios then auto loads on boot so u can reset it.

Removing the cmos battery is the last resort! do not do this if u are unsure how or faint of heart.
if u are daring enough to go the latter route, make sure u have the hard drive specs so you can set that up in case it does not do it automatically.

most bios nowadays are fully automatic but you should always be prepared.

---

