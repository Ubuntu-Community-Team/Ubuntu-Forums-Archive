---
title: "Installing a Second Hard drive??"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by Beano on 2005-05-16
Could anyone give me some Idea as to how to Install a second hard drive onto Hoary? 

I recently aquired a 40gb seagate drive from a friend - it has stuff on it. However ive plugged in it and its only detected as a 64mb drive. Anyone know how I can reformat it via the command line?

Thanks, 

Bean

---

### Post by Strife on 2005-05-16
Have you properly formatted the drive? If so, have you tried mounting it?

If you haven't formatted it, try using cfdisk to partition it first (to use it, you have to specify what hard disk to partition, so if the new drive is /dev/hdc, you would run cfdisk /dev/hdc). Then to format, use the mkfs.ext3 utility.

A quick Google search gave me this: [http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml).

There are also probably graphical tools available to use instead of command line, but command line is what I know, so it's what I'm suggesting :)

---

### Post by Sam on 2005-05-16
Prepare the partition(s) with
```
$ sudo cfdisk /dev/hdX
```
(replace hdX with your drive)
Format with ext3:
```
$ sudo mkfs.ext3 /dev/hdX
```

---

### Post by Beano on 2005-05-16
Ok thanks man :D i dont much like the GUI - I do most of the stuff from the command line too so that suits me perfectly :)

---

### Post by Beano on 2005-05-16
Id say the disk was fucked - it cant get the disk size and therefore I cant format

---

