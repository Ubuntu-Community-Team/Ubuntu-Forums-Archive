---
title: "External WD Hard Drive doesn't shop up in GParted"
date: 2014-02-26
forum: Hardware
---

### Post by pepe8 on 2014-02-26
Hi, I have an external WD hard drive which suddenly stopped working. It was Fat32 formatted and now it's basically non existant to Windows (except for the Device Manager) and it only shows up in the Disk Utility with 500gb of unallocated space, if I want to format it there it gives me an "operation failed" error. It doesn't show up in GParted. When I tried using some Windows Recovery Software it gave me an error that it was Read-Only, could that be the problem? Do any of you have an idea if I can do something or should I give up the drive? Thanks in advance!

edit: in windows 8 when I try to create a new MBR in the Drive Management thing it also tells me "Access denied". Is there a way to retake ownership?

---

### Post by varunendra on 2014-03-01
Welcome to the forums pepe8!

It sounds like a hardware failure to me. How old is the drive? Portable 2.5" or the normal 3.5" with external power source?

I think it is best to open up the casing, and connect it internally to an available SATA port. That will reduce any added complexities due to its USB interface.

By the way, no data-recovery software should ask for 'Write' access to the drive it is going to recover. So the "Read-Only" error might have been just a notification, not an error. The program should have been able to continue with read-only access.

If you can connect it internally, and if Ubuntu recognizes it, we may try "TestDisk" to do the data recovery if you need that.

---

### Post by pepe8 on 2014-03-03
thanks a lot i havent thought about connecting it manually, i'll try that thanks

---

