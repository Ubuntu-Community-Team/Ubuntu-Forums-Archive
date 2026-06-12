---
title: "usb-pendrive weirdness - 2 icons on the desktop"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by neutronstar on 2005-11-18
Hi,

when I plug my usb-pendrive, I get 2 icons on the desktop: "usbdisk" and "usbdisk-1". They're both under /media.

"usbdisk" reports 250MB, while "usbdisk-1" reports 249.8MB. Only "usbdisk-1" shows the real content of the pendrive, "usbdisk" is useless and cannot be mounted.

When I click "unmount" on "usbdisk-1", it disappear and I cannot remount it without phisically unplugging it from the port.

On the pendrive there is only a FAT32 primary partition.

All those things do not happen with another pendrive and a USB external harddisk, both formatted as FAT32. It works like a charm with these.

Anybody has an idea of what's going on?

Thanks

---

### Post by daller on 2005-11-18
[QUOTE=neutronstar]Hi,

when I plug my usb-pendrive, I get 2 icons on the desktop: "usbdisk" and "usbdisk-1". They're both under /media.

"usbdisk" reports 250MB, while "usbdisk-1" reports 249.8MB. Only "usbdisk-1" shows the real content of the pendrive, "usbdisk" is useless and cannot be mounted.

When I click "unmount" on "usbdisk-1", it disappear and I cannot remount it without phisically unplugging it from the port.

On the pendrive there is only a FAT32 primary partition.

All those things do not happen with another pendrive and a USB external harddisk, both formatted as FAT32. It works like a charm with these.

Anybody has an idea of what's going on?

Thanks[/QUOTE]

Did you incidentially format /dev/sda instead of /dev/sda1???

...If so, I'm having the same problem :)

---

### Post by neutronstar on 2005-11-18
[QUOTE=daller]Did you incidentially format /dev/sda instead of /dev/sda1???

...If so, I'm having the same problem :)[/QUOTE]

No, I even tried to reformat it under windows without any luck...

Greetings from Milano, Italy

---

### Post by chinocracy on 2007-01-31
I'm having the problem of the USB thumb drive disappearing from my desktop.
Maybe it has to do with getting specific files related to one's kernel being used. For example, the files from: 
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/)
(since I use this kernel)
Perhaps you might need to reinstall the USB-modules files specifically for your kernel version... unless you've done so already.

---

### Post by disturbedite on 2007-01-31
> **neutronstar said:**
> Hi,

when I plug my usb-pendrive, I get 2 icons on the desktop: "usbdisk" and "usbdisk-1". They're both under /media.

"usbdisk" reports 250MB, while "usbdisk-1" reports 249.8MB. Only "usbdisk-1" shows the real content of the pendrive, "usbdisk" is useless and cannot be mounted.

When I click "unmount" on "usbdisk-1", it disappear and I cannot remount it without phisically unplugging it from the port.

On the pendrive there is only a FAT32 primary partition.

All those things do not happen with another pendrive and a USB external harddisk, both formatted as FAT32. It works like a charm with these.

Anybody has an idea of what's going on?

Thanks

did you accidentally partition the filesystem?

---

