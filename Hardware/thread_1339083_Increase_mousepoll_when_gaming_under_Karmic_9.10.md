---
title: "Increase mousepoll when gaming under Karmic 9.10"
date: 2009-11-27
forum: Hardware
---

### Post by automaton26 on 2009-11-27
I've got a Logitech G5, and I'm trying to increasing the mouse poll rate. I can:

```
sudo nano /sys/module/usbhid/parameters/mousepoll
```
and change it to "2" - then unplug and replug the mouse.

But I'd like the setting made permanent. I've seen recommendations about adding "usbhid.mousepoll=2" to the kernel line, but that's the old GRUB way.

Has any serious gamer managed to do this with Karmic 9.10 ?

---

### Post by lloyd_b on 2009-11-27
Maybe add "usbhid.mousepoll=2" to the file "/etc/sysctl.conf"?  I *think* that accomplishes the same thing as the grub change.

Lloyd B.

---

### Post by automaton26 on 2009-11-27
Thanks - I've done that and rebooted, but I'm not sure how to confirm it's definitely set.

I can try playing UT2004 and checking if it seems more responsive, but that "/sys/module/usbhid/parameters/mousepoll" file still contains zero.

Any ideas how I can confirm the setting ?

---

### Post by automaton26 on 2009-11-27
I've also tried this:

> sudo rmmod usbhid && sudo modprobe usbhid mousepoll=2

After that, the /sys/module/usbhid/parameters/mousepoll file *does* contain 2, but I'm still not sure how to verify it is definitely set.

Anyone ?

---

### Post by automaton26 on 2009-11-27
I think I've got the solution to persisting the value of 2 after reboot. You just need to edit the /etc/modules file, and add the following section:

> # Change the mouse polling rate
-r usbhid
usbhid mousepoll=2


After a reboot, doing "cat /sys/module/usbhid/parameters/mousepoll" shows it as 2.

---

