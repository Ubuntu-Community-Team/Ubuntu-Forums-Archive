---
title: "Block claimed for no reason"
date: 2009-03-04
forum: Hardware
---

### Post by ryanlutz on 2009-03-04
Every time I run fsck, I get an error (maybe warning?). It says Programming error? Block #xxxxx claimed for no reason. any idea how to fix this? I have tried running fsck but that does not seem to fix it. It does not seem to affect my data or ability to store files on the hard drive, but I want to head off any errors before they become worse.

```

fsck /dev/sda1 -f -y -v               
fsck 1.40.6 (09-Feb-2008)                              
e2fsck 1.40.6 (09-Feb-2008)                            
Pass 1: Checking inodes, blocks, and sizes             
Programming error?  block #33088 claimed for no reason in process_bad_block.
Programming error?  block #33090 claimed for no reason in process_bad_block.
Programming error?  block #33091 claimed for no reason in process_bad_block.
Programming error?  block #33092 claimed for no reason in process_bad_block.
Programming error?  block #33093 claimed for no reason in process_bad_block.
Programming error?  block #33094 claimed for no reason in process_bad_block.
Programming error?  block #33095 claimed for no reason in process_bad_block.
Programming error?  block #33097 claimed for no reason in process_bad_block.
Programming error?  block #33098 claimed for no reason in process_bad_block.
Programming error?  block #33099 claimed for no reason in process_bad_block.
Programming error?  block #33100 claimed for no reason in process_bad_block.
Programming error?  block #33101 claimed for no reason in process_bad_block.
Programming error?  block #33102 claimed for no reason in process_bad_block.
Programming error?  block #33103 claimed for no reason in process_bad_block.
Programming error?  block #33105 claimed for no reason in process_bad_block.
Programming error?  block #33106 claimed for no reason in process_bad_block.
Programming error?  block #33107 claimed for no reason in process_bad_block.
Programming error?  block #33108 claimed for no reason in process_bad_block.
Programming error?  block #33109 claimed for no reason in process_bad_block.
Programming error?  block #33110 claimed for no reason in process_bad_block.
Programming error?  block #33111 claimed for no reason in process_bad_block.
Programming error?  block #33113 claimed for no reason in process_bad_block.
Programming error?  block #33114 claimed for no reason in process_bad_block.
Programming error?  block #33115 claimed for no reason in process_bad_block.
Programming error?  block #33116 claimed for no reason in process_bad_block.
Programming error?  block #33117 claimed for no reason in process_bad_block.
Programming error?  block #33118 claimed for no reason in process_bad_block.
Programming error?  block #33119 claimed for no reason in process_bad_block.
Programming error?  block #33121 claimed for no reason in process_bad_block.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 3A: Optimizing directories
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

    33 bad blocks
   119 large files

  5144 regular files
   190 directories
     0 character device files
     0 block device files
     0 fifos
     0 links
  3869 symbolic links (490 fast symbolic links)
     0 sockets
------
  9203 files

```

---

