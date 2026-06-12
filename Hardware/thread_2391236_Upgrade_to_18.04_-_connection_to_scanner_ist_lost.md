---
title: "Upgrade to 18.04 - connection to scanner ist lost"
date: 2018-05-07
forum: Hardware
---

### Post by Ben_Nemsi on 2018-05-07
Used to work with 16.04 and everything was fine.
After the upgrade to 18.04 I lost the connection to my epson perfection v80 scanner.
Even with the latest iscan (recent download from epson support site) i only get 
"could not send command to scanner. Check the scanner's status"

Now. One could say hardware or cable is broke ...

However  on a virtual 16.04 machine on the same host the scanner works perfect.

It is in deed annoying to fire up the virtual machine for scanning purposes only!

Please help!
Ben

---

### Post by ismaelteodoro on 2018-05-07
check udev rules
check by ~#udevadm monitor (plug and unplug device several times)
check permissions on ~#ls -la /dev/bus/usb/xxx/xxx/
~#crw------- 1 root root 189, 19 mai  7 21:55 020

---

### Post by Ben_Nemsi on 2018-05-09
Hi ismaelteodoro
thanks for you rreply.

since I'm not firm with udev you may have some additional advice

>check udev rules
what is to check here? 
checked the directory /etc/udev/rules.d and coudn't find a rule including a scanner.

>check by ~#udevadm monitor (plug and unplug device several times)
if I plug in I get:
[FONT=courier new]KERNEL[170983.342701] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0 (usb)
KERNEL[170983.342830] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0 (usb)
KERNEL[170983.343306] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-4 (usb)
KERNEL[170983.343427] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-4 (usb)
UDEV  [170983.346209] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0 (usb)
UDEV  [170983.347888] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0 (usb)
UDEV  [170983.350076] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-4 (usb)
UDEV  [170983.356347] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-4 (usb)
KERNEL[170983.801538] add      /devices/pci0000:00/0000:00:14.0/usb3/3-4 (usb)
KERNEL[170983.802056] add      /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0 (usb)
KERNEL[170983.804043] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0 (usb)
KERNEL[170983.804143] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-4 (usb)
KERNEL[170984.227485] add      /devices/pci0000:00/0000:00:14.0/usb3/3-14 (usb)
KERNEL[170984.228084] add      /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0 (usb)
KERNEL[170984.228261] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-14 (usb)
UDEV  [170984.375488] add      /devices/pci0000:00/0000:00:14.0/usb3/3-4 (usb)
UDEV  [170984.378169] add      /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0 (usb)
UDEV  [170984.378962] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0 (usb)
UDEV  [170984.379755] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-4 (usb)
UDEV  [170984.383574] add      /devices/pci0000:00/0000:00:14.0/usb3/3-14 (usb)
UDEV  [170984.385084] add      /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0 (usb)
UDEV  [170984.385923] bind     /devices/pci0000:00/0000:00:14.0/usb3/3-14 (usb)[/FONT]

unpluging  shows:
[FONT=courier new]KERNEL[171111.492585] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0 (usb)
KERNEL[171111.493081] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-14 (usb)
KERNEL[171111.493147] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-14 (usb)
UDEV  [171111.494985] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0 (usb)
UDEV  [171111.496855] unbind   /devices/pci0000:00/0000:00:14.0/usb3/3-14 (usb)
UDEV  [171111.503899] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-14 (usb)[/FONT]



>check permissions on ~#ls -la /dev/bus/usb/xxx/xxx/
>~#crw------- 1 root root 189, 19 mai  7 21:55 020
Permissions to the last plugged in usb device looks like 
[FONT=courier new]crw-rw-r-- 1 root root 189, 256 Mai  7 18:22 001
crw-rw-r-- 1 root root 189, 257 Mai  7 18:22 002
crw-rw-r-- 1 root root 189, 259 Mai  7 18:22 004
crw-rw-r-- 1 root root 189, 260 Mai  9 17:56 005
crw-rw-r-- 1 root root 189, 267 Mai  9 17:51 012[/FONT]

Does any of this make sense to you??

Looking forward to your reply
Ben

---

