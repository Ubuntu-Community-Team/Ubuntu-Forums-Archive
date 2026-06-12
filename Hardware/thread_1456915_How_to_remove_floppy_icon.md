---
title: "How to remove floppy icon"
date: 2010-04-17
forum: Hardware
---

### Post by bodrisch on 2010-04-17
Does anybody know how to remove the floppy drive icon from the computer menu???...I'm am using Ubuntu 9.10 and I don't have a floppy drive.

Thanks in advance.

---

### Post by sirko on 2010-04-21
I aslo need advice hot to do that, it's really annoying

---

### Post by hsoulen on 2010-04-21
Have you tried looking in your file system table?

$gksudo gedit /etc/fstab

Look for a line like this:

"/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0"

If you don't have a floppy drive in your system, just comment out the line with a # (I don't like to delete from system files unless I have to). Save the file and reboot...

Hank

---

