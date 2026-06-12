---
title: "hibernation not working"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by danip on 2005-04-12
When I try to put my computer into hibernation it goes black screen, sounds like it is doing something  then it boots right back up to my normal desktop. Can anyone help?

---

### Post by Laurent Cazalet on 2005-04-13
- have you got a big enough swap partition? (about twice your RAM is needed I believe)
- is the RESUME parameter set in /etc/mkinitrd/mkinitrd.conf, as directed in 
[http://www.ubuntulinux.org/support/ReleaseNotes504/view?searchterm=RESUME](http://www.ubuntulinux.org/support/ReleaseNotes504/view?searchterm=RESUME)
- are you using acpi or apm (if you know). If you use acpi, maybe the poweroff method is not correct. check your acpi settings.
hth

---

### Post by danip on 2005-04-15
I guess it's my swap then.  I set it equal to the ammount of ram I have.

---

