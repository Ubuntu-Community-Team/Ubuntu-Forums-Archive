---
title: "Automount SATA NTFS"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by mickc1303 on 2005-08-17
I managed to get my SATA raid array recognised by following the information from [http://www.ubuntuforums.org/showthread.php?t=2557](http://www.ubuntuforums.org/showthread.php?t=2557)

I know have a script which contains:

```
dmraid -ay -v
mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/pdc_fihcedja3 /mnt/windows

``` 

which I have to manually run to enable access to the drive.  How can I get it so that this automatically happens upon startup?

---

### Post by mickc1303 on 2005-08-19
Sorry to bump this topic, but it's gone 4 pages back in a day and I could really use some help

---

