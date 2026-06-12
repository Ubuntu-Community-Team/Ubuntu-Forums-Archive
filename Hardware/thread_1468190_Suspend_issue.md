---
title: "Suspend issue"
date: 2010-05-01
forum: Hardware
---

### Post by oz_ on 2010-05-01
Hi,

I have just recently upgraded my laptop to the new 10.04.

everything seems to have worked well except for the Suspend.

Now when I try to suspend I get a frozen laptop with a background in low resolution (sometimes flashing). This only happens on the second suspend. In other words the first suspend (sleep) works but then when I suspend again I get the issue as stated.

Has anyone else encountered this problem?
Is there a work around for this?

I am currently using an acer extensa 5630.

please help, I need my suspend back! ;)

---

### Post by oz_ on 2010-05-05
bump ... ](*,)
anybody ?

---

### Post by dino99 on 2010-05-05
sudo /etc/default/grub

find the line where "quiet splash" is

and modify it by: "quiet acpi=force"

then : sudo grub-mkconfig && update-grub
sudo update-initramfs -u
sudo dpkg --configure -a

(work for some users only sadly, you may google around with your config)

---

### Post by oz_ on 2010-05-05
thanks for the post,

However, I am not sure how changing the grub boot splash configuration will help.

---

### Post by SyAu on 2010-05-26
Its working for me and others also finding the same.

Please see this thread,

[http://ubuntuforums.org/showthread.php?t=1469340&page=4](http://ubuntuforums.org/showthread.php?t=1469340&page=4)

---

