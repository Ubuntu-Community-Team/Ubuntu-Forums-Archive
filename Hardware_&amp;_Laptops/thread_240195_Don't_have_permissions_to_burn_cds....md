---
title: "Don't have permissions to burn cds..."
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by kufford on 2006-08-20
Hello all,

I'm having some difficulties using my dvd burner on my dell e1505. In both k3b and gnome baker, i get an error that my permissions won't allow it to access the cd. 

Here is my fstab: 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I've never ran into this problem before. Thanks for any help!

---

### Post by kufford on 2006-08-21
ttt?

---

### Post by ltmon on 2006-08-22
In K3B, when you get this error you can click on a button to get debugging information.

This will (most likely) show you that you have problems getting permissions for /dev/sg1 or something like that.

Next go the menu entry: Settings -> K3B Setup.  Type in your password.

The second box down in this screen is "Devices".  Check that your device that you don't have permissions for is listed here.  If not, add it.

And that should be it...  this should probably fix your issues with GnomeBaker also I think.

L.

---

### Post by kufford on 2006-08-22
Thanks for the reply. I had checked it out earlier but I can't find anything that I could change to alleviate the issue. I've attached a screen shot of the k3b setup. Please take a look.

---

### Post by ltmon on 2006-08-22
Yes that looks about right.

Try (not as root)
```

cdrecord --scanbus

```

This should give you an exact error on what devices is missing permissions.  For example, on mine (before I fix it) it gives

```

Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.

```

Then I just added /dev/sg0 to the list of devices in the K3B setup page and it fixed it for me.  I could have also done:

```

sudo chgrp cdrom /dev/sg0

```

L.

---

### Post by kufford on 2006-08-23
Hey... That worked. Thank you so much!

Could you please explain what this code does? 

```
sudo chgrp cdrom /dev/sg0
```

I like to know what is going on so I can keep learning... Thanks again

Ken...

---

### Post by ltmon on 2006-08-24
Well to understand that you need to read about the Unix security model.  A good start is here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

The simplest way I can explain is that:
 1. Everything in Linux acts like a file (i.e. the device /dev/sg0 is simply a file).
 2. You need to be able to write to that file.
 3. Making that file belong to the "cdrom" group means that everyone in the "cdrom" group can write to it.

I've just noticed on my computer that the device /dev/sg0 is resetting it's permissions every time I reboot, and I need to change them again.  I think it's a bug... the system isn't recognizing /dev/sg0 as part of the cdrom device and therefore not automatically making it owned by the cdrom group.

I'll post back if I find a solution.

---

