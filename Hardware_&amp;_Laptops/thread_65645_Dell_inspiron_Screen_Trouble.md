---
title: "Dell inspiron Screen Trouble"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by Hairy_Palms on 2005-09-14
i have adell inspiron 5160 and i have a problem that when i close the lid the screen doesnt go off, ive tried a number of solutions editing /etc/acpi/lid.sh and none of them have worked, anyone else got any ideas to get the screen to turn off when i close the lid?

---

### Post by bullpa on 2005-09-14
co-ask for my Inspiron 6000

---

### Post by mlord on 2005-09-14
Enable "lid" events for acpid?

In Kubuntu, this is in the (KDE) Control_Center -> Power_Control -> Laptop_Battery ->  menus.

---

### Post by Hairy_Palms on 2005-09-15
im using gnome not kde and the lid event is enabed, ive tried running the lid.sh manually and this is the output
> xscreensaver-command: warning: $DISPLAY is not set: defaulting to ":0.0".
xscreensaver-command: not throttled.

cat: /var/lib/acpi-support/lidstate: No such file or directory
chvt: Wrong number of args


if that helps thanks in advance

lid.sh calls /usr/share/acpi-support/screenblank and if i manually run the screenblank script it turns off the screen so i can only assume its not calling the screenblank script.

---

### Post by Hairy_Palms on 2005-09-16
noone? :(

---

