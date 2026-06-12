---
title: "USB HDD not working properly"
date: 2014-04-05
forum: Hardware
---

### Post by Kevin h II on 2014-04-05
Hello this is that my USB HDD fuijistu mount pocketec 30 gb drive isn't working with my ubuntu for the past 3 days have this error

(org.freedesktop.DBus.Python.dbus.exceptions.DBusException: com.ubuntu.USBCreator.Error.NotAuthorized)

i didn't understand this as i am the only linux user on this pc

This is the terminal of the usb

(USER@USER:~$ lsusbBus 001 Device 002: ID 13d3:5108 IMC Networks 
Bus 004 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub)

sorry for the page space  i am noob on the forums.

(USER@USER:~$ lsusb
Bus 001 Device 045: ID 0dbf:0300 Jess-Link International Storage Adapter
Bus 001 Device 002: ID 13d3:5108 IMC Networks 
Bus 004 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub)

thank you for any help provided.

---

### Post by tripp98 on 2014-04-06
Does it work with anything else besides your laptop?
Did it previously work with your laptop?
with USB drive plugged in try sudo fdisk -l to list devices or open gpart and/or hard drives and see if it shows up.

30gb drives are pretty old.  Drive may have died.

---

### Post by Kevin h II on 2014-04-14
Yes i have had it working again since my laptop with ubuntu is not loading it goes immediately into safe graphics and i have no idea how to stop this i loaded my inspiron 6000 with a  live cd of centos and made a partition into it and now the drive is functional :) now to spend time working on my asus 1005ha working with ubuntu 13.10. laters and help would be appreciated.

---

