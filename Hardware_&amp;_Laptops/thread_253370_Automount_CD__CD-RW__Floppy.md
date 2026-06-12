---
title: "Automount CD / CD-RW / Floppy"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by gushy on 2006-09-08
Not sure what broke my system, but it no longer automounts cds or floppies.  Checking dmesg after putting a CD show no new entries at all so I'm kinda stuck as to diagnosing the problem

I can still manually mount my drives, so it's just the automounting that's gone.

---

### Post by Leppiz on 2006-09-09
I'm experiencing the same problem with my 64-bit Dapper. Laptop with 32-bit Dapper works just fine. USB Drives mount fine on both systems.

I can mount the CD-drive manually, but it won't show on desktop.

---

### Post by tommcd on 2006-09-10
have you had a look at /etc/fstab? You should have a line similar to this (from my /etc/fstab):

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Has your /etc/fstab changed?

---

### Post by Leppiz on 2006-09-10
I've got the line there
```

leppis@kissa:~$ cat /etc/fstab | grep hd
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto 0       0

```

---

### Post by gushy on 2006-09-10
my fstab is fine, no changes from before.

---

### Post by Leppiz on 2006-10-01
I solved this problem by first completely removing hal, hal-device-manager, gnome-volume-manager and after that installing ubuntu-desktop again from the command line. Now cds automount again :)

---

### Post by gushy on 2006-10-01
I'll have to try that.  The problem fixed itself for a while but it's appeared again, so this could be the solution.

Thanks.

---

### Post by gushy on 2006-10-03
yup that worked a treat, thanks Leppiz.

---

