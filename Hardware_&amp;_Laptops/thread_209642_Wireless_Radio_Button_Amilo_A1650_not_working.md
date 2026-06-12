---
title: "Wireless Radio Button Amilo A1650 not working"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by muse54 on 2006-07-05
Hi

I have recently installed Ubuntu 6.06 on my Fujitsu Siemens Amilo A1650.  

The wireless radio button, which works perfectly well in Winblowz, simply doesn't work when pressed.  Without this I cannot use Wi-Fi.

There is also a hot key, Fn+F10, which also does not work.

Does anyone else have, or has had, this problem and fond a solution?

Thanks in adavance for your replies.

---

### Post by Eversmann on 2006-07-05
Read this to see if it suits to you: 

[http://www.ubuntuforums.org/showthread.php?t=207428](http://www.ubuntuforums.org/showthread.php?t=207428)

---

### Post by freak101 on 2006-09-08
On my laptop I've solved using acer_acpi (amilo a1650 not acer):
[http://archernar.co.uk/acer_acpi/acer_acpi_main.html](http://archernar.co.uk/acer_acpi/acer_acpi_main.html)

compile and load the module, it will add to /proc a new entry "acer":

$ ls /proc/acpi/acer/
total 0
-rw-r--r-- 1 root root 0 2006-09-07 03:34 bluetooth
-rw-r--r-- 1 root root 0 2006-09-07 03:34 mailled
-rw-r--r-- 1 root root 0 2006-09-07 03:34 version
-rw-r--r-- 1 root root 0 2006-09-07 03:34 wireless

to activate the wireless type:
$ sudo chmod 666 /proc/acpi/acer/wireless
$ sudo echo "enabled : 1" > /proc/acpi/acer/wireless

and your wireless led should light up.

HTH
Antonio

---

