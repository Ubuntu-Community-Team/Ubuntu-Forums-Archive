---
title: "Invisible Card reader"
date: 2008-09-22
forum: General Help
---

### Post by mulanee on 2008-09-22
It's a long time I try to read cards from my camera.
I tried different things but it's worde and worse.
Firstly , lsusb gave: 
```
Bus 004 Device 009: ID 058f:6366 Alcor Micro Corp.
Bus 004 Device 003: ID 059f:0651 LaCie, Ltd
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000
```

Then I install and uninstall libccid , and I got :
```
Bus 004 Device 003: ID 059f:0651 LaCie, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

Mount:
```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda3 on /home type ext3 (rw)
/dev/sdb1 on /media/LaCie type vfat (rw,noexec,nosuid,nodev,utf8,umask=002,gid=100)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

fstab:
```
proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=92906ca5-2c7f-4506-ac18-5a978296c98e / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=6298bb48-be2b-413d-bcde-0c4cba2547f1 /home ext3 defaults 0 2
# Entry for /dev/sda2 :
UUID=8479ab1b-8aa0-4b07-8844-811c8922363e none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

#/dev/sdc1
UUID=6853-5BA9 /media/LaCie vfat  defaults,user,utf8,umask=002,gid=100  0 0

```

dmesg | grep usb:
```
[   32.258388] usbcore: registered new interface driver usbfs
[   32.258482] usbcore: registered new interface driver hub
[   32.287895] usbcore: registered new device driver usb
[   32.606811] usb usb1: configuration #1 chosen from 1 choice
[   32.713752] usb usb2: configuration #1 chosen from 1 choice
[   32.818207] usb usb3: configuration #1 chosen from 1 choice
[   32.933538] usb usb4: configuration #1 chosen from 1 choice
[   33.813090] usb 4-3: new high speed USB device using ehci_hcd and address 3
[   33.946275] usb 4-3: configuration #1 chosen from 1 choice
[   34.184992] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   34.305073] usb 2-2: device descriptor read/64, error -71
[   34.528959] usb 2-2: device descriptor read/64, error -71
[   34.744939] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   34.864922] usb 2-2: device descriptor read/64, error -71
[   35.088882] usb 2-2: device descriptor read/64, error -71
[   35.310047] usb 2-2: new full speed USB device using uhci_hcd and address 4
[   35.720794] usb 2-2: device not accepting address 4, error -71
[   35.832779] usb 2-2: new full speed USB device using uhci_hcd and address 5
[   36.240697] usb 2-2: device not accepting address 5, error -71
[   36.241023] usbcore: registered new interface driver libusual
[   36.277200] usbcore: registered new interface driver usb-storage
[   36.277574] usb-storage: device found at 3
[   36.277584] usb-storage: waiting for device to settle before scanning
[   41.276332] usb-storage: device scan complete
[  165.553592] usb 2-2: new full speed USB device using uhci_hcd and address 6
[  165.681614] usb 2-2: device descriptor read/64, error -71
[  165.909577] usb 2-2: device descriptor read/64, error -71
[  166.125517] usb 2-2: new full speed USB device using uhci_hcd and address 7
[  166.253539] usb 2-2: device descriptor read/64, error -71
[  166.481506] usb 2-2: device descriptor read/64, error -71
[  166.697485] usb 2-2: new full speed USB device using uhci_hcd and address 8
[  167.113390] usb 2-2: device not accepting address 8, error -71
[  167.225392] usb 2-2: new full speed USB device using uhci_hcd and address 9
[  167.645425] usb 2-2: device not accepting address 9, error -71
[  190.930589] usb 2-2: new full speed USB device using uhci_hcd and address 10
[  191.054573] usb 2-2: device descriptor read/64, error -71
[  191.282543] usb 2-2: device descriptor read/64, error -71
[  191.498518] usb 2-2: new full speed USB device using uhci_hcd and address 11
[  191.622506] usb 2-2: device descriptor read/64, error -71
[  191.850478] usb 2-2: device descriptor read/64, error -71
[  192.066454] usb 2-2: new full speed USB device using uhci_hcd and address 12
[  192.478397] usb 2-2: device not accepting address 12, error -71
[  192.590393] usb 2-2: new full speed USB device using uhci_hcd and address 13
[  192.998338] usb 2-2: device not accepting address 13, error -71
[  207.924600] usb 2-2: new full speed USB device using uhci_hcd and address 14
[  208.048580] usb 2-2: device descriptor read/64, error -71
[  208.276551] usb 2-2: device descriptor read/64, error -71
[  208.492527] usb 2-2: new full speed USB device using uhci_hcd and address 15
[  208.616513] usb 2-2: device descriptor read/64, error -71
[  208.844488] usb 2-2: device descriptor read/64, error -71
[  209.060463] usb 2-2: new full speed USB device using uhci_hcd and address 16
[  209.472406] usb 2-2: device not accepting address 16, error -71
[  209.584402] usb 2-2: new full speed USB device using uhci_hcd and address 17
[  209.992346] usb 2-2: device not accepting address 17, error -71
[  270.965214] usb 2-2: new full speed USB device using uhci_hcd and address 18
[  271.089204] usb 2-2: device descriptor read/64, error -71
[  271.317174] usb 2-2: device descriptor read/64, error -71
[  271.533162] usb 2-2: new full speed USB device using uhci_hcd and address 19
[  271.657140] usb 2-2: device descriptor read/64, error -71
[  271.885112] usb 2-2: device descriptor read/64, error -71
[  272.101080] usb 2-2: new full speed USB device using uhci_hcd and address 20
[  272.517032] usb 2-2: device not accepting address 20, error -71
[  272.629029] usb 2-2: new full speed USB device using uhci_hcd and address 21
[  273.036970] usb 2-2: device not accepting address 21, error -71
[  281.072054] usb 2-2: new full speed USB device using uhci_hcd and address 22
[  281.196571] usb 2-2: device descriptor read/64, error -71
[  281.427987] usb 2-2: device descriptor read/64, error -71
[  281.643974] usb 2-2: new full speed USB device using uhci_hcd and address 23
[  281.767944] usb 2-2: device descriptor read/64, error -71
[  281.995929] usb 2-2: device descriptor read/64, error -71
[  282.211904] usb 2-2: new full speed USB device using uhci_hcd and address 24
[  282.627846] usb 2-2: device not accepting address 24, error -71
[  282.739836] usb 2-2: new full speed USB device using uhci_hcd and address 25
[  283.147785] usb 2-2: device not accepting address 25, error -71
[46836.856008] usb 2-2: new full speed USB device using uhci_hcd and address 26
[46836.979988] usb 2-2: device descriptor read/64, error -71
[46837.207950] usb 2-2: device descriptor read/64, error -71
[46837.424016] usb 2-2: new full speed USB device using uhci_hcd and address 27
[46837.547904] usb 2-2: device descriptor read/64, error -71
[46837.775888] usb 2-2: device descriptor read/64, error -71
[46837.991856] usb 2-2: new full speed USB device using uhci_hcd and address 28
[46838.407797] usb 2-2: device not accepting address 28, error -71
[46838.519822] usb 2-2: new full speed USB device using uhci_hcd and address 29
[46838.935747] usb 2-2: device not accepting address 29, error -71
[46845.710965] usb 2-2: new full speed USB device using uhci_hcd and address 30
[46845.834965] usb 2-2: device descriptor read/64, error -71
[46846.066943] usb 2-2: device descriptor read/64, error -71
[46846.282904] usb 2-2: new full speed USB device using uhci_hcd and address 31
[46846.406879] usb 2-2: device descriptor read/64, error -71
[46846.634853] usb 2-2: device descriptor read/64, error -71
[46846.850831] usb 2-2: new full speed USB device using uhci_hcd and address 32
[46847.266752] usb 2-2: device not accepting address 32, error -71
[46847.378765] usb 2-2: new full speed USB device using uhci_hcd and address 33
[46847.794704] usb 2-2: device not accepting address 33, error -71
[47072.424406] usb 2-2: new full speed USB device using uhci_hcd and address 34
[47072.548430] usb 2-2: device descriptor read/64, error -71
[47072.776374] usb 2-2: device descriptor read/64, error -71
[47072.992331] usb 2-2: new full speed USB device using uhci_hcd and address 35
[47073.120326] usb 2-2: device descriptor read/64, error -71
[47073.348281] usb 2-2: device descriptor read/64, error -71
[47073.568261] usb 2-2: new full speed USB device using uhci_hcd and address 36
[47073.984229] usb 2-2: device not accepting address 36, error -71
[47074.096224] usb 2-2: new full speed USB device using uhci_hcd and address 37
[47074.516153] usb 2-2: device not accepting address 37, error -71
[47174.628412] usb 2-2: new full speed USB device using uhci_hcd and address 38
[47174.748389] usb 2-2: device descriptor read/64, error -71
[47174.972382] usb 2-2: device descriptor read/64, error -71
[47175.188341] usb 2-2: new full speed USB device using uhci_hcd and address 39
[47175.308339] usb 2-2: device descriptor read/64, error -71
[47175.532302] usb 2-2: device descriptor read/64, error -71
[47175.748278] usb 2-2: new full speed USB device using uhci_hcd and address 40
[47176.156217] usb 2-2: device not accepting address 40, error -71
[47176.268218] usb 2-2: new full speed USB device using uhci_hcd and address 41
[47176.676158] usb 2-2: device not accepting address 41, error -71

```

Any help appreciated.

---

