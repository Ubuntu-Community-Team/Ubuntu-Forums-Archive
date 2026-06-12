---
title: "External Hard Drive Is Read-Only"
date: 2014-09-06
forum: Hardware
---

### Post by ScooterBoogles on 2014-09-06
Hi there,

I'd love some help with a issue around a Toshiba External Hard Drive. 

A friend of mine messed around with this external to transfer some large files from a Mac. Now I want to use it to back up small files on Ubuntu 12.04 but it's saying "Read Only."

Here's a screenshot from Disk Utility:

[ATTACH=CONFIG]256223[/ATTACH]

And here's a screenshot from after I Check Filesystem:

[ATTACH=CONFIG]256224[/ATTACH]

Can you help? Thanks!

---

### Post by Vladlenin5000 on 2014-09-06
Do you have something you need from that drive as it is now? If so, please do your backup first and then reformat the whole thing. Why complicate things further? Its file system is indeed broken and Linux cannot fix it. Somehow, your friend must have formated it with a MacOS proprietary file system.

---

### Post by ScooterBoogles on 2014-09-06
I tried reformatting the volume and that didn't work. Should I reformat the drive?

---

### Post by Vladlenin5000 on 2014-09-06
> **ScooterBoogles said:**
> I tried reformatting the volume and that didn't work. Should I reformat the drive?

Yes. You should removed the 'offending' partition altogether and create & format a new one (or more than one if you wish). Choose NTFS for better compatibility with other OSs if you need it to store big files (>4GB); otherwise FAT32 will give you the maximum compatibility; typical Unix/Linux file systems like EXTx (x=2,3 or 4) will only work in Unix/Linux systems.

---

### Post by ScooterBoogles on 2014-09-06
Should I choose:

Master Boot Record
GUID Partition Table
Don't partition

?

---

### Post by ScooterBoogles on 2014-09-06
I reformatted the drive using Master Boot Record and it's still showing as read only! Hmm, maybe it's just busted.

---

### Post by Vladlenin5000 on 2014-09-06
Sorry, that just can't be... What file system have you choose? And whatever that was you're probably NOT doing it right...

Please describe EXACTLY what steps you took to format it?!?...

---

### Post by ScooterBoogles on 2014-09-06
I reformatted the drive using Master Boot Record.

It asked me to create a partition, and I did, choosing FAT.

I let it process. I checked the volume, the filesystem is clean.

Still read only! Thanks for all your help, I'm puzzled. :)

---

### Post by Vladlenin5000 on 2014-09-06
If you intend to avoid question by repeating yourself, I'm out of here...

When someone asks you to describe _EXACTLY_ what the steps were, the expect answer should go like this: 

I used/opened app/tool X...
I did A...
I did B...
And finally I did C...
The results were...


Now, what you probably didn't do: Remove the old partition(s). You need to remove *everything*!!! Assuming you're using the Disks utility, you need to select the partitions one by one and press the "-" sign to remove the selected partition. Only when you're left with one continuous UNALLOCATED space you're in a good place to start by a) select the unallocated space, then b) (at the same Disk utility) press the "+" sign to create a new partition.
If this doesn't work install and use GParted.

---

### Post by ScooterBoogles on 2014-09-06
I'm very sorry, didn't mean to waste your time. I'm just not all that expert. Thank you for all your assistance!

I followed your last post and didn't get a new result -- I'll try GParted. Thank you again!

---

### Post by ScooterBoogles on 2014-09-06
You know what? It's actually a different problem. Suddenly my CPU is showing ALL externals as read only. Weird!

---

