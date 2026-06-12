---
title: "Adb devices list empty"
date: 2017-10-01
forum: Hardware
---

### Post by yann-brizais on 2017-10-01
Hello
I have a smart-phone "Zuk Z2 pro" that is not detected by the command "adb devices" ( usb debug on)
I have another phone that is well detected by the command "adb devices"
I can copy files to the phone

```
yann@pc-yann:~$ adb devices
List of devices attached 

yann@pc-yann:~$ 


/etc/udev/rules.d/51-android.rules
# ZUK
SUBSYSTEM=="usb", ATTR{idVendor}=="2b4c", MODE="0666", GROUP="plugdev"

lsusb
Bus 003 Device 004: ID 2b4c:1013 Zuk Z2 Row

ls -l /dev/bus/usb/003
yann@pc-yann:~$ ls -l /dev/bus/usb/003
total 0
crw-rw-r--  1 root root  189, 256 oct.   1 08:13 001
crw-rw-r--  1 root root  189, 258 oct.   1 08:13 003
crw-rw----+ 1 root audio 189, 259 oct.   1 08:23 004
```

At the last line I should have "plugdev" instead of "audio"

how to fix 
Yann

---

