---
title: "Fix for fan control and brightness on Toshiba laptops"
date: 2010-08-08
forum: Hardware
---

### Post by tadaskr on 2010-08-08
Hello everyone. Today I find how fix fan speed control and use fn + f6 f7 keys on Toshiba laptops. Maybe something like this is on other models. So there instructions: 
1) Install these packages from synaptic package manager toshset, toshutils, fnfxd, acpi-support, acpitool, acpitool-dbg if you have one or more of them installed remove it and use command in terminal > sudo update-grub. 
2) After these installed use command > sudo update-grub and restart computer
3) if it is working next time you restart or turn off computer this not work, so you need remove packages again use > sudo update-grub and install again, then again > sudo update-grub and then restart computer
I know, it's funny, but it is work for me on Toshiba satellite a300
If it work for someone write here and if someone know something better write here too :)

---

