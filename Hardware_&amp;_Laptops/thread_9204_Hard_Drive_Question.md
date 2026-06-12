---
title: "Hard Drive Question"
date: 2004-12-25
forum: Hardware &amp; Laptops
---

### Post by dgantony on 2004-12-25
Hi all,
   I am a new Linux user (about 4 weeks now). I've been trying a bunch of distros (Mandrake, Fedora, Suse) and finally found Ubuntu. I like it and looks like I finally found THE distribution thanks in part to this excellent and very helpful forums.

   Now my question. I have a bunch of external USB harddrives connected to my laptop running Ubuntu. I usually turn them off when I shut down. When I start the computer the next day, the mounting gets messed up. All of them are in /dev/sd*. I've set up my /etc/fstab so that /dev/sda1 will mount on /mnt/extdrv1, /dev/sdb1 on /mnt/extdrv2 and so on. The problem is /dev/sda* does not always point to the same drive.  So during one session, /mnt/extdrv1 may be hard drive #1 and in another session, it may be drive #2. This becomes even more complicated when I plug in my ipod. Is there any way to fix /dev/sd* to certain drives? 

Thanks.

George.

---

