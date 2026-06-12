---
title: "[SOLVED] ext3 partitions mounting as readonly"
date: 2008-06-11
forum: Hardware
---

### Post by Benedict on 2008-06-11
Hello all,

I'm having problems mounting ext3 partitions.

I have 3 partitions on two internal sata drives. These partitions were set up in OpenSuse 10.3. I deleted OpenSuse and installed Ubuntu 8.04. I can mount the partitions but as read only.

How do I write to these partitions? What information do I need to supply so people can help me with this?

I'm fairly new to linux so please explain things very clearly.

Cheers
Benedict

---

### Post by logos34 on 2008-06-11
You may have to just chown and chmod them.


post the output from these commands:

sudo fdisk -l

ls -l /media

cat /etc/fstab

---

### Post by Benedict on 2008-06-12
Thanks logos34, you're correct. 

I figure out how to use chown and chmod and I've fixed it.

Cheers
Benedict

---

