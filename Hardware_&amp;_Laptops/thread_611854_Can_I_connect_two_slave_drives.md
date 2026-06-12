---
title: "Can I connect two slave drives?"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by El Muelio on 2007-11-13
I want to run Linux alongside Windows, I have a 80gb HD with windows and a 40gb HD with linux installed.

If I connect both HDs as slaves, is it possible to configer it so that the computer will prompt me to tell it which to boot from when I power up?

---

### Post by taurus on 2007-11-13
One has to be a master and the other has to be a slave drive (for PATA).  Why don't make the drive that windows is on as master since it always wants to reside on the first drive.  Then, set the jumper for the second drive as a slave and install Ubuntu on that.  However, install GRUB to MBR--/dev/hda (or /dev/sda) and you can boot either one when you turn on your machine.

---

### Post by El Muelio on 2007-11-13
Thanks for the reply, but I am very new to Linux and havn't got the grasp of doing most stuff yet.

I don't understand this bit, but I am very keen to get the results.

GRUB to MBR--/dev/hda (or /dev/sda)

---

