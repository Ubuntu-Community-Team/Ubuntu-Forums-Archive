---
title: "How to permanently fix graphic cards order in system?"
date: 2023-05-12
forum: Hardware
---

### Post by Raymond Curtis on 2023-05-12
Hello guys,

a Linux newbie here. I am using hardware acceleration(Intel and Nvidia based) in my programs, but recently I've discovered that the order of my graphics cards can change after reboot of the system. What I mean by that is that today, my order is like this:

ls -l /sys/class/drm/renderD*/device/drive
lrwxrwxrwx 1 root root 0 maj 11 20:54 /sys/class/drm/renderD128/device/driver -> ../../../bus/pci/drivers/i915
lrwxrwxrwx 1 root root 0 maj 11 20:54 /sys/class/drm/renderD129/device/driver -> ../../../../bus/pci/drivers/nvidia

So to renderD128 I have intel card attached and to renderD129 I have nvidia attached. However, yesterday before reboot, they were switched like this:

lrwxrwxrwx 1 root root 0 maj 11 20:54 /sys/class/drm/renderD128/device/driver -> ../../../../bus/pci/drivers/nvidia
lrwxrwxrwx 1 root root 0 maj 11 20:54 /sys/class/drm/renderD129/device/driver -> ../../../bus/pci/drivers/i915

This poses problem to my programs as they are expecting constant ordering of graphic cards. What can I do, to make that ordering constant? I would like to always have Intel under renderD128 and nvidia under renderD129.

Thank you for any help.

---

