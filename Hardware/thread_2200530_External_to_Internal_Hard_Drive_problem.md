---
title: "External to Internal Hard Drive problem"
date: 2014-01-19
forum: Hardware
---

### Post by amanpreetsarna on 2014-01-19
Hello all!

I want to take an external hard drive (Seagate Expansion Drive 3TB) and remove the hard drive itself so that I can install it into my newly-built PC. I removed the drive successfully, installed it in my case and hooked up the power and SATA cables and...

1. The BIOS recognises that there is a 3TB SATA Drive
2. Gparted can also see a 3TB drive but is unable to gather more info re the partitions. The drive is NTFS formatted (with lots of data on it and so formatting is not an option until I purchase a replacement drive).
3. I am unable to read anything off my drive when connected internally and I cannot mount it at all via terminal.
4. Thinking I may have damaged the drive when removing it from its enclosure, I plugged it back in via USB and it all works completely fine!

Is there a step I have missed? (this being the first time I have tried something like this!) Should Ubuntu/Debian recognise the partitions on my drive without me needing to do anything else?

Thank you for your help!

---

### Post by Bashing-om on 2014-01-19
amanpreetsarna; Hi !

One must attach the device as a file system to ubuntu's file system. This is done via a "mount point" and "mounting" -automatically - via the File System TABle file located at /etc/fstab. NTFS needs special options to set access and permissions to the partitions on the drive, set within the fstab file.

Details:
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

As you have additional questions, do not hesitate to ask.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by amanpreetsarna on 2014-01-20
Thanks for replying. I think my original post wasn't very clear, far too late to make much sense!

Anyways I am not able to mount the drive and I get an error along the lines of: this drive does not appear to have a valid NTFS.
In GParted the drive does not have a valid filesystem: approx 400GB is of unknown filesystem, and around 2.3TB is "unallocated" (yet the disk has a single NTFS partition of approx 2.7TB).

I have been reading around this further and it looks like either the SATA to USB bridge that is built in with the enclosure has some proprietary method of partitioning stored within it or that the disk is formatted in a non-standard fashion. I unfortunately do not have enough spare storage to backup this drive and experiment with ways to try and restore it so I may just take the plunge and purchase it a separate drive!

Has anyone else been in a similar situation? (and hopefully found a much cheaper solution?)

---

### Post by Bashing-om on 2014-01-20
amanpreetsarna; Hey, not good !

As ubuntu is hollering about "this drive does not appear to have a valid NTFS." have you looked at the drive from Windows' perspective with the Windows' disk utilities ?
Nothing like using the native tools on the native file system.

[INDENT]a procedure - and -
[INDENT][INDENT][INDENT]the right tool for the right job
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by amanpreetsarna on 2014-01-20
The thing is Ubuntu can read the drive without any problems if connected via USB. You're right though - one thing I haven't done is install the drive into my other PC which dual boots with windows 7

---

### Post by Bashing-om on 2014-01-20
amanpreetsarna;  Hey !

When the disk passes windows disk checks, 
next I would swap the sata cables around in the case ( make sure to inspect for bent pins), see if the problems move with moving the cables (??)
And take a long read in the system log files, see if the system reports any problems.

[INDENT][INDENT]gotta be a cause
[INDENT][INDENT][INDENT][INDENT]gotta be a solution
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by amanpreetsarna on 2014-01-21
I'm gonna hook it up via USB to my Windows machine, see if there are any problems with the disk. I am guessing that there shouldn't theoretically be any problems with connecting an external drive via internal SATA?

---

### Post by Bashing-om on 2014-01-21
amanpreetsarna; Hey,

Nope, should have no problem at all, When it is time to make it a permanent arrangement, will need to set up a mount point to attach file systems and edit the /etc/fstab file to make the system aware of the hard drive automagically at boot. (as I am sure you have learned by now)

Let us know how it goes, and how we can assist further.

[INDENT][INDENT][INDENT]I like it 
[INDENT][INDENT][INDENT][INDENT]like that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

