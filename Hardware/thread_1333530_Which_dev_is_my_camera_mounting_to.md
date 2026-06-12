---
title: "Which /dev is my camera mounting to?"
date: 2009-11-21
forum: Hardware
---

### Post by mike-g2 on 2009-11-21
Hi,

I have some deleted files I want to recover from its memory card and I need to be able to copy the card/filesystem over to my laptop using the dd command.  I'm running 9.04 and am trying to figure out which /dev device is being used to mount my camera.

When I plug the camera in a window pops up and asks me if I want to open the camera with f-spot, open folder, ... etc.  I choose the "Do nothing" option which results in a folder for the camera being placed on my desktop, but I can't figure out which dev location the camera is using.

If I look in /var/log/messages I see something like:
[INDENT]
Nov 21 14:11:24 ocoee kernel: [265351.781071] usb 1-5: new high speed USB device using ehci_hcd and address 35
Nov 21 14:11:24 ocoee kernel: [265351.934432] usb 1-5: configuration #1 chosen from 1 choice
[/INDENT]

If I try
[INDENT]ls -ltrh /dev | tail [/INDENT]
I get 
[INDENT]
crw-------  1 root   root      5,   1 2009-11-21 10:18 console
crw-rw-rw-  1 root   tty       5,   0 2009-11-21 13:38 tty
lrwxrwxrwx  1 root   root          15 2009-11-21 14:11 libmtp-1-5 -> bus/usb/001/035
crw-rw----  1 root   root    252,  25 2009-11-21 14:11 usbdev1.35_ep00
crw-rw----  1 root   root    252,  22 2009-11-21 14:11 usbdev1.35_ep81
crw-rw----  1 root   root    252,  23 2009-11-21 14:11 usbdev1.35_ep02
crw-rw----  1 root   root    252,  24 2009-11-21 14:11 usbdev1.35_ep83
drwxr-xr-x  2 root   root        3.6K 2009-11-21 14:11 char
prw-r-----  1 syslog adm            0 2009-11-21 14:20 xconsole
crw-rw-rw-  1 root   tty       5,   2 2009-11-21 14:24 ptmx
[/INDENT]

Which I find confusing since it indicates there are multiple locations associated with usbdev1.35, but none of them seem to be an actual disk (which is what I'm expecting).

Further, I don't see any USB devices listed  if I try fdisk -l

Can someone help me understand what's going on here and how to solve this problem?

Many thanks.

Mike

---

### Post by sisco311 on 2009-11-21
It's probably mounted in ~/.gvfs.

the
```
mount
```command should list the device and the path to the mount point.

---

### Post by renkinjutsu on 2009-11-21
also, you should look into dmesg instead of /var/log/messages

dmesg will give you the device name in brackets like

[sdc]

---

