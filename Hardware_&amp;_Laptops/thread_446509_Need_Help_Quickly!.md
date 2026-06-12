---
title: "Need Help Quickly!"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by tylermenezes on 2007-05-17
long story short, I run Windows Vista and when I started up it said "Unmountable Boot Volume". Right now I'm trying to get my files, but I can't figure out how to do this from the Live CD. Someone willing to help me?

Please, I have a project due in two days.


Thanks so much,
Tyler

---

### Post by hardyn on 2007-05-17
two snotty comments off the bat...

pleeeese give the subject a better title than "help"
don't play with the computer before a project is due, im bad for it too ;)


hokay...

boot the live disk.
start the command shell

sudo mkdir /media/windowsc
sudo mount /dev/sda1 /media/windowsc

it will appear on the desktop; this help assumes that what you want is on the the first hard disk, and windows is partition 1

when you are done

sudo umount /media/windowsc

good luck.

---

### Post by tylermenezes on 2007-05-17
Thanks

(And I couldn't think of anything better, though UNMOUNTABLE_BOOT_VOLUME, or Accessing NTFS w/ Ubuntu from Live CD)

---

