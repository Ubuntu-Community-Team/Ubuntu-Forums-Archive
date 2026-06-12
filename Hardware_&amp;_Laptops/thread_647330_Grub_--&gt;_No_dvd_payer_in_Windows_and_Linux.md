---
title: "Grub --&gt; No dvd payer in Windows and Linux"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by jeroenzw on 2007-12-22
I have a problem with Kubuntu Gutsy. If I start up my laptop (Zepto Znote 6625WD) with the live-cd, I have a symlink /dev/cdrom, and some messages in dmesg about the cd player, so no problem there. I install Kubuntu, reboot, and the grub menu shows the normal thing (Ubuntu entries, and Windows XP). The problem is: 

When I boot in either Windows or Kubuntu, I don't have a dvd player anymore. In Windows it's just gone from the device manager, and it doesn't show up in dmesg in Linux. 

So i boot from a Windows CD, run fixmbr, and reboot to start up the 'normal' way (directly into Windows) and the DVD-player is back again. So the problem must be somewhere in grub, but I have no idea where. The BIOS settings are all normal (no AHCI, no 32 bit I/O mode on the DVD). 

What could be wrong here?

There is [one post here on the forums]("http://ubuntuforums.org/showthread.php?t=282535") that describes the same, and that user switched to lilo work around the problem. But it would be nice to just have it work with grub.

---

### Post by ollesbrorsa on 2007-12-22
Hello,

I too have the Znote 6625WD laptop. I had the same problem until I found a solution on the notebookreview forums. Last post on the page. [http://forum.notebookreview.com/showthread.php?t=160496&page=5](http://forum.notebookreview.com/showthread.php?t=160496&page=5)

In short set the 2nd IDE-channel to **None** in BIOS settings.

This is only a temporary fix since you have to change it back to **CD-ROM** or **Auto** if you want to be able to boot from your cd/dvd-drive.

Hope this helps.

Br,
ollesbrorsa

---

### Post by jeroenzw on 2007-12-22
Thanks for the reply, but I solved the problem differently. Even though I didn't want to do it, I installed and used Lilo as my bootloader, and that works like a charm! I have my dvd back in both windows and Linux, so it's definitely a grub issue.

---

### Post by ollesbrorsa on 2007-12-22
Probably not a grub issue since some of the guys over at the notebookreview forum have windows only setups...

Br,
ollesbrorsa

---

### Post by jeroenzw on 2007-12-27
Well, maybe the people over at notebookreview have a different problem, because I have no problem at all in Windows, unless I boot with Grub: Windows only, no problem. Lilo and Windows, no problem. Ah well, it works now. 
But I want to add some extra info concerning running lilo:
Lilo (by default) hides the other partitions when you log in an os started with Other. You have to add some extra lines in lilo.conf to disable the hiding:

other=/dev/sda1
   label="Windows"
# ADD below lines to disable hiding partitions (use your own sda/hda settings of course)
change
partition=/dev/sda2
	set=ntfs_normal

---

### Post by Jeanpaul145 on 2008-06-18
see my reply [here]("http://ubuntuforums.org/showthread.php?t=656408").

---

