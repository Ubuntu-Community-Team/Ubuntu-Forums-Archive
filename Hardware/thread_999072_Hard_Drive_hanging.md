---
title: "Hard Drive hanging"
date: 2008-12-01
forum: Hardware
---

### Post by occams_beard on 2008-12-01
I'm hoping someone can help me because this is driving me crazy...

I'm having a seemingly random issue with my hard drive.  Previously I was running Hardy, and every once in a while everything would freeze and the hard drive would repeatedly make a “seek” noise.  This would mostly occur during a cold boot, but it also happened while I was using the system, requiring a hard reboot.  

I've since upgraded to Intrepid, and everything has been great for the last couple weeks, however this morning the freezing hard drive problem returned. My desktop froze for about 20 seconds, and the hard drive made the seek noise. 

I have no idea what any of this means, but here's the relevant log data for when the problem occurred...

```

Dec  1 11:22:28 pandora kernel: [  735.000049] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec  1 11:22:28 pandora kernel: [  735.000061] ata1.00: cmd 35/00:08:8d:94:c9/00:00:14:00:00/e0 tag 0 dma 4096 out
Dec  1 11:22:28 pandora kernel: [  735.000063]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Dec  1 11:22:28 pandora kernel: [  735.000067] ata1.00: status: { DRDY }
Dec  1 11:22:28 pandora kernel: [  735.000075] ata1: hard resetting link
Dec  1 11:22:33 pandora kernel: [  740.512011] ata1: link is slow to respond, please be patient (ready=0)
Dec  1 11:22:38 pandora kernel: [  745.048015] ata1: SRST failed (errno=-16)
Dec  1 11:22:38 pandora kernel: [  745.058743] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  1 11:22:38 pandora kernel: [  745.058753] ata1: link online but device misclassified, retrying
Dec  1 11:22:38 pandora kernel: [  745.058759] ata1: hard resetting link
Dec  1 11:22:43 pandora kernel: [  750.572018] ata1: link is slow to respond, please be patient (ready=0)
Dec  1 11:22:48 pandora kernel: [  755.108014] ata1: SRST failed (errno=-16)
Dec  1 11:22:48 pandora kernel: [  755.118767] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  1 11:22:48 pandora kernel: [  755.118783] ata1: link online but device misclassified, retrying
Dec  1 11:22:48 pandora kernel: [  755.118790] ata1: hard resetting link
Dec  1 11:22:53 pandora kernel: [  760.632020] ata1: link is slow to respond, please be patient (ready=0)
Dec  1 11:23:23 pandora kernel: [  790.152010] ata1: SRST failed (errno=-16)
Dec  1 11:23:23 pandora kernel: [  790.162741] ata1: SATA link down (SStatus 21 SControl 300)
Dec  1 11:23:28 pandora kernel: [  795.160026] ata1: hard resetting link
Dec  1 11:23:29 pandora kernel: [  796.532061] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec  1 11:23:29 pandora kernel: [  796.565352] ata1.00: configured for UDMA/133
Dec  1 11:23:29 pandora kernel: [  796.565365] ata1: EH complete
Dec  1 11:23:29 pandora kernel: [  796.565868] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Dec  1 11:23:29 pandora kernel: [  796.566088] sd 0:0:0:0: [sda] Write Protect is off
Dec  1 11:23:29 pandora kernel: [  796.566098] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec  1 11:23:29 pandora kernel: [  796.566482] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```


Now, I'm not sure if this is related... but after this occurred, I booted the live cd and tried to fsck my partition. However, gparted complained saying “The kernel is unable to re-read the partition tables on the following devices: - /dev/sda.  Then when I tried to check the partition with gparted I got the following output:

```

check filesystem on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( ERROR )
     	
e2fsck -f -y -v /dev/sda5
     	

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

e2fsck 1.41.3 (12-Oct-2008)
e2fsck: No such file or directory while trying to open /dev/sda5 

```

I would suspect the drive is failing, however, I also dual boot with Vista, and I don't have any problems at all.  In addition, I've ran countless diagnostic tools on the drive and they all report that it's fine.  Also the drive's SMART data looks ok, from what I can gather.

Can anyone shed some light on this?  I'd love to know what the log is saying, and how I can run a fsck on my ext3 partition and see the results.

My system specs are:
Dell Inspiron 530 desktop.  Intel Q6600 Core 2 Quad  w 3GB of RAM.  Western Digital 500 GB SATA drive.

---

### Post by occams_beard on 2008-12-02
bump. Anyone?

---

### Post by cubeist on 2008-12-02
I am not a HDD expert, but you have a great user name, so I will try to help!  Anyway I have the 320Gb version of the same WD drive running on ibex and it works great, and it worked great on hardy as well.  But, some people have a similar problem, see here:

[http://ubuntuforums.org/showthread.php?t=736216]("http://ubuntuforums.org/showthread.php?t=736216")

and it appears that it is a jumper issue, see the last post here:

[http://fixunix.com/ubuntu/397814-cant-install-ubuntu-8-04-lts.html]("http://fixunix.com/ubuntu/397814-cant-install-ubuntu-8-04-lts.html")

---

