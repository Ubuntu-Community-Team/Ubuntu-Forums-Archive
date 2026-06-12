---
title: "I can read but not write/delete on external USB NTFS  (WD 'Elements') Hard drive."
date: 2008-09-02
forum: Hardware
---

### Post by fatagnus on 2008-09-02
In Ubuntu Hardy (8.04):

I have a Western Digital "Elements" external USB hard drive, NTFS formatted, for making backups.
**Ubuntu recognizes it and mounts it without problem**.

I can read all the files created and navigate through folders without any issue, but when I try to create a file/folder I get an error, for example:

mkdir: cannot create directory 'test': Operation not supported

I can't see where the error is.
[edit: ntfs-3g is installed, ntfs-config is not, and I tried it and didn't work]

Here's the related output for some commands, if it helps:

mount -l:
```
/dev/sdb1 on /media/Elements type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096) [Elements]

```

sudo fdisk -l :
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   7  HPFS/NTFS

```

sudo blkid:
```
/dev/sdb1: UUID="1C9C7F279C7EFB1A" LABEL="Elements" TYPE="ntfs" 
```

sudo ntfsfix /dev/sdb1 (after unmounting it):
```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.

```

---

### Post by in-dust-rial on 2008-09-02
hi,
```
$ sudo aptitude search ntfs
```

is that ntfs-3g lib installed?

here what my output is like:
```
p   libntfs-3g-dev                                                             - ntfs-3g filesystem in userspace (FUSE) library headers
c   libntfs-3g12                                                               - ntfs-3g filesystem in userspace (FUSE) library
i A libntfs-3g23                                                               - ntfs-3g filesystem in userspace (FUSE) library
p   libntfs-dev                                                                - library that provides common NTFS access functions (development files)
p   libntfs-gnomevfs                                                           - NTFS GNOME virtual filesystem module
i A libntfs10                                                                  - library that provides common NTFS access functions
i   ntfs-3g                                                                    - read-write NTFS driver for FUSE
p   ntfs-config                                                                - Enable/disable write support for any NTFS devices
p   ntfsdoc                                                                    - documentation about NTFS partitions format
i   ntfsprogs                                                                  - tools for doing neat things in NTFS partitions from Linux
```

---

### Post by fatagnus on 2008-09-02
hi, this is what I got:

```

p   libntfs-3g-dev                                                  - ntfs-3g filesystem in userspace (FUSE) library headers                   
i   libntfs-3g23                                                    - ntfs-3g filesystem in userspace (FUSE) library                           
p   libntfs-dev                                                     - library that provides common NTFS access functions (development files)   
p   libntfs-gnomevfs                                                - NTFS GNOME virtual filesystem module                                     
i A libntfs10                                                       - library that provides common NTFS access functions                       
i   ntfs-3g                                                         - read-write NTFS driver for FUSE                                          
p   ntfs-config                                                     - Enable/disable write support for any NTFS devices                        
p   ntfsdoc                                                         - documentation about NTFS partitions format                               
i   ntfsprogs                                                       - tools for doing neat things in NTFS partitions from Linux                

```

Looks like it's installed, except some development files and what I think it's an older version of ntfs-3g.

BTW: now that I saw it, I installed 'ntfs-config' (as it says 'Enable/disable write support for any NTFS devices') and enabled write support for NTFS, but still doesn't work.

---

### Post by in-dust-rial on 2008-09-02
mm remove ntfs-config? 
read the many google hits (most in this forum) about issues with ntfs and ntfs-config... 
gooood luck ;D

---

### Post by fatagnus on 2008-09-03
I removed ntfs-config ,but the problem is still there.
Anyway, **it was already there before installing ntfs-config**.

---

### Post by fatagnus on 2008-09-03
Well, since I'm unable to use ntfs properly, and there seems to be no solution for my problem..

I'll copy the existing files and format the drive again in another format more stable under Linux, but.. wich filesystem will work best? and, are there drivers for accessing it from windows? (read only is fine)

---

### Post by fatagnus on 2008-09-04
SOLVED:

I mounted it on a Windows XP machine and ran checkdisk on it.
Now the GUI disk mounter on Ubuntu tells me I don't have enough privileges to mount it, but if I use `sudo mount -t ntfs-3g /dev/sdb1 /media/Elements` it works OK.

---

