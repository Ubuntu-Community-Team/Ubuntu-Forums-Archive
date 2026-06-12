---
title: "Not loading a kernel module"
date: 2012-05-28
forum: Hardware
---

### Post by jfmanamtr on 2012-05-28
I just reinstalled Ubuntu Server 12.04 LTS (32-bit) on a computer I use as a webserver (A Dell Dimension 4400). I put phpsysinfo on the system so that I can keep an eye on the computer temp using lmsensors. I ran the sensor-detect & it found a smsc47m1 chip. I added smsc47m1 to /etc/modules & rebooted the computer. Once I got logged, I ran sensors & was told:

```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

So, I checked /etc/modules to make sure I added the module & it is there. I check dmesg & find this: 

```
[  178.497328] smsc47m1: Found SMSC LPC47M10x/LPC47M112/LPC47M13x
[  178.497356] ACPI: resource smsc47m1 [io  0x0804] conflicts with ACPI region RNT3 [io 0x804-0x804]
[  178.497361] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```

I think this means I am conflicting with another device. I am not aware of any other  module for smsc47m1. So, any idea on what I can do to get this fixed?

~JFM

---

### Post by jfmanamtr on 2012-05-29
Bump. Any ideas about this? I would like this to work.

~John

---

### Post by jfmanamtr on 2012-05-31
Bump #2.

---

