---
title: "USB disk problem"
date: 2008-05-01
forum: Hardware
---

### Post by rado3105 on 2008-05-01
I am using USB disk formated to ext3 in samba sharing, the problem is that disk after a while is not accesible(at first it is).
When I try dmesg, it shows many lines with:
>  46
[43320574.510000] usb 4-4: device descriptor read/64, error -71
[43320574.740000] usb 4-4: device descriptor read/64, error -71
[43320574.970000] usb 4-4: new high speed USB device using ehci_hcd and address                                                                 47
[43320575.090000] usb 4-4: device descriptor read/64, error -71
[43320575.320000] usb 4-4: device descriptor read/64, error -71
[43320575.550000] usb 4-4: new high speed USB device using ehci_hcd and address                                                                 48
[43320575.970000] usb 4-4: device not accepting address 48, error -71
[43320576.090000] usb 4-4: new high speed USB device using ehci_hcd and address  

and when I use df -Th, it shows the same disk mounted two times, and they cant unmount(device is busy).
> 
root@ubuntu:~# df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3    3.8G  634M  3.0G  18% /
varrun       tmpfs    125M  100K  125M   1% /var/run
varlock      tmpfs    125M  4.0K  125M   1% /var/lock
udev         tmpfs    125M   80K  125M   1% /dev
devshm       tmpfs    125M     0  125M   0% /dev/shm
/dev/sda1     ext3    917G  544G  328G  63% /media/WD1TB
/dev/sdb1     ext3    917G  544G  328G  63% /media/WD1TB

Only restarting the system helped, could you tell me what is the problem?

---

