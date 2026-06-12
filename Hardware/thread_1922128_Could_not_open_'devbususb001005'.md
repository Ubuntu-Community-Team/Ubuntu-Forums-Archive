---
title: "Could not open '/dev/bus/usb/001/005'"
date: 2012-02-08
forum: Hardware
---

### Post by dimamali on 2012-02-08
I am trying to use x32 on a nexys2  FPGA board for an academic project. The tool chain requests for a 

```
   x32-upload helloworld.ce -c /dev/ttyX 
```]command to upload my code to the fpga. I am using a USB to serial cable which is connected as seen by lsusb
  
```
Bus 001 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
``` However when i issue the upload command i get the following error
  
```
Could not open '/dev/bus/usb/001/005'   
```I guess it is not a permissions issue since i get the same error when i try it as a root. Any ideas?

---

