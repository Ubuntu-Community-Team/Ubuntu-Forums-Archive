---
title: "external hard drive not detecting"
date: 2011-08-22
forum: Hardware
---

### Post by aloksethi on 2011-08-22
Hi,
I have an external hard drive (80 gb, almost 3 years old). It is not getting detected in 11.04 ubuntu.
The same drive used to work on 8.10  on the same laptop. It is also working on another Dell laptop with 10.10 on it.
dmesg shows the following
```

[ 4032.540313] usb 2-1: new high speed USB device using ehci_hcd and address 17
[ 4032.683565] scsi16 : usb-storage 2-1:1.0
[ 4055.120045] usb 2-1: reset high speed USB device using ehci_hcd and address 17
[ 4065.364079] usb 2-1: reset high speed USB device using ehci_hcd and address 17
[ 4081.608116] usb 2-1: reset high speed USB device using ehci_hcd and address 17
[ 4081.856218] usb 2-1: reset high speed USB device using ehci_hcd and address 17
[ 4092.100058] usb 2-1: reset high speed USB device using ehci_hcd and address 17
[ 4092.233358] scsi 16:0:0:0: Device offlined - not ready after error recovery

``````

root@baba-laptop:/etc/udev/rules.d# lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 017: ID 3495:8666**  
Bus 002 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I am running 11.04, kernel version is 2.6.38-11. no sd* device is getting shown in 
fdisk -l either

Thanks

---

### Post by aloksethi on 2011-08-22
anybody??

---

### Post by Basher101 on 2011-08-22
do you have windows? does it work on windows then?

---

### Post by aloksethi on 2011-08-22
yes it works in windows too

---

### Post by aloksethi on 2011-08-22
problem solved
seems to be problem caused by a loose usb port
not sure why my 750gb external drive(external powered) works seamlessly with the same cable and same port but with this drive I have to twist the cable a little bit

---

