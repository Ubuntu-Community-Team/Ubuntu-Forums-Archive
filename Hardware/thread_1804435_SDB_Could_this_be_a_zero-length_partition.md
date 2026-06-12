---
title: "SDB: Could this be a zero-length partition?"
date: 2011-07-14
forum: Hardware
---

### Post by TonyDeWittePony on 2011-07-14
Hello everyone,

Coming from Fedora, I had a Web/Mail/SQL server with 2 hdd's. One (sda1) was the one with Fedora on, and all backups were on sdb1.
Now, I started having issues with SDA1, so I started copying files to SDB1. 2 weeks later I noticed similar issues, and started copying new back files to SDB1. But once I started doing this I lost connection with the server.
Turns out that (in rescue mode) that I couldn't access SDA anymore, it couldn't even read stored data on it, etc. It didn't show up in fdisk anymore either.

So after a lot of trying I asked to replace the disk and started installing Ubuntu 10.04 LTS on it. After having installed everything, I tried to restore one of the MySQL backups that was on the SDB disk, but halfway I started getting errors. I stopped the restore and did some other stuff that I wanted to take care of first (apache2 config etc.).
I then tried to reboot to be sure that that was working as well, and then the problems started. I couldn't access the server anymore, and in rescue mode (which is a live cd my host provides, it's a dedicated server btw.) I didn't see SDB anymore.
I told them this and now after they told me that they managed to get it back, I went into the rescue mode and tried to recover bad blocks with the e2fsck command.

```
8 root@rescuecd64 / # e2fsck -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?

```

```
root@rescuecd64 / # mke2fs -n /dev/sdb1
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122096000 blocks
6104800 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 102400000

```

Trying to restore this bad superblock doesn't work. I've tried for almost all of them:
```

1 root@rescuecd64 / # e2fsck -b 32768 -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
8 root@rescuecd64 / # e2fsck -b 98304 -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
8 root@rescuecd64 / #
8 root@rescuecd64 / # dumpe2fs -f /dev/sdb1 | grep -i superblock
dumpe2fs 1.41.3 (12-Oct-2008)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.
root@rescuecd64 / # e2fsck -f -b 32768 /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
8 root@rescuecd64 / # e2fsck -b 163840 -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
8 root@rescuecd64 / # e2fsck -b 229376 -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
8 root@rescuecd64 / # e2fsck -b 294912 -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
8 root@rescuecd64 / # e2fsck -b 819200 -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
8 root@rescuecd64 / # e2fsck -b 884736 -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
8 root@rescuecd64 / # e2fsck -b 1605632 -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
8 root@rescuecd64 / # e2fsck -b 2654208 -y -f -v /dev/sdb1
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?

```

What are the chances of TWO hard disks failing? Surely there must be something else wrong? Did a bad driver (which would be weird, since I didn't do any updates like that) screw both of my hard disks up in Fedora?

Also, I must note that when I tried to copy the backups from SDB1 to SDA1 (the new one). I got a read only (??) error, and some other I/O errors.

Just for information, I'll show fstab and mtab as well:
/etc/fstab
```
root@rescuecd64 /mnt # cat /mnt/sda/etc/fstab

/dev/sda1               /       ext3    noatime         0 1
/dev/sda2               none    swap    sw              0 0
#/dev/sdb1              /backup ext3    defaults        0 2

```
I commented sdb1 now out, just to see whether it does something at the restart. But I have no idea how this could be the problem.

/etc/mtab
```
1 root@rescuecd64 /mnt # cat /mnt/sda/etc/mtab
/dev/sda1 / ext3 rw,noatime 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
none /var/lib/ureadahead/debugfs debugfs rw,relatime 0 0

```
I haven't added the sdb here yet, but it was here in Fedora so that can't be the problem.

Edit: Oh and this is /var/log/messages when the problems emerged
```

Jul 14 11:59:07 pitwall kernel: [55258.256241] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 14 16:29:00 pitwall kernel: [71451.038942] ata2: hard resetting link
Jul 14 16:29:01 pitwall kernel: [71451.560117] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 14 16:29:06 pitwall kernel: [71456.562598] ata2: hard resetting link
Jul 14 16:29:06 pitwall kernel: [71457.090107] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 14 16:29:06 pitwall kernel: [71457.127577] ata2.00: disabled
Jul 14 16:29:06 pitwall kernel: [71457.127601] ata2: EH complete
Jul 14 16:29:06 pitwall kernel: [71457.127637] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.127640] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.127644] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 01 00 00
Jul 14 16:29:06 pitwall kernel: [71457.132863] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.132865] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.132868] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 59 ff 00 01 00 00
Jul 14 16:29:06 pitwall kernel: [71457.137626] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.137626] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.137626] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:06 pitwall kernel: [71457.144161] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.144163] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.144166] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:06 pitwall kernel: [71457.150233] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.150235] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.150238] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:06 pitwall kernel: [71457.156420] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.156422] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.156425] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:06 pitwall kernel: [71457.162572] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.162575] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.162578] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:06 pitwall kernel: [71457.168719] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.168721] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.168724] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:06 pitwall kernel: [71457.175008] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.175010] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.175013] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:06 pitwall kernel: [71457.181238] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.181240] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.181244] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:06 pitwall kernel: [71457.187377] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.187379] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.187382] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:06 pitwall kernel: [71457.193354] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:06 pitwall kernel: [71457.193356] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:06 pitwall kernel: [71457.193359] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
...
(the same lines over and over)
...
Jul 14 16:29:07 pitwall kernel: [71457.345981] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:07 pitwall kernel: [71457.345983] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:07 pitwall kernel: [71457.345986] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:07 pitwall kernel: [71457.348106] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:07 pitwall kernel: [71457.348108] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:07 pitwall kernel: [71457.348111] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:07 pitwall kernel: [71457.350251] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:29:07 pitwall kernel: [71457.350253] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:29:07 pitwall kernel: [71457.350256] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:29:08 pitwall kernel: 57.578483] end_request: I/O error, dev sdb, sector 52844799
...
And then it restarts with the same over and over, here it ends:
Jul 14 16:31:09 pitwall kernel: [71577.980577] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:31:09 pitwall kernel: [71577.980578] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:31:09 pitwall kernel: [71577.980580] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 16:31:09 pitwall kernel: [71577.981090] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 16:31:09 pitwall kernel: [71577.981091] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 16:31:09 pitwall kernel: [71577.981093] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 03 26 58 ff 00 00 08 00
Jul 14 19:06:09 pitwall kernel: [80879.980158] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 19:06:09 pitwall kernel: [80879.980161] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 19:06:09 pitwall kernel: [80879.980165] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 30 bf 00 00 10 00
Jul 14 19:06:09 pitwall kernel: [80879.983113] sd 1:0:0:0: [sdb] Unhandled error code
Jul 14 19:06:09 pitwall kernel: [80879.983115] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jul 14 19:06:09 pitwall kernel: [80879.983118] sd 1:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 30 87 00 00 08 00
Jul 14 19:06:09 pitwall kernel: [80879.986837] lost page write due to I/O error on sdb1
Jul 14 19:50:55 pitwall kernel: Kernel logging (proc) stopped.

```

If anyone can help, I'd be very thankful. Otherwise I'll just have lost a project I started in 2004 :(

---

### Post by psusi on 2011-07-14
You should use smartctl to check the SMART status of the drive for errors.  Also see if you can read it with dd if=/dev/sdb1 of=/dev/null count=8

---

### Post by TonyDeWittePony on 2011-07-14
I ran smartctl and it gave me this:
```
root@rescuecd64 / # smartctl -l selftest /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

2 root@rescuecd64 / # smartctl -l selftest -T permissive /dev/sdb
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Short INQUIRY response, skip product id
Device does not support Self Test logging
```

Can I just run that dd command? It won't mess up any files on that drive? I just need to be very sure as these are my last backups.

---

### Post by psusi on 2011-07-14
> **TonyDeWittePony said:**
> Can I just run that dd command? It won't mess up any files on that drive? I just need to be very sure as these are my last backups.

Yes; it just reads the first 8 sectors.

---

### Post by TonyDeWittePony on 2011-07-14
I suppose then that this isn't much better news:
```

6 root@rescuecd64 / # dd if=/dev/sdb1 of=/dev/null count=8
dd: reading `/dev/sdb1': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0,000305067 s, 0,0 kB/s

```

---

### Post by psusi on 2011-07-15
Yep, it is looking like the drive took a hike.  It might be a bad controller or cable.  Have you tried rebooting the machine?

---

### Post by TonyDeWittePony on 2011-07-15
They replaced the entire system except for the hard drives, and the same problems still emerge. I thought it was a bad controller, but looks like it isn't. I still can't comprehend how 2 separate hard drives crash within 24 hours, that's why I thought it was a bad controller.
Rebooting doesn't help really. Half of the time it means that no hard disk shows up, and the technicians need to work on the machine.

---

### Post by jiapei100 on 2012-08-16
Did you have this problem solved? I'm now having exactly the same issue as yours.


1) 
```
pei@pei-GA-870A-UD3:/dev$ ls -l sd*
brw-rw---- 1 root disk 8,  0 Aug 15 17:57 sda
brw-rw---- 1 root disk 8,  1 Aug 15 17:55 sda1
brw-rw---- 1 root disk 8,  2 Aug 15 17:57 sda2
brw-rw---- 1 root disk 8,  5 Aug 15 17:55 sda5
brw-rw---- 1 root disk 8,  6 Aug 15 17:57 sda6
brw-rw---- 1 root disk 8, 16 Aug 15 17:57 sdb
brw-rw---- 1 root disk 8, 17 Aug 15 17:55 sdb1
brw-rw---- 1 root disk 8, 48 Aug 15 18:18 sdd
brw-rw---- 1 root disk 8, 49 Aug 15 18:18 sdd1
brw-rw---- 1 root disk 8, 64 Aug 16 01:04 sde
```


2)
```
pei@pei-GA-870A-UD3:~/Desktop$ sudo dd if=/dev/sde of=/dev/null count=8
dd: reading `/dev/sde': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 16.2421 s, 0.0 kB/s
```


3)
```
pei@pei-GA-870A-UD3:~/Desktop$ sudo smartctl -d scsi -T permissive -a /dev/sde
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-29-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Vendor:               Generic 
Product:              Storage Device  
Revision:             0.00
User Capacity:        16,005,464,064 bytes [16.0 GB]
Logical block size:   512 bytes
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page

Error Counter logging not supported
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
Device does not support Self Test logging

```



Please, help....


Cheers
Pei

---

### Post by overdrank on 2012-08-16
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

