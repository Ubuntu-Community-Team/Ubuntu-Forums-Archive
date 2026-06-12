---
title: "Gutsy and sata drives missing (ide drive with sata adapter)"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by jonssoni on 2007-10-25
Okey.
I've used ubuntu since Dapper and it's the first time when I don't find any answers from any forum. Everything has worked just fine (expect my 9600 radeon sometimes...) but now when I upgraded Edgy to Gutsy I've got serial problems.

I've got four hard drives. All of them are ide -drives. Two of them are connected via ide-ports.
I've got Windows XP on the firstr drive and Ubuntu on the second. XP's nfts drive has worked well in Gutsy and I've been able to use files on that drive.

Two other drives are connected with ide to sata adapters to sata bus.
I hadn't any problems with Dapper or Edgy to mount or use these adapter connected hard drives. But now when I upgraded to Gutsy, these adapter connected drives won't mount. I don't even see  them with GParted.

I'm a beginner with hard drive and Linux knowledge. This is what I've done so far:

sudo mount -a shows: (i've translated finnish expressions to english)
```

mount: specialdevice /dev/disk/by-uuid/451E-9E53 does not exist
mount:specialdevice /dev/disk/by-uuid/451E-A6A1 does not exist
```

I expect that these are the two missing hard drives?

dmesg after```
 sudo mount -a
``` (this shows also when i start ubuntu in recovery mode)

```
 1305.889224]  =======================
[ 1305.889594] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[ 1305.889600] ata1.00: limiting speed to UDMA7:PIO5
[ 1306.392549] ata1: hard resetting port
[ 1307.439511] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1307.447506] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[ 1307.447542]  [<f89b60bb>] ata_hsm_move+0x16b/0x740 [libata]
[ 1307.447579]  [<c0124290>] process_timeout+0x0/0x10
[ 1307.447599]  [<f89ba577>] ata_pio_task+0x27/0xf0 [libata]
[ 1307.447617]  [<f89ba550>] ata_pio_task+0x0/0xf0 [libata]
[ 1307.447629]  [<c012a4f8>] run_workqueue+0x78/0x100
[ 1307.447641]  [<c012ace0>] worker_thread+0x0/0x100
[ 1307.447645]  [<c012ad7d>] worker_thread+0x9d/0x100
[ 1307.447651]  [<c012db20>] autoremove_wake_function+0x0/0x50
[ 1307.447658]  [<c012ace0>] worker_thread+0x0/0x100
[ 1307.447662]  [<c012d792>] kthread+0x42/0x70
[ 1307.447666]  [<c012d750>] kthread+0x0/0x70
[ 1307.447672]  [<c0105187>] kernel_thread_helper+0x7/0x10
[ 1307.447682]  =======================
[ 1307.448058] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[ 1307.950973] ata1: hard resetting port
```

then i tried sudo fdisk -l and it doesn't show my missing drives, dmesg gives me:

```
[ 1313.729645] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[ 1313.729652] ata1.00: limiting speed to UDMA7:PIO5
[ 1314.032784] ata2: soft resetting port
[ 1314.188643] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1314.188661] ata2: EH complete
```

I downloaded Gutsy 6.10 and burned it on cd but it won't boot.

What should I try next...? I wouldn't like to go and buy sata drives.... (maybe the best alternative..?) :)

EDIT: /etc/fstab gives:

```
jonsson@jonsson-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=6e8d8eaa-313b-432e-8c97-b57165f5a241 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5 -- converted during upgrade to edgy
UUID=f79ab9ab-0379-453c-96b5-ee608ac25a16 none swap sw 0 0
/dev/cdrom        /media/cdrom0   utf8,udf,iso9660 user,noauto     0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=451E-9E53 /media/Leffat vfat iocharset=iso8859-15,umask=000 0 0
# /dev/sdb1 -- converted during upgrade to edgy
UUID=451E-A6A1 /media/mp3 vfat iocharset=iso8859-15,umask=000 0 0
```

---

### Post by jonssoni on 2007-10-28
Anyone...? Anything...?

---

### Post by Helix. on 2007-10-29
I would really like an answer to this too...having close to the same problem.

---

### Post by rupierto on 2007-10-29
me too.
See: [http://ubuntuforums.org/showthread.php?t=594180](http://ubuntuforums.org/showthread.php?t=594180)
Still no resolve

---

### Post by 57on3d on 2008-02-14
I have the identical problem. I have a freshly installed gutsy system. formerly suse 10.2. I have 2 drives connected via sata and they are fine. I have another older drive that i used to back up my data prior to reformatting [connected to sata via an IDE adapter] this drive is still showing properly in the bios, but i am not able to see it AT ALL in gutsy. currently i have moved it to another test machine to access the data, but it is slow and inconvenient. i have tried several different settings in the bios, as there is an independent RAID bios that might be causing a conflict. but from what ive read here, im wasting my time.

---

### Post by JRoush on 2008-03-16
I am having a similar problem when attempting to boot ubuntu from the current version of the live cd.  I found a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153096") online, and if I'm reading it correctly it appears that initial versions of the Gutsy kernel have outstanding issues with IDE -> SATA adapters.  Doesn't help me much, but maybe it will help someone else.

---

### Post by Kraziejake on 2008-04-17
I am having the exact same problem.  I'm installing Ubuntu 7.10 (64-bit) on a SATA Raptor hard drive.  I have four IDE drives connected to SATA ports via Syba adapters.  Ubuntu does not seem to recognize them at all.  I know they work because when I boot to my Windows drive it recognizes them.  That said I can not tell what is going on in the backround when the computer is booting since as soon as I get passed the GRUB screen my screen goes black and does not show anything until the log-on screen (about 20 - 30 minutes later).  Has anyone heard if the new 8.04 release will support IDE to SATA adapters?  I am really anxious to drop Windows Vista.

---

### Post by subzero316 on 2008-04-18
This has been around for a while for few i know. Few say it goes after a kernel upgrade. Try reading this link it has a few good suggestions.[<<--Link-->>]("http://http://linuxmafia.com/faq/Hardware/sata.html")

---

