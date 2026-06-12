---
title: "Another Filesystem that cannot be renamed...can it?"
date: 2008-09-27
forum: General Help
---

### Post by wolterh on 2008-09-27
This is the situation. My computer has to physical drives. SDA1 is mounted as the filesystem ( in root "/" ) and SDA5 is mounted as /home.
I want to rename SDA1 because when I browse "Computer" it appears to be named as "Filesystem" and that sounds a bit to OSsy to me, so I wanted to change it to "Hard Drive" or something similar.

The methods I've tried:
-Normal rename (Select+F2) does not let me and gives me this error:
```
Sorry, couldn't rename "Filesystem" to "Hard Drive": Operation not supported by backend
```
-e2label (my drives are formatted as ext3). It actually worked, because when I enter e2label /dev/sda1 on the terminal, it tells me that the drive is named as "Hard Drive", but still, when I browse Computer the drive appears to be named as "Filesystem"
-reiserfstune --l "Label" /dev/sda1 tells me that:
```
reiserfs_open: the reiserfs superblock cannot be found on /dev/sda1.
reiserfstune: Cannot open reiserfs on /dev/sda1

```

So, here I wait expecting the rename of my filesystem soon.

---

