---
title: "Verbatim 1.5tb not recognized"
date: 2010-11-06
forum: Hardware
---

### Post by Gregg0 on 2010-11-06
I have a verbatim 1.5tb external hdd that isn't recognized automatically, while my other maxtor hdd is. I can't see anything on fdisk, nor dmesg when turning it on/off as well. It's a USB with NTFS filesystem. 

Anyone knows how can I fix this? 

Thanks.

---

### Post by P4man on 2010-11-06
So plugging it in doesnt trigger any event line in dmesg ? I suppose lsusb doesnt show anything either then? Are you sure the drive actually works?

---

### Post by Gregg0 on 2010-11-06
> **P4man said:**
> So plugging it in doesnt trigger any event line in dmesg ? I suppose lsusb doesnt show anything either then? Are you sure the drive actually works?


I even tried turning it on/off while plugged. Nothing. 

I'm positive it works. I just installed ubuntu over windows 7 and the hdd was working perfectly under windows.

---

### Post by P4man on 2010-11-06
thats really odd. Even when plugging in a completely unsupported device (and usually even a broken one) at the very least shows up in dmesg as an event.

Have you tried other usb ports or a powered USB hub? Does hotplugging say, a USB mouse work?

---

### Post by Gregg0 on 2010-11-06
> **P4man said:**
> thats really odd. Even when plugging in a completely unsupported device (and usually even a broken one) at the very least shows up in dmesg as an event.

Have you tried other usb ports or a powered USB hub? Does hotplugging say, a USB mouse work?

I have my other HDD working on USB. My mouse as well and it's USB.

---

### Post by P4man on 2010-11-06
I mean if you unplug it, and plug it back in, preferably a different port (or the same port you use for the problematic drive), does the mouse still work?

---

### Post by Gregg0 on 2010-11-06
> **P4man said:**
> I mean if you unplug it, and plug it back in, preferably a different port (or the same port you use for the problematic drive), does the mouse still work?

Sure. I tried plugging/unplugging the USB HDD on all ports. None worked.

---

### Post by P4man on 2010-11-06
Im just trying to make sure USB hotplugging works. If it doesnt, then the problem isnt with the drive but the USB controller. But I take it now it does work.

Can you post your dmesg log? Preferably one after you disconnect and reconnect both a mouse and that drive.

---

### Post by Gregg0 on 2010-11-06
> **P4man said:**
> Im just trying to make sure USB hotplugging works. If it doesnt, then the problem isnt with the drive but the USB controller. But I take it now it does work.

Can you post your dmesg log? Preferably one after you disconnect and reconnect both a mouse and that drive.

Here it is. 

```
 dmesg 
[ 4415.808140] usb 6-1: USB disconnect, address 6
[ 4420.480303] usb 6-1: new low speed USB device using uhci_hcd and address 7
[ 4420.678900] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input16
[ 4420.679237] generic-usb 0003:0458:003A.0008: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:1d.1-1/input0

```

That's the mouse. When I connect/disconnect the HDD it doesn't show anything. I tried it on each of the USB ports (I have three).

---

### Post by P4man on 2010-11-06
Does the drive have its own AC adaptor or does it pull power from the USB ports?

---

### Post by Gregg0 on 2010-11-06
> **P4man said:**
> Does the drive have its own AC adaptor or does it pull power from the USB ports?

It has it's own AC (the other one that work has it's own AC as well).

---

### Post by P4man on 2010-11-06
In that case, Im stumped. Perhaps you can try booting with the drive connected and check if the bios can find the drive (eg by accessing the bios boot menu) and if maybe ubuntu sees the drive if it was connected before the boot, but frankly, I have no real idea what it could be.

---

