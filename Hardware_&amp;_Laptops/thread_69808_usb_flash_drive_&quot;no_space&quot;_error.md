---
title: "usb flash drive &quot;no space&quot; error"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by rosslaird on 2005-09-28
I have tried copying files to two different usb flash drives (in Nautilus, after the drives are correctly detected). Both times I get the error that there is not enough space on the drives (they are 50 megs, and their size is shown correctly; the copied files are far less than that).

What should I try next to figure this out?

Ross

---

### Post by matthew on 2005-09-28
First thing that came to mind: Did you delete stuff off of the drives just before trying to put the files on them? If so, check to see that there is not a hidden .Trash directory full of stuff on the drives.

---

### Post by rosslaird on 2005-09-28
Indeed, I did erase some files first. But even after I deleted them (from the .Trash directory), there seem to be still more files on the device. When I try to delete these files from the command line (in /media/usbdisk), I get errors such as this:

rm: cannot lstat `rosslaird.ics': Input/output error

When I ls the files, I get errors like this:

ls: rosslaird.ics: Input/output error

Some of the files (and directories) that give the errors do not show up in Nautilus but do from the command  line.

Hm.

---

