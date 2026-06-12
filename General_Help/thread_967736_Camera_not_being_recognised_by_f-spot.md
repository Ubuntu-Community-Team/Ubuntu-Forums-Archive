---
title: "Camera not being recognised by f-spot"
date: 2008-11-02
forum: General Help
---

### Post by Robbyx on 2008-11-02
I do not know how to get my Fuji S5000 digital camera to transfer to the computer. 

It stopped working under 8.04. I have just upgraded to Intrepid and it is still not being recognised.


Lsub shows:
> robin@robin:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 04cb:0130 Fuji Photo Film Co., Ltd FinePix S5000 Zoom (DSC)
Bus 002 Device 005: ID 043d:0014 Lexmark International, Inc. InkJet Color Printer
Bus 002 Device 004: ID 043d:002d Lexmark International, Inc. X70/X73 Scan/Print/Copy
Bus 002 Device 003: ID 043d:0029 Lexmark International, Inc. Scan Print Copy
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Devices:
> robin@robin:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 003e4d16-908b-442c-92a6-9c3578d12c36 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 0F64D5B930A9A26F -> ../../sdb6
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 107E-9F7D -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 26b10955-df89-4b53-ace4-e4b4e8afa042 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 45a2e92c-c759-4732-9662-988da7f8ea7b -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 724E07853D78E7A8 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 7b859c36-c68d-408f-9425-de9f525f3c71 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 7E0442D704429257 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 86290d05-e673-4310-9f3e-93af30cc13af -> ../../sda7
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 e299fa84-e829-4f1c-b4ef-ad5329aec9ad -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 e36cb6cf-f372-4418-bd8b-f36a27dc3e76 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-11-02 10:41 f35c7bf9-9c2b-4ec9-9522-84d73f3c37db -> ../../sda5


I tried to mount it to sda7 but it made no difference after creating media/camera

robin@robin:~$ sudo mount /dev/sda7 /media/camera

What should I do to mount the camera?

Robin

---

