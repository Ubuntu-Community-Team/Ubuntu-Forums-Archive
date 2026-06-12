---
title: "keyboard not working:::sort of"
date: 2009-01-17
forum: Hardware
---

### Post by Re1lly on 2009-01-17
hello
yesterday i left my laptop on working perfectly.came back after fifteen minutes and the keyboard stopped working: after going crazy for a while pressing all the keys like an idiot i figured out that by holding the shift key i am able to write and do stuff:
i cant even highlight any type of text (to copy and paste) or click on the menus without holding the shift key and the keyboard is just useless unless i keep it pressed the whole time
:::and no punctuation as you can tell!!

i have absolutely no idea on what to do any suggestions?thanks!!!!

---

### Post by linux_tech on 2009-01-17
Did the keyboard work again after a restart? 
what make and model laptop is this?  What kernel are you using?

---

### Post by Re1lly on 2009-03-18
problem still exist from time to time;sometimes it last for three or four days and then disappears for like a week and then comes back again even after latest updates; i found a work around to get my usb keyboard and mouse to work but then the laptop keyboard and the touchpad dont work untill next restart and it goes back to not working just like i described above;                                                                again sorry but i cant punctuate :S                     i have an acer5672 wlmi

---

### Post by Re1lly on 2009-03-18
sorry forgot to mention: this is the workaround:```
sudo sh -c 'echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind'

```

---

### Post by Re1lly on 2009-04-18
UP!! problem still persists. the workaround completely turns off the built-in keyboard and touchpad.

---

### Post by Re1lly on 2009-09-09
Sorry if i continue to UP this post but i've updated to jaunty and i have been experiencing this problem again for a week.

does anybody know if this problem has been brought up elsewhere? the only thing i get when i search for this are suspend/hybernate related issues..

THANKS!!!!!!

---

