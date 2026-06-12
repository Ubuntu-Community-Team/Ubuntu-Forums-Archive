---
title: "move data from bad blocks and sectors marked to be reallocated"
date: 2016-12-27
forum: Hardware
---

### Post by sushi-addiction13 on 2016-12-27
I'm NOT asking how to fix a bad block. The HDD is 7 years old and has developed a small amount of errors very slowly. It'll last a few more years.


I want to scan the whole disk and have data on sectors or blocks with errors moved. How can I do this?

I'm unsure if ```
fsck -cc /dev/sdXX
``` will do this. I assumed it would.

> -c This option causes e2fsck to use badblocks(8) program to do a read-only scan of the device in order to find any bad
blocks. If any bad blocks are found, they are added to the bad block inode to prevent them from being allocated to a
file or directory. If this option is specified twice, then the bad block scan will be done using a non-destructive
read-write test.

"If this option is specified twice, then the bad block scan will be done using a non-destructive read-write test." I assume that would mark bad blocks and move the data too.

Back when HDD were around 20MB-500MB I use to do the same using some DOS program I've forgotten the name of. It usually worked and drives lasted for years. It would read/write bad blocks X number of times to be sure the block was bad and if it was, it would move data. Very good software.

Not as good but the same idea [URL="http://askubuntu.com/a/765440"]http://askubuntu.com/a/765440


[/URL]

---

### Post by TheFu on 2016-12-27
I would use badblocks directly.

Also, modern HDDs automatically relocate bad blocks when discovered, as long as spare blocks still exist on the disk.  Use the SMART data to see how many spares remain.  When the spares go to zero, throw out the disk (drill some holes through it first), and put in new disks if you care about the data at all.  Actually, I usually replace disks when 10 blocks have been relocated. Data is just too important to risk.

---

