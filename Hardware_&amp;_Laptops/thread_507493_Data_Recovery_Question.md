---
title: "Data Recovery Question"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-07-23
I've used test disk a little, but I don't know if it can do what I need....

I recently reinstalled Ubuntu after wiping every partition off my hard drive.  Ubuntu was installed on a secondary hard drive, but is now installed on the primary hard drive, replacing the once existant NTFS partition that used to be there.  I forgot to back a lot of stuff up off the drive (I can't believe that, but I did).

It's a 100 GB HD, and I know Ubuntu doesn't take up anywhere near that much space.  So there is a chance a lot of the data I forgot to backup is still in tact and I was wanting to see if I could find anything salvageable.

I have testdisk doing a cylinder analysis of the drive, but I don't think this is what I need.  I need something that will scan all the sectors and be able to restore files if they are intact and uncorrupted.  Can testdisk do this?  Or do I need to find a different utility?

I used to use a program in Windows called Get Data Back which did a very thorough job of scanning and finding lost files.  Any chance there is something out there that can do what it did?

---

### Post by ramjet_1953 on 2007-07-23
If you did an automatic install of Ubuntu onto your drive and allowed it to use the whole disk, then I'm afraid that your disk has been re-formatted to ext3 and any data you had on the disk previously has been over-written.

During the install, you are warned that this will happen and you have to press enter to proceed.

Regards,
Roger

---

### Post by Cappy on 2007-07-23
Well there is PhotoRec:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It is installed with testdisk, I think the command is
```
photorec
```=P

You should be able to recover a large portion of your hard drive (only a small amount of your files have actually been overwritten, the rest is just sitting there). Obviously you shouldn't recover files to the same hard drive as you are recovering them from.

There are also some live CDs with testdisk on them:
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Finally, I've used [www.R-STUDIO.com](www.R-STUDIO.com) in the past and it worked perfectly so I would recommend that too. Expensive bugger though.

---

### Post by Data Recovery Guy on 2008-05-09
Whenever you delete or "wipe" your hard drive all the data is still intact. It is just inaccessable until you find the right tool(s) to recover it. However once you install new applications that is what partially overwrites the old data and makes it unrecoverable. There was recoverable data on that drive you just need to find the right tools (software)or service to help you. 

In this case data recovery software is still an inexpensive option but some of these over the counter software programs will write to the target drive you are trying to recover the data from. Thats why they are so cheap becuase they dont offer
a very secure way of recovering the data without further damage.

I am not familar with any over the counter software that can help becuase we dont use those types of tools. (All our stuff is custom written by our programmer.)But I am sure if you do a little research you might be able to find something that claims to be a "read only" tool. 

If you need some assistance we are availible:)

Sincerely, 

Data Recovery Guy

InterData hard drive data recovery services. Emergency repair and data recovery for hard drives, RAID, servers, DVD, CDROM, flash drives, and many more. Located in Orange County, CA. Recover data from clicking or malfunctioning hard drives with mechanical damage. [www.interdata-services.com](www.interdata-services.com) [www.interdatarecovery.com](www.interdatarecovery.com)

---

### Post by justin67 on 2008-07-24
You can also try Stellar Phoenix [linux data recovery]("http://www.stellarinfo.com/linux-data-recovery.htm") software.I have used this software it helps me to recover all my data.May be it will help you.This software free demo version will scans all the sectors of your hard drive and you will able to see the preview of your recoverable file. This software is user friendly interface thatswhy very easy to use.

---

