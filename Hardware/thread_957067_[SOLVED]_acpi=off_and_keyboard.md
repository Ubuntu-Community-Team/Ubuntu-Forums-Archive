---
title: "[SOLVED] acpi=off and keyboard"
date: 2008-10-23
forum: Hardware
---

### Post by lgeek on 2008-10-23
i am having a lenovo 3000 y500 laptop.i am using hary heron and vista with dual boot.my keyboard and touchpad are not detected in ubuntu while they work fine in vista. i tried searching it on net and found that i have to pass acpi=off boot parametre while booting.i did the same thing.however,now when i use acpi=off the sound of the laptop does not waork and also i cannot use suspend or other battery modes.infact there is no battery icon being displayed.without acpi=off everyhing works fine except the touchpad and keyboard.can anybody fix this so that my keyboard is detected and the sound also works...plz help..

---

### Post by lgeek on 2008-10-25
it has been long enough no body replied to the post.i made a vigorous google search for the same problem and was lucky to found a sloution that worked which i am posting here too.
instead of acpi=off i passed the boot parametre i8042.reset and it worked like a charm.i do have now sound working and keyboard n touchpad too. i learnt that acpi has got some issue with 8042 interrupt controller.i can't say wether this is going to work for other or not but may be it can be of use.
for some guys i8042.nomux=1 may work.finally i appended the line
in /boot/grub/menu.lst adding i8042.reset

---

### Post by rakris on 2008-10-31
hi lgeek.
Thanks. I was looking for this.

---

### Post by rakris on 2008-10-31
Can I know your model number. Just want to make sure If I can follow your method when i get back home.

Mine is 776137Q.

---

