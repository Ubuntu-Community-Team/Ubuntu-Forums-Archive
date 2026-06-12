---
title: "Non-destructively change partition alignment?"
date: 2012-07-19
forum: Hardware
---

### Post by trovatore on 2012-07-19
Hi guys,

I have a new laptop, windows pre-installed (of course they used the whole partition table, so I had to figure out which ones I could delete, grr).  Anyway I repartitioned it before finding out about the 4096 blocksize issue.  Fortunately I haven't gone crazy yet -- I have sda1 and sda2 for Windows (sda2 is the main Windows partition), sda3 for Linux root, sda4 extended, sda5 is /home, and sda6 is swap.

Sda1 and sda2 have sizes that are multiples of 4096, but sda3 does not, so the extended partition does not start on a physical block.

Is there any way to non-destructively move the start point of the extended partition?  I'm guessing not, but just in case.  If I have to delete the extended, that's not too bad, because I don't have much on /home yet, which is the only non-swap partition in there.

Assuming I do have to delete the extended partition, (1) how do I make it start on a multiple of 4096, and (2) how do I recreate my user, with a home directory in /home and all the defaults?  (Using ecryptfs, if that makes a difference.)

Thanks for any help.

---

