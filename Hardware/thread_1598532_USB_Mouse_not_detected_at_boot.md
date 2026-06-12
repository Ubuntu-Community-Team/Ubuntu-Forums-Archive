---
title: "USB Mouse not detected at boot"
date: 2010-10-16
forum: Hardware
---

### Post by BicLighter on 2010-10-16
I recently upgrade my ancient USB Microsoft optical mouse from circa 1999 to a Razer Imperator mouse.  Neither Ubuntu 10.04 nor 10.10 (amd-64) will detect this new mouse at boot - immediately after the grub selector, the mouse light goes off as if it's lost power.  If I unplug in and plug it back in though, it detects and works perfectly fine.  If it makes a difference, my mainboard is an eVGA FTW-200 series running an i5.  The mouse works perfectly fine under Windows 7.

I have tried a couple of tricks mentioned on the forums, upgrading the mouse firmware to the latest (1.15) and editing my grub command line to include "acpi=force irqpoll", but neither has made a difference.

Any ideas on how to fix this?

---

### Post by BicLighter on 2010-12-18
So the mouse is still not detecting correct at boot, but does detect after a unplug/plug on latest kernel, 2.6.34.

/var/log/dmesg contains the following suspicious lines:

[    5.257470] usb 8-2: device descriptor read/64, error -71
[    5.487022] usb 8-2: new full speed USB device using uhci_hcd and address 3
...
[    5.616760] usb 8-2: device descriptor read/64, error -71
...
[    6.085844] usb 8-2: new full speed USB device using uhci_hcd and address 4
[    6.505015] usb 8-2: device not accepting address 4, error -71
..
[       7.043954] usb 8-2: device not accepting address 5, error -71
[       7.043969] hub 8-0:1.0: unable to enumerate USB device on port 2

Running an lsusb after boot does not display anything related to the mouse, but causes several background messages to be piped to the console which are similar to the above dmesg errors, just with different address numbers and timestamps.

Unplugging and plugging the mouse back in does succesfully let lsusb show the mouse as:

Bus 008 Device 018: ID 1532:0017 Razer USA, Ltd 

And no more background error messages are piped to the console.

Does anybody have any idea what this mysterious error -71 is?  The USB is plugged directly into the Intel P55-based motherboard if that makes a difference, but I am at a loss.

---

### Post by edantes on 2011-01-26
I am bumping this post as I have been having this same problem off-and-on with a variety of generic USB mice.  

I'm running Ubuntu 10.10 AMD-64

Mouse won't be recognized at boot, but will work fine after unplugging and plugging it back.

It looks like boot is bypassing the mouse device activation. There are no messages issued at boot time. When I unplug and plug back, these messages are issued:

> Jan 26 11:44:36 ggv-desktop kernel: [ 2386.080807] usb 3-2: USB disconnect, address 6
Jan 26 11:44:59 ggv-desktop kernel: [ 2408.230076] usb 3-2: new low speed USB device using ohci_hcd and address 12
Jan 26 11:44:59 ggv-desktop kernel: [ 2408.439003] input: USB Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input4
Jan 26 11:44:59 ggv-desktop kernel: [ 2408.449192] generic-usb 0003:1BCF:0007.0002: input,hiddev96,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:13.1-2/input0


---

### Post by IWantFroyo on 2011-01-26
I know this might be stupid, but have you plugged it in and ran additional drivers? Sometimes you also have to get a driver of the web.

---

### Post by edantes on 2011-01-26
> **IWantFroyo said:**
> I know this might be stupid, but have you plugged it in and ran additional drivers? Sometimes you also have to get a driver of the web.

Thanks for your suggestion.  The mouse works fine if I plug it in after booting, I assume all drivers are present.

Tried the following  suggestions from other threads, but my partivcular problem was NOT solved:

1. Plug the mouse to a different USB interface.   My motherboard has 3(?).  The mouse works at boot time from one of them.

2. Enable the USB Mouse at the BIOS configuration

---

### Post by infomissing123 on 2011-09-14
See if your bios has an option for "USB Legacy" or something similar.  Some of the older boards require this to have usb device support in the bios for keyboards and mice.

---

