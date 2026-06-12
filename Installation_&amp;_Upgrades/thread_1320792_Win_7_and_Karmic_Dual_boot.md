---
title: "Win 7 and Karmic Dual boot"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by scuba7183 on 2009-11-09
I started with 1 clean 320gb HDD. Installed 9.10 as a 100mb /boot a 1gb swap and a ~240gb / partition (All of those were logical partitions). It worked perfectly. 
Next, I installed Windows 7 on the remaining space, automatic install. Afterward, as to be expected, Windows 7 booted as default. I booted up a live cd and changed the bootable partition to the 100mb /boot. Now, all I get a blinking cursor.

---

### Post by darkod on 2009-11-09
Did you re-install grub? If you just made changes in grub that wouldn't help I think since windows boot loader is still the one kicking in.

Personally, if planning a dual boot I always install windows first. Then upon install ubuntu recognizes windows partition and adds it to grub. Smooth.

PS. Also, I believe I read somewhere about windows being a pain unless installed on the first partition. But you say it booted OK after you installed it after ubuntu.

---

### Post by Sef on 2009-11-09
> PS. Also, I believe I read somewhere about windows being a pain unless installed on the first partition.

That is correct.  Windows should be on the first primary partition.

> I started with 1 clean 320gb HDD. Installed 9.10 as a 100mb /boot a 1gb swap and a ~240gb / partition (All of those were logical partitions). It worked perfectly. 
Next, I installed Windows 7 on the remaining space, automatic install. Afterward, as to be expected, Windows 7 booted as default.

So you installed Windows 7 on a logical partition?

---

### Post by scuba7183 on 2009-11-09
No, Windows 7 is on a primary partition. It was installed using the default settings on the free space left over from the Karmic install

Here's a screenshot of gParted:

[http://www.flickr.com/photos/22800514@N07/4091332938/](http://www.flickr.com/photos/22800514@N07/4091332938/)

The FAT partition is just for sharing files between the OS's

---

### Post by oldfred on 2009-11-09
Windows does not have to be the first partition, but it just about has to be a primary partition. The boot flag has to be on the windows partition for it to boot. Ubuntu does not use the boot flag. Put the boot flag back on windows and make sure it boots. If so reinstall grub2 to the MBR and the update-grub2 command should find windows and add an entry to the grub.cfg file.

Because you have a separate boot partition the way you reinstall grub may be slightly different. Most assume the root partition has the grub and all the boot files.

I believe Herman has done most of the varieties and on his site for grub2 should be better info on reinstalling grub2.

reinstall grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)
[http://members.iinet.net/~herman546/p20/GRUB2%20Edit%20Mode.html](http://members.iinet.net/~herman546/p20/GRUB2%20Edit%20Mode.html)
[https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202](https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202)
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)

---

### Post by scuba7183 on 2009-11-09
It works perfectly! I love you in a completely non-sexual way

used [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

