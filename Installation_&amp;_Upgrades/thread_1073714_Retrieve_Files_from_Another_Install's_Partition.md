---
title: "Retrieve Files from Another Install's Partition?"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by wmichaelb on 2009-02-18
Having tried it on another partition, I'd like to upgrade my existing Hardy 32-bit install to an Intrepid 64-bit. Is there a way to back up the home directory so that I can recover it after I upgrade the install? When I last tried this to a DVD, all the files were set to read-only. 

For that matter, could I back up all my various installs (I'm currently running three, two of them Ubuntu) to another partition, and recover them? So far, when I try to use Nautilus to do this, I can't find the home files on those other partitions, even after putting in my password.

Thanks in advance!

---

### Post by ajgreeny on 2009-02-18
I think if you just copy the files and burn them to a CD or DVD, they will always be read only.  This is simply because you can not write to a file on a CD.  I'm not certain, but I think if you use rsync or grsync to do the backup to CD the files will normally retain the permissions of the original files.  I don't use CDs or DVDs for backup, so am not able to tell you for certain if this is so, but certainly it is the case if you use a USB hard drive for the backup.

The files that you can not see in other partitions are probably given permissions that forbid everything to all except the owner, ie 700.  You may therefore need to go back to those partitions and reset the permissions to be readable by others, then they should show.  Ubuntu sets home as 755, ie read and write for owner, read and execute for others; other distros may set the home files differently.  Wait for other peoples ideas before rushing to do anything, however, as I am often a bit rusty on these sort of things

---

