---
title: "Time to run e2fsck -f -y -v"
date: 2008-09-24
forum: General Help
---

### Post by willyaranda on 2008-09-24
I had a big problem with my partitions. I changed from primary to logical and I can't boot Ubuntu. It result in a lot of errors in inodes and blocks when I try to start up.

So, actually, I'm doing the e2fsck -f -y -v (as a friend recommend) in a 50GB partition of ext3. Do you know approximately how much time does it will take?

Now it is running for 13h and my HD is working very hard but the progress bar is very useless.

Thanks!

If this doesn't work, there is another way to recover the data?

---

### Post by The Cog on 2008-09-24
As far as I know, the files that have to change are /boot/grub/menu.lst to change the root partition, and /etc/fstab to change the root partition. You would either have to edit these before copying the partition contents, or use a live CD to make the changes after the transfer. I've never tried this though, so I could be missing a bucket load of other details that need fixing.

---

### Post by willyaranda on 2008-09-24
the problem is that i couldn't mount the HD... :(

---

### Post by willyaranda on 2008-09-24
```
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          0079ed23-a07d-45e1-8800-79ff9e9e111c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index
filetype sparse_super large_file
Default mount options:    (none)
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              3186688
Block count:              12719455
Reserved block count:     508778
Free blocks:              4971981
Free inodes:              3014514
First block:              0
Block size:               4096
```

---

### Post by willyaranda on 2008-09-25
any help?

related: [http://ubuntuforums.org/showthread.php?t=927762](http://ubuntuforums.org/showthread.php?t=927762)

---

### Post by The Cog on 2008-09-25
This used to be on a paimary partition, right? You justcopied the contents? If so, did you correct /etc/fstab? Iwould mount hda5 with a live CD and check the contents of fstab. You can use the commadn **blkid** to find the new UUID, or just change the line to read /dev/sda5 instead.

---

