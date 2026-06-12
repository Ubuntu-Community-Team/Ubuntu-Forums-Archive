---
title: "Permanent Location for HDDs"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by Maverickprowls on 2007-05-14
I've just installed Feisty Fawn after migrating from SuSE, and I'm having a slight difficulty with the way the system works.

It seems that I need to sudo to access one of the other (physical) hard-drives on my system.  I understand that this is because mounting drives is reserved for root, but is there a way of making my system mount them at boot so I have permanent access to them without having to enter my password?

The other issue I have is the dynamic mounting.  I use OpenOffice with it's "create backup" option set, and being a little paranoid, I like to keep the backups on a different physical drive. Ubuntu's way of doing things thus creates two problems for me.  First, if I haven't already mounted the drive I cannot access it; and second, if I mounted the drives in a different order the file-system address is different (i.e. /media/disk-1/BackUp as opposed to /media/disk-2/BackUp.)

Is there a simple way for me to enable mounting of the drives at boot to a set filesystem location, or am I going to be editing fstab again :-P

Thanks for the help.

---

### Post by Spartan.II.117 on 2007-05-14
editing fstab seems to be the only way to do it properly, idealy you should use the UUID's of each partition in order to prevent them from getting mixed up in any case.

---

### Post by Maverickprowls on 2007-05-14
How would I go about using the UUIDs to address the drives in, for example, OpenOffice's "Path" dialogue?

---

### Post by Spartan.II.117 on 2007-05-14
you wouldn't. you would use the uuid's in fstab to tell the system where to put each drive.

---

### Post by psusi on 2007-05-14
Yes, you need to edit your fstab to tell the system to mount the drive at boot.

---

### Post by Maverickprowls on 2007-05-15
Thanks for the pointers, I now have all my drives mounted where I want them.

---

