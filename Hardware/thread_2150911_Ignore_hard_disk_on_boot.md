---
title: "Ignore hard disk on boot"
date: 2013-06-02
forum: Hardware
---

### Post by buluba89 on 2013-06-02
I have a multi boot setup with windows 8 and ubuntu 13.04 and i'd like ubuntu to ignore completly the disks tha  are related with windows.
I know that i could write some script to delete devices by 
```
echo 1 > /sys/block/sdX/delete 
```
for every disk tha i want ubuntu not to show up but it would be better not to add these disks in the first place.

Also tried to ignore from udev by placing a rules file in /etc/udev/rules.d/  with something like:
```
SUBSYSTEM=="block", ENV{ID_SERIAL_SHORT}=="XXXXXXXX",OPTIONS+="ignore_device"
```
but with no luck.

Anyone has any idea how to prevent ubuntu from using disks?

---

