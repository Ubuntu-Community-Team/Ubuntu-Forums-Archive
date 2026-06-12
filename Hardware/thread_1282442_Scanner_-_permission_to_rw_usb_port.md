---
title: "Scanner - permission to rw usb port"
date: 2009-10-04
forum: Hardware
---

### Post by cjcj on 2009-10-04
I have an Epson all-in-one printer-scanner so I have installed iscan. However, iscan does not work because it says it cannot authenticate (i.e. get permission) to read-write to /dev/bus/usb/001/xxx where xxx is a number that changes every time I switch on the scanner. I can solve this by doing sudo chmod 777 /dev/bus/usb/001/xxx but i have to look up the number (i.e. xxx) of the file that has appeared in /dev/bus/usb/001/ every time the scanner is switched on. How can I make it give me permission to rw automatically? It does not seem to be in the user management dialogue to give me the rights. 

Can anyone tell me how. Is there a config file somewhere for usb devices that sets up the default permissions? Why don't other people have this problem? (I am running karmic but I had the same problem in jaunty - so have posted it here.)

Thanks

---

### Post by Bachstelze on 2009-10-04
Paste the output of

```
ls -l /dev/bus/usb/001/xxx
```

**before** you chmod it 777.

---

### Post by cjcj on 2009-10-04
The result is 

root@chris-desktop:/dev/bus/usb/001# ls -l
total 0
crwxrwxrwx 1 root root 189,  0 2009-10-04 15:34 001
crwxrwxrwx 1 root root 189,  1 2009-10-04 15:34 002
crw-rw-r-- 1 root root 189, 10 2009-10-04 16:58 011

011 is the file that appears when the scanner is switched on.

Does this help?
Thanks

---

