---
title: "Cloning a windows drive fails"
date: 2014-06-22
forum: Hardware
---

### Post by theryanproject0195 on 2014-06-22
Hello, I have a Windows 98 drive I am trying to clone through ubuntu because the old drive is failing. The new drive is 120gb while the old is 2.1gb. I partioned the new one correctly to match and both give this output when I type:
```

sudo fdisk -l

```

The output is:
```

Disk /dev/sdb: 2111 MB, 2111864832 bytes
64 heads, 63 sectors/track, 1023 cylinders, total 4124736 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9751a219

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       44352     4116671     2036160    b  W95 FAT32
/dev/sdb2              63       44351       22144+  12  Compaq diagnostics

Partition table entries are not in disk order


```

To clone the drives I used dd to move backup the hard drive to a file then dd to write it. I did mark the Windows 98 partition as bootable. When I plug the drive into the Windows 98 computer, manufactured in around 2000, I get 
```

Verifying DMI Data Pool....

```
and then it hangs.

The computer the drive was originally in was broken so I had to switch it. I could probably switch the drive to a computer that doesn't have DMI Data Pool verifying but would prefer not to.

Thanks for reading this,
Ryan

---

### Post by Mark Phelps on 2014-06-22
Cloning a "failing" drive is asking for trouble -- because if the clone process works faithfully, data errors will be duplicated with the cloning operation.

Also, my own experience has been that cloning Windows filesystems tends to work better with Windows utilities, not Linux utilities.

---

### Post by Vladlenin5000 on 2014-06-22
> **Mark Phelps said:**
> Cloning a "failing" drive is asking for trouble -- because if the clone process works faithfully, data errors will be duplicated with the cloning operation.

+1 :p

> Also, my own experience has been that cloning Windows filesystems tends  to work better with Windows utilities, not Linux utilities.

Agreed. However, in this case, it doesn't apply. It's an old "Windows 98" drive (=FAT32) and any Linux tool can handle that perfectly.

---

