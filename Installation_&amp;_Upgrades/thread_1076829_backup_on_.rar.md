---
title: "backup on .rar"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by aznpwnzor on 2009-02-21
for some reason i have an ubuntu backup on .rar

i think it is from my wubi days.  How can I restore my ubuntu through this rar?

---

### Post by aznpwnzor on 2009-03-14
can anybody help me with this?

---

### Post by kellemes on 2009-03-14
> **aznpwnzor said:**
> for some reason i have an ubuntu backup on .rar

i think it is from my wubi days.  How can I restore my ubuntu through this rar?

What's in the rar? The hole system?

---

### Post by aznpwnzor on 2009-03-18
that's what i'm guessing

---

### Post by Mark Phelps on 2009-03-18
You can't guess -- you'll have to open the rar and find out what's in it.  We can't tell you whether or not it will work without first know what "it" is!

---

### Post by aznpwnzor on 2009-03-19
yes it is the backup
it came from the wubi installation which i'm guessing i backed up before i used lubi to transfer to real partition

---

### Post by Mark Phelps on 2009-03-21
Not a Wubi expert, but my guess would be that you could NOT use a Wubi backup to install a standalone Ubuntu installation.

If you want to try anyway, you could do the following:
1) Partition the drive for Ubuntu, with at least a root partition and a swap partition
2) Expand the .rar, complete with all directories and files, onto some medium (external drive?)
3) Boot using an Ubuntu LiveCD, attach the medium containing the expanded .rar, and (as root), copy the files and directories into your Ubuntu partition.
4) When done, using the liveCD again, install GRUB to the MBR.
5) Remove the Live CD and boot

If all went well, you should be OK.

If it failed, can't help you -- as I said, I'm not a Wubi expert so I have no idea what may or may not be missing from a Wubi install.

---

### Post by aznpwnzor on 2009-03-23
when you say partition for ubuntu is a regular partitioning from within windows ok or is there a special way for the root and swap to be made

how about putting it back to a wubi based installation? anybody know how to do that?  cause from there i can easily get it to a normal installation

thanks for all the help guys

---

### Post by aznpwnzor on 2009-04-02
any wubi experts know anything about this?

---

