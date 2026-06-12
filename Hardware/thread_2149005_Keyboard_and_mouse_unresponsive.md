---
title: "Keyboard and mouse unresponsive"
date: 2013-05-27
forum: Hardware
---

### Post by fratellino78 on 2013-05-27
Hello,
I have installed Ubuntu 13.04 X64 on a desktop machine with ASUS M3N78-EM Motherboard (NVidia GeForce 8300 chipset).

Sometimes the mouse or keyboard (both USB and made by Logitech) stop working. Even Unplugging and plugging the device solves the problem, I must reboot the system.

Do you have any idea about the reason of this problem?

Thank you.

---

### Post by Jonor on 2013-05-27
When unplugging and replugging, are you tring all the different unused usb ports on the board and getting no response ?

---

### Post by fratellino78 on 2013-05-28
Yes I have tried also all other unused ports with same result.
When the mouse is unresponsive the LED of the optical sensor is still on, but when I unplug and plug again (in whatever USB port) the LED does not light again until I reboot the machine.

Thank you

---

### Post by Jonor on 2013-05-28
Depending on how you might want to solve the problem i suggest two things :

1. Analyse messages and google the results for solutions (might be time consuming)
Typing into a terminal :
```
dmesg | more
```
will start to list the messages at boot and perhaps hundreds of lines in (press return to move through the messages)
you should see the usb mouse and keyboard being found. Google any problematic looking keyboard / mouse messages or show them here 
if you are not sure and i might be able to help further.

2. Add another card to your system (might cost a little)
Sometimes the usb power on boards partially fails, if you happen to have one as i did when having a similar problem to you,
put a pci usb card into the board and try using the usb sockets on that if your Asus will allow it.

---

### Post by fratellino78 on 2013-06-04
Finally It seems I have solved this issue by disabling ACPI.

Thanks.

---

