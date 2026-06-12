---
title: "Sony vaio LCD brightness problem"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by nakuro on 2007-10-01
I cant change the brightness in my sony vaio VGN fe31h, i tried some tutoriais:
[https://www.granny.homelinux.org/%7Elinho/files/delta.ubuntu]("https://www.granny.homelinux.org/%7Elinho/files/delta.ubuntu")
[https://help.ubuntu.com/community/SonyVaioBrightness?action=show&redirect=Changing+the+brightness+of+a+sony+VAIO]("https://help.ubuntu.com/community/SonyVaioBrightness?action=show&redirect=Changing+the+brightness+of+a+sony+VAIO")

but they had not resulted, and i cant change the brightness...
I tried change manually: sudo echo 4 > /proc/acpi/sony/brightness, but no result


hope that you guys can help me with this problem

---

### Post by adr50c on 2007-10-02
This works for Vaio FZ (vgn-fz11ll) using the nvidia 8400 chipset, running ubuntu 7.10

currently trying to getting fn keys working.

If you are running a laptop with the nvidia chipset and all packages are installed correctly, run following from a terminal:

```
nvidia-settings
```

brings up "nvidia x server settings".

scroll down to "X Server Color Correction." There you can change brightness settings.

Current solution is  add the nvidia-settings program to the top panel

add to panel/customs application launcher/ 

in the command box add nvidia-settings.

see also:

[http://ubuntuforums.org/showthread.php?t=486861](http://ubuntuforums.org/showthread.php?t=486861)

---

### Post by nakuro on 2007-10-05
Thanks a lot adr50c , i did it, my problem is resolved:)

---

### Post by hihihi on 2008-05-07
wrong way!!
this does not change the light brightness, but the color brightness,
nonono

---

