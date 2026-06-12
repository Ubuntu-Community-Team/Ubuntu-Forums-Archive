---
title: "[SOLVED] NTFS partition read only..trying to make read/write"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by kyleabaker on 2007-10-10
I've recently installed Ubuntu and previously had only Windows Vista installed. I have them installed to dual boot on the same hard drive. I noticed that my windows partition was recognized immediately, but has only read permissions. Is there a way that I can edit the /etc/fstab file to allow writing as well? I'd like to avoid installing ntfs-3g, etc. if at all possible. I used ntfs-3g and ntfsmount in Fedora Core 6 about a year ago, and while it seemed to work, I'd prefer to use the abilities that are already built into Ubuntu if at all possible and just edit the file to enable read/write. Here is my fstab file..

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=51c043b0-b855-4eed-8d76-2028aa26a45c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=AE04FE3004FDFB63 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=72F03DEAF03DB4E7 /media/750GB    ntfs    nls=utf8,umask=007,gid=46 0       1

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

the sda1 is the windows partition, the 750gb is just another drive that I have and have manually added. I'd also like to get it read/write enabled. Thanks in advanced.

---

### Post by jocko on 2007-10-10
You didn't say which version of ubuntu you have. Irregardless, as far as I know, ntfs-3g is the only safe way to get write support.
If I remember correctly, in feisty you have to install ntfs-3g and ntfs-config to enable ntfs write support.
In gutsy ntfs-3g is already installed and enabled by default, so there's nothing you need to do to enable it.

Oh, and have a look at your fstab, there seems to be a missing "defaults" in the line for your /media/750GB:
I think it should be like this:
```
# /dev/sda1
UUID=AE04FE3004FDFB63 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sdb1
UUID=72F03DEAF03DB4E7 /media/750GB ntfs [COLOR=Red]defaults,[/COLOR]nls=utf8,umask=007,gid=46 0 1
```

---

### Post by taurus on 2007-10-10
Sorry but if you want to write to ntfs filesystem, you need to use ntfs-3g.  A lot has chance for ntfs-3g in a year since you last tried it.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by kyleabaker on 2007-10-10
Sorry, I forgot to mention that I am using Ubuntu 7.04 x64. I installed ntfs-3g and edited fstab a bit to enable read/write.

@taurus
I was just hoping that Ubuntu had native support for writing to NTFS since it seems to have native support for read.

Thanks though for the help guys.

---

