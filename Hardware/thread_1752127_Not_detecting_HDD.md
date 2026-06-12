---
title: "Not detecting HDD"
date: 2011-05-07
forum: Hardware
---

### Post by Sputnikz on 2011-05-07
Hi everyone, this is my first post on the Ubuntu forums, and I'm coming here because I have a bit of an urgent problem-
First off, I have an ASUS N61JQ (laptop) that's been running in near perfect condition for about 6 months.  All of the sudden, though, when I decided to do a little partition editing to my HDD, GParted doesn't detect my hard drive.  I boot into my BIOS, and to my horror, my hard drive isn't listed as a boot option and the first ATA port (where my HDD has been) is listed as empty.  I updated my BIOS, to no avail.

Since I've had a horrible time with ASUS support and I'm not getting any replies anywhere else, I was just wondering if anyone can narrow this problem down to a fried hard drive, etc.

Thanks!

---

### Post by Vishnu V on 2011-05-07
Is that hard disk working properly ?
please post the output of fdisk -l after connecting harddisk
Try disk utility also

---

### Post by Sputnikz on 2011-05-07
Thanks-
I forgot to mention that I already tried looking in disk utility.  The disk is recognized, but I can't edit the partition table and it shows the disk having 0.0kb of space on it.

I tried fdisk -l, however it gives no output whatsoever.  Based on this I'm guessing the hard drive is shot.  

The main thing I'm questioning now, based on that assumption, is whether I should A. void my warranty, open up my computer, and replace the hard drive without knowing exactly what the problem is or B. wait for ASUS support to respond and (potentially) get a replacement.

---

### Post by jmore9 on 2011-05-07
Before you decide it is shot , you should try Gpartd live cd.  This boots you into gparted from startup(boot).  It should give you a good idea on what is happening with your hard drive.  It can also tell you what the flags are on each partition it sees.  Like is it flagged as boot or does it have any flags at all ?

---

### Post by Sputnikz on 2011-05-07
GParted simply says "No devices detected" in the bottom left hand corner.  I also tried repairing the MBR (since the last OS I had was Windows) from my Windows 7 install CD and that didn't help.  Final verdict?

---

### Post by oldfred on 2011-05-07
What tool did you use to edit partitions. Some windows tools do not see Linux partitions and corrupt partition table.

You could see if testdisk finds older partitions on drive.

Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Sputnikz on 2011-05-07
Thanks for the advice!  I'm going to go through those sites right now and see if I can do anything.

In the mean time, I was wondering if there is any definitive way to tell if my hard drive is completely dead.  Is the fact that it shows up in Disk Utility a sign that it isn't?

---

### Post by oldfred on 2011-05-07
Does disk utility show it smart status - healty, when you click on drive? smart data has lots of detail but I do not know what is acceptable other than the pass/fail it posts.

---

### Post by Sputnikz on 2011-05-07
It does NOT show smart status.
I also downloaded testdisk, and the only "media" it allows me to select is my DVD drive and my external USB drive.

---

### Post by oldfred on 2011-05-07
If testdisk does not see it, is your BIOS seeing the drive now. Sometimes you have to turn smart status on in BIOS. If so it will not have any history to show. Any relatively newer drive should have smart capability.

If BIOS does not see drive double check all physical connections. After that I am not sure.

---

### Post by Sputnikz on 2011-05-08
Thanks for all of the advice you've given me!  However in the end I just ended up going out and buying a different (Faster/bigger :D ) hard drive.  I stuck it in and had no problems right away.

---

