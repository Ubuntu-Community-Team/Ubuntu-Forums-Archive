---
title: "NTFS or Ext3"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by dpacmittal on 2009-09-20
Don't flame me if this is a noob question but you ask and you learn, so my question is:

Can we install Ubuntu on NTFS? I googled and found that we can't but I didn't find anything about 9.04.

Does it supports NTFS natively? I would like to have dual boot with XP and would like to access the linux partition in xp as well, so that in case something goes wrong with linux, I can still access the linux partition and backup my data.

Thanks.

---

### Post by Partyboi2 on 2009-09-20
You will need to use the ext3 file system to install Ubuntu.
Ubuntu can read/write to ntfs but windows can not read/write to ext unless you install  some software that allows you to do this like [[COLOR=Blue]this[/COLOR]]("http://www.fs-driver.org/"). Allowing windows to read/write to your ext partitions is not very secure though.
> so that in case something goes wrong with linux, I can still access the linux partition and backup my data.If this was to happen you should be able to use a Ubuntu live cd to access your data.

---

### Post by dpacmittal on 2009-09-20
> **Partyboi2 said:**
> You will need to use the ext3 file system to install Ubuntu.
Ubuntu can read/write to ntfs but windows can not read/write to ext unless you install  some software that allows you to do this like [[COLOR=Blue]this[/COLOR]]("http://www.fs-driver.org/"). Allowing windows to read/write to your ext partitions is not very secure though.
If this was to happen you should be able to use a Ubuntu live cd to access your data.

Thankyou for your reply.
Cheers

---

