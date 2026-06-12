---
title: "Controlling brightness on 12.04 Toshiba L650"
date: 2012-05-23
forum: Hardware
---

### Post by sn3ak3r on 2012-05-23
Good evening everyone, I've just installed today Ubuntu 12.04 and I'm very happy with all the great features, there's only one problem I can't control the brightness of the screen.

The fn keys works since the bar appears on the corner of the screen but it stays the same. Is there any way to fix this?


Thanks in advance for helping out.

---

### Post by hexion on 2012-05-24
This is what worked for me:

1) Edit /etc/default/grub and change this variable:
> GRUB_CMDLINE_LINUX="pcie_aspm=force acpi_osi=Linux acpi_backlight=legacy"2) Edit /etc/modprobe.d/blacklist.conf and add this line at the end of the file:
> blacklist toshiba_acpi3) Update the grub config file:
> sudo grub-mkconfig -o /boot/grub/grub.cfgReboot and the problem should be gone.
Good luck.

---

### Post by proseliet on 2012-05-26
> **hexion said:**
> This is what worked for me:

1) Edit /etc/default/grub and change this variable:


2) Edit /etc/modprobe.d/blacklist.conf and add this line at the end of the file:


3) Update the grub config file:


Reboot and the problem should be gone.
Good luck.

Added another quote at the end of the 'GRUB etc' line.
Works like a charm.
Thanks
Paul

---

