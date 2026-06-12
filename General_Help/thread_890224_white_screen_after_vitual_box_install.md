---
title: "white screen after vitual box install"
date: 2008-08-14
forum: General Help
---

### Post by Howitzer777 on 2008-08-14
alright, i installed virual box but for some reason i installed a whole bunch of the others things listed in the synaptic manager. like virutal modules and stuff. it told me to restart. when i logged in the screen is pure white. i can still c my mouse, and my settings and everythings there,its just white. i kno my settings are there cause i can do the cubething. but its only.....white. please understand taht i have files on there that i cannot lose. is ther any fix to this? please help.

---

### Post by Gannon8 on 2008-08-14
Try pressing Ctl + Alt + F1, logging in, and uninstalling the packages.

And please use descriptive titles.

---

### Post by Howitzer777 on 2008-08-14
and how exactly do i get to uninstalling the files?


i tried reconfigureing the xserver but when i get to "add keyboard variant" i press okay and it stops.

---

### Post by overdrank on 2008-08-14
> **Howitzer777 said:**
> and how exactly do i get to uninstalling the files?


i tried reconfigureing the xserver but when i get to "add keyboard variant" i press okay and it stops.

Hi and what is the model of the graphics card and have you tried booting into recovery mode and use the xfix option?

Edit I have changed the title of the thread :)

---

### Post by Howitzer777 on 2008-08-14
> **overdrank said:**
> Hi and what is the model of the graphics card and have you tried booting into recovery mode and use the xfix option?

Edit I have changed the title of the thread :)


alright i went into failsafe gnome and completely removed the files but still no dice. 

i have ATI radeon hd 2600 xt 

failsafe=recorvymode?

do not know about the xfix option

---

### Post by overdrank on 2008-08-14
> **Howitzer777 said:**
> alright i went into failsafe gnome and completely removed the files but still no dice. 

i have ATI radeon hd 2600 xt 

failsafe=recorvymode?

do not know about the xfix option

Ok I assumed you are using Hardy. Recovery mode is usually the second choice from the grub. If you are not using Hardy then you may and try reconfigure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Howitzer777 on 2008-08-14
i'm using wubi. i don't have grub. i am using hardy but when i tryed taht code i get

```
jack@jack-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080814221713
jack@jack-desktop:~$
```

edit:i'm using wubi because when i used the live cd of hardy, it woudlnt let me install. it just froze

---

### Post by Howitzer777 on 2008-08-14
help/

---

### Post by overdrank on 2008-08-15
> **Howitzer777 said:**
> i'm using wubi. i don't have grub. i am using hardy but when i tryed taht code i get

```
jack@jack-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080814221713
jack@jack-desktop:~$
```

edit:i'm using wubi because when i used the live cd of hardy, it woudlnt let me install. it just froze

Hi and I am not familiar with installations with wubi. It sounds like that you installed some kernel additions for virtual box and it changed the kernel which in turn messed up your graphics. If the reconfigure does not work then I cannot help other than move to the Wubi forum and you may receive assistants there. :)

---

