---
title: "hdparm with laptop"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by molsen on 2007-06-21
i'm trying to tune my hd on my laptop, but am having trouble with hdparm.

default IO is 16 bit, so im trying to change it to 32 bit but it's not working.  what am i missing?

```
matt@matt-laptop:~$ sudo hdparm -c3 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)

```

current benchmark:
```
matt@matt-laptop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   550 MB in  2.03 seconds = 270.30 MB/sec
 Timing buffered disk reads:   68 MB in  3.07 seconds =  22.12 MB/sec
```
:-\

---

### Post by trak87 on 2007-06-21
If you have an sata drive, hdparm won't do much for you.

---

### Post by molsen on 2007-06-21
i dont think it's SATA...this laptop is 6 years old...

i just set -W1 and -A1 and got:

```
matt@matt-laptop:~$ sudo hdparm -tT /dev/sda
Password:

/dev/sda:
 Timing cached reads:   582 MB in  2.00 seconds = 290.64 MB/sec
 Timing buffered disk reads:   68 MB in  3.04 seconds =  22.37 MB/sec
```

so yea, not much improvement

is there a utility i can use that will make an improvement?

---

### Post by trak87 on 2007-06-22
I think Ubuntu has been changing the HD designations in the /dev directory. Sometimes even though you have an EIDE (PATA) drive, Ubuntu will refer to it as /dev/sda, which previously was used to designate only SATA drives and I think SCSI drives. /dev/hda on the other hand was traditionally used to specify the older (but still widely available) PATA or EIDE drives. So, I'm not much help here except to suggest determining which type of drive you do have. The fact that when you ran hdparm you don't see anything about a DMA setting leads me to believe you don't have an EIDE drive that would benefit from hdparm. And as for a utility to set SATA drives, I've heard one is in the works, but I've also heard that SATA drives don't have many meaningful user modifiable settings. Apparently SATA is better designed and doesn't need the tweaks.

Check out this Google search: 

[http://www.google.com/search?q=%22hdparm+for+sata%22&btnG=Search](http://www.google.com/search?q=%22hdparm+for+sata%22&btnG=Search)

---

