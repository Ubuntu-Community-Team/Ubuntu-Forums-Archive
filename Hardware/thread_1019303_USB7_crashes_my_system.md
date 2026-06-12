---
title: "USB7 crashes my system"
date: 2008-12-23
forum: Hardware
---

### Post by davidfg4 on 2008-12-23
So I recently got a [USB7]("http://spiffie.org/kits/usb7/"). I assembled it and it works perfectly on a windows system. On Linux it is supposed to make a fake serial port at /dev/ttyACM0 or similar, and any text directed to it will display.
It crashes my Ubuntu 8.10 (kernel 2.6.27-9-generic) system when plugged in. I have tried it on three different computers all running 8.10 and they all do the same thing: the screen freezes and mouse and keyboard input does nothing. Sometimes the mouse will continue to work after the keyboard stops working, but it eventually freezes too, after less than 15 seconds. The only solution is holding the power button for 10 seconds. If I boot with the the USB7 already plugged in and the fancy boot screen turned off so I can see the messages, it stops booting when loading the GNOME Desktop Environment.
Based off of [this info]("http://spiffie.org/kits/usb7/driver_linux.shtml"), I needed a patched kernel. Based off of [this guide]("https://help.ubuntu.com/community/Kernel/Compile"), I managed to compile and install a kernel with the patch for 
"2.6.23 and Above" kernels. My computer boots fine, but the computer still freezes when the device is plugged in.
I also tried some live CD's of puppy linux and knoppix, both of which fall under the "2.6.22 and Below" category. Neither of them worked.

If anyone has gotten one of these to work with Linux please tell me what you did.
Thanks!

---

### Post by davidfg4 on 2009-03-30
I got it to work.
I tried it on Ubuntu 9.04 beta and it didn't crash the system. I then [applied]("https://help.ubuntu.com/community/Kernel/Compile") the [patch]("http://spiffie.org/kits/usb7/driver_linux.shtml") and it worked.
It automatically shows up as /dev/ttyACM0 and I can echo text to it.

---

