---
title: "external hard drive won't mount"
date: 2009-08-18
forum: Hardware
---

### Post by hockey97 on 2009-08-18
Hi, I can't mount my external hard drive anymore. I used to be able to mount it. I backed up my website files on this external hard drive.

Now for some reasons I am getting an error message when trying to mount but I do see the device being seen by ubuntu. Just won't mount.

I ran dmesg in the terminal and this is what I get :


```
[  367.430226] JBD: no valid journal superblock found
[  367.430249] EXT3-fs: error loading journal.
[  752.919641] JBD: no valid journal superblock found
[  752.919662] EXT3-fs: error loading journal.
[ 1166.500023] JBD: no valid journal superblock found
[ 1166.500043] EXT3-fs: error loading journal.
[ 1227.681022] JBD: no valid journal superblock found
[ 1227.681044] EXT3-fs: error loading journal.
[ 1315.369106] JBD: no valid journal superblock found
[ 1315.369127] EXT3-fs: error loading journal.
[ 1326.665064] JBD: no valid journal superblock found
[ 1326.665085] EXT3-fs: error loading journal.
[ 1361.178262] JBD: no valid journal superblock found
[ 1361.178286] EXT3-fs: error loading journal.
[ 1404.740989] JBD: no valid journal superblock found
[ 1404.741010] EXT3-fs: error loading journal.

```

I would get an error message when trying to mount the drive. It would say something along the lines like :  mount:  wrong fs type bad superblock on /dev/sdc5  missing codepage or helping program or other error then is says to type in dmesg in terminal for descriptive details to errors.

that is what I get. I think the permissions might be messed up or something not fully sure. 

What should I do to fix this? I need to backup new work done on my site.

The external hard drive is a usb drive and has the file system of EX3 linux type.

---

### Post by timcredible on 2009-08-18
if there are errors on the drive it will either not mount or will mount in readonly mode.  if it's fat32 formatted, run dosfsck on it.  i forget the exact option, i think it's something like ```
dosfsck /mnt/sdf1 -a
```

---

### Post by hockey97 on 2009-08-18
> **timcredible said:**
> if there are errors on the drive it will either not mount or will mount in readonly mode.  if it's fat32 formatted, run dosfsck on it.  i forget the exact option, i think it's something like ```
dosfsck /mnt/sdf1 -a
```

No it's not fat32 nore ntfs formated. It's formatted with linux file system the EX3 file system format.

---

### Post by hockey97 on 2009-08-19
do you think I can reformat the external hard drive? I mean I can do that and just back up what I have right now.

If that's the best method right now then how do I reformat it?

Do a fdsk?

---

