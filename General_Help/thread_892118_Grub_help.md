---
title: "Grub help"
date: 2008-08-16
forum: General Help
---

### Post by Comzee on 2008-08-16
So this is how I have my system set up.

#1:  300gb ntfs partition (Windows XP installed)
#2:  10gb ext3 partiion (Ubuntu 8.04 installed)
#3:  2bg linuxswap partition
#4:  Random unallocated space.

I had my system setup so it would boot into grub and I could choose between Ubuntu or Windows. I reformatted Windows and it redid the Master Boot Record so now it doesn't go to grub, but automatically boots into Windows. I assume grub is held in my ext3 partition, so if I get my machine to boot from my ext3 partition first instead of my ntfs one, I think that will solve the problem.

I don't know for sure that grub is held in the ext3 partition though, correct my if I'm wrong?

How do I edit my Master Boot Record, or just fix whatever I need to fix so grub boots again?

Thanks in advance for any help. :D :D :D

---

### Post by Shazaam on 2008-08-16
If Windows took over the mbr grub was likely installed there. Here is a very good tutorial for reinstalling grub using the livecd....
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

