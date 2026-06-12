---
title: "usb/vga adapter"
date: 2014-12-30
forum: Hardware
---

### Post by stefano23 on 2014-12-30
I have recently bought a j5 creative usb/vga adapter (jua210). However, there is no way to get it working.
When plugged:

lsusb:
Bus 002 Device 011: ID 0711:5200 Magic Control Technology Corp. 

dmesg:
[19028.340787] usb 2-3: new high-speed USB device number 11 using xhci_hcd
[19028.359550] usb 2-3: New USB device found, idVendor=0711, idProduct=5200
[19028.359563] usb 2-3: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[19028.359571] usb 2-3: Product: Trigger II External Graphics
[19028.359576] usb 2-3: Manufacturer: MCT Corp.

However, the second screen is not recognized:
xrandr:
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
eDP1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

Any idea?

Thanks,
Stefano

---

