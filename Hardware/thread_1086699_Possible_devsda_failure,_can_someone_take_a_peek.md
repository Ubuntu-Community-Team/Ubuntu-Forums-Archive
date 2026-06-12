---
title: "Possible /dev/sda failure, can someone take a peek?"
date: 2009-03-04
forum: Hardware
---

### Post by Huufarted on 2009-03-04
I'm getting a few pages worth of errors on boot-up and I think it's due to a failing harddrive (RMA is already put in).  Bought an Asus eee 1000HA netbook.  Comes with a stock 160 GB SATA drive, replaced it with a 500 GB SATA.  That's the drive I think is failing.  So far, it's about a 10-minute boot up with the following message:

```
[ 1156.521945] end_request: I/O error, dev sda, sector 181644505
```

Of course the seconds count changes, but the rest is the same.  There are about 120 lines of the above message.  The sector changes about every 20 errors.  In the middle of it all is

```
[ 1156.526869] EXT3-fs error (device sda5): ext3_get_inode_loc: unable to read inode block - inode=431769, block=1736714
```

Am I correct in assuming that it's an HDD failure?

Once Linux finishes booting (if it does) I will pull a more comprehensive excerpt from the logs.

---

### Post by albandy on 2009-03-04
It seems a hw failure. 
Boot with the ubuntu cd and type fsck /dev/sda

---

### Post by Huufarted on 2009-03-04
Not worth the effort.  I'm going to load up a gparted live cd and wipe the drive before sending it back to Newegg for the RMA.  Done deal, new HDD already on the way.

---

### Post by Huufarted on 2009-03-04
Albandy, forgot to say thanks for looking at it and confirming that with me.  :)  I appreciate it.

---

