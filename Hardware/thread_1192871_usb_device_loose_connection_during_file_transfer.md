---
title: "usb device loose connection during file transfer"
date: 2009-06-20
forum: Hardware
---

### Post by s_ø on 2009-06-20
During file transfer from camcorder (canon hf100) to computer an error occurs, I/O error, the connection is dropped and the camcorder no longer appears when running lsusb.
The camcorder still 'thinks' it is connected to the computer. Its built-in fail-safe against someone shutting it off during file transfer means I have to remove the battery to cut the connection.

lsusb before file transfer:
```
Bus 001 Device 010: ID 04a9:31a7 Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 002: ID 04f9:01ce Brother Industries, Ltd DCP-135C
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```lsusb after conection loss:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 002: ID 04f9:01ce Brother Industries, Ltd DCP-135C
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```I have managed to get some recordings off the camcorder, and can view them. But only about 200-300 MB at a time then the connection is lost.

Any help is greatly appreciated.

---

