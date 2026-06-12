---
title: "Ubuntu disk issue (mdadm marks it as F)"
date: 2016-01-05
forum: Hardware
---

### Post by Stefanvds on 2016-01-05
i'm having some issues with my raid 6. two disks dropped out a few days ago, the e-mail failed, and then one day ago another disk dropped.

there must be some connection issue or something with the raid card.

anyway, when i recreate the array with the last 4 disks, all seems OK.

that is untill i add a spare (one of the previously DCd disks)

after a minute of rebuilding the array, sdb drops out, marked as F

log shows: 

dmesg | grep error


```

[37830.676226] Add. Sense: Unrecovered read error
[37830.676233] end_request: critical medium error, dev sdb, sector 1264024
[37830.676240] md/raid:md6: read error not correctable (sector 1263984 on sdb1).
[37830.676243] md/raid:md6: read error not correctable (sector 1263992 on sdb1).
[37830.676244] md/raid:md6: read error not correctable (sector 1264000 on sdb1).
[37830.676244] md/raid:md6: read error not correctable (sector 1264008 on sdb1).
[37830.676245] md/raid:md6: read error not correctable (sector 1264016 on sdb1).
[37830.676246] md/raid:md6: read error not correctable (sector 1264024 on sdb1).
[37830.676247] md/raid:md6: read error not correctable (sector 1264032 on sdb1).
[37830.676248] md/raid:md6: read error not correctable (sector 1264040 on sdb1).
[37830.676249] md/raid:md6: read error not correctable (sector 1264048 on sdb1).
[37830.676250] md/raid:md6: read error not correctable (sector 1264056 on sdb1).
[37834.133828] Add. Sense: Unrecovered read error
[37834.133835] end_request: critical medium error, dev sdb, sector 1264024
[37834.140291] Buffer I/O error on device md6, logical block 976257024
[37834.140292] lost page write due to I/O error on md6
[37834.242495] Buffer I/O error on device md6, logical block 0
[37834.242498] lost page write due to I/O error on md6
[37834.242514] EXT4-fs error (device md6): ext4_journal_check_start:56: Detected aborted journal
[37834.242520] EXT4-fs (md6): previous I/O error to superblock detected
[37834.253682] Buffer I/O error on device md6, logical block 0
[37834.253684] lost page write due to I/O error on md6
[37836.037574] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 202900002, block 0)
[37836.037716] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 202900010, block 0)
[37836.037836] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 202900014, block 0)
[37836.037950] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 202899986, block 0)
[37836.038061] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 202900018, block 0)
[37836.038169] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 202899994, block 0)
[37836.038283] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 202900060, block 0)
[37836.153231] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 202900022, block 0)
[37836.313611] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729505: block 805830730: comm java: unable to read itable block
[37836.313615] EXT4-fs (md6): previous I/O error to superblock detected
[37836.313814] Buffer I/O error on device md6, logical block 0
[37836.313815] lost page write due to I/O error on md6
[37836.313850] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729505: block 805830730: comm java: unable to read itable block
[37836.313851] EXT4-fs (md6): previous I/O error to superblock detected
[37836.313857] Buffer I/O error on device md6, logical block 0
[37836.313860] lost page write due to I/O error on md6
[37836.328577] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 100794627, block 0)
[37836.366532] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #203555482: block 1628438601: comm java: unable to read itable block
[37836.366535] EXT4-fs (md6): previous I/O error to superblock detected
[37836.366545] Buffer I/O error on device md6, logical block 0
[37836.366547] lost page write due to I/O error on md6
[37836.366620] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #203555482: block 1628438601: comm java: unable to read itable block
[37836.366621] EXT4-fs (md6): previous I/O error to superblock detected
[37836.366625] Buffer I/O error on device md6, logical block 0
[37836.366626] lost page write due to I/O error on md6
[37836.366910] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #203555482: block 1628438601: comm java: unable to read itable block
[37836.366911] EXT4-fs (md6): previous I/O error to superblock detected
[37836.366916] Buffer I/O error on device md6, logical block 0
[37836.366918] lost page write due to I/O error on md6
[37836.366982] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #203555466: block 1628438600: comm java: unable to read itable block
[37836.366983] EXT4-fs (md6): previous I/O error to superblock detected
[37836.366988] Buffer I/O error on device md6, logical block 0
[37836.366989] lost page write due to I/O error on md6
[37836.367043] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #203555466: block 1628438600: comm java: unable to read itable block
[37836.367044] EXT4-fs (md6): previous I/O error to superblock detected
[37836.367047] Buffer I/O error on device md6, logical block 0
[37836.367048] lost page write due to I/O error on md6
[37836.367160] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #203555466: block 1628438600: comm java: unable to read itable block
[37836.367162] EXT4-fs (md6): previous I/O error to superblock detected
[37836.367217] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #203555547: block 1628438605: comm java: unable to read itable block
[37836.367273] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #203555547: block 1628438605: comm java: unable to read itable block
[37836.385648] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 203030954, block 0)
[37839.798732] EXT4-fs (md6): previous I/O error to superblock detected
[37839.799112] quiet_error: 312 callbacks suppressed
[37839.799115] Buffer I/O error on device md6, logical block 0
[37839.799117] lost page write due to I/O error on md6
[37839.799357] EXT4-fs (md6): previous I/O error to superblock detected
[37839.799382] Buffer I/O error on device md6, logical block 0
[37839.799384] lost page write due to I/O error on md6
[37840.571181] EXT4-fs (md6): previous I/O error to superblock detected
[37840.571517] Buffer I/O error on device md6, logical block 0
[37840.571521] lost page write due to I/O error on md6
[37840.571774] EXT4-fs (md6): previous I/O error to superblock detected
[37840.571800] Buffer I/O error on device md6, logical block 0
[37840.571803] lost page write due to I/O error on md6
[37841.134033] EXT4-fs (md6): previous I/O error to superblock detected
[37841.134406] Buffer I/O error on device md6, logical block 0
[37841.134410] lost page write due to I/O error on md6
[37841.134556] EXT4-fs (md6): previous I/O error to superblock detected
[37841.134566] Buffer I/O error on device md6, logical block 0
[37841.134568] lost page write due to I/O error on md6
[37841.134740] EXT4-fs (md6): previous I/O error to superblock detected
[37841.134749] Buffer I/O error on device md6, logical block 0
[37841.134750] lost page write due to I/O error on md6
[37841.134807] EXT4-fs (md6): previous I/O error to superblock detected
[37841.134813] Buffer I/O error on device md6, logical block 0
[37841.134813] lost page write due to I/O error on md6
[37841.134970] EXT4-fs (md6): previous I/O error to superblock detected
[37841.134974] Buffer I/O error on device md6, logical block 0
[37841.134975] lost page write due to I/O error on md6
[37841.135181] EXT4-fs (md6): previous I/O error to superblock detected
[37841.135186] Buffer I/O error on device md6, logical block 0
[37841.135187] lost page write due to I/O error on md6
[37841.956564] EXT4-fs error: 323 callbacks suppressed
[37841.956568] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729142: block 805830707: comm java: unable to read itable block
[37841.956865] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729142: block 805830707: comm java: unable to read itable block
[37841.956940] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729141: block 805830707: comm java: unable to read itable block
[37841.956998] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729141: block 805830707: comm java: unable to read itable block
[37841.957141] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729141: block 805830707: comm java: unable to read itable block
[37841.957337] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729135: block 805830706: comm java: unable to read itable block
[37841.957396] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729135: block 805830706: comm java: unable to read itable block
[37841.957513] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729135: block 805830706: comm java: unable to read itable block
[37841.957570] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729136: block 805830706: comm java: unable to read itable block
[37841.957621] EXT4-fs error (device md6): __ext4_get_inode_loc:3979: inode #100729136: block 805830706: comm java: unable to read itable block
[37842.008294] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 203555886, block 0)
[37842.008330] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 100794762, block 0)
[37842.008352] EXT4-fs warning (device md6): __ext4_read_dirblock:901: error reading directory block (ino 203424011, block 0)


```

when i check the SMART, it says Disk OK, 2 bad sectors.

is this disk for RMA? any things i can scan/debug/... for bad sectors.

---

### Post by weatherman2 on 2016-01-05
Install GSmartControl and use it to run tests on your hard drives.  Run the short test first; if that passes, run the extended test (may take hours).  Two bad sectors could cause failures - even one bad sector could.

In the S.M.A.R.T. Attributes, see which type of sector error you have.  Reallocated sectors are not catastrophic, but a pending sector (sector that cannot be read) could be.

---

