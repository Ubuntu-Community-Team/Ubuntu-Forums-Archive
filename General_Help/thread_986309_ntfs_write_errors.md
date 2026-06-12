---
title: "ntfs write errors"
date: 2008-11-18
forum: General Help
---

### Post by xeddog on 2008-11-18
I have a small 160GB Western Digital external USB hard drive that I have a problem with using Ubuntu.  The drive is formatted ntfs and I am fairly certain that the disk is fine, but ...

I bought the drive a few months ago to use as a holding disk for downloaded media.  I have been using Azureus on a Windows XP machine to download tv shows etc., copy them onto the disk, and then unmount the disk and take it to another room and plug it into a D-link DSM-520 media server for viewing.  This is an almost daily task that worked well for several months.

Now I have migrated the download function to Ubuntu starting with Hardy for a short time, and now Intrepid.  It works just fine.  MOST of the time...  

In just 2 or 3 weeks there have been a few occasions where files that I have copied onto the disk from Ubuntu and played on the D-Link have stopped playing right in the middle as if it reached end of file.  I know the source files are ok because I can stream them using mediatomb and they play just fine.  Just something wrong with the copy. 

And on two occasions now, I have come across a situation where certain files on the disk become completely unreadable by either the D-Link, Ubuntu, or Windows XP.   The last time, there was a weird character that looked like a Chinese symbol in the file names of about 10 different files (just one character per file).  It might be noteworthy to say that when these characters have appeared, they appear in new and old files alike.  Not just the newest copies. 

Fortunately, I have been able to run chkdsk /f on the XP machine and it seems to fix everything and I have not lost any data yet.  But I am now very leery of using the disk on Ubuntu.  I have started using XP to do all of the copying to this drive by setting up nfs shares from linux.  Doing the copying from XP this way seems to have circumvented the problem, but I still need to know why this is happening and what to do to fix it.

I have read some older threads going back as far as 2006 that claim the ntfs-3g driver to be even more stable than windows, but at this point I don't think so.

Any ideas??

xeddog

In case you are wondering why I don't just stream using mediatomb, I copy to the disk so I can shutdown my computer and my network.  The d-link only uses 17 watts where the computer uses . . .what . . .200-300 watts and the network (dsl modem, router, and 24 port switch) another . . .100W???

Secondly, Yes, I have been umounting the disk before unplugging it from the linux machine.

Thirdly, the XP machine is a separate machine and not a dual boot, virtual machine, or anything like that (else I wouldn't be able to use nfs).  Both are fairly equivalent in terms of cpu, ram, etc.  The linux machine is dual boot between Hardy installed on sda (which I hardy use anymore  :) ), and Intrepid installed on sdb, both 32-bit.

---

### Post by Mark Phelps on 2008-11-18
I've used NTFS-3G as well, and while I don't believe that it's "more stable than windows", I do think that it's safer than the default packages that preceded it.  But, I too have had situations where an external NTFS-formatted drive, after being updated in Linux, would not mount the next time -- and I had to go into Windows to run chkdsk on it.

Sorry, don't have a solution.  Just wanted to let you know that you're not alone in this problem.

---

