---
title: "USB ports not working..."
date: 2010-08-19
forum: Hardware
---

### Post by jamesbeat on 2010-08-19
I've just installed Ubuntu on an older machine:

Pentium 4 1.5GHZ
1Gb RAM
Northbridge: VIA VT8751 (P4M266)
Southbridge: VT8233 

Everything seemed to go ok when I installed 10.04, but when I plugged in a USB wifi dongle, it didn't show.
I then tried a flash drive, nothing happened.

I read that there was a bug in 10.04 that prevented the USB ports working properly because of something to do with legacy floppy support, so I tried diabling the floppy drive in the bios and using this command:
```
sudo modprobe -r floppy
```

That didn't work, so I gave up and installed 9.10, reasoning that if I could get my USB wifi dongle working, I could update from there.

Unfortunately, that didn't solve the problem.
I still have no USB ports, and now I'm completely stumped.

The computer is in another room, and I have no internet access on it, so I can't copy and paste text, but I tried lsusb and got something like this for all three USB controllers:

```
Linux Foundation 1.1 root hub

```

This is with devices (wifi dongle and flash drive) plugged into the ports. They aren't showing up at all, as if there is nothing plugged into the ports.

A couple of other things I have tried:
I have definitely enabled USB in the bios
I have tried both enabling and disabling legacy usb support in the bios
I have tried both booting with devices connected to the usb ports and also booting with the ports empty and plugging in the devices afterwards.
I have tried disabling acpi in the bios.
I have tried both of the built in usb ports on the motherboard, and also tried external usb ports connected to both of the headers on the motherboard.

So far, nothing I have tried has given any kind of result. The devices have never been recognized and the output from lsusb has always been the same.

I'm really stumped.

This pc is for an 8 year old kid who wants to watch Dragonball Z and play Club Penguin. If we get this fixed, it will make his day :KS

---

### Post by Fafler on 2010-08-20
Have you tried a PCI card? This baby will most likely fix your problem for only $0.99, shipping included: [http://cgi.ebay.com/5-Port-USB-2-0-High-Speed-PCI-Controller-Card-HUB-Slim-/280550112398?pt=LH_DefaultDomain_0](http://cgi.ebay.com/5-Port-USB-2-0-High-Speed-PCI-Controller-Card-HUB-Slim-/280550112398?pt=LH_DefaultDomain_0)

---

### Post by jamesbeat on 2010-08-20
I did consider just getting a PCI card, and I guess that would be good as a last resort, but I'd rather get the existing ports to work if possible. It seems silly to buy more hardware, but if that's the only option I'll do it.

So, any other ideas?
And how likely is a PCI card to work?

---

### Post by jamesbeat on 2010-08-21
Forget it, I just went with a PCI USB card as suggested.
I think the ports were physically damaged, or the BIOS drivers were corrupted.
I couldn't risk trying to do anything with the BIOS because I'm not 100% sure exactly what model the motherboard is.

Good news is that the new ports are working fine :KS

---

