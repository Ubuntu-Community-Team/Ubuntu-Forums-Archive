---
title: "Canon Powershot g5 digital camera not mounting"
date: 2006-08-13
forum: Hardware &amp; Laptops
---

### Post by moaxey on 2006-08-13
just trying this camera for the first time with dapper...

found this old thread where same camera/platform 'just works' in ubuntu 4.1

[http://www.tuxme.com/node/436](http://www.tuxme.com/node/436)

lsusb reveals:
mjoakes@mjoakes-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 004: ID 04a9:3085 Canon, Inc. PowerShot G5
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
mjoakes@mjoakes-laptop:~$

and i found some more tips where you could mount thru fstab as a block device, but this camera doesnt seem to have a block device id in HAL

help appreciated
:-k

---

