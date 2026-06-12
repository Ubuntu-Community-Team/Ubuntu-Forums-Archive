---
title: "SD Card formatted to ext2 will not mount after reboot"
date: 2009-05-25
forum: Hardware
---

### Post by nucleocide on 2009-05-25
I recently installed the Ubuntu Netbook Remix on my eeepc 900, and it's 1000x better than the xandros thing that it came with... Despite the initial headache of having to fix the windowmanager and panels once switching to the Classic Desktop mode... But thats behind us now lol.

I just purchased a 4GB SD card with the intent of permanently using it for storage. I opted to format it using ext2 since I'd hopefully never take the card out and move it to a windows box. The card formatted and mounted fine, and I was able to write a lot of files to it, however upon reboot I am unable to access the files or properly mount the drive.

Here's the relevant syslog output:

```

May 25 20:31:13 phobos kernel: [ 1386.917364] sd 2:0:0:0: [sdb] 7995392 512-byte hardware sectors: (4.09 GB/3.81 GiB)
May 25 20:31:13 phobos kernel: [ 1386.917850] sd 2:0:0:0: [sdb] Write Protect is off
May 25 20:31:13 phobos kernel: [ 1386.917856] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
May 25 20:31:13 phobos kernel: [ 1386.917861] sd 2:0:0:0: [sdb] Assuming drive cache: write through
May 25 20:31:13 phobos kernel: [ 1386.918473] sd 2:0:0:0: [sdb] 7995392 512-byte hardware sectors: (4.09 GB/3.81 GiB)
May 25 20:31:13 phobos kernel: [ 1386.918970] sd 2:0:0:0: [sdb] Write Protect is off
May 25 20:31:13 phobos kernel: [ 1386.918975] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
May 25 20:31:13 phobos kernel: [ 1386.918979] sd 2:0:0:0: [sdb] Assuming drive cache: write through
May 25 20:31:13 phobos kernel: [ 1386.918987]  sdb: sdb1
May 25 20:31:13 phobos kernel: [ 1387.405350] EXT2-fs error (device sdb1): ext2_check_descriptors: Block bitmap for group 1 not in group (block 0)!
May 25 20:31:13 phobos kernel: [ 1387.405365] EXT2-fs: group descriptors corrupted!
```

Here's the cryptic popup ubuntu gives me when the GUI tries to mount it:

```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,       missing codepage or helper program, or other error       In some cases useful info is found in syslog - try     dmesg | tail or so

```

Any clue on how I can properly mount this device to the proper location? Prefferably so that it is done automatically upon all boots?

---

### Post by nucleocide on 2009-05-25
Ok, so I did an fsck on the drive, and was able to mount it. Apparently it isn't being umounted properly, so as long as I'm manually umounting it before rebooting the system there isn't an issue...

---

### Post by Dark_Stang on 2009-05-25
I'd try to run an fsck on it and see what happens.

---

