---
title: "web cam blacklist that does not blacklist"
date: 2009-03-21
forum: Hardware
---

### Post by esj on 2009-03-21
upgraded to 8.10 from 8.04 and as to be expected, the webcam failed in it's usual way

Mar 21 14:58:36 first-triad kernel: [  620.717639] gspca: probing 046d:0892
Mar 21 14:58:37 first-triad kernel: [  620.924434] vc032x: check sensor header 44
Mar 21 14:58:37 first-triad kernel: [  620.925200] usb 5-8: USB disconnect, address 50
Mar 21 14:58:37 first-triad kernel: [  620.925212] vc032x: I2c Bus Busy Wait 0
Mar 21 14:58:37 first-triad kernel: [  620.925220] vc032x: I2c Bus Busy Wait 0
Mar 21 14:58:37 first-triad kernel: [  620.925229] vc032x: I2c Bus Busy Wait 0
Mar 21 14:58:37 first-triad kernel: [  620.925237] vc032x: I2c Bus Busy Wait 0
Mar 21 14:58:37 first-triad kernel: [  620.925245] vc032x: I2c Bus Busy Wait 0
Mar 21 14:58:37 first-triad kernel: [  620.925253] vc032x: I2c Bus Busy Wait 0
Mar 21 14:58:37 first-triad kernel: [  620.925258] vc032x: Unknown sensor...
Mar 21 14:58:37 first-triad kernel: [  620.925279] vc032x: probe of 5-8:1.0 failed with error -22
Mar 21 14:58:37 first-triad kernel: [  621.202960] usb 5-8: new high speed USB device using ehci_hcd and address 51
Mar 21 14:58:37 first-triad kernel: [  621.377290] usb 5-8: configuration #1 chosen from 1 choice


blacklisting failed.

# acer vid camera sucks.
blacklist gspca
# blacklist vc032x

what should I try next.  my machine is really unusable until I can get the constant retrys halted.

thanks

---

### Post by esj on 2009-03-22
found the solution.  Someone suggested that I try looking at the modules in a different way.

modprobe -c  --showconfig | more

This was a good clue.  it showed lots of gspca associated symbols.  Using a part of the USB ID found in log files, I found the module associated with it.
 
modprobe -c  --showconfig | grep 0892
alias usb:v046Dp0892d*dc*dsc*dp*ic*isc*ip* gspca_vc032x

blacklisting gspca_vc032x blacklisted the module and stopped the repeated attempts to load the module.

---

