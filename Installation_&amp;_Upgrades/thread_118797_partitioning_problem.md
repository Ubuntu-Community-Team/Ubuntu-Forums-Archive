---
title: "partitioning problem"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by lawcab on 2006-01-17
I have a PIII 
SCSI 9 GB 9 (disk 0)
SCSI 35 GB (disk 1)

I have my ubuntu installed on disk 0. But I forgot to partition disk 1 as a FAT 32 as I wish to share it as well with my windows box. 

Can anyone tell me is there an easy way to partition and format the other disk?

thanks,
law

---

### Post by Sef on 2006-01-17
> an anyone tell me is there an easy way to partition and format the other disk?

Use GParted from the Live CD and on one disk just make a FAT32 partition.  

Applications ---> System Tools ----> GParted

---

### Post by guy_smiley:) on 2006-01-17
[QUOTE=lawcab]I wish to share it as well with my windows box.[/QUOTE]
Is this another computer on a network? or windows installed on a different disk?

[QUOTE=Sef]Use GParted from the Live CD and on one disk just make a FAT32 partition.[/QUOTE]

Don't do this. There is a better option. Format as Ext2. If you are using Samba in Ubuntu, this should still allow you to share this over the network with your windows box. Otherwise, if windows is installed on the same computer, there is a driver that allows windows to read/write to ext2 partitions, quite handy actually.

---

### Post by lawcab on 2006-01-18
Actually the windows machine is on the network. So I can still partition and format it as an ubuntu drive and share it as a samba share?

Can you walk me on how to do that?

thanks,
law

---

### Post by guy_smiley:) on 2006-02-01
Sorry mate. Working on the mines for the past coupla weeks. There should be plenty of tutorials on how to use Samba on the web. Unfortunately, it can be a very long and arduous task if you do not know what you are doing. I tried it once before and couldn't be bothered, not to discourage you but I was only trialling it. When I get into the swing with Ubuntu in Feb/March, I should have Samba set up, and maybe who knows, more posts.

---

