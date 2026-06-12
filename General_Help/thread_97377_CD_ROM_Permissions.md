---
title: "CD ROM Permissions"
date: 2005-11-30
forum: General Help
---

### Post by LinuxLars on 2005-11-30
New to Ubuntu - I do like what I see. However, WHY are the default permissions for writing to CD's root only? 

And - what's the best way to change that in Ubuntu? So that if you load the CD, you can write to it.

Thanks.

---

### Post by Bachstelze on 2005-11-30
I can run GnomeBaker just fine without root access... What's your problem ?

---

### Post by invalid on 2005-11-30
If you are mounting the cd as a root user, you must be root to make modifications on it.

Default settings, however, are for the user to have permissions. Check your /etc/fstab file for a line that looks like
```
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

```
If you are missing this, it could quite likely be your problem.

Cb

---

### Post by LinuxLars on 2005-12-01
Cb - thanks.

My /etc/fstab has a line:

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

If I wanted any user (since this is a laptop) to be able to create writable CD's....

---

### Post by akiro.yamamoto on 2005-12-01
It's not necessary for any user to have write access to the cd-rw drive..
It's very easy... any user can create data, music or video cd/dvd without it...
None of the Gnome writing utilities need write access to the drive in order to write to the media....

This is my entry:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
And with the above setting in my fstab file I can burn audio cds, DVDs etc with no problem.
I'm not sure about KDE apps... like K3B et all.... but I believe that the above will work with them as well..
Regards.
:smile:

---

