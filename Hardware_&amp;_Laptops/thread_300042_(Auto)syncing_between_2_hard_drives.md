---
title: "(Auto)syncing between 2 hard drives"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by aweller on 2006-11-15
Dear all,

In my Ubuntu *Edgy Eft* box I have one internal hard drive with the following partitions:

/dev/sda5 / reiserfs notail 0 1
/dev/sda7 /home reiserfs defaults 0 2
/dev/sda6 none swap sw 0 0
/dev/sda1 /media/win_system ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda2 /media/win_data vfat defaults,utf8,umask=007,gid=46 0 1

The /media/win_data contains **everything** on it. I have a relatively new external USB drive that I would like to format as ext2.

The idea is, can both /media/win_data and this new external USB drive be auto-synced so that I have a backup of one to the other?

So, for example, if I open Nautilus and copy a new file to /media/win_data this will also automatically be copied to the external USB drive (and vice-versa)?

This way I will always have an up-to-date backup of all my data.

Many thanks, Andy

---

### Post by yabbadabbadont on 2006-11-15
After doing some google searches, I think you can do this "RAID 1" configuration using LVM with the partitions/drives configured in "clone" mode.  I've never really used LVM myself, but what I've read seems to say that it can be done.  Perhaps an LVM guru can confirm or deny this?

---

### Post by aweller on 2006-11-15
Can anyone shed any light on this issue? LVM...?

Cheers, Andy

---

### Post by aweller on 2006-11-15
Just a thought: would this work by giving both drives the same mount point in fstab? i.e. '/media/win_data'?

Perhaps I have the wrong idea...

---

### Post by bitwise5 on 2006-11-15
If you want to keep a running back up of your data, pointing two phyiscal drives to the same mount point seems like going against the grain - at least from what I know. I've been looking to this for my own machine, and I might settle on using RAID and logical volume manager (LVM); which requires me shelling for two identical, internal drives (just to keep things easy), and spending the time it takes to get it running smooth. 
If you don't need your data backed up more than once a day, why not just schedule a cron job? You could just push the whole directory branch over to you external drive daily.

---

### Post by aweller on 2006-11-16
Schedule a cron job?

How would I do this so I can:

1. Switch on my external USB ext2 (or fat32) drive
2. Check its contents against my internal fat32 drive
3. Copy changes/sync between these two drives

Thanks for your help, Andy

---

### Post by bitwise5 on 2006-11-16
Cron jobs just run a script/program when you tell them to. So if you want to write your own syncing script, you will have to execute a series of shell commands. Simpliest, but rather brutal on your hardware, would be like this:

rm -rf /media/usb-external
cp -R /home/dir_to_keep_backed_up /media/usb-external

 I don't recommend this though, you really only need to copy the files which have changed or are new, right? Possibly delete the ones which aren't there anymore? 
 You could do it with a shell script and common unix command line tools (diff, ls, cp), which could be a lot of work depending on how often you do stuff like that. 

So, if you really just want the hardware/OS to handle the sync, then you might need new hardware! Also check out rsync, it's really for syncing between two machines across a network, but you may be able to hack that too.
Hope this helps

---

### Post by aweller on 2006-11-17
Thanks bitwise5.

I've checked out some old forums for rsync and found the nice little GUI program Grsync ([www.opbyte.it/grsync)](www.opbyte.it/grsync)). It seems to be doing exactly as I want as I type.

Perhaps as I get more accustomed to rsync I can set it up to auto-sync at a particular time/day.

---

### Post by bitwise5 on 2006-11-17
so, someone already solved this problem and even distributes it as a GUI app? nice

---

