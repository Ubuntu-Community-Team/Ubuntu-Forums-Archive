---
title: "Button problems with Fujitsu T4220"
date: 2008-08-30
forum: Hardware
---

### Post by miyoung on 2008-08-30
So, I had the fn+f6 and fn+f7 buttons working on my fujitsu t4220 tablet notebook and I also had the buttons on the screen working.  For the fn+f6 and fn+f7 buttons I added this line to the menu.lst file;

acpi_osi="!Windows 2006"

For the table buttons I had to compile the drivers per this webpage for a x64 bit OS;

[https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)

All was well and good up until a few updates ago when I lost the use of all of the keys which I have listed.  I run xbindkeys -k to try and find the key map but there is nothing.  It sounds like another acpi issue.

Does anyone know what happened and how it can be fixed?

---

### Post by miyoung on 2008-08-30
Well fortunately I got my computer back to full working condition (button wise).  However, it isn't really a fix.  It seems like the problem is associated with the newer kernels for linux.  I went back to kernel

kernel 2.6.24-16-generic

And everything was okay again, however -18 and -19  have the problems which I described.  Does anyone know why this is?

---

