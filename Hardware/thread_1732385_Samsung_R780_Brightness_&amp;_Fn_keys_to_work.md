---
title: "Samsung R780 Brightness &amp; Fn keys to work"
date: 2011-04-18
forum: Hardware
---

### Post by Mido_67 on 2011-04-18
Hello,
To make work fn keys and brightness adjustment please do what follow:

install nvidia-bl-dkms & samsung-tools >> cmd: sudo add-apt-repository ppa:voria/ppa
sudo apt-get install nvidia_bl_dkms
sudo apt-get install samsung-tools

then edit grub >> cmd: sudo gedit /etc/default/grub

modify this line like that: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=Red]acpi_osi=linux acpi_backlight=vendor splash[/COLOR]"

and update grub >> cmd: sudo update-grub

and finally edit /etc/modules >> sudo gedit /etc/modules by adding this line: nvidia_bl max_level=0x1ffff shift=11

now reboot and enjoy!

---

