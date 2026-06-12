---
title: "Ubuntu not booting from live CD on hp pavilion dm4-1162u"
date: 2011-04-22
forum: Hardware
---

### Post by gsphanikumar on 2011-04-22
Hi all,

I have a new laptop hp pavilion dm4-1162u(64 bit laptop). I am trying to install ubuntu 10.10 (64 bit) on the laptop. When i try to boot from the live CD, the screen goes blank after starting. It just stays like that even after 30 mins. 

Can any one help me with this please :confused:

---

### Post by gsphanikumar on 2011-04-27
Figured out that the while installing the Backlight goes off and need manually switch it on by pressing F3.

---

### Post by mrinvader on 2012-12-15
Try this kernel parameter as listed at the following:
[https://wiki.archlinux.org/index.php/Lenovo_Thinkpad_SL500](https://wiki.archlinux.org/index.php/Lenovo_Thinkpad_SL500)

Edit /etc/default/grub and insert acpi_backlight=vendor to the GRUB_CMDLINE_LINUX_DEFAULT line:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor quiet splash"

```

And then automatically re-generate the grub.cfg file with:
```
# grub-mkconfig -o /boot/grub/grub.cfg

```


Screen now starts with backlight enabled!!

search acpi_backlight=vendor in the google for more background on this..

---

### Post by rajhanschinmay on 2012-12-16
If you are not able to boot using live cd then kindly check ur cd again.

One best option available today is USB bootable pen drive.
Kindly create one using USB disk creator option in Ubuntu, give it ur .iso image file of the Ubuntu version u want and it will create u one bootable pen drive.

You can do live boot from it and also installations.
Advantage is that it is more reliable compared to a CD.

Thank you.

---

