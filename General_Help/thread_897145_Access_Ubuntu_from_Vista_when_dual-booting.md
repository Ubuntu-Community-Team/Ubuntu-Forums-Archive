---
title: "Access Ubuntu from Vista when dual-booting"
date: 2008-08-21
forum: General Help
---

### Post by EVA01 on 2008-08-21
Hey guys,
I was wondering if it is possible in any way to access Ubuntu from Windows Vista when I'm dual-booting. For example, I'd like to use Microsoft Word 2007 to type stuff (as opposed to LaTeX), but I'd also like to run MATLAB which is only installed on Linux. Basically, I'm wondering if there is any way to run programs installed under Ubuntu while I'm currently on Vista.
I've tried using Xming to access Ubuntu remotely, but I'm guessing that's not possible since Ubuntu is shut down while Vista is running...

---

### Post by y@w on 2008-08-21
You could always run one of your OS's in a virtual machine :) Otherwise there are Linux emulators like Cygwin. X11 doesn't work overly well on

---

### Post by mb_webguy on 2008-08-21
On a dual-boot system, it's not possible to run Linux software while running Windows without using a VM or emulator, which is a completely separate issue from dual-booting.  You *can* run Windows programs under Linux using Wine (which is not a VM or emulator), but only those installed using Wine, and not those installed on your Windows partition.

---

### Post by EVA01 on 2008-08-21
Ah I see. That's what I was afraid of, but it makes sense. Thanks!

---

### Post by cybrsaylr on 2008-08-22
In general Windows treats the linux partition as an unknown and won't let you in. There are a few linux apps that run on Windows.
Linux on the other hand, lets you go into the Windows partition and move files back and forth with no problems but you may not be able to open all those windows files in linux.

---

### Post by zekica on 2008-08-22
There is a utility that can read and write to ext2/ext3 partitions natively from windows 2000/XP/Vista.

It is called [ext2 ifs]("http://www.fs-driver.org/"), but keep in mind if your computer doesn't shutdown properly (since the driver doesn't support journaling), it will have to scan your partition for errors, and in rare events lose some of your data.

You still can't use applications from linux, since they are not compatible, but you can use windows versions of some applications to do the same work (and should work with files from linux partition(s)).

---

