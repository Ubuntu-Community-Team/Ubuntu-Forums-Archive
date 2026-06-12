---
title: "NTFS drive won't use utf8 for drive name"
date: 2010-03-23
forum: Hardware
---

### Post by sublimation on 2010-03-23
I have a drive formatted with NTFS, and named using utf8 characters. When mounted by the system it replaces all unicode with '?' in the drive name. However, it does a fine job handling unicode within the drive itself. The drive name is identified correctly through ntfslabel
the important line in fstab:
```
UUID=xxxxxxxxxxxxxxxx /media/w&#618;ndo&#650;ws-C ntfs-3g defaults,nls=utf8 0 0
```
obviously the &#618; and &#650; are the unicode symbols replaced with ? by nautilus when referring to the drive. 

I have an NTFS USB drive that behaves the same way, however that even picks the mount point "/media/w?ndo?ws-usb" rather than utilizing the proper encoding.

I can't imagine it would be a font issue, as using nautilus to check the drives displays unicode like a charm.

any clues?

in case it's pertinent: 
```
:~$ uname -rmo
2.6.31-20-generic x86_64 GNU/Linux
```

---

