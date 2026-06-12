---
title: "Good partition tools? (I need to fix a part table)"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by seanmc42 on 2006-03-18
I got an HDD that the partition table got wiped on when Linux went down -
I would like to restore the partition table and hopefully the partitions themselves as there was lots of data on there ... it's a 300GB HDD which had four ext2 partitions.

Recommendations?

Thanks!

---

### Post by saphil on 2006-03-18
Are you sure it is a partition issue and not a MBR issue?

From the "recover the data" standpoint...
Have you looked at the partition table from the install program on your install disk?  You can probably see the partitions that are there and recover them with gparted from the new installation of Ubuntu.
You might be able to boot a knoppix live cd and look at the data-bearing partitions from there, and maybe transfer the data to a different drive.  

[http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=503&st=288](http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=503&st=288)
for partitioning ideas

Most times when one of my students or clients hoses a drive, I have been able to get somewhere by putting it in a machine as slave and move the data off.  In some cases low-level formatting is the only solution.  There  may be a forensic solution for the problem.

[http://www.linux-forensics.com/downloads.html](http://www.linux-forensics.com/downloads.html)
has pretty good forensics info and a live disc issue.  I am downloading that iso right now.  It looks a lot like KnoppixSTD in content.  I guess I will tell you later if it is useful to me.  I would be interested to know what ends up working for you.

---

### Post by seanmc42 on 2006-03-18
Well, it's not a bootable disk so I'm nto sure the MBR is relevant (am I wrong?)
but using fdisk shows no partition table at all...

[EDIT]
Sorry - I didn't give enough info ( posted a couple places, got lazy here ...)
I have a working system, but it crashed a couple weeks back. When it died,
Ubuntu 4.5 died taking with it the partition table of a seperate HDD that wasn't
even mounted!!!

I have re-installed Ubuntu (4.10 now), but I'd like to get my data back... fdisk
shows no entried at all on the data HDD...

---

### Post by az on 2006-03-19
If you boot from a live cd (or the installer and go to the shell) run parted and try to rescue your partitions.

Once you boot the installer, let it detect your hardware and load all the components (then it goes to the partitionner)  Leave that and go to the shell (CTRL-ALT-F2)

parted
print
rescue
(enter the area of the disk where you think the partition used to be.)

---

### Post by seanmc42 on 2006-03-19
Hmmm.... maybe I'm missing something:
(Please understand this is a data-only disk that is not mounted automatically by the OS):

If I run parted on this drive, and execute 'print', I get:
"Error: Unable to open /dev/hdd - unrecognised disk label."

This is why I think the partition table itself is hosed.
So, what I'm saying is that first I need to rescue the partition table, THEN the partitions - is this possible?

PS> What does the label error mean?

---

### Post by az on 2006-03-20
[QUOTE=seanmc42]"Error: Unable to open /dev/hdd - unrecognised disk label."

This is why I think the partition table itself is hosed.
So, what I'm saying is that first I need to rescue the partition table, THEN the partitions - is this possible?
[/QUOTE]


Yes.

Use fdisk to create a blank partition table and then use parted to "rescue" any partitions that are on the disk itself.  Rescue will detect them and then ask you if you want to add them to the partition table.

---

