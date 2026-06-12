---
title: "Pic Microchip not visible in /dev"
date: 2014-08-10
forum: Hardware
---

### Post by cdd854 on 2014-08-10
Hi,

When connecting to a PIC microchip using a usb connector my cpu does not recognize that anything is connected.  After connecting the PIC18f87j50 and running: 

```
 ls -ltr /dev/ 
``` 

 nothing new shows up. I expect to see something like:

```
/dev/ttyACM0
```

  I have tested the usb ports with other devices such as a mouse and do see the device appear. I have also tested the usb/PIC connection with a mac running linux virtually and was able to connect fine.

I am using a Lenovo L430 with Kubuntu.  Any ideas on how I can detect the PIC microchip?

Thanks

---

### Post by cdd854 on 2014-08-11
I also wanted to add that after I plug is the usb and run dmesg I get the following:

```

[12212.702772] usb 1-1.2: new full-speed USB device number 8 using ehci-pci
[12212.774832] usb 1-1.2: device descriptor read/64, error -32
[12212.950943] usb 1-1.2: device descriptor read/64, error -32

```

any ideas on how I can fix this?

---

### Post by cdd854 on 2014-08-11
Turns our that the usb was drawing too much current.  Fixed by using an external powered usb port.

---

