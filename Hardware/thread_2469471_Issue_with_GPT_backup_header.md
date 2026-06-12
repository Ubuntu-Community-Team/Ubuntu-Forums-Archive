---
title: "Issue with GPT backup header"
date: 2021-11-30
forum: Hardware
---

### Post by hornetster on 2021-11-30
Having probs with the GPT header on an SSD in a laptop.
Have used gdisk to try and fix, but doesn't seem to be. The output when I run gdisk is:
```
GPT fdisk (gdisk) version 1.0.8

Type device filename, or press <Enter> to exit: /dev/sda
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!
Main header: OK
Backup header: ERROR
Main partition table: OK
Backup partition table: OK

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
```

Have already used gdisk, and run on /dev/sda, with options: 
r
d
e
v
w

Still getting the above message.
What am I doing wrong?
Thanks.

---

### Post by sudodus on 2021-11-30
I use a different sequence of commands for gdisk in the shellscript [gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix). You can use it as it is or borrow the sequence of commands and run them manually in gdisk. Good luck :-)

---

