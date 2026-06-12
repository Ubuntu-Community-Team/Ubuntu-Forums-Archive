---
title: "howto: backlight fix acer aspire 5734z ubuntu 11.series"
date: 2011-10-09
forum: Hardware
---

### Post by SE7EN-LOCSTA on 2011-10-09
there are alot of various workarounds to fix the backlight issue that started in ubuntu 11.04, and have continued into 11.10 (at least til beta2). my fix is as follows, and WILL allow backlight to come on after dim/suspend.

to install:
set command 'acpi_os= "
- i dont know if it is needed, but hold your brightness button up in as it boots.

once installed:
Edit /etc/default/grub, edit the line GRUB_CMDLINE_LINUX_DEFAULT:
GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash acpi_os= "

also, /etc/rc.local and add before exit 0:
"setpci -s 00:02.0 F4.B=00"

[on all above there is a space after acpi_os= 
this has fixed the backlight issue for me, confirmed on Ubuntu 11.04, Ubuntu 11.10 beta2, and BackTrack5 r1 [kde], all x64 versions. I don't know why this works, or what these commands do, but this is the combination that FINALLY allow me to enjoy the 11 series... using 'acpi_os=linux" would not turn the backlight back on after suspend/screen dim. this will NOT return brightness up/down functions, you will be at 100%, but at least you won't have to run a command or reboot if your screen dims/suspends.

---

### Post by ariesjd on 2011-10-21
Hi! I have an acer aspire 5734z too, and i want ubuntu 11.10 on it, but i´m quite new on this stuff, please, can you help me a bit more, where do i have to run this commands? in the instalation? or until the instalation is finished?

---

