---
title: "External Hard Drive Problems"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by toran on 2007-09-03
I have a seagate external harddrive formatted as ext3.

Right now I can mount it and unmount it fine, and it works well. Unfortunately, however, after staying mounted for some time, it will become read-only. It also sometimes has input/output errors after some time of being mounted. Sometimes I can unmount it and remount it and it will be read-write accessible. Sometimes, though, I cannot access it and when I try to mount it it gives me an error about being unable to read the superblock.

How can I get my drive to work and stay working?

---

### Post by logos34 on 2007-09-03
You might want to run a filesystem check on that drive partition.
[B]
sudo fsck /dev/sda1[/B]

or with superblock option:

**sudo e2fsck -b <*superblock*> -f -v -y /dev/sda1**

for details, see

**man e2fsck**

---

### Post by Inxsible on 2007-09-03
You might also want to try mounting it using pmount since its an external drive.

Look at my signature for a mini howto.

---

