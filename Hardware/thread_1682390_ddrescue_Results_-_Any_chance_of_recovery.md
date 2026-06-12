---
title: "ddrescue Results - Any chance of recovery?"
date: 2011-02-05
forum: Hardware
---

### Post by MrWylbur on 2011-02-05
Last week I bought a new laptop hard drive and used ddrescue to replicate the disk contents to the new disk.  I used my desktop machine, and copied the ddrescue command to the terminal.  Needless to say, that did not go well, since the command contained the locations of my two existing drives - rather than the target and destination laptop drive locations.  

The ddrescue command ran for just a second until I realised what happened, and I shut down the machine to stop it.  (And I mean a second!)

I have the disk installed, and ubuntu sees the volume, but can't mount it.  When attempting the mount, the help screen suggested the command:
```
dmesg | tail
```
The question is, what does the output from that command mean?  Can I salvage the contents of the drive?

[  860.330914] scsi 2:0:0:0: Direct-Access     ATA      ST31000333AS     CC1F PQ: 0 ANSI: 5
[  860.331250] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  860.331322] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[  860.331418] sd 2:0:0:0: [sdb] Write Protect is off
[  860.331426] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  860.331465] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  860.331746]  sdb: sdb1 sdb2 < >
[  860.395581] sd 2:0:0:0: [sdb] Attached SCSI disk
[  875.712513] JBD: no valid journal superblock found
[  875.712523] EXT4-fs (sdb1): error loading journal

Your helpful reply would be most appreciated!

---

