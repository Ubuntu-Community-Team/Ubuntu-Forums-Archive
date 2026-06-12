---
title: "External Hard Drive Input/Output Error"
date: 2008-10-01
forum: Hardware
---

### Post by offchance on 2008-10-01
Hi! My external harddrive fails to mount in Hardy. I made a back up to it before updating and now the drive will not show up in Ubuntu or OSX. I used a Puppy livecd and mounted it successfully but could not copy any files to my internal HD (got more i/o errors). 

Any help is appreciated! I have attached a small text file of the terminal commands I have used to solve the problem and their outputs. Here's an example:

```
damion@deck:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force
Error reading $MFT: Input/output error
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
damion@deck:~$ 
```

---

### Post by offchance on 2008-10-08
bump?

---

### Post by offchance on 2008-10-10
No suggestions? No one interested in my little text file? I feel so alone, so...cold.

---

### Post by VanHammersly on 2008-10-11
I would like to know, too. I am experiencing this with an external hard drive. I mounted the drive in my tower and am still getting this error.

---

### Post by willywortel on 2008-10-22
Hi,

Try ¨sudo ntfs-config¨

Unplug the device and plug it in again. Worked for me.

cheers

---

### Post by offchance on 2008-10-23
ntfs-config doesn't address the problem with the drive. My system is already set up to deal with ntfs file systems. I'm glad it worked for you, though!

---

