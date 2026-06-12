---
title: "Wifi card not detected"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by JesusAddict3791 on 2005-06-20
I just installed Ubuntu on my laptop and it refuses to automatically detect my wifi card. I installed the drivers for it and got it working, but every time I reboot I need to insmod the drivers again before it'll detect it. Once I do that then all I have to do is go through Networking and activate it, then it works. How can I get it so that I don't have to insmod it every time I boot?

---

### Post by SqdnGuns on 2005-06-20
[QUOTE=JesusAddict3791]I just installed Ubuntu on my laptop and it refuses to automatically detect my wifi card. I installed the drivers for it and got it working, but every time I reboot I need to insmod the drivers again before it'll detect it. Once I do that then all I have to do is go through Networking and activate it, then it works. How can I get it so that I don't have to insmod it every time I boot?[/QUOTE]

Had the same problem......to prevent this from happening again, I diabled my "wired" NIC in the BIOS and probelm was solved. If I have to use a hardwired connection, I just re-enable it. When I disable it again, my wireless works just fine.

---

### Post by JesusAddict3791 on 2005-06-21
My BIOS doesn't have an option to turn off the integrated NIC. Insteard I tried unchecking "This device is configured" for eth0. That solved another problem I've been having when it was booting where if I didn't have eth0 plugged in then it would hang for a minute when initializing the network interface. It didn't fix the wifi card detection, though.

---

### Post by hw-tph on 2005-06-21
[QUOTE=JesusAddict3791]My BIOS doesn't have an option to turn off the integrated NIC. Insteard I tried unchecking "This device is configured" for eth0. That solved another problem I've been having when it was booting where if I didn't have eth0 plugged in then it would hang for a minute when initializing the network interface. It didn't fix the wifi card detection, though.[/QUOTE]
 Add the name of the module (without the .o or .ko file extension) that you're inserting manually to /etc/modules. That should be enough to create the actual device on boot. Then either configure it as usual using GUI tools or by editing /etc/network/interfaces.

Håkan

---

