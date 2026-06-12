---
title: "MSI Wind and Bluetooth/Wifi Switch"
date: 2009-03-23
forum: Hardware
---

### Post by mrmrmrmr on 2009-03-23
Hi,

I have a MSI Wind U100 netbook with internal bluetooth hardware.
This netbook also has a switch (Fn+F11) to cycle through wireless options (wifi , bluetooth, wifi + bt , none)

The switch functions very well on Win32 operating systems.
It also functions correctly on Linux Backtrack 4.
But on various Ubuntu versions (8.04, 8.10 , 9.X) the switch only affects the wireless led of the netbook.
Bluetooth led never turns on.

I noticed that during press Fn+F11 under Ubuntu following warning is written in logs:
```
Mar 9 18:21:55 ubuntu kernel: [ 1874.533998] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0).
Mar 9 18:21:55 ubuntu kernel: [ 1874.534029] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
Mar 9 18:21:55 ubuntu kernel: [ 1874.537842] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0).
Mar 9 18:21:55 ubuntu kernel: [ 1874.537863] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
```

Maybe it is related to non-recognized bluetooth hardware, but I don't know how to check that.
I'd like to state once more that other Linux distro (Backtrack) can use my bluetooth adapter and switch functions as expected.

Thanks.

---

### Post by mrmrmrmr on 2009-03-23
Any ideas ?

---

### Post by mrmrmrmr on 2009-03-24
Hi,

nobody has the same issue ?

---

### Post by kevinalle on 2009-05-17
same issue..
help appreciated

from: [http://wiki.msiwind.net/index.php/Ubuntu_9.04_Jaunty_Jackalope#Bluetooth](http://wiki.msiwind.net/index.php/Ubuntu_9.04_Jaunty_Jackalope#Bluetooth)
"some people are having problem with the Fn+F11 function hotkey not seeming to work correctly in Jaunty. For some, the command works without a problem. For others, it only works if your initial bootup bluetooth state is on; if the bootup bluetooth state is off, the Fn+F11 combo will not enable it. If that is the case for you, a workaround is to use Fn+F11 to enable it while running a different OS such as Windows or Ubuntu 8.10, and then reboot into Jaunty. Just make sure that you remember to turn your bluetooth back on again before you power down your Wind/Advent 4211, if you're suffering from this issue"

---

### Post by mrmrmrmr on 2009-05-17
Yes; I know that workaround.
But is it a real solution ? No.
Because on some Linux distributions (like Backtrack 4) Fn+F11 works as expected.

---

### Post by kevinalle on 2009-05-17
ok,
but i dont have another OS (and no CD drive)
how can I enable bluetooth?
thanks

---

