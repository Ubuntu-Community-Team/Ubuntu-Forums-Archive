---
title: "adding SHT11 sensor to sysfs"
date: 2012-06-22
forum: Hardware
---

### Post by swooppl on 2012-06-22
hi,

a few days ago I decided to connect to the SMBus bus in my computer SHT11 sensor. I have no idea how to add this sensor to sysfs. This sensor is quite specific in that it uses the address 0x00 and such can not be put in new_device:
```
$ sudo bash -c 'echo sht15 0x00 >  /sys/bus/i2c/devices/i2c-0/new_device'
bash: line 0: echo: write error: wrong argument
```when i try put 0x50, there's no error:
```
$ sudo bash -c 'echo sht15 0x50 >  /sys/bus/i2c/devices/i2c-0/new_device'
```it creates folder /sys/bus/i2c/devices/0-0050, but without measurements

---

