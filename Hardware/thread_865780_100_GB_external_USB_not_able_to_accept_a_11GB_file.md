---
title: "100 GB external USB not able to accept a 11GB file"
date: 2008-07-21
forum: Hardware
---

### Post by mdsharp24 on 2008-07-21
I'm using Ubuntu Hardy on amd64. I have an external 100 GB USB drive that auto mounts fine when connected:

/dev/sdb1 on /media/disk-2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

When trying to mv an 11 GB file via the CL as root it says there isn't enough space?   Why might this be?

Michael

---

### Post by Dark_Stang on 2008-07-21
Is it fat32? If that's the case the largest filesize a fat32 file system can support is 4gb. I'd suggest reformatting the drive to ext3, reiserfs, or ntfs.

---

### Post by grim4593 on 2008-07-21
Another option would be to split the file into smaller chunks. You can do this with Winrar/Winzip.

After typing the command "split" in a terminal, it looks like it would work too.

---

### Post by mdsharp24 on 2008-07-21
DOH!  I forgot about the 4GB limit on msdos partitions!  Thanks for both post!  Since this External HD is going to be dedicated to just backing up my box with partimage I went ahead and formatted it to ext3. But for anyone coming across this thread, like the user above said about breaking files into smaller parts (under the 4GB per file) limit for those that don't want to format their External drives partimage has that ability.

Again, thanks!

Michael

---

