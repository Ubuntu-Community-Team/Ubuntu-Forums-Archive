---
title: "Nvidia problems"
date: 2022-01-25
forum: Hardware
---

### Post by leunam12 on 2022-01-25
Hello, I have a computer with Ubuntu 20.04, it is a dual boot with Windows 10 and two monitors. The computer was having problems with Windows with the dual-monitor setup and the video provided by the CPU (Intel i7 8700K), so I installed an Nvidia card (GEForce 1070Ti), it works well on Windows, no more crashing. On Ubuntu I have it running with the recommended driver (GP104), and it works but every time the computer comes back from suspend the bar at the top is garbled and so are the icons on the side bar, sometimes Firefox is also garbled, all I see is a colorful noise effect, the only way to fix it is to restart Gnome (Alt+F2+r). I wonder if someone may help me solve this. Thanks 

[https://ibb.co/442Y6xD](https://ibb.co/442Y6xD)

---

### Post by TheFu on 2022-01-25
Did you use Ubuntu's nVidia driver installer?  Never get GPU drivers directly from the vendor for us on Ubuntu.  It never turns out well.
The easiest solution, if you did get drivers directly from nvidia, is to change to a different tty, purse the existing nvidia drivers and support code nvidia*, then use
```
$ sudo ubuntu-drivers autoinstall
```
This will get the correct drivers for your card and your system and make APT handle all future patching/upgrades to those drivers.

A reboot might be necessary after the removal and again after the autoinstall.

All of this may not help, but at least you'll have the drivers everyone here expects you to be running.
If you used the GUI "Additional Drivers" to install the GPU drivers already, that's the same as the command above, just harder to explain across 10 *buntu flavors.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) has more details.

---

### Post by leunam12 on 2022-01-26
I tried it, but it installed the same driver, so, the problem remains. Thanks anyway

---

### Post by leunam12 on 2022-02-04
Apparently the last update solved the problem.

---

