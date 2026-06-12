---
title: "Fill tape with data using tar"
date: 2009-02-09
forum: Hardware
---

### Post by geohei on 2009-02-09
Hi.

I have a problem with a streamer (HP C7438A) connected to the Adaptec ASC 19160 SCSI card. For troubleshooting purpose, I would like to use Ubuntu to fill up the DAT72 tape (native 36 GB) to the top with data. I only have a very small Ubuntu installation on my harddisk, hence no big files to backup.

How can I use the tar command to generate data on the fly (without storing it into a file) and write in to the tape?

Many thanks!

---

### Post by Yashiro on 2009-02-10
Use dd not tar.

---

### Post by geohei on 2009-02-10
Thanks for the reply.

Sorry, I'm newbie.
Would you mind posting the complete command.

TIA

---

### Post by Yashiro on 2009-02-11
Create a 36GB file containing only zeros

dd if=/dev/zero of=/dev/sda1/bigfile.out bs=1000 count=36000000

---

### Post by geohei on 2009-02-14
Thanks for your reply. However ...
```
ubuntu@ubuntu:/dev$ sudo dd if=/dev/zero of=/dev/st0 bs=1000 count=36000000
dd: writing `/dev/st0': Invalid argument
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000737073 s, 0.0 kB/s
ubuntu@ubuntu:/dev$ dd if=/dev/zero of=/dev/st0/bigfile.out bs=1000 count=36000000
dd: opening `/dev/st0/bigfile.out': Not a directory
ubuntu@ubuntu:/dev$ sudo mt -f /dev/st0 status
drive type = 114
drive status = 1191215104
sense key error = 0
residue count = 0
file number = 0
block number = 0

```
Thanks!

---

