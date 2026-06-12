---
title: "how to format?"
date: 2005-11-10
forum: General Help
---

### Post by mad_alfred on 2005-11-10
Hi!

I'd like to format in ext3 my 2nd drive ( IDE slave ) /dev/hdb and all it's partitions ( it used to be formatted in ntfs ( ex windowsXP).

what command shall i execute ??

thanx

---

### Post by etc on 2005-11-10
sudo cfdisk /dev/hdb
and play around with it
or 
sudo mkfs /dev/hdb

Do what he said VV

---

### Post by Kyral on 2005-11-10
Make sure it isn't mounted, then

```
sudo mke2fs -j /dev/hdbX
``` where X is the partition number (1,2,3)

Should do it

---

### Post by mad_alfred on 2005-11-10
thanx

it was quicker than i thought! ...now i don't even have the smallest bit of windows on my sistem!:D

---

### Post by Kyral on 2005-11-10
Oh in case anyone wants to know

"mke2fs" is the command to make an ext2 FS. The -j option adds a Journal onto it, which is basically the only difference between ext2 and ext3, that ext3 has a journal (This is the reason why you can make an ext2 filesystem into an ext3 FS without data loss)

---

