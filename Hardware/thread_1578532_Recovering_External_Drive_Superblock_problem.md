---
title: "Recovering External Drive: Superblock problem"
date: 2010-09-20
forum: Hardware
---

### Post by spegru on 2010-09-20
I'm having a problem mounting an external drive due to corruption.
I have read about superblocks and alternate superblocks but I can't make the mounting process work. There appears to be a reserve superblock at 1605632


So I tried this:

 sudo mount -t ext3 -b 1605632 /dev/sdb1 /sdb1-backup


But when I execute the command I get loads of error messages about the usage of the Mount command - as if I just got the syntax wrong

Where is my error?

thanks

---

### Post by willPower on 2010-09-20
dmesg usually shows you why your mount commands aren't working. Try posing the output of ```
$ dmesg|tail -30
``` immediately following your failed mount command.

---

### Post by spegru on 2010-09-20
Thanks. I tried that but the messages were not that helpful.
I know the area of the problem though becuase the first part of the main error message is "mount: invalid option -- 'b'"

What I am trying to do is mount the disc using a reserve superblock  but I cant work out the correct command

---

### Post by spegru on 2010-09-21
I got the syntax to work at last with the -o switch as well as sb=.......
It looks like this:

sudo mount -t ext3 -o sb=1605632 /dev/sdb1 /sdb1-backup/image/

where 1605632 is the duplicate superblock, /sdb1-backup....etc is the location you have chosen to mount it and sdb1 is the name of the partition you want to  mount

---

### Post by spegru on 2010-09-26
Still struggling with this

Whatever I do with fsck I keep getting this error

Pass 2: Checking directory structure
Error reading block 1544 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? 

Doesn't seem to matter what I do about superblocks etc

Any Ideas?

---

### Post by IcarusR on 2010-09-26
Not really got any help on this. 
But I hope you have a backup of the drive, I would take an image of it before doing anything, then if you accidentally screw it up you have not lost all data.

Just my 2p worth of friendly advice.

---

### Post by IcarusR on 2010-09-26
Check out this page...

[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/]("http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/")

I think you should use fsck -b on the unmounted file system to repair it, then mount it as normal.

---

