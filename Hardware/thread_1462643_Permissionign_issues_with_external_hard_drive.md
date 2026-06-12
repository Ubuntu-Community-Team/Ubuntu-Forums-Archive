---
title: "Permissionign issues with external hard drive"
date: 2010-04-25
forum: Hardware
---

### Post by cheics on 2010-04-25
I am unable to copy files off my external hard drive to my local drives

I am able to see the file hierarchy in a terminal and in Nautilus. I can copy a file from local drive to the external drive and copy it back.

I cannot however copy files from the external to my local drives.

I receive the following error:
cp: cannot open `file_x' for reading: Permission denied
Even though the permissions of the file hierarchy and the file itself are all enabled (chmod 777).

When looking at the properties of a folder in Nautilus, the "file access" dropdown reads dashes. Upon setting the dropdown to "Read and write" and selecting "Apply permissions to enclosed files" the dropdown reverts to dashes

Any ideas as to why I cannot get files off the drive?

---

### Post by cheics on 2010-04-29
The files were encrypted in WinXP; that is why it is inaccessible

---

