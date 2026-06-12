---
title: "recover external hard drive"
date: 2010-09-24
forum: Hardware
---

### Post by ehsaan_sh on 2010-09-24
Hi

My 500Gb external usb drive stopped working. I have tried many different routes but am afraid i might make it any worse than this. 

On windows it is recognized as an external drive but is not mounted (windows tries to reformat it then) 

the results so far:

disk utility on maverick:
shows it as 500G of empty space. Does creating a partition table there erase all the data?
SMART data: self test went through almost all the way and then failed. 15 bad sectors.
Warning (197) on current pending sector counts



$ sudo  fsck /dev/sdb1
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?


$ sudo testdisk
Disk /dev/sdb - 500 GB / 465 GiB - WD 5000BMV External
check_FAT: can't read FAT boot sector
Invalid FAT boot sector
 1 * FAT32 LBA                0   1  1 60799 254 63  976751937
 1 * FAT32 LBA                0   1  1 60799 254 63  976751937

---

### Post by CharlesA on 2010-09-24
I'd say the drive is hosed. You could format it in Windows and see if it completes, but if there was any data on it, it's probably lost.

Your other option is to run [badblocks]("http://linux.die.net/man/8/badblocks") on it, but that'll take a long time.

---

### Post by ehsaan_sh on 2010-09-24
it is extremely important to get my data (AKA my thesis) back. 

Saw somewhere that i can make an image of the data on the file using ddrescue but the image would be 500G large right?

trying badblocks now

---

### Post by Rasa1111 on 2010-09-24
i know someone who just hosed a 1TB external drive simply by 
"tripping over the cord"..
so he says. lol

 Now it just clicks and makes weird noises..
but is not recognized by anything. 

Hope you get your data back man. <3

---

