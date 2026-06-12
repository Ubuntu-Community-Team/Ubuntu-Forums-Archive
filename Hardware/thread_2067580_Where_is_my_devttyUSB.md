---
title: "Where is my /dev/ttyUSB*?"
date: 2012-10-07
forum: Hardware
---

### Post by marwooj on 2012-10-07
There always was ttyUSB for linux.
Now (12.04) I am connecting my usb device into usb port.
I see dmesg
 usb 3-2: new full-speed USB device number 4 using uhci_hcd
but how it transfer to my /dev/ttyUSB ?

---

### Post by Slashthedragon on 2013-02-10
I too did not find a /dev/ttyUSB*. 
This is what I did.
I was installing an Arduino Replace Arduino with <YourDevice>

Without Arduino plugged in
$ lsusb 

With Arduino plugged in.
$ lsusb 

I looked at the addition line.
It Looked like this
Bus 004 Device 003: ID 2341:0043
I inserted the numbers in the command below.

$ sudo modprobe usbserial vendor=0x2341 product=0x0043 

Without Arduino plugged in I:
$ cd /dev
$ ls
With Arduino plugged in.
$ ls
I looked for the additional tty* NAME. I saw ttyAMC0, (yours may be ttyUSB* or ttyS*.)

I did
$ sudo minicom -s. but got "command not found" so I  $ sudo apt-get install minicom then tried again.


I changed the first line to /dev/ttyAMC0 (yours may be different.)

I selected Save setup as dfl.
Now my Arduino worked.

---

