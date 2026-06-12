---
title: "SATA disk fails occasionally in Karmic"
date: 2010-01-22
forum: Hardware
---

### Post by zwaardmeester on 2010-01-22
*Ubuntu 9.10 Karmic, kernel 2.6.31-17-generic*

Hi all, 

i'm having huge trouble with a new harddisk of mine, I hope y'all can shed some light on the case. The problemmaker is an 1.5 TB Samsung F2 Ecogreen disk (SATA), and has been my data disk for over 3 months now. I formatted it into one ext4 partition, since I intend to be storing large files on it. 

The problem is that occasionally, about once a week, the disk stops operating completely! I can still access it in Nautilus, then it seems mounted as read-only and all files are missing (only the folderstructure is there). Fdisk stops recognizing it as  well, i.e. it's not in the output of "fdisk -l" anymore. 

The problem can sometimes be fixed by rebooting. In case the problem persists, I disconnect the disk from the motherboard, reboot&shutdown, then reconnect the disk. THis usually does the trick. 

The relevant dmesg output is below in the codeblock. 

Do i have to RMA this disk or is something deeper going on? My other disk is SATA as well and functions properly for over a year now. 

Thanks in advance!

```
[ 2504.916000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x80000 action 0x0
[ 2504.916033] ata2.00: BMDMA2 stat 0x6d0019
[ 2504.916038] ata2: SError: { 10B8B }
[ 2504.916048] ata2.00: cmd c8/00:08:5f:f6:43/00:00:00:00:00/e2 tag 0 dma 4096 in
[ 2504.916049]          res 51/04:00:66:f6:43/00:00:00:00:00/e2 Emask 0x1 (device error)
[ 2504.916053] ata2.00: status: { DRDY ERR }
[ 2504.916056] ata2.00: error: { ABRT }
[ 2504.924572] ata2.00: both IDENTIFYs aborted, assuming NODEV
[ 2504.924577] ata2.00: revalidation failed (errno=-2)
[ 2504.924591] ata2: hard resetting link
[ 2505.244061] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 2505.468436] ata2.00: configured for UDMA/100
[ 2505.468477] ata2: EH complete
[ 2506.030169] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2506.030175] ata2.00: BMDMA2 stat 0x6d0019
[ 2506.030185] ata2.00: cmd 25/00:c0:5f:80:f6/00:00:29:00:00/e0 tag 0 dma 98304 in
[ 2506.030187]          res 51/04:9f:80:80:f6/00:00:29:00:00/e0 Emask 0x1 (device error)
[ 2506.030191] ata2.00: status: { DRDY ERR }
[ 2506.030194] ata2.00: error: { ABRT }
[ 2506.052383] ata2.00: both IDENTIFYs aborted, assuming NODEV
[ 2506.052387] ata2.00: revalidation failed (errno=-2)
[ 2506.052397] ata2: hard resetting link
[ 2506.372062] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 2506.380382] ata2.00: both IDENTIFYs aborted, assuming NODEV
[ 2506.380386] ata2.00: revalidation failed (errno=-2)
[ 2511.372034] ata2: hard resetting link
[ 2511.692055] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 2511.708425] ata2.00: both IDENTIFYs aborted, assuming NODEV
[ 2511.708429] ata2.00: revalidation failed (errno=-2)
[ 2511.708434] ata2.00: disabled
[ 2511.708456] ata2: EH complete
[ 2511.708478] sd 1:0:0:0: [sdb] Unhandled error code
[ 2511.708481] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2511.708486] end_request: I/O error, dev sdb, sector 704020575
[ 2511.708515] sd 1:0:0:0: [sdb] Unhandled error code
[ 2511.708517] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2511.708521] end_request: I/O error, dev sdb, sector 29409599
[ 2511.708548] sd 1:0:0:0: [sdb] Unhandled error code
[ 2511.708550] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2511.708554] end_request: I/O error, dev sdb, sector 1464074367
[ 2511.708616] Aborting journal on device sdb1:8.
[ 2511.708644] sd 1:0:0:0: [sdb] Unhandled error code
[ 2511.708647] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2511.708650] end_request: I/O error, dev sdb, sector 1464074303
[ 2511.708654] __ratelimit: 3 callbacks suppressed
[ 2511.708658] Buffer I/O error on device sdb1, logical block 183009280
[ 2511.708661] lost page write due to I/O error on sdb1
[ 2511.708669] JBD2: I/O error detected when updating journal superblock for sdb1:8.
[ 2511.708706] sd 1:0:0:0: [sdb] Unhandled error code
[ 2511.708709] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2511.708713] end_request: I/O error, dev sdb, sector 704020575
[ 2511.708959] sd 1:0:0:0: [sdb] Unhandled error code
[ 2511.708963] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2511.708966] end_request: I/O error, dev sdb, sector 704020575
[ 2511.709017] sd 1:0:0:0: [sdb] READ CAPACITY(16) failed
[ 2511.709020] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2511.709024] sd 1:0:0:0: [sdb] Sense not available.
[ 2511.709059] sd 1:0:0:0: [sdb] READ CAPACITY failed
[ 2511.709062] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2511.709065] sd 1:0:0:0: [sdb] Sense not available.
[ 2511.709105] sd 1:0:0:0: [sdb] Write Protect is on
[ 2511.709108] sd 1:0:0:0: [sdb] Mode Sense: c8 60 82 e9
[ 2511.709123] sd 1:0:0:0: [sdb] Asking for cache data failed
[ 2511.709126] sd 1:0:0:0: [sdb] Assuming drive cache: write through
[ 2511.709133] sdb: detected capacity change from 1500301910016 to 0
[ 2511.709162] EXT4-fs error (device sdb1): __ext4_get_inode_loc: unable to read inode block - inode=1015809, block=3676192
[ 2511.711509] EXT4-fs error (device sdb1): __ext4_get_inode_loc: unable to read inode block - inode=1015810, block=3676192
[ 2511.711522] EXT4-fs (sdb1): previous I/O error to superblock detected
[ 3175.054073] EXT4-fs error (device sdb1): ext4_journal_start_sb: Detected aborted journal
[ 3175.054083] EXT4-fs (sdb1): Remounting filesystem read-only
[ 3175.923199] EXT4-fs error (device sdb1): ext4_find_entry: reading directory #1277954 offset 0
[ 3177.668763] EXT4-fs error (device sdb1): __ext4_get_inode_loc: unable to read inode block - inode=1015809, block=3676192
[ 3177.669254] EXT4-fs error (device sdb1): __ext4_get_inode_loc: unable to read inode block - inode=1015810, block=3676192
[ 3180.537726] EXT4-fs error (device sdb1): __ext4_get_inode_loc: unable to read inode block - inode=1015809, block=3676192
[ 3180.538339] EXT4-fs error (device sdb1): __ext4_get_inode_loc: unable to read inode block - inode=1015810, block=3676192
[ 3189.200805] EXT4-fs error (device sdb1): ext4_find_entry: reading directory #1081346 offset 0
```

---

### Post by zwaardmeester on 2010-01-22
```
leo@zwaardmeester:~$ sudo umount /media/SA150/
[sudo] password for leo: 
leo@zwaardmeester:~$ sudo mount /media/SA150/
mount: special device UUID=893e7339-8359-4ad1-9813-356e65a8cf84 does not exist

```

---

### Post by paulisdead on 2010-01-22
Try installing smartmontools and see what comes up with
smartctl --all /dev/sdX

The big thing to look for is what the SMART overall-health self-assessment says in the output.

You could also try running the manufacturer's disk test utility.  I'm not familiar with Samsung's, but normally you can get it as a bootable ISO on the manufacturer's website.  I'm pretty sure I've seen it included on the Ultimate Boot CD, as well.

If all checks out with the drive, how's your power supply?  I've seen similar behavior when the power supply wasn't able to keep up, and a drive spun down.  If you can get your hands on another to test it with, maybe give that a shot.  Maybe try another port or different sata controller if your motherboard has more than one.

---

### Post by zwaardmeester on 2010-01-23
Thank you for your reply Paul. I ran smartctl and the Palimpsest Disk Utility today, not giving any questionable result. The power supply should be sufficient as well, given that I had another disk before the Samsung, which was PATA, and never had any troubles with that one. The powersupply is of a good brand and of sufficient wattage.

I did not yet try the Samsung test utility, because i discovered something I wanted to try first. Namely, my motherboard is an Abit NF7-S v2, which is still socket A :) and dating back from the early 00s. The Bios was already at the newest version, but the SATA-controller Bios was not. I found an (non-official) updated Bios on the [NforcersHQ forum]("http://www.nforcershq.com/forum/nf7-nf7-s-nf7-v-v-2-0-2-0-1-0-bios-2-7-with-sata-bios-4284-t70849.html"), which I just installed in Windows using Abit Flashmenu. I hope this new Sata-controller bios, which is 6 versions and 2 years newer than the one i had, will get rid of the weird problem i was experiencing.

---

### Post by zwaardmeester on 2010-01-23
I marked this thread as "SOLVED" in order to no longer distract the good people of the forums, although i'm not 100% sure the problem has vanished, but I'm having good hope!

---

