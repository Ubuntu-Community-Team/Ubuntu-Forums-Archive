---
title: "installing xserver-xgl !! is it ok ??"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by cyrax2kx on 2008-04-10
[B][COLOR="DarkRed"]Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  libglitz-glx1 xserver-xgl libglitz1 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": no[/COLO[/B]R]


what should i do, i once said yes and there was no display after reboot. then i had to install ubuntu again. please tell me what to do now ??

:confused:

---

### Post by chewearn on 2008-04-11
This will usually fix the error message:
```
sudo apt-get update
```

Sometimes, you still get the error message, then try again another day.  It's usually sorted itself within a day.

If you are using nvidia restricted driver, do not install xserver-xgl.

---

