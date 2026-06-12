---
title: "Disabling a USB Bluetooth adapter"
date: 2011-08-13
forum: Hardware
---

### Post by SteveWilliams on 2011-08-13
Hi All!

I recently purchased an Asus e35m1-i Deluxe which has onboard bluetooth on the rear panel which I cannot remove. Because I want to use the system as a HTPC, I got a second bluetooth adapter so that my bluetooth devices would be able to reach the distance that I'd like to have.

The problem is that I cannot find a way to disable the onboard bluetooth without disabling it all. I have figured out that the adapter that I want to remove sits on the USB bus, as an ASUS EDR 2.0 adapater, but every trick I have found to disable it, turns off the entire bluetooth subsystem rather than the adapter on its own.

I know that in Windows, I could just head to device manager and disable it, but I cannot find any similar way in Ubuntu of achieving this.

Thanks in advance

Steve

---

### Post by sbraz on 2011-08-13
rather than disabling it i'd try blacklisting the device entirely.

i don't know if this works for usb devices too, but it sounds promising. just use **lsusb** instead **lspci**
[http://www.ehow.com/how_6885724_disable-linux-pci-device.html](http://www.ehow.com/how_6885724_disable-linux-pci-device.html)



another way could be using udev rules.
[B]man udev
/etc/udev/rules.d/*[/B]
[http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-11/msg01527.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-11/msg01527.html)

---

### Post by SteveWilliams on 2011-08-15
Thanks for the response sbraz!

I have tried both the solutions, I had tried the first one before posting, which brought me no luck.

Upon trying the second solution, I seemed to have disabled the entire USB hub, which in turn, disabled the other USB dongle that I needed to use. It seems the front ports are on the same root hub as the onboard BT.

I have contacted Asus to request a change in the BIOS for now and see how I get on with that.

Best Regards

Steve

---

