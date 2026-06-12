---
title: "Printer stopped working"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by putte30 on 2007-03-08
Hi all!

Suddenly after som system updates my printer stopped working. I have an Canon ip2000 and uses turboprint drivers. The printer has worked flawless untill now. When i run xtpsetup i just get the error messages that the printer is not connected. If i boot into windows the printer is just fine.... anyone?

---

### Post by Judicata on 2007-03-08
Hey, I was about to post with the same problem (different printer):

Brother HL-2070N
Connected through USB

Was working for fantastically, then nothing.  I try to add the printer through gnome and it doesn't detect it at all.

dmesg | tail
```
[17179760.344000] ohci_hcd 0000:07:00.0: wakeup
[17179760.728000] usb 6-1: new full speed USB device using ohci_hcd and address 2
[17179760.952000] usb 6-1: configuration #1 chosen from 1 choice
[17179760.964000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0029
```

lsusb:
```
Bus 006 Device 002: ID 04f9:0029 Brother Industries, Ltd 
```

Then System -> Administration -> Add Printer.  

Nothing.

---

### Post by putte30 on 2007-03-08
Weird...

lsusb:

Bus 001 Device 003: ID 04a9:108d Canon, Inc.

---

### Post by Fenix-TX on 2007-03-08
Perhaps this help

[http://ubuntuforums.org/showthread.php?t=379319](http://ubuntuforums.org/showthread.php?t=379319)

---

### Post by Judicata on 2007-03-08
Frustrating, but at least the printer isn't broken.

---

### Post by Judicata on 2007-03-08
I wouldn't have guessed it, but Fenix-TX's link worked! Now, I just wonder what I broke be deleting that file.

---

