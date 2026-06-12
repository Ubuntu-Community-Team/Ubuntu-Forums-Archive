---
title: "external hard drive unable to mount"
date: 2010-07-31
forum: Hardware
---

### Post by BAB SWAIN on 2010-07-31
hi
i have my very very imp data on my external hard drive (transcend storejet 320M), NOW I AM UNABE TO MY EXTERNAL HARD DRIVE AND IT IS SHOWING THIS MESSAGE,PLEASE HELP ME HOW TO DO THIS.
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
i want to recover my data.pl help me..........
thank you. 
bab

---

### Post by Araja on 2010-08-01
Im having the same problem too! Getting pretty much the same message for "My Book". Please help us!

---

### Post by Araja on 2010-08-01
Nevermind I found my answer and it worked! :o

Here is the link. [http://ubuntuforums.org/showthread.php?t=1518031&highlight=unable+mount](http://ubuntuforums.org/showthread.php?t=1518031&highlight=unable+mount)

---

