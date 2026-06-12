---
title: "Edgeport USB to Serial causes lsusb hang"
date: 2009-11-09
forum: Hardware
---

### Post by brookbgd on 2009-11-09
Had Jaunty running, and needed a serial port.  Added an Edgeport/22c USB to serial port convertor.  lsusb showed the device OK (Inside Out Networks device), but neither of the two serial ports on this device ever showed up in /dev as /dev/ttyUSB0 or /devUSB1.   The Edgeport appeared to initialize ok though, as the LED on it began to blink green, which indicates that it has been recognized and initialized.

Karmic came out about that time, so I decided to upgrade and see if that resolved the missing /dev/ttyUSB devices.  Once I upgraded and got Karmic running, I plugged in the Edgeport.  The LED on the Edgeport blinked Red and never turned green (meaning it didn't ever get initialized).  I ran lsusb, and the command prompt froze with no output.  Ctrl-C and other attempts to break out of lsusb failed.  I had to close the terminal window.  Other USB devices that usually work would now not show up if I plugged them in.  A reboot was required.

I rebuilt the kernel, making sure that the Edgeport devices were included in the kernel (not as modules).  The results were the same - lsusb hanging.

I think this is likely a bug, but I'm all ears if anyone has configuration or kernel rebuild ideas to resolve it.

I'm glad to run commands to provide more debug information if anyone can help.

Thanks,

Brook

---

