---
title: "Computer name conflicting with bluetooth manager..."
date: 2013-01-29
forum: Hardware
---

### Post by CajunPirate on 2013-01-29
Running 12.10 on an Acer Chromebook. I originally followed the "chrubuntu" installation procedure which gave my computer the default name: "Chrubuntu"

Using the "gksudo gedit /etc/hostname" method, I renamed my computer. 

Popped in my bluetooth dongle and installed Blueman Bluetooth Manger which gave me the option of searching for devices which "Chrubuntu-0" or "MyNewComputerName-1"

Nothing showed up with "Chrubuntu-0" but my mouse successfully linked and worked under "MyNewComputerName-1"
No surprise there.

However, after removing Blueman, I attempted to do the same with the default Bluetooth Manager. No dice. But I noticed something odd. By the Visibility toggle it says: "Visibility of "Chrubuntu-0"

My guess is that the default bluetooth manager is still looking for something associated with the old computer name. Re-installing the manager did not work.

-Cheers!

---

### Post by CajunPirate on 2013-01-29
Nevermind. Removed the default manager, rebooted, re-installed the manager, voila.

---

