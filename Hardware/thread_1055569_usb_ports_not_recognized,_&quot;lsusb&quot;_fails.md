---
title: "usb ports not recognized, &quot;lsusb&quot; fails"
date: 2009-01-30
forum: Hardware
---

### Post by dragonpaint37 on 2009-01-30
AMD Athlon 64 x2 4200+ dual-cure 2.2 GHz
1GB DDR2 667MHz ram
Sapphire ATI Radeon x1950 pro 512 MB 

I just installed ubuntu 8.10 
I had a black screen but it was fixed by adding "noapic acpi=off irqpoll" at the end of the boot line before the installation. 
When i plug in any usb, such as, ipod, camera, or flash drive, the icon of it does not appear on my desktop, the device is not powered, and when i type in "lsusb" in the terminal there is no output.

Can someone please help?

---

### Post by nixscripter on 2009-01-31
The first place to look would be in the system bootup logs. Open a terminal and type: ```
dmesg | grep -i usb
```

See if the device appears in there. If you're not sure, you can post it here (make sure to put [code] forum tags around it).

---

### Post by dragonpaint37 on 2009-01-31
ol@ola:~$ dmesg | grep -i usb
[    1.938265] usbcore: registered new interface driver usbfs
[    1.938289] usbcore: registered new interface driver hub
[    1.938328] usbcore: registered new device driver usb
[    1.947257] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
ol@ola-dragon:~$

---

### Post by nixscripter on 2009-01-31
Okay, so it can see the controller.

Now, run this command: ```
sudo tail -0lf /var/log/messaegs
```

type your password, and plug in your drive. You should get a message or two about usb devices.

When you're done, hit Control-C to break out of it.

---

