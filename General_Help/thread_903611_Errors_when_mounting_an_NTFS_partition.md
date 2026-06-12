---
title: "Errors when mounting an NTFS partition"
date: 2008-08-28
forum: General Help
---

### Post by Ernir on 2008-08-28
This is what I get when I try to mount through the terminal:

```
ernir@ernir-desktop:~$ sudo mount -a
[sudo] password for ernir:
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

Is there any way to access the partition without hunting down a computer with a working copy of Windows? Could this be a simple problem with my NTFS-3G or something?

Interestingly enough, trying to mount through the GUI just gives me a simple "permissions denied". =/

---

### Post by cariboo on 2008-08-28
Have you tried ntfsprogs? there are tools included to repair ntfs formated partitons. ntfsprogs is available for install with Add/Remove Programs, Syanptic Package Manager and of course the command line.

Jim

---

### Post by Ernir on 2008-08-28
Ooo, no I had not heard of that one. Will try now. Thanks!

---

### Post by vanadium on 2008-08-28
> Is there any way to access the partition without hunting down a computer with a working copy of Windows?

The utility that you are looking for is ntfsfix, which comes with ntfsprogs to which cariboo907 referred. It can repair common errors on ntfs volumes, but, as the manual states, is NOT a Linux version of chkdsk.

ntfs is a proprietary file system. linux tools to check and repair ntfs volumes are limited. For this reason, you should preferably not be using ntfs if you do not have also a windows computer available. You should consider reformatting your disk to ext3 or another native linux file system.

---

### Post by Ernir on 2008-08-28
> **vanadium said:**
> The utility that you are looking for is ntfsfix, which comes with ntfsprogs to which cariboo907 referred. It can repair common errors on ntfs volumes, but, as the manual states, is NOT a Linux version of chkdsk.

Well, it tried. And it gave me the information that the partition really is corrupt. =(
Off to my brother it is.

> **vanadium said:**
> ntfs is a proprietary file system. linux tools to check and repair ntfs volumes are limited. For this reason, you should preferably not be using ntfs if you do not have also a windows computer available. You should consider reformatting your disk to ext3 or another native linux file system.

Yep. Trust me, I will be getting rid of that file system soon enough. Just need to rescue a few files I would really dislike losing permanently. Of course, I did not manage to remember them until the day after I got rid of my last Windows installation. Just glad I had not wiped it yet. =(

---

