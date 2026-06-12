---
title: "Damaged Drive?"
date: 2008-10-21
forum: General Help
---

### Post by mewejo on 2008-10-21
Hey...

I have a 1tb Drive mounted on my Ubuntu 8.04 Server...

When I access the drive with Samba through XP or Mac, its REALLY SLOW.

Until today, there was no screen attatched to the server, not there is, and I saw loads of errors when I tried to open the drive.

It opens, but its just really slow.

Here are the logs from /var/log/kern.log


> Oct 21 18:52:10 ubuntu-server kernel: [  465.197784] ata2: EH complete
Oct 21 18:52:10 ubuntu-server kernel: [  465.197796] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=60874753, block=243499010
Oct 21 18:52:10 ubuntu-server kernel: [  465.198954] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Oct 21 18:52:10 ubuntu-server kernel: [  465.199329] sd 1:0:0:0: [sdb] Write Protect is off
Oct 21 18:52:10 ubuntu-server kernel: [  465.199333] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct 21 18:52:10 ubuntu-server kernel: [  465.199350] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 21 18:52:10 ubuntu-server kernel: [  465.199369] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Oct 21 18:52:10 ubuntu-server kernel: [  465.199379] sd 1:0:0:0: [sdb] Write Protect is off
Oct 21 18:52:10 ubuntu-server kernel: [  465.199382] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct 21 18:52:10 ubuntu-server kernel: [  465.199396] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


Any ideas?


Obviousy, if I need to frmat the drive, I NEED to keep all the info on it, as its very important to business.

Thanks in advance.

Josh

Age 16

---

### Post by mewejo on 2008-10-21
Bad grammar there, I dont want to format the drive but if push comes to shuv, then I can try and back it all up onto a 500gb drive in the server. But I dont know how to do that :(

Regards,

Josh

---

