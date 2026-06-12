---
title: "No Resume after Suspend on netbook Eee PC 1101HA"
date: 2014-04-25
forum: Hardware
---

### Post by Katzinski on 2014-04-25
Hi,

The problem occurs under Xubuntu 14.04. Once in Standby (S3), there is no way to resume. Power LED is blinking, no fan, no hard disk running, no backlight. Does not react to any key pressed. No way to shut down besides hard reset. Suspend worked before under Xubuntu 12.04. Standby cannot be accessed by pressing the power button (though set in the preferences of Xfce's power manager). Standby can be accessed by Xfce's menus, by closing the lid, and by *# echo mem > /sys/power/state*. I also checked *pm-is-supported --suspend* is positive.

I loaded latest BIOS (0323 of 12/01/09), tried boot kernel setting "acpi_osi=linux" and "acpi=force", tried to activate all devices listed in /proc/acpi/wakeup (there are only POP4, POP5, USB0, USB1, USB2 and EUSB) and tried to add *HandlePowerKey=suspend* to */etc/systemd/logind.conf* but I'm not sure if I configured that one correct. 

It seems that Suspend is not configured to notice when the power button is pressed. Does anybody know how to fix that? Could I try some other workaround? 
Thank you for reading. :)

---

### Post by eages on 2014-05-23
I'm seeing the same problem on Xubuntu 14.04 and Lubuntu 14.04. The laptop model is 1101HAb for both. I've also gone to great pains to resolve the issue but with no luck. Standby seemed to work perfectly before the upgrade to 14.04.

Edit: There are also several apportcheckresume errors once logged in on both systems.

---

### Post by gsedej on 2014-08-12
I have the same problem! (Ubuntu 14.04 + gnome shell classic)

THE PROBLEM is that "POWER BUTTON" does not work at all. If you press power button on desktop, nothing happens - kernel does not grab that button.
There is program "kbd_mode". If you run it in VT with parameter -s, you get raw input form all (hot)keys... except power button.
(I did use *acpi_osi=Linux and acpi_backlight=vendor*)

I think problem is in kernel - it works until kernel 3.13 (the Ubuntu 14.04 kernel). 

tested - works
3.9, 3.10, 3.11, 3.12
[B]tested - does not work
3.13, 3.16[/B]
(kernels from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/))
Something probably happened from 3.12 to 3.13

in dmesg I always get
```
[  4617.278] (II) config/udev: Adding input device Power Button (/dev/input/event4)
```
->it should be ok...

**solution**
Working, but not really good is to use kernel 3.12
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-trusty/)



This is also probably connected with kernel modul "eeepc_laptop" and "eeepc_wmi". the wmi is newer (still old), but ubuntu keeps loading "eeepc_laptop". Don't know how to use "eeepc_laptop". Neither is blacklisted in /etc/modprobe.d/
I might be wrong....
**edit1: its not connected with those modules **
sources
[https://bbs.archlinux.org/viewtopic.php?pid=1052065#p1052065](https://bbs.archlinux.org/viewtopic.php?pid=1052065#p1052065)
[http://lwn.net/Articles/391230/](http://lwn.net/Articles/391230/)
[http://xf.iksaif.net/blog/index.php?tag/eeepc-wmi](http://xf.iksaif.net/blog/index.php?tag/eeepc-wmi)

**edit: it is dependent on kernel parameter. Without parameter eeepc-wmi gets loaded, with acpi-osi=Linux eeepc-laptop.**  The wmi isn't able to switch wlan (Fn+F2).



**BTW - AUDIO**
Audio works very bad - like it's not synced,  "tearing"... Any idea why?

BTW2
there is effort to put 3D accel driver "EMGD" (intel prop blob) back to work. I did not yet test it...
[http://ubuntuforums.org/showthread.php?t=2107593](http://ubuntuforums.org/showthread.php?t=2107593)

---

### Post by gsedej on 2014-08-13
I reported bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1356229](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1356229)

---

