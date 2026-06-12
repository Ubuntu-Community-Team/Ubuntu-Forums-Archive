---
title: "How do i access my secong internal hd?"
date: 2009-10-14
forum: Hardware
---

### Post by cooltuyul on 2009-10-14
i formatted a new 1tb hd. i got the hd mounted. however, its under root and i cant copy, cut or paste! also i have to type in my password to access it but i still cannot copy, cut, or paste. how do i change this hd so that i can have full access to it?

"second", not secong, my bad...

---

### Post by ajgreeny on 2009-10-14
You just need to edit your /etc/fstab file and add a line.  You will need to make sure that the mount point directory exists first, and the line will depend on the file type format of the disk partition(s), and the dev name, for which you can use the way shown below, (/dec/sdx#) or UUID=long-string-number. You can get UUIDs from ```
sudo blkid
```

Automount linux partition. Add line to /etc/fstab:-
/dev/sdb1 /media/linux ext3 defaults, relatime 0 1

Automount fat32 windows. Add line to /etc/fstab:-
/dev/sda1 /media/windows vfat iocharset=utf8,umask=000 0 0
or
/dev/sda2 /media/data1 vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
or
/dev/sdb1 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0

Automount ntfs windows. Add line to /etc/fstab:-
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0

---

### Post by cooltuyul on 2009-10-14
uhh. thats a little too complex for me. could you make it a little more newbie friendly?

---

### Post by nzadLithium on 2009-10-15
run "sudo blkid" in a terminal and paste the output here.
Also run "sudo fdisk -l" in a terminal and paste output here.

---

### Post by cooltuyul on 2009-10-28
```
/dev/sdb1: UUID="daff938a-d4d6-4158-bc84-9306453f98f9" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="9dc4a7da-9dd1-48a4-860e-631fd9c28c92" 
/dev/sda1: LABEL="1 TB HD" UUID="fe6cc5b7-e1d1-4c49-8ecb-8fa9177e74b9" TYPE="ext3" 

```
for sudo blkid

AND

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003f768

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00036e1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38172   306616558+  83  Linux
/dev/sdb2           38173       38913     5952082+   5  Extended
/dev/sdb5           38173       38913     5952051   82  Linux swap / Solaris

```
for sudo fdisk -l

---

