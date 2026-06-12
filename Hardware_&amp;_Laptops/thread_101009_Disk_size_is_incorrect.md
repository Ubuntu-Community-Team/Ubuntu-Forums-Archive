---
title: "Disk size is incorrect"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by chiefofthejojos on 2005-12-08
Hi everyone,

My 200 GB hard drive is only showing up as ~128 GB on any operating system.  
It's an external firewire drive.  I installed it into the enclosure myself.  I'm assuming that I did something wrong but I don't know what.  I set the jumper to master before I installed it, but I didn't know if there were any other settings I should look for.  There was a lot of corruption to the data when I plugged it in (presumably because suddenly >%25 of the medium dissappeared), most of which I was able to recover after using e2fsck.
Any ideas?

Thanks,
Brad

---

### Post by gruepig on 2005-12-08
Were all 200 GB ever recognized?  What file system type is it (I'm guessing ext2/3 since you used e2fsck)?

---

### Post by chiefofthejojos on 2005-12-09
I think it used to show up as ~180 gb.  I remember when I bought the disk, the manual said I would need to do something to enable the full 200 GB, but I assumed it was a M$ thing.  
The drive was ext3 before.  I thought that formatting the disk might fix the problem, so, using gparted I formatted to reiserfs.  No luck.  My disk-admin freezes on startup (related?) so I can't use it.  I have given up and deleted any partitions, hoping a genius on these boards can show me the way! :)
Just to reiterate: in gparted and in windows disk manager the disk appears to be ~128.

---

### Post by davidsrsb on 2005-12-10
180 GB sounds about for a so called 200 GB drive, the old 1024 vs 1000 k problem.

---

### Post by tonysathre on 2005-12-10
i remember reading somewhere that certain file systems ( i think it was FAT and VFAT) that only allow partition sizes up to a certain size. if u specify a partition size thats over this amount it will only show up as the maximum allowed size.  i dont know if this is your  problem or not but i know it has been an issue with HDDs and FSs

---

### Post by chiefofthejojos on 2005-12-10
When hard drives fail is it usually an all or nothing situation, or do single platters die?  I did bang it up a little bit as I was moving it so I wonder if a single disk could have failed.  Is that possible?

---

### Post by simon.schmidt on 2005-12-11
I have no idea what I'm talking about but:
[quote=http://en.wikipedia.org/wiki/Advanced_Technology_Attachment]The original ATA specification used a 28-bit addressing mode. This allows for the addressing of 268,435,456 512-byte sectors (128 GiB or 137 GB).[/quote]

---

### Post by chiefofthejojos on 2005-12-15
so.. maybe the hardware in my enclosure is old?  That would explain it, because it worked fine internally.  I guess now I know another important spec. to look for. :)

---

### Post by chiefofthejojos on 2005-12-15
[QUOTE=simon.schmidt]I have no idea what I'm talking about but:[/QUOTE]

actually, VERY good call!  I just switched this hard drive into a different enclosure and the whole ~200 GB show up!  The funny thing is that my old (1.5 years) USB 2.0 enclosure supports the big size, but my new (2 weeks old) Firewire enclosure doesn't. :confused: 
But, no matter.  All is good for me!
Thanks, Simon!:D

---

