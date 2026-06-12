---
title: "Weird numbers from &quot;Disk Usage Analyzer&quot; (8.04LTS)"
date: 2010-03-04
forum: Hardware
---

### Post by hbquikcomjamesl on 2010-03-04
While sizing my newly refurbished box for a "backup appliance," I discovered something rather odd:

The label on the hard drive (the only one) says "Maxtor DiamondMax 21, STM3160215A" and gives the capacity as 160G.

And the Seagate/Maxtor web site confirms a match between the model number and the capacity.

The drive is partitioned with a fairly small DOS Primary, a somewhat larger Extended (containing DOS volumes D through G and Linux /boot), a very large Linux Root, and a decent-sized swap.

Also present are 360k and 1.44M floppy drives, a 250M Zip drive, a CD-ROM drive, and a memory card reader. But the Maxtor (smallish by the standards when I bought it, tiny by today's standards, yet the 1.2% given over to DOS volumes is cavernous by DOS standards, bigger than the entire hard drives of my two DOS notebooks combined) is the only hard drive.

Yet "Disk Usage Analyzer" claims I have 286.9G. in the file system.

And the System Monitor's "File Systems" tab has a line for something called "gvfs-fuse-daemon," that has exactly the same capacity as the /root partition. If I include that, I get a total that's approximately the number given in Disk Usage Analyzer, but if I leave it out, I get a total that leaves room for the swap partition.

So what's up with these numbers?

--
James H. H. Lampert

---

### Post by 2hot6ft2 on 2010-03-04
Disk Usage Analyzer only shows you how the files are spread out in your filesystem not on the partition. To see how much is used on your partitions run
```
df -h
```
in a terminal
Applications > Accessories > Terminal

See this thread: [Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")

Also when running the Disk Usage Analyzer and it's looking at / all the drives are looked at since they are mounted in /media and such so I suggest not even using it since it just creates confusion.

---

### Post by 2hot6ft2 on 2010-03-04
I even looked into uninstalling (its name is baobab) it but it's part of the Gnome utilities package
> GNOME is the "GNU Network Object Model Environment".
It is a project to build a complete, user-friendly desktop based
entirely on free software.

This package contains the following utilities for the GNOME desktop:

 - baobab, a disk usage analyser
 - gfloppy, a tool for formatting floppy disks
 - gnome-dictionary, a program which can look up the definition of words
   over the internet (including a panel applet to do the same)
 - gnome-search-tool, with which one can find files by name or content
 - gnome-system-log, a log viewing application
 - gnome-screenshot, a tool to take desktop screenshots and save them into
   a file
So there it sits. I just make it not show up in the menu by editing the menu and unchecking it's box so it wont be visible.

---

### Post by hbquikcomjamesl on 2010-03-04
Well, it is somewhat useful (and paints pretty pictures of how space is allocated in the file system tree), but if it can't come up with a meaningful number on the total size of the file system, it at least shouldn't show a bogus one.

The only reason why I'd even noticed it was that the first time I tried to size the system for a backup appliance, I'd forgotten the proper way to do an "fdisk -l" (and the man page wasn't helping), and was a bit desperate to get a number without having to open up the access panel and read the label on the drive.

---

