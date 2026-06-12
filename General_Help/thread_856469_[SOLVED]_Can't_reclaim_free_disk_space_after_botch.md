---
title: "[SOLVED] Can't reclaim free disk space after botched sudo Nautilus delete"
date: 2008-07-11
forum: General Help
---

### Post by stopthewar24 on 2008-07-11
Hello everybody,

Here's my problem: I recently deleted about 4.1GB of files (digital camera images) on my ~10.1GB Ubuntu ext3 main partition.  The files aren't visible or accessible anywhere anymore, as far as I can tell, yet the space that they occupied is unusable -- I can't put more files on it, and Nautilus reports only ~725MB of free space on the partition.  How can I reclaim this space and be able to use it again?

The backstory: The files in question (about 4.1GB of digital camera files, in one big folder with numerous sub-folders) were copied onto my computer from a burned data DVD.  After a time, I wanted to remove the files from my hard drive, so I deleted them (off of my desktop, where I was storing them) and they went to the Trash.  I then opened the Trash in Nautilus and clicked "Empty Trash," but the files stayed where they were.  I had other various files in the trash as well which emptied sucessfully, but all 4.1GB of my digital camera files refused to go away.  I guessed that this was a permission error -- somehow the read-only flag seemed not to have been dealt with properly on the copy from my read-only DVD disc, denying my user account permission to delete the files -- so I ran Natulius with sudo and tried once again to delete the 4.1GB of images from the trash.  This time, it seemed to succeed -- they dissappeared.  However, the space that they occupied hasn't been reclaimed by the filesystem yet, as it appears.

GParted shows my partition as 10.24GiB in size, with 9.02GiB occupied and 1.22GiB unused.  Nautilus (currently) reports 724.5MB of free space.  After running a scan with the Ubuntu Disk Usage Analyzer, the results pane shows that I have 4.6GB of files on my partition, which is correct.  However, the "Total filesystem capacity" summary line indicates that my 10.1GB partition has 8.9GB used and 1.2GB available.

In working to troubleshoot this myself, I've run fsck on my partition (while it was unmounted) off of a Hardy LiveCD with the -f option to force a check.  The check ran for a while and completed with no problems, yet it didn't do anything about my issue.

Can any of you brilliant people out there help me?  I'm relatively new to Linux, though not to computers in general.  I'm on a Dell Inspiron 1520 laptop with a 160GB hard drive, dual-booted between Ubuntu Hardy 8.04 (ext3 partition) and Windows Vista Home Premium (Vista-type NTFS partition).  Most of my data is stored on the Windows Vista partition and I use the Vista install extensively as well, and therefore I don't want to affect or touch that partition at all.  If possible, I would like to keep the Ubuntu partition in the ext3 format, simply because it has worked well for me up to this point, I have no need for any other format, and I believe it must be possible to get it working again.

Thanks in advance for any help or ideas you could send my way.

---

### Post by Elfy on 2008-07-11
Run nautilus as root and check in root's trash - also when in trash do Ctrl+H to see if you have hidden files

```
gksudo nautilus
```

---

### Post by dracayr on 2008-07-11
root doesn't have a seperate trash (as far as I know files deleted by root go into ~/.local/share/Trash/files/ too)

dracayr

---

### Post by Elfy on 2008-07-11
My trash is in /home/kevin/.local

My root's trash is in /home/.Trash-0

---

### Post by stopthewar24 on 2008-07-11
Wow!  When I'm in Nautilus as root and go to "~/.local/share/Trash/files/", I see my 4.1GB!  Can I delete them graphically in Nautilus as root (by clicking their folder and pressing the delete key), or is there a better method I should use?

Thanks!

---

### Post by Elfy on 2008-07-11
You should be able to delete them as root in the gui - it should say something along the lines of permanently delete

---

### Post by coffeecat on 2008-07-11
> **stopthewar24 said:**
> Can I delete them graphically in Nautilus as root (by clicking their folder and pressing the delete key)

Normally you can delete things immediately (without sending them to Trash) with shift-delete. It's a bit more convenient than deleting from a terminal - worth trying.

---

### Post by stopthewar24 on 2008-07-11
Ohh, y'all are wonderful... the shift-delete in the Nautilus gui (run with gksudo) worked perfectly.  Nautilus now reports that I have 4.8GB of free space on my drive, which is exactly right!  Thanks a ton... this problem seems to be solved now.

(as I'm new to the forums, is there any protocol for marking a thread as 'solved' that I should follow?)

Many thanks!

---

### Post by coffeecat on 2008-07-11
> **stopthewar24 said:**
> (as I'm new to the forums, is there any protocol for marking a thread as 'solved' that I should follow?)

I *think* it's 'thread tools' at the top. If not you could always start a new help thread. :wink:

---

