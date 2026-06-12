---
title: "Ubuntu 11.10 and Samsung NP300E5Z brightness prob"
date: 2012-02-15
forum: Hardware
---

### Post by 3dmatrix on 2012-02-15
In my Samsung NP300E5Z series laptop i could not use the function keys to control brightness. Even if i adjusted the brightness, in Ubuntu 11.10, it got reset on every boot to maximum. Moreover, on every boot the bluetooth and wifi used to remain ON.

I added the following lines to the /etc/rc.local file

echo 0 > /sys/class/backlight/acpi_video0/brightness
rfkill block bluetooth
rfkill block wifi

* after that, bluetooth and wifi prob was solved.
* the brightness used to remain as per adjusted value unless i again tried to adjust it, when it would suddenly jump to maximum. Same thing happened in case of computer running on battery.
* Still could not use the function key to control brightness.

then i edited the /etc/default/grub file and added acpi_backlight=vendor
to make the line as 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

* after that the brightness could be controlled by the function keys at GRUB screen and after booting is complete but not at User login, but 
* the brightness level again resets to Maximum after every boot
* and bluetooth again gets ON after every boot.

Plz advise

---

### Post by 3dmatrix on 2012-02-18
Can anyone plz help with this !

---

