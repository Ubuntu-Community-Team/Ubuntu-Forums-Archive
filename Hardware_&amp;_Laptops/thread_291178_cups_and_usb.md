---
title: "cups and usb"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by Lykurg on 2006-11-02
Hi,

I have problems to install my Kyocera usb printer. Usb is correct installed, but I get no interface to usb in my cpus.

```
lykurg@philoktetes:~$ lsusb
[...]
Bus 002 Device 002: ID 0482:0010 Kyocera Corp.

lykurg@philoktetes:~$ ls -la /dev/usb*
crw-rw---- 1 root lp 180, 0 2006-11-02 11:28 /dev/usblp0

lykurg@philoktetes:~$ lsmod | grep usb
usb_storage            73408  1
scsi_mod              141320  4 sg,sd_mod,sbp2,usb_storage
libusual               15632  1 usb_storage
usbhid                 42464  0
usblp                  14336  1
usbcore               130304  8 usb_storage,libusual,usbhid,usblp,ehci_hcd,uhci_hcd

lykurg@philoktetes:~$ lpinfo -v
network socket
network beh
network bluetooth
direct hp:/no_device_found
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct canon:/dev/lp0
direct epson:/dev/lp0
network smb
```

How I can make, that there is also an "direct usb:/dev/usblp0"?


Thanks,

Lykurg

---

