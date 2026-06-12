---
title: "Lenovo G780"
date: 2013-10-23
forum: Hardware
---

### Post by mechevar21 on 2013-10-23
Pretty much got everything working on my Lenovo G780 in Ubuntu 13.10, amd64.  The hiccups I had were with wireless, hybrid graphics (intel/nvidia) and a blank screen on logout or use of the a control terminal (ctrl+alt+f1).  

I was able to get wifi working by reinstalling the broadcom drivers
```
sudo apt-get install --reinstall bcmwl-kernel-source
```

To get hybrid graphics working so that I could use my graphics card with a command like
```
optirun firefox
```
I had to install bumblebee
```
sudo apt-get install bumblebee bumblebee-nvidia
```

Finally, to deal with the blank screen I had to edit grub
```
sudo gedit /etc/default/grub
```
Make sure the options were set like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
Finally update everything
```
sudo update-grub
```
The brightness was really low on reboot, but editing the brightness via  the control panel (not hardware keys) got things permanently set.

---

### Post by vzkratos on 2013-11-05
thanks a lot i really mean that i just followed your steps on lenovo g780 running on ubuntu 13.04 and so far wifi is pretty stable i'll reboot and hopefully i don't loose wifi.

p.s. these 2 codes below didn't work but wifi does the terminal told  first command does not exixt or not found and the 2 one didn't have dependecies to be run  on 13.04,well so far so good.
optirun firefox
sudo apt-get install bumblebee bumblebee-nvidia

---

