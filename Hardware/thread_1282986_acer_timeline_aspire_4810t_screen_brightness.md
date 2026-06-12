---
title: "acer timeline aspire 4810t screen brightness"
date: 2009-10-05
forum: Hardware
---

### Post by defazn on 2009-10-05
Screen brightness adjusting don't work. Brightness stays at one level and its not the brightest. I already tried one of the suggested solutions where i can change the brightness in terminal, that didn't help. any more solutions? thanks  (im on the latest ubuntu 9.10 beta, same thing happened with other ubuntu versions)

---

### Post by cnkk on 2009-11-03
I've got the same problem.. any solutions? :/

---

### Post by miegiel on 2009-11-03
I don't have this problem with my 3810T (as long as my caps-lock isn't on), but this has been discussed in several threads already. [Acer Timeline 4810TG on Jaunty - ATI Driver]("http://ubuntuforums.org/showthread.php?t=1242590") and [Acer Timeline 3810T]("http://ubuntuforums.org/showthread.php?t=1165087") (46 pages discussing all timelines, not just the 3810T) to mention just 2 of them. From what I've understood some people have gotten it to work while others haven't.

---

### Post by seomka on 2009-11-04
Me too!

---

### Post by iamcowdrunk on 2010-03-24
If you add 'nomodeset acpi_backlight=vendor' to the grub boot menu it should solve the problem. However it might mess up the boot sequence visually [confirmed in 10.04] but once you get the the login screen it will be all pretty again.

---

### Post by Foxcow on 2010-06-17
> **iamcowdrunk said:**
> If you add 'nomodeset acpi_backlight=vendor' to the grub boot menu it should solve the problem. However it might mess up the boot sequence visually [confirmed in 10.04] but once you get the the login screen it will be all pretty again.

Do you put it anywhere in there uncommented?

---

### Post by gizmo_3010 on 2011-02-26
but is there a right solution for this?

---

