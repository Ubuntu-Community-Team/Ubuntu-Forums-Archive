---
title: "Encrypted harddisk unaccessible for certain software?"
date: 2008-07-18
forum: General Help
---

### Post by kzm. on 2008-07-18
Hey..

I have an external harddisk as data disk. This disk was fat32 (but then 1TB), i wrote it full with ```
dd if=/dev/random
``` encrypted (cryptsetup) it, mounted it from /dev/mapper and formated it ext3. fstab got update to ```
/dev/mapper/fuji /mnt/fuji auto defaults,noexec,umask=002 0 0
``` I can access the disk through the commandline, crontab+rsync can do its job on it.. but so far everything based on PHP from/or apache fails even though the folder on which it should work is set to drwxrwxrwx.

So I assume:
- file-permission is correct
- fstab permission is correct

leaves me with big questionmarks..

Can anybody bring in some light for me? I am really lost with this one.. i dunno even know what to search on.. :confused:

thanks a lot.

---

### Post by kidders on 2008-07-20
Hi there,

Could you give an example of something that fails, and how?

For example, do simple tests like this work?[PHP]<?php
`touch /mnt/fuji/test1`;
$fp=fopen('/mnt/fuji/test2','w');
fclose($fp);
?>[/PHP]

---

### Post by dcstar on 2008-07-20
> **kzm. said:**
> 
......```
/dev/mapper/fuji /mnt/fuji auto defaults,noexec,**umask=002** 0 0
```
......

Why are you using a umask?

---

### Post by kidders on 2008-07-20
> **dcstar said:**
> Why are you using a umask?

Good question ... won't specifying invalid mount options prevent the filesystem from mounting?

---

