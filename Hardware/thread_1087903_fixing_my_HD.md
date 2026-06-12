---
title: "fixing my HD"
date: 2009-03-05
forum: Hardware
---

### Post by Humans_Are on 2009-03-05
Hi,
I had two HDs one with windows xp and ubuntu 7.10, and one EXT2 HD for just storage. I reformatted and did a fresh install on the HD with the OSs. 

Now the storage HD is not working properly. It didn't show up in windows (probably because it is EXT2 and I didn't install fsdriver yet.). so anyway I tried to do Chkdsk on windows repair and it said it could not be repaired. 
I used an ubuntu live cd mounted the drive and I could see the files but couldn't use them. and also all of the folders were turned into files(?)... 

I ran 'badblocks -s-u' and 'fsck -f -y' on the HD but it didn't work... 

help.

I'm running badblocks again now and will try fsck again after that. 

thanks
-matt

---

### Post by Humans_Are on 2009-03-05
> ubuntu@ubuntu:~$ sudo fsck -lu /dev/hdb1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
read_bad_blocks_file: No such file or directory while trying to open u
ubuntu@ubuntu:~$ sudo badblocks /?
badblocks: No such file or directory while trying to determine device size
ubuntu@ubuntu:~$ sudo badblocks ?
badblocks: No such file or directory while trying to determine device size
ubuntu@ubuntu:~$ sudo badblocks -s -v /dev/hdb1
Checking blocks 0 to 199141707
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.
ubuntu@ubuntu:~$ sudo fsck -f -y /dev/hdb1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/hdb1: 41066/24903680 files (26.9% non-contiguous), 42337304/49785427 blocks
ubuntu@ubuntu:~$ 


i'm going to try chkdsk from windows repair again.

---

### Post by Humans_Are on 2009-03-05
I think it's fixed for now. 

chkdsk still didn't work it said it was unrecoverable...  so I rebooted into XP and the drive is working... and i'm currently copying the important stuff to another drive.

---

