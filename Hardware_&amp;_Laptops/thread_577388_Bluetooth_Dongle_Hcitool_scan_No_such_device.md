---
title: "Bluetooth Dongle: Hcitool scan No such device"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by Baender on 2007-10-16
I got a very mysterious Hardware Problem. I have a Bluetooth Dongle and Mouse by Trust. I used the Tuturial from your Site 
[http://ubuntuforums.org/showthread.php?t=224673&highlight=bluetooth+no+such+device]("http://ubuntuforums.org/showthread.php?t=224673&highlight=bluetooth+no+such+device")

but after i installed the bluetooth software (it adds the bluetooth symbol in taskbar), i can not find any devices with lsusb or hcitool scan.

aleksandr@vanderfall-ubuntu:~$ lsusb
Bus 005 Device 003: ID 04a9:10b7 Canon, Inc. 
Bus 005 Device 002: ID 0457:0150 Silicon Integrated Systems Corp. Super Talent 1GB Flash Drive
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 010: ID 0a5c:3503 Broadcom Corp. 
Bus 004 Device 009: ID 0a5c:3502 Broadcom Corp. 
Bus 004 Device 004: ID 04f2:0200 Chicony Electronics Co., Ltd 
Bus 004 Device 006: ID 0a5c:200a Broadcom Corp. 
Bus 004 Device 005: ID 0a5c:3535 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  

aleksandr@vanderfall-ubuntu:~$ hcitool scan
Device is not available: No such device

It is curios that the mouse doen't work when i login into ubuntu, but when i first login into windows, move the mouse a bit and login into ubunto the mouse works. It is pesky to load windows first and start ubuntu after. In both cases (when in login into ubuntu first, or login into windows first and load ubuntu after mouse moving) i can not find any devices also when the mouse works :lolflag:

---

### Post by linuxwizard on 2007-10-16
[https://help.ubuntu.com/community/BluetoothMouse](https://help.ubuntu.com/community/BluetoothMouse)

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

