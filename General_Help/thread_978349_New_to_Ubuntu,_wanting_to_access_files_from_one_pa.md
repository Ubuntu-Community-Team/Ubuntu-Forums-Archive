---
title: "New to Ubuntu, wanting to access files from one partition from another"
date: 2008-11-11
forum: General Help
---

### Post by shortyr87 on 2008-11-11
So I just installed ubuntu onto my dell inspiron 1525, and everything works fine, it's just i dual booted it with windows xp and now i wanted to try and copy/transfer the files from xp to ubuntu. I'm not sure if that's even possible, or how to go about if it is possible. Anyways if anyone has any info about that, (getting files from one partition to another, specifically from the xp partition to linux partition) let me know! thanks in advance!

---

### Post by Ryadt on 2008-11-11
Under Places you should see your xp partition (Media).

---

### Post by Sef on 2008-11-11
Do you have a separate home partition?   

If you are not sure, then let's find out.

Applications > Accessories > Terminal

Then paste or type in this command:

```
sudo fdisk -l
``` small L   Then paste what the results here.

---

### Post by shortyr87 on 2008-11-11
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11226    90172813+   7  HPFS/NTFS
/dev/sda2           11227       30401   154023187+   5  Extended
/dev/sda5           11227       29617   147725676   83  Linux
/dev/sda6           29618       30401     6297448+  82  Linux swap / Solaris


that's what i got... but i did find it under places! (it was really easy actually... haha) thanks for your help!

---

