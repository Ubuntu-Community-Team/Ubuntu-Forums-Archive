---
title: "USB-problems with LG E300"
date: 2008-11-18
forum: Hardware
---

### Post by Diskdoc on 2008-11-18
Running Intrepid Ibex (amd64) with the latest updates on my new laptop. Everything works fine now (needed to manually install .deb for WLAN) except the USB-ports.

USB works..somewhat. I'm able to use a GSM-modem for internet and occationally to mount and use a flash memory. But working with files on an external hard drive results in errors and moving larger files to a USB-memory likewise. Mounting takes a long time.

Here's some dmesg output from just inserting a USB-flashmemory:

[ 3635.708076] usb 1-1: new high speed USB device using ehci_hcd and address 22
[ 3650.856080] usb 1-1: device descriptor read/64, error -110
[ 3666.096110] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 164
[ 3666.108076] usb 1-1: device descriptor read/64, error -110
[ 3666.324077] usb 1-1: new high speed USB device using ehci_hcd and address 23
[ 3681.472079] usb 1-1: device descriptor read/64, error -110
[ 3696.725041] usb 1-1: device descriptor read/64, error -110
[ 3696.940057] usb 1-1: new high speed USB device using ehci_hcd and address 24

Any module/kernel-options I should try? "noapic" didn't help.

---

### Post by Diskdoc on 2008-11-19
Also having WLAN-trouble. Samba on the house network barely works and fails quickly. Lots of theese in dmesg:

[24940.524066] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 164
[25060.540062] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 164
[25180.556062] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 164

..later. Fixed WLAN problems using newer driver. Still having USB-problems!

---

### Post by Diskdoc on 2008-12-03
After much trying and Googling I finally stumbled upon a solution:

modprobe -r ehci_hcd

before plugging in the external USB drive! Seems like some kind of kernel bug, although as I understand it it would be more correct to put the blame on hardware not following the USB specifications.

---

