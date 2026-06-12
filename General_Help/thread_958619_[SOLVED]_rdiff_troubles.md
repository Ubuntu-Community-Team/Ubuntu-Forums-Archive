---
title: "[SOLVED] rdiff troubles"
date: 2008-10-25
forum: General Help
---

### Post by AceDip on 2008-10-25
When i try backing up data from my hard disk to my external hard drive, using
```
$ rdiff-backup MyHardDisk/drive MyextrnDisk/drive 
```
The files in the MyHardDisk/drive do get copied but with a change in their file name i.e.
EasyRider.jpg  =becomes>  ;069asy;082ider.jpg
and also the terminal gives the following output
```

Warning: hard linking not supported by filesystem at MyextrnDisk/drive/rdiff-backup-data
```

---

### Post by AceDip on 2008-10-25
And also
the output of the following command on my External Drive is
```

$ sudo sfdisk -l /dev/sdb
 Device       Boot Start  End   #cyls    #blocks   Id System
/dev/sdb1          0       -       0          0    0  Empty
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

```

---

