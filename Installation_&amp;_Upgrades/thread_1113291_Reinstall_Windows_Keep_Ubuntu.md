---
title: "Reinstall Windows Keep Ubuntu"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by spidy_x5 on 2009-04-01
I am new to the forum and I'm sure someone has already addressed this, but I couldn't seem to find it, if anyone has a link that will work just as well. Anyway, I have Ubuntu 8.10 x64 installed on my laptop dual booting with Windows XP x86, I have 4 partitions, 1 windows system, 1 windows storage, and then the linux and swap partitions. Right now I am dual booting Windows and Ubuntu with the grub loader. I want to reinstall Windows and delete the 2 windows partitions but I want to keep my Ubuntu intact because I have a lot of stuff install on it. I would also like to re-size the Ubuntu partition. I know that if I try to reinstall Windows over my current setup it will kill my grub loader and make my linux partition unavailable. So once all is said and done i want to be able to have windows installed on one larger partition and have a bigger partition for my Ubuntu. Let me know if you need anymore info or anything. Thanks!

---

### Post by ajgreeny on 2009-04-01
Boot to the ubuntu live CD and use the System > Administration > Partition Editor to delete your windows partitions (after backing up all your files, of course).  Now make a new partition for windows of the size you want and format it to NTFS.  Now you can enlarge your ubuntu main (root) partition to fill the empty space left unallocated.  That may take a long time as it will have to move the partition backwards on the disk, but don't panic, just leave it running and it will get there.  Your ubuntu should now be larger and you can shutdown the live CD and boot it to check it out.  Now boot to the WinXP Cd to install in the new NTFS partition (I think that's the only space windows will see, but just make sure that is the only partition being used)

Grub will now be gone and replaced with the windows MBR, but you can get it back easily by following this page:-
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by spidy_x5 on 2009-04-01
Awesome, thanks man! Think I'll try this out this weekend.

---

### Post by spidy_x5 on 2009-04-01
ajgreeny you are the man! I had time to do this today while working and it worked like a charm. Not one hiccup.

---

### Post by ajgreeny on 2009-04-02
Great!  Glad it worked.  I think gparted is worth its weight in gold sometimes.  And yet some people pay good money for partitioning software for windows.  I wonder why?

---

