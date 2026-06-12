---
title: "bios/grub help"
date: 2008-10-29
forum: General Help
---

### Post by ibootindos on 2008-10-29
So I run ubuntu on my main laptop, on my alternate laptop I ran windows vista, but I got a bios error that froze up the computer. I formated the hard drive using the ubuntu partition tool and took off windows and install ubuntu. Then I reformatted the hard drive using a dos application, trying to prepare the computer to re-install windows (its for a friend of mine, I've quit windows, lol) but I can't get the grub loader off, and I think I might still have the bios error. So, um, in so many words.. help

---

### Post by Ocxic on 2008-10-29
grub will be automatically removed when you install windows. 
If you really want to remove grub manually "sudo dd if=/dev/zero of=/dev/your_hdd  bs=512 count=1" is the command to use

---

### Post by bodhi.zazen on 2008-10-29
> **ibootindos said:**
> So I run ubuntu on my main laptop, on my alternate laptop I ran windows vista, but I got a bios error that froze up the computer. I formated the hard drive using the ubuntu partition tool and took off windows and install ubuntu. Then I reformatted the hard drive using a dos application, trying to prepare the computer to re-install windows (its for a friend of mine, I've quit windows, lol) but I can't get the grub loader off, and I think I might still have the bios error. So, um, in so many words.. help

Install 8.10 and tell your friend it is Vista SP1

---

### Post by markharding557 on 2008-10-29
If reinstalling windows vista(uuuurrrgh)does it not foramt from the install disc?

---

### Post by caljohnsmith on 2008-10-29
> **Ocxic said:**
> grub will be automatically removed when you install windows. 
If you really want to remove grub manually "[COLOR="Red"]sudo dd if=/dev/zero of=/dev/your_hdd bs=512 count=1[/COLOR]" is the command to use
[CENTER][COLOR="Red"][SIZE="5"]**WARNING**[/SIZE][/COLOR][/CENTER]
Please do not use that command above in the quote, because not only will it wipe Grub, but it will also zero your HDD partition table; you'll be left with a HDD that will look like it is unformatted. If that is what you want, that's fine, I'm just warning you. The partition table is from bytes 447-510 in the MBR (Master Boot Record), so if you want to just zero the boot loader portion, you could do:
```
sudo dd if=/dev/zero of=/dev/<your HDD> bs=440 count=1
```
Note that Windows OSes use bytes 441-444 as a "disk signature", so it is not generally a good idea to zero those bytes since it can cause problems in particular with Vista. If you want a real life example of some poor soul who unfortunately ran exactly the command given above in the quote and zeroed his partition table, see this thread:

[http://ubuntuforums.org/showthread.php?t=958364](http://ubuntuforums.org/showthread.php?t=958364)

I trust that you have no malicious intentions, Ocxic, but please be more careful about giving commands like that in the future. :)

---

### Post by ibootindos on 2008-10-30
> **bodhi.zazen said:**
> Install 8.10 and tell your friend it is Vista SP1

hahahaha I would, but he's paying me for the windows vista software, and he wants to play windows games play regular DVD's on it, and I'm not that much of a friend to spend all the time installing the codec's for that crap. lol

---

### Post by ibootindos on 2008-10-30
> **Ocxic said:**
> grub will be automatically removed when you install windows. 
If you really want to remove grub manually "sudo dd if=/dev/zero of=/dev/your_hdd  bs=512 count=1" is the command to use

when I install windows will it adjust whatever the crazy bios error is?

---

### Post by Absolut Newbee on 2008-10-30
Try starting the Vista install disk, starting the Repair Windows instaltion. type FIXMBR on the command line.

see 
[http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

PS I know it is for XP, but havn't haerd you can't use it

---

