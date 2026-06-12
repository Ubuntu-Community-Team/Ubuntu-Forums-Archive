---
title: "usb devices issue"
date: 2009-04-30
forum: Hardware
---

### Post by nategood on 2009-04-30
i have an install of mythbuntu/ubuntu v 8.04.2.  i've been having issues with all usb devices.  i've tried using a usb optical mouse and a WD elements external HDD with no luck.  with both plugged in lsusb yields...

nathan@ubuntwo:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

and after plugging in the WD HDD the kernel log states...

nathan@ubuntwo:~$ tail -n 2 /var/log/kern.log
Apr 30 22:19:12 ubuntwo kernel: [ 5521.357644] usb 5-5: new high speed USB device using ehci_hcd and address 13
Apr 30 22:19:13 ubuntwo kernel: [ 5521.764608] usb 5-5: device not accepting address 13, error -71

any ideas?

thanks

---

### Post by garythegoth on 2009-04-30
Get rid of 8.04. Its junk.

---

### Post by nategood on 2009-05-01
so i tried to upgrade to 8.10 and now upon restart, the machine freezes after the main ubuntu load screen.  so then i...

burnt an iso of ubuntu 9.
reboot the machine with the iso cd.
tried "try without changing anything", "install ubuntu", and "install ubuntu" in graphics safe mode options and each time after the ubuntu load screen i get a blank screen (or in graphics safe mode, a screen with a blinking underscore).

help?

---

