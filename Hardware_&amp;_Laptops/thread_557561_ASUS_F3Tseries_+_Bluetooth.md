---
title: "ASUS F3Tseries + Bluetooth"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by javaCachaca on 2007-09-22
Hi,
  I have a notebook ASUS F3Tseries with Feisty (7.04), but the blutooth don't work.

  When I execute the command "hcitool scan" the return is:
      "Device is not available: No such device"

    Help, please !!!.

---

### Post by linuxwizard on 2007-09-22
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by javaCachaca on 2007-09-29
Welll,
   I have this packages installed in my Ubuntu:
   
  - bluetooth
  - bluez-cups
  - bluez-gnome
  - bluez-pin
  - bluez-utils
  - gnome-bluetooth
  - libbluetooth2
  - libbtctl4
  - libgnomebt0
  - obexftp

the command dmesg show-me:

[  290.161259] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-52 processors (version 2.00.00)
[  290.160736] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[  290.160741] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[  290.160991] powernow-k8: ph2 null fid transition 0x8
[  295.453908] ppdev: user-space parallel port driver
[  306.864914] vboxdrv: Trying to deactivate NMI watchdog permanently...
[  306.864919] vboxdrv: Successfully done.
[  307.302809] Bluetooth: Core ver 2.11
[  307.302882] NET: Registered protocol family 31
[  307.302884] Bluetooth: HCI device and connection manager initialized
[  307.302889] Bluetooth: HCI socket layer initialized
[  307.347007] Bluetooth: L2CAP ver 2.8
[  307.347012] Bluetooth: L2CAP socket layer initialized
[  307.376032] Bluetooth: RFCOMM socket layer initialized
[  307.376047] Bluetooth: RFCOMM TTY layer initialized
[  307.376049] Bluetooth: RFCOMM ver 1.8
[ 6271.326993] eth0: no IPv6 routers present

But, my bluetooth don't work :(.

Ideas ? suggestions ?

---

### Post by javaCachaca on 2007-10-09
Help, please !  :lolflag:

---

### Post by offbyte on 2007-10-09
blueman bluetooth manager worked likee  wonder to me
[http://ubuntuforums.org/showthread.php?t=559089&highlight=blueman](http://ubuntuforums.org/showthread.php?t=559089&highlight=blueman)

---

