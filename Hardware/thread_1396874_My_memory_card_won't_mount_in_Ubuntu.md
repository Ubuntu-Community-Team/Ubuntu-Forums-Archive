---
title: "My memory card won't mount in Ubuntu"
date: 2010-02-02
forum: Hardware
---

### Post by kixdrummond on 2010-02-02
I am using Ubuntu 9.10 and I can't get my memory card to be read. This is what it says when I try to read it(I have attached a screenshot):

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



Can anyone tell me what is wrong/ how I can fix it? It would be extremely helpful. Thanks!

---

### Post by efflandt on 2010-02-02
So what does the tail end of **dmesg** (typed in a terminal) show after you plug it in?  What type of memory and/or memory card reader?  What filesystem is on it, or did you unplug it earlier while something may have been still writing to it (in Windows or Linux)?  Does it work on any other computer/OS?

When it is connected does it show up in **sudo fdisk -l** (small L)?

Older memory card readers (or laptop memory slots) might not handle "fast" SD larger than 2 GB or SDHC.

---

### Post by kixdrummond on 2010-02-03
> **efflandt said:**
> So what does the tail end of **dmesg** (typed in a terminal) show after you plug it in?  What type of memory and/or memory card reader?  What filesystem is on it, or did you unplug it earlier while something may have been still writing to it (in Windows or Linux)?  Does it work on any other computer/OS?

When it is connected does it show up in **sudo fdisk -l** (small L)?

Older memory card readers (or laptop memory slots) might not handle "fast" SD larger than 2 GB or SDHC.

Do I have to enter "demsg" into terminal? It works on all computers (Ubuntu and Windows) but mine. It was working earlier but does not now.

---

### Post by kixdrummond on 2010-02-08
> **efflandt said:**
> So what does the tail end of **dmesg** (typed in a terminal) show after you plug it in?  What type of memory and/or memory card reader?  What filesystem is on it, or did you unplug it earlier while something may have been still writing to it (in Windows or Linux)?  Does it work on any other computer/OS?

When it is connected does it show up in **sudo fdisk -l** (small L)?

Older memory card readers (or laptop memory slots) might not handle "fast" SD larger than 2 GB or SDHC.

[60119.598337] sd 7:0:0:0: [sdb] Write Protect is off
[60119.598341] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
[60119.598344] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[60119.614081] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[60119.614088]  sdb: sdb1
[60119.635110] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[60119.635121] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[60120.811102] UDF-fs: No anchor found
[60120.811111] UDF-fs: Rescanning with blocksize 2048
[60120.927105] UDF-fs: No anchor found
[60120.927112] UDF-fs: No partition found (1)
[60121.274104] ISOFS: Unable to identify CD-ROM format.

---

