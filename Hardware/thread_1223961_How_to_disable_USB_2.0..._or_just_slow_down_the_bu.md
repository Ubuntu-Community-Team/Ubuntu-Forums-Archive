---
title: "How to disable USB 2.0... or just slow down the bus?"
date: 2009-07-26
forum: Hardware
---

### Post by hemlockz on 2009-07-26
Hi All,  Thanks in advance for any help you provide me.  

I'm trying to work around some issues with my USB extender cables.  The longer the cables are, the more errors I get in dmesg.  Basically I wanted to see if I could force it to use 1.1 USB, ie disable USB 2.0 support so the speed drops to 12Mbit versus 480Mbit.  The actual device is a Bluetooth dongle...   To get better reception I put it on a 10' extension cable. When I use that cable I loose HCI data and sometimes the device completely disappears from the bluetooth driver.  (not listed under "sudo hcitool dev") When that happens there are connection errors in "dmesg", but its still listed under "lsusb"  Since I don't really need high-speed on this system, I want to try to slow down the USB speed and hopefully eliminate the errors from this cheap USB cable.  Oh FWIW, the same dongle plugged directly to the USB port on my notebook will not give any errors in dmesg, and will stay connected, and can see more discoverable devices with the same antenna placement, just not running over a 10' USB extension cable.  So experiments have lead me to the conclusion that the USB extension cable is loosing data.  The obvious solution is to not use the extension cable, or get a better one, but first I want to try and slow down the connection speed to mitigate these errors.  If there is another way to accomplish that besides dropping it to USB 1.1, please share!  

I already bought several TripLite cables for this and sometimes there are no problems, but with about 1/2 the cables I get these errors.  I always had good experience with TripLite cables in the past, but recently these USB cables appear to have gotten thinner (cheaper, less shielding) because I have some from a couple years ago, same part number, just look thicker.

I've searched and found the suggestion to remove the USB 2.0 module by typing "sudo modprobe -r uhci_hcd" but get FATAL: module not found.  Uhhhhh does that mean this default installation 9.04 have USB2.0 support compiled into the kernel instead of a module?  How do I force USB 1.1?

Thanks.

---

### Post by lswb on 2009-07-26
You appear to be correct about usb support being compiled in on 9.04. In 8.04 the ehci_hcd.ko module was still used but I don't have it on my 9.04 system. 

There is usually a way to disable/enable compiled in drivers by echoing values to certain files in the /sys directories but I'm not an expert on it. This is kind of old info:
[http://lwn.net/Articles/143397/](http://lwn.net/Articles/143397/)
but maybe can point you in the right direction.

---

### Post by hemlockz on 2009-07-27
Okay, I just installed a kernel from array.org with module uhci_hcd... and when i disabled it all my usb ports stopped working.

---

### Post by hemlockz on 2009-07-27
sorry, hahah modprobe uhci_hcd  DUH

---

