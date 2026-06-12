---
title: "help fixing my partitions"
date: 2009-06-28
forum: Hardware
---

### Post by dagoth_pie on 2009-06-28
hey there,
the problem so far as i can figure out is, when I had to reinstall windows, it wiped grub as it does, but now i cant reinstall it because grub cant find my ubuntu partition, with the grub config files on it. As far as I can tell, my hard drive is getting some bad clusters on it, which is probably the cause, is there any way i can use the live cd to fix the partitions without wiping them, or something i can download to use, I'm fed up with using windows, no media player should take 3ghz to play music
any help would be good

---

### Post by jimv on 2009-06-28
How do you know htat Grub can't find your Ubuntu partition?

---

### Post by Dysport on 2009-06-28
Have you tried automated GRUB-recovery with [Super-GRUB-Boot-Disk]("http://www.supergrubdisk.org/") yet?
It's a really neat tool I had to use often while I was still dualbooting Ubuntu. Hope that helps.

---

### Post by dagoth_pie on 2009-06-28
Ive tried using a live cd to install grub, the way I ususally do, but when I type:```
$find /boot/grub/stage1
``` I get an error saying file not found
and a similar error when I specify the partition, (hd0,1) second partition and only one hard drive (although I did try every number up to 5, just in case the random blank spots of unpartitioned space (who knows how they got there) make a difference)

I have also tried the super grub boot disk, and it had the same problem with not being able to find any grub files, on both auto and manual installs. The part that leads me to believe my partitions are a lil out of place, is that when I put in a Fedora 11 Live cd, I figured putting a new set of grub files to run an install off may help, but right upon login it came up with a message saying my hard drive is reporting health problems, and a more thorough reading of the error, summed it up as bad clusters, anyway I gave up on that approach because of all the errors that came up when I tried to get it to format the last 50gb on my hard drive.

Sorry I missed out quite a bit in the first post, anything else you need to know?
and thanks for the responce

---

