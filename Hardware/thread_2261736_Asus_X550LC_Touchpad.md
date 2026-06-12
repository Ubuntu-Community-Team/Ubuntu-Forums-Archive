---
title: "Asus X550LC Touchpad"
date: 2015-01-20
forum: Hardware
---

### Post by Hesediel on 2015-01-20
Hello my mom bought a Asus X550 and there is no way i can the touchpad working, i have issues also if i connect a usb mouse, it doesn't work. Any solution about that...it's like impossible also to install the system. My mom would like to use ubuntu but it seems that only windows works on this pc.

---

### Post by Pilot6 on 2015-01-21
Try to boot with 'i8042.noloop=1' parameter. The touchpad should work in mouse emulation mode.
If you need full support, you will have to install a custom kernel.

---

### Post by Hesediel on 2015-01-21
How can i do this? I don't know how to start that command
Ty

---

### Post by Pilot6 on 2015-01-22
run

sudo gedit /etc/default/grub

Edit the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

so it looks this way

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1"

Save the file.
Then run

sudo update-grub

and reboot.

---

