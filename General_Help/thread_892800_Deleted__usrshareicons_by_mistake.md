---
title: "Deleted  /usr/share/icons/ by mistake"
date: 2008-08-17
forum: General Help
---

### Post by wivelden on 2008-08-17
Hi,
I wonder if anyone could help me.
I am running Hardy 8.04.1 and I accidently deleted the usr/share/icons folder and all the folders under it by mistake using gnome.
This means I deleted the default icons for battery and network etc and now I cant get online because of this.

How can I restore the folder back as a lot of programs are missing the icons?

Thanks

:oops:](*,)

---

### Post by Tim Sharitt on 2008-08-17
I suppose you could copy the /usr/share/icons/ from the live cd.

---

### Post by wivelden on 2008-08-17
I dont see it anywhere on the disc.

---

### Post by sisco311 on 2008-08-17
Open a terminal and run:
```
sudo aptitude reinstall gnome-icon-theme
```

---

### Post by Elfy on 2008-08-17
I assume you deleted them as root - did you do it with nautilus or the command line with rm.

Have you checked in roots trash to see if the folder is there still or did you empty trash.

---

### Post by wivelden on 2008-08-17
Do I need to be online to do this as I cant get online with the icon missing for wireless?

---

### Post by wivelden on 2008-08-17
Yes I deleted them as root under the terminal using the command rm.

---

### Post by wivelden on 2008-08-17
Anyone help as I have tried everything including downloading on a seperate pc the deb file gnome-theme-icons but it fails on install with no error.
:confused:

---

### Post by Elfy on 2008-08-18
Boot your livecd - then you will have to copy the directory from there to your installation

[http://ubuntuforums.org/showpost.php?p=3412160&postcount=5](http://ubuntuforums.org/showpost.php?p=3412160&postcount=5)

---

