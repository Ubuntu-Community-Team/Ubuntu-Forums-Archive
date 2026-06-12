---
title: "restarting and other problems"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by talbain on 2006-12-07
a friend of mine just bought a notebook into which i installed edgy...

the main problem is that i cant restart properly

i boot normally and everything goes fine, i log in and then choose to restart, ubuntu exits and i can see the bios messages, but then when it tries to boot again the screen goes black with a blinking cursor on top, the hard disk indicator turns on and remains like that, if i wait, 10 mins later the display shows "grub loading stage1.5" and if i wait another 10 mins i get "grub loading please wait..." and after that i can wait as much as i want, nothing happens. Some other times, it shows no messages and after a while the hard disk indicator turns off and nothing else happens.

its an old hitachi notebook, a japanese model (hitachi flora 220fx np7) intel 440bx chipset with a celeron 600 and 256 mb of ram.

everything seems to work fine except that... that, and the resume function, which wont wake up no matter what, i have to turn the notebook off.

i tried fiddling with the bios power management options to no avail and also disabling the acpi using acpi=off noacpi and adding the apm module.

the computer is not going to be using the batteries at all so i dont care about suspending, we dont really need it, but then i would like to at least remove the suspend option from the shutdown menu, and also restart if cant be fixed.

it would also be nice to disable the hardware *sleep* button because i found myself pressing it by accident.

thank you very much in advance for any ideas

---

### Post by 23meg on 2006-12-07
> 
i boot normally and everything goes fine, i log in and then choose to restart, ubuntu exits and i can see the bios messages, but then when it tries to boot again the screen goes black with a blinking cursor on top, the hard disk indicator turns on and remains like that, if i wait, 10 mins later the display shows "grub loading stage1.5" and if i wait another 10 mins i get "grub loading please wait..." and after that i can wait as much as i want, nothing happens. Some other times, it shows no messages and after a while the hard disk indicator turns off and nothing else happens.

Try the *acpi=noirq* kernel parameter.

> it would also be nice to disable the hardware *sleep* button because i found myself pressing it by accident.
In gconf-editor uncheck the /apps/gnome-power-manager/can_suspend key.

---

### Post by talbain on 2006-12-07
thanks for the quick reply,
disabling can_suspend removed the suspend choice from the shutdown menu, great!

but the restart function is still crazy, same symptoms after adding acpi=noirq :???:

---

### Post by talbain on 2006-12-08
well then... i guess i can live without the restart function... (wow! that sounds weird)

---

### Post by 23meg on 2006-12-09
Try the *irqpoll* kernel parameter as well; it helped me reboot properly on one occassion.

---

### Post by talbain on 2006-12-12
Thanks again, it didn't work.

---

