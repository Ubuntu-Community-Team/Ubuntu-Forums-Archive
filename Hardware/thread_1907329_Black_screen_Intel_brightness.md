---
title: "Black screen Intel brightness"
date: 2012-01-11
forum: Hardware
---

### Post by nyslay on 2012-01-11
Hi.
Hello.
I have the same problem as that: [https://bbs.archlinux.org/viewtopic.php?id=116471](https://bbs.archlinux.org/viewtopic.php?id=116471)
```

The reason is that black screen, who appeared together with kernel26-2.6.37 (for the kernel26-2.6.38).
I have tried other Linux distributions with the same versions of kernel26 to check whether the kernel is actually the cause of the problem. It turns out that YES.
Yesterday on a separate partition I installed Arch with unlocked testing repository. I made complete configuration X(xfce4) and added user to all groups. Unfortunately, I only pre-load system. Log on to shell the user account and the execution startx is already taking place with the black screen. Graphical environment is loaded as if my monitor was only 10% brightness. To see what I'm doing on the desk, I have to watch from a distance of 5-10cm. Black screen appears regardless of whether the KMS is active or inactive.
I join the logs to read: dmesg.log and Xorg.0.log.
How to deal with this problem? Who should I report it?
If you need more information ... please write and I'll try to put them here.
```That solution work for me when i install Linux with the Kernel LTS (2.6.35), apply that solution and update
```

[I had the same problem, solved by adding a /etc/rc.local
setpci -s 00:02.0 F4.B=00

To adjust the brightness to add to the kernel line:
acpi_osi=Linux

```Have you any ideas how can I install Ubuntu 11.10 or 12.04(alpha/ daily build ??
Sorry for my English.

---

### Post by nyslay on 2012-01-13
Now I have correctly instaled Ubuntu 12.04 Daily Build (alternate CD), but I can it use/boot only in Safe Mode becouse in normal mode I have a black screan, but in Safe Mode everything was fine.

Have you any ideas what should I do to fix the normal mode ?

---

