---
title: "Set FAT32 Cluster Size with mkdosfs/mkfs.fvfat/mkfs.dosfs ?"
date: 2008-08-28
forum: Hardware
---

### Post by aphirst on 2008-08-28
I am an avid user of Nintendo DS Flashcard technology; and have learned that "Larger FAT(32) Cluster sizes result in quicker random-access". Slow Random-Access causes some DS applications/games to freeze. In these circumstances, since the smallest files I'm dealing with are 512KB save files (40% of files, and 99% of space, is occupied by 5-to-100MB+ Files), "wasted space" isn't an issue.

I know that in Windows, the command to format a device to FAT32 with the largest available (to my knowledge) cluster size is:
```
FORMAT X: /FS:FAT32 /A:64K
```

Here in Linux-Land, things are different (and in almost all cases, better). But one thing snags me on the mkdosfs man page:
There are two options, -s, and -S. -s is sectors-per-cluster. -S is logical sector size.

My question is this: What command in linux is equivelant to the DOS command above: would it suffice/be reccommended to disregard the -s and set -S to 65536 ?

Thanks for the input: I don't have access to a Windows/DOS machine when I have access to my DS or my MicroSDHC. :D

---

### Post by az on 2008-08-28
> **aphirst said:**
> I am an avid user of Nintendo DS Flashcard technology; and have learned that "Larger FAT(32) Cluster sizes result in quicker random-access". Slow Random-Access causes some DS applications/games to freeze. In these circumstances, since the smallest files I'm dealing with are 512KB save files (40% of files, and 99% of space, is occupied by 5-to-100MB+ Files), "wasted space" isn't an issue.

I know that in Windows, the command to format a device to FAT32 with the largest available (to my knowledge) cluster size is:
```
FORMAT X: /FS:FAT32 /A:64K
```

Here in Linux-Land, things are different (and in almost all cases, better). But one thing snags me on the mkdosfs man page:
There are two options, -s, and -S. -s is sectors-per-cluster. -S is logical sector size.

My question is this: What command in linux is equivelant to the DOS command above: would it suffice/be reccommended to disregard the -s and set -S to 65536 ?

Thanks for the input: I don't have access to a Windows/DOS machine when I have access to my DS or my MicroSDHC. :D

Well, I don't know about performance, but the quote you mention only refers to cluster size and not block size.  Is would make sense that the command you want to try is:

sudo mkdosfs /dev/sdc1 -s 64 -F 32  

*Be sure to specify the correct device instead of "sdc1"*

---

### Post by aphirst on 2008-08-28
Thank you very much (!).
I had tried, funnily enough, this exact command (except for the -I that was needed to format the entire drive as FAT32); and it seemed to work smashing (even the random-access problems went away magically). It was just my "was that the correct way around the problem/would that have caused problems later on" uncertainty. At least now I have some confirmation that I did the right thing.

Again, thanks ( ^_^ ), and just in case you care: [[color=red]'Proof' that I had tried this command, and of my uncertainty as to its 'correctness':oops:[/color]](http://ezflash.sosuke.com/viewtopic.php?f=16&t=13003&p=56126#p56126)

---

### Post by evaldas on 2009-01-17
I would think that the proper command should be:
```
sudo mkdosfs /dev/sdc1 -s 128 -F 32
```
since the author wanted 64KB clusters.

And because -s means sectors-per-cluster and the sector is usually is 512 bytes, so that's why 128 sectors. And I guess the above command is equally the same as:
```
sudo mkdosfs /dev/sdc1 -s 128 -S 512 -F 32
```

And I'd like ask what tool can give me the information about FAT type (12, 16 or 32) and cluster sizes used on already formatted FAT partition.

---

### Post by Dwaalspoor98 on 2009-04-28
Late answer, I know but maybe helpful for other people: minfo is what you're looking for, you first need to assign a drive letter to your device in /etc/mtools.conf, after that you can use it for example like this:
$ sudo minfo -v d:

---

### Post by moli on 2010-01-09
**I've tested** my *DS Lite v5* + *Acekard v2.1* + *Akaio v1.5.1* 
with sector size (-S parameter) from 1024 bytes to 8192 bytes neither worked, only 512 byte sector worked. 
Maximum cluster size of 64 sectors works. 
So **maximum cluster size is 32768** bytes instead of the desired 524288 bytes (at which ~12MB Akaio took up 100MB).

---

