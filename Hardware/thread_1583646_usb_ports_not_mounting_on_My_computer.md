---
title: "usb ports not mounting on My computer"
date: 2010-09-28
forum: Hardware
---

### Post by suparubo on 2010-09-28
i am running ubuntu 10.04 and im having a problem with the usb port
flash drives and external drives wont mount they show up on disk utility and under SMART status it says not supported i clicked mount volume and it gave me this error

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

it used worked before and after the recent clean install it hasn't. can someone please help!

---

### Post by linux-hack on 2010-09-28
did you plug them to a windows system ? if so you need to disconnect them properly in order for them to work on linux.

if you plus you usb drive and type in a terminal ```
lsusb
``` what do you get ? post the out put here.

---

### Post by andrewkevin on 2010-09-28
We just figured out what the problem was!   When I first got my G1, I  plugged it into the USB port and 'mounted' the USB device.  This set a  device drive letter of "**F**:" on my PC for that device.  Last week,  I remapped that drive letter to another device (network location)  during a period when my G1 was not plugged in.  Windows isn't smart  enough to simply assign the *next *drive letter to the USB device when it's plugged in.  Windows saw that previously I had assigned "**F**:" to my G1 and since "**F**:" was already taken by my newly mapped network location, Windows simply gave up and didn't reassign the G1 to "**G**:" as one would expect.

To  fix this, on your PC click "Start" - "Control Panel" - "Administrative  Tools" - "Computer Management" - "Disk Management".   Find the G1 on the  device list at the bottom and right-click to "Change Drive Letter and  Paths..."   Then assign the G1 to a drive letter that is not currently  in use.

Close out all windows and look for the G1 in Windows Explorer.

_________________________________________________________________________
[Portable Hard Drives]("http://go.iomega.com/en/products/external-hard-drive-portable/?partner=4750") | [Desktop Hard Drives]("http://go.iomega.com/en/products/external-hard-drive-desktop/?partner=4750") | [Network Storage solutions]("http://iomega.com/nas/network-attached-storage.html")

---

### Post by suparubo on 2010-09-28
> **linux-hack said:**
> did you plug them to a windows system ? if so you need to disconnect them properly in order for them to work on linux.

if you plus you usb drive and type in a terminal ```
lsusb
``` what do you get ? post the out put here.

ruben@ruben-desktop:~$ lsusb
Bus 002 Device 002: ID 054c:04bb Sony Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 03f0:0f0c Hewlett-Packard Wireless Keyboard and Optical Mouse receiver
Bus 001 Device 002: ID 046d:09a2 Logitech, Inc. QuickCam Communicate Deluxe/S7500
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

