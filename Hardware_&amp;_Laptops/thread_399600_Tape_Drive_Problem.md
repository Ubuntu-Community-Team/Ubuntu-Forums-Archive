---
title: "Tape Drive Problem"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by Lexrst on 2007-04-02
Hello all!

I am trying to read some old 8mm Exabyte tapes with data presumeably written from/for Unix. The label says it's in unix tar format and that there are 4 files on the tape. Here is what happens when I try to list the 1st file's file-type:

[INDENT]user@pc-linux:~$ sudo mt -f /dev/nst0 status
drive type = Generic SCSI-2 tape
drive status = 335545344
sense key error = 0
residue count = 0
file number = 0
block number = 0
Tape block size 1024 bytes. Density code 0x14 (EXB-8200 (RLL 43245 bpi)).
Soft error count since last status=0
General status bits on (45010000):
BOT WR_PROT ONLINE IM_REP_EN
user@pc-linux:~$ sudo mt -f /dev/nst0 setblk 1024
user@pc-linux:~$ sudo file - < /dev/nst0
bash: /dev/nst0: Permission denied
user@pc-linux:~$ sudo tar tvf /dev/nst0
tar: /dev/nst0: Cannot read: Input/output error
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
user@pc-linux:~$ [/INDENT]

If I advance to the next file, I get the same result. I also get the same result with other (Linux tar) tapes. I am by no means a Linux expert, so I would appreciate any insight into what these errors are referring to and if there is a fix for my problem.

Thanks,
Leigh Johnson

---

