---
title: "Truecrypt 6.0a Hidden Volumes"
date: 2008-08-21
forum: General Help
---

### Post by shizow on 2008-08-21
I try to make a hidden volume inside a truecrypt partition (in my case a whole external disk /dev/sdb).
I tried it with the graphical client, which first formats the outer volume with vfat after this you can enter the size of the hidden volume, but it said to me, there is only max 47.5 GB for the hidden volume, but my disk is 500 GB disk.
It seems to be the same problem as reported here [https://bugs.launchpad.net/ubuntu/+bug/252939](https://bugs.launchpad.net/ubuntu/+bug/252939)
The truecrypt forums are closed at the moment.

So i tried it with the text client.
In the help of the client it is written:
```

 Inexperienced users should use the graphical user interface to create a hidden
 volume. When using the text user interface, the following procedure must be
 followed to create a hidden volume:
  1) Create an outer volume with no filesystem.
  2) Create a hidden volume within the outer volume.
  3) Mount the outer volume using hidden volume protection.
  4) Create a filesystem on the virtual device of the outer volume.
  5) Mount the new filesystem and fill it with data.
  6) Dismount the outer volume.
  If at any step the hidden volume protection is triggered, start again from 1).

```
I created a outer volume on /dev/sdb with
truecrypt -t -c
no filesystem
and then i created a hidden volume on /dev/sdb with
truecrypt -t -c
no filesystem
then i mounted the outer volume with protection for the hidden one
then mkfs.ext2 /dev/loop0
then i started the graphic client and it said that the 
volume protection was used
and i cannot mount the filesystem of the outer volume
gives me a wrong filesystem type/bad superblock error
(i think the mkfs.ext2 formatted the whole volume)

what is the correct way to make a hidden volume on my disk /dev/sdb?

---

### Post by shizow on 2008-09-07
Can anyone help, please?

---

### Post by Chunky Dunk on 2008-12-11
I don't know if your still having this problem (which I can personally verify), but they seemed to have fixed this in version 6.1

---

