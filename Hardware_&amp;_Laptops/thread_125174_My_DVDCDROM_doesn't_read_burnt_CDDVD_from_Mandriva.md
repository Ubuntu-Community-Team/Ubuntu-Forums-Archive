---
title: "My DVD/CDROM doesn't read burnt CD/DVD from Mandriva &amp; Windows"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by Europeen on 2006-02-03
Hello people !

My Plextor PX-716A DVD-CD/RW burner refuse to read all CD/DVD burnt under Mandriva and Windows. If I burn under Ubuntu, I can read this one.

Mount :

> 
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=kawada)
/dev/hdd on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=kawada)



Fstab :

> /dev/hdc        /media/cdrom0   udf,utf8 ro,user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


Thanks for your help !

Under Ubuntu Breezy.

---

### Post by MentalPatient on 2006-02-03
The only thing I can think of that would explain things is that perhaps you're trying to mount packet written media as is9660 when you should be using udf?

Try changing the filesystem type to auto and see if that helps. Barring that, I have no other ideas.

HTH

---

### Post by Europeen on 2006-02-04
[QUOTE=MentalPatient]Try changing the filesystem type to auto and see if that helps. Barring that, I have no other ideas.

HTH[/QUOTE]

Hi! I tested  :

> /dev/hdc        /media/cdrom0   auto,iso8859-15 ro,user,noauto     0       0

> /dev/hdc        /media/cdrom0   auto,iso9660 ro,user,noauto     0       0

> /dev/hdc        /media/cdrom0   udf, ro,user,noauto     0       0

But nothing.

Well, can we consider this problem is a bug ?

---

### Post by lcg on 2006-02-04
[QUOTE=Europeen]Well, can we consider this problem is a bug ?[/QUOTE]
If it were, I'm pretty sure a lot of people had stumbled upon it before.

First of all, try one of the problematic CDs on another Ubuntu box. In those very rare cases where a bug exists on only one computer most often it is no bug at all.
Second, please remove UTF-8 or ISO-8859-15 as file systems from your fstab. Those are text encodings, not file systems. :)

HTH,
Lars

---

### Post by Europeen on 2006-02-05
Hello !

I should reboot to execute something... And now..... :

I can read Windows CD/DVD, but always impossible for Mandriva CD/DVD. :)

---

