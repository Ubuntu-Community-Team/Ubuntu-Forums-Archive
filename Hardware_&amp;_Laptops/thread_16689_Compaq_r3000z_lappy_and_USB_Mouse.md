---
title: "Compaq r3000z lappy and USB Mouse"
date: 2005-02-23
forum: Hardware &amp; Laptops
---

### Post by Guid0 on 2005-02-23
I have a compaq r3000 model laptop using x86 build distro of Ubuntu.  When I am booting, it loads the mouse as a generic PS/2 device.   cat /dev/psaux doesn't load the device and when I issue this in CLI, it freezes the machine.  I am apparently either NOT loading USB drivers or the USB mouse isn't loading correctly...any ideas? ](*,)

---

### Post by Guid0 on 2005-02-23
Failsafe doesn't load it either....just a quick tidbit...

---

### Post by gmc on 2005-02-23
[QUOTE=Guid0]I have a compaq r3000 model laptop using x86 build distro of Ubuntu.  When I am booting, it loads the mouse as a generic PS/2 device.   cat /dev/psaux doesn't load the device and when I issue this in CLI, it freezes the machine.  I am apparently either NOT loading USB drivers or the USB mouse isn't loading correctly...any ideas? ](*,)[/QUOTE]

Are you able to check what device driver are being loaded? (/sbin/lsmod). I recall having this problem with my system when I ran Debian. As I recall I had to add the following to /etc/modules

usbcore
mousedev

Note: usbcore also loaded usbhid, ehci_hcd and ohci_hcd - both *_hcd drivers were needed for me as my system supports usb v1.1 and v2.0

Gord

---

### Post by gmc on 2005-02-23
[QUOTE=Guid0]Failsafe doesn't load it either....just a quick tidbit...[/QUOTE]

Ohh! O-tay, try booting with the installation CD, then when you can switch to the command line console (alt-f2), try mking a temporary mount point, mount your harddrive (the partition with /etc on it) and try adding the drivers I suggested in my other message.

In case you're not sure

1) Boot from the install CD
2) Alt-F2 to switch to the command console
3) modprobe ide_generic
4) mkdir /tmpmnt
5) mount -t ext3 /dev/**hdaX** /tmpmnt (replace hdaX with appropriate drive)
6) nano /etc/modules
7) add usbcore
7a) add mousedev
9) Save the file and then reboot (shutdown -r now)

Gord

---

