---
title: "Need help debugging dd IO error - clone of HDD - ddrescue needed?"
date: 2022-07-21
forum: Hardware
---

### Post by steve234 on 2022-07-21
Morning all,

tldr; is my new, or old, hard drive toast? or am I doing something wrong? Is this a case for ddrescue? I'm on Lubuntu 20.04.4 LTS

I use a 1TB (/dev/sda) spinner for backup and archiving on my desktop PC. I do a lot of video editing (my scratch disk is an SSD). I have run out of space on the 1TB drive, so I bought a 4TB drive (dev/sde). My disks are set-up as so :

```
sda      8:0    0 931.5G  0 disk
&#9492;&#9472;sda1   8:1    0 931.5G  0 part
sde      8:64   0   3.7T  0 disk
&#9492;&#9472;sde1   8:65   0 931.5G  0 part
sdf      8:80   0 223.6G  0 disk
&#9492;&#9472;sdf1   8:81   0 223.6G  0 part /

```
(command run after error)
I am trying to clone the 1TB disk to the 4TB one (i'll extend the partition later with gparted). Both disks were unmounted then I ran:

```
sudo dd if=/dev/sda of=/dev/sde status=progress

```

I'm somewhat stumped by dd throwing an IO error after a measley 27GB:

```

28661154816 bytes (29 GB, 27 GiB) copied, 1132 s, 25.3 MB/s
dd: writing to '/dev/sde': Input/output error                                                                       
56030241+0 records in                                                                                               
56030240+0 records out                                                                                              
28687482880 bytes (29 GB, 27 GiB) copied, 1140.63 s, 25.2 MB/s 

```                                                    

I've looked on the usual places (stackexchange etc) and am somewhat confused about what I'm looking at. Particularly whether my dd command was wrong, or which disk the error is with.

Before I started I checked both drives with ```
smartctl 
```and neither reported any issues.

Dmesg output is as follows (sdc was an SD card I used loading a file to my 3D printer):

```
[ 1546.534520] sdc: detected capacity change from 0 to 7741440
[ 1546.540877]  sdc: sdc1
[ 1547.362260] FAT-fs (sdc1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[ 2064.339165] ata2.00: exception Emask 0x0 SAct 0x8000 SErr 0x0 action 0x0
[ 2064.339182] ata2.00: irq_stat 0x40000008
[ 2064.339189] ata2.00: failed command: READ FPDMA QUEUED
[ 2064.339193] ata2.00: cmd 60/08:78:20:f4:56/00:00:03:00:00/40 tag 15 ncq dma 4096 in
                        res 41/40:00:22:f4:56/00:00:03:00:00/40 Emask 0x409 (media error) <F>                       
[ 2064.339208] ata2.00: status: { DRDY ERR }
[ 2064.339213] ata2.00: error: { UNC }
[ 2064.341470] ata2.00: configured for UDMA/133
[ 2064.341495] sd 1:0:0:0: [sde] tag#15 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE cmd_age=1s
[ 2064.341503] sd 1:0:0:0: [sde] tag#15 Sense Key : Medium Error [current]
[ 2064.341508] sd 1:0:0:0: [sde] tag#15 Add. Sense: Unrecovered read error - auto reallocate failed
[ 2064.341513] sd 1:0:0:0: [sde] tag#15 CDB: Read(16) 88 00 00 00 00 00 03 56 f4 20 00 00 00 08 00 00
[ 2064.341517] blk_update_request: I/O error, dev sde, sector 56030242 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0                                                                                                                  
[ 2064.341545] ata2: EH complete
[ 2071.141758]  sde: sde1
[ 2078.363621] sdc: detected capacity change from 7741440 to 0
[ 2817.007979] perf: interrupt took too long (4410 > 4341), lowering kernel.perf_event_max_sample_rate to 45250
[ 2941.874281] apple 0005:05AC:0250.0005: unknown main item tag 0x0
[ 2941.875043] input: Keychron K8 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0/bluetooth/hci0/hci0:12/0005:05AC:0250.0005/input/input23
[ 2941.875606] apple 0005:05AC:0250.0005: input,hidraw3: BLUETOOTH HID v1.1b Keyboard [Keychron K8] on 00:16:a4:56:fb:5e
[ 4085.299208] ata2.00: exception Emask 0x0 SAct 0x400 SErr 0x0 action 0x0
[ 4085.299224] ata2.00: irq_stat 0x40000008
[ 4085.299230] ata2.00: failed command: READ FPDMA QUEUED
[ 4085.299234] ata2.00: cmd 60/08:50:20:f4:56/00:00:03:00:00/40 tag 10 ncq dma 4096 in
                        res 41/40:00:22:f4:56/00:00:03:00:00/40 Emask 0x409 (media error) <F>                       
[ 4085.299250] ata2.00: status: { DRDY ERR }
[ 4085.299255] ata2.00: error: { UNC }
[ 4085.301192] ata2.00: configured for UDMA/133
[ 4085.301214] sd 1:0:0:0: [sde] tag#10 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE cmd_age=1s
[ 4085.301221] sd 1:0:0:0: [sde] tag#10 Sense Key : Medium Error [current]
[ 4085.301226] sd 1:0:0:0: [sde] tag#10 Add. Sense: Unrecovered read error - auto reallocate failed
[ 4085.301232] sd 1:0:0:0: [sde] tag#10 CDB: Read(16) 88 00 00 00 00 00 03 56 f4 20 00 00 00 08 00 00
[ 4085.301235] blk_update_request: I/O error, dev sde, sector 56030242 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0                                                                                                                  
[ 4085.301265] ata2: EH complete
[ 4091.760642]  sde: sde1

```

the presence of ```
Unrecovered read error
``` makes me think that sda is not a happy disk? Is that right, it works fine, and tested ok?

---

### Post by sudodus on 2022-07-21
- If there are some sectors, that are hard to read, ddrescue is much better than dd for that purpose. Please read the tutorial 
```

info ddrescue

```
before you start working with it. There are good examples and good descriptions of how to use a logfile in order to use several runs, a fast run where things are easy and a slow run, where it is difficult to read.

- But you might also check/fix the file systems with
```

sudo e2fsck -f /dev/sdxn

```
and after that you can copy the whole directory structure with all the files with something like
```

sudo rsync -Havn source/ target/

```
between the mountpoints of the file systems on the two drives.

If there are bad sectors 'between' files (so not affecting them) this will work well. Maybe a few files are damaged (with bad sectors in them), but if you are lucky, you have backup copies of them somewhere else.

---

### Post by steve234 on 2022-07-21
Thanks,

Sorry was being a dummy getting "bad superblock" issues because I didn't add a drive letter

Will report back

---

### Post by steve234 on 2022-07-21
So ddrescue worked at a drive level - no issues - the few files I have tried were fine:

```

sudo ddrescue /dev/sda /dev/sdb --force  status=progress
GNU ddrescue 1.23
Press Ctrl-C to interrupt
     ipos:  741829 MB, non-trimmed:        0 B,  current rate:  70516 kB/s rate:  74973 kB/s MB, non-scraped:        0 B,  average rate:  86300 kB/s
     opos:  741829 MB, non-scraped:        0 B,  average rate:       0 B/s rate:  86299 kB/s MB,   bad areas:        0,        run time:  2h 23m 15s
non-tried:  258375 MB,  bad-sector:        0 B,    error time:         58m rate:       0 B/s            time since last successful read:          0s
     ipos:  741910 MB, non-trimmed:        0 B,  current rate:  81395 kB/s                                      
     opos:  741910 MB, non-scraped:        0 B,  average rate:  86298 kB/s                                      
non-tried:  258293 MB,  bad-sector:        0 B,    error rate:       0 B/s                                      
     ipos:  741983 MB, non-trimmed:        0 B,  current rate:  72613 kB/s                                      
     opos:  741983 MB, non-scraped:        0 B,  average rate:  86297 kB/s                                      
non-tried:  258221 MB,  bad-sector:        0 B,    error rate:       0 B/s                                      
     ipos:    1000 GB, non-trimmed:        0 B,  current rate:  34168 kB/s     opos:    1000 GB, non-scraped:        0 B,  average rate:  77033 kB/s
non-tried:        0 B,  bad-sector:        0 B,    error rate:       0 B/s  rescued:    1000 GB,   bad areas:        0,        run time:  3h 36m 23s
pct rescued:  100.00%, read errors:        0,  remaining time:         n/a                              time since last successful read:         n/a

```

The new drive is still very noisy, like it's constantly seeking whether it's being accessed or not.

Now need to need to use gdisk to free myself of the MSDos MBR - fingers crossed

---

### Post by oldfred on 2022-07-21
If old drive is MBR and new drive over 2TB, then it has to be gpt.
You then cannot clone MBR to gpt. Or you just convert new drive to same size as old drive as MBR.

Better to create gpt partitions on new drive with gparted or gdisk and use rsync to copy data.

---

### Post by steve234 on 2022-07-21
Thanks, I think that's what sudodus was alluding to.

After using gdisk, and resizing the main partition, it seems all is ok. 

Now just need to update Unison (which syncs to my SSD) and add the uid to (I forget where) to get automount.

Hopefully I won't get any issues down the line.

---

