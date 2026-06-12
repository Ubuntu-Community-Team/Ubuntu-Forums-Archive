---
title: "[SOLVED] how to find name &amp;amp; model #'s for hardware components?"
date: 2008-12-13
forum: Hardware
---

### Post by 3katie3 on 2008-12-13
Hello, i bought an old used ibmthinkpad40 with no OS and ubuntu installed perfectly! 

but the dual boot W2K sp4 cant find drivers or the names of half a dozen critical components such as ethernet controller, wireless card, video card, etc.

is there a way to find out in Ubuntu what the manufacturer names and model numbers are for the hardware components.   sort of like system device manager in windows.

if Ubuntu can detect and display the IDs of the system devices then i can search for windows drivers.

the thinkpad has to be used as a dual boot.

---

### Post by taurus on 2008-12-13
```
lshw
```

---

### Post by lensman3 on 2008-12-13
lspci will list the hardware attached to the pci buss.

"/sbin/lspci -n"

This dump will dump a hexidecimal number of the form xxxx:yyyy.  That number is unique for that device.  Google  the number and you can find the specific driver(s).  This is the number that device driver tests for during a boot.

Hope this helps.

---

### Post by MonkeyPaw on 2008-12-14
If you're in windows, Everest is a nice program for identifying hardare.
[http://majorgeeks.com/download4181.html](http://majorgeeks.com/download4181.html)

---

### Post by 3katie3 on 2008-12-14
wow!  very cool.


thank you
thank you
thank you.

---

