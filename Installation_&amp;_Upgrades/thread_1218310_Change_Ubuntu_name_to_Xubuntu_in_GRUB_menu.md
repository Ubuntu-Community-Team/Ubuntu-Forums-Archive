---
title: "Change Ubuntu name to Xubuntu in GRUB menu?"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2009-07-20
Hi.
I have installed Xubuntu as a dual boot with XP on my old PC. I notice that Xubuntu always shows up as Ubuntu in the GRUB menu.

Could I change the grub menu to rename Ubuntu to Xubuntu under
## ## End Default Options ##
in
```
gedit /boot/grub/menu.lst
```

I ask as I don't want to mess up the install without first checking.

---

### Post by presence1960 on 2009-07-20
yes, but you will need root permission to do so. preface the command with gksu or sudo.

---

### Post by ramnarayan on 2009-07-20
> **Rytron said:**
> Hi.
in
```
gedit /boot/grub/menu.lst
```

I ask as I don't want to mess up the install without first checking.

Yes you can
```
sudo gedit /boot/grb/menu.lst
```

navigate down to the line and replace whatever you want

*DON'T FIDDLE WITH ANYTHING ELSE*

also read:

[http://ubuntuforums.org/showthread.php?t=1213169&highlight=grub+bookmark](http://ubuntuforums.org/showthread.php?t=1213169&highlight=grub+bookmark)

***
infact once you get comfortable you can fiddle with quite a lot, like colors and such, even your own background image :-)

---

### Post by Rytron on 2009-07-20
Thanks guys. That was a very quick reply to my thread. I think this Ubuntu Linux society here is so helpful and friendly. Cheers.

---

### Post by ramnarayan on 2009-07-20
what comes around, goes around

:-)

---

