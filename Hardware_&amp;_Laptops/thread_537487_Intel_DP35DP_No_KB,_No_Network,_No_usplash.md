---
title: "Intel DP35DP: No KB, No Network, No usplash"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by espi3d on 2007-08-29
Hi, this is my hardware:
Motherboard Intel DP35DP
Micro Intel Core 2 Duo
RAM 2GB DDR2 in dual channel
Video GeForce 8600 GT PCIexpress x16
Logitech TrackMan Marble Whell (USB Trackball)
Keyboard Genius Slimstar (USB)

The motherboard doesnt support PS/2 nor floppy drive

The case is, when running the live CD the keyboard works at GRUB but not in the loaded desktop.
When the desktop is loading usplash does not show up, instead, the monitor turns like it's off (the "On" light is blinking) then, when the desktop is loaded, I have no keyboard and no network, but the trackball works perfectly.

I got to install ubuntu using an onscreen keyboard and when it comes to the grub part (after the installation) the keyboard doesnt work, but it works when on "safe mode" (F windows menu.
This is strange. The keyboard works under windows.

Ah, and the Legacy USB support is enabled in BIOS.

I dont know what else to ask. I have spent too much money on this computer just for this to not work.
Please help me I'm desperate.

---

### Post by gertmul on 2007-08-29
Try Gutsy Gibbon, 7.10

(I had the network working...and then enabled the nVidia proprietary driver which cancelled networking, so don't do that yet if you have such a card)

---

### Post by espi3d on 2007-09-05
I just tried Gutsy Tribe 5 in live CD and the results were:
1- At GRUB the usb keyboard works fine
2- No usplash (screen is gone and monitor power led is blinking)
3- No keyboard working on live CD desktop
4- My usb logitech trackball works flawlessly all the time

What keyboard brand/model do you have?
Is the keyboard malfunctioning?
how am I supose to install this in order to work?

---

### Post by espi3d on 2007-09-07
Now, after a few tests I found that if I unplug the keyboard and replug it several times, it works after a while. But it might have to do with some usbkbd vs usbhid stuff. so it is not like usbhid being a superset of usbkbd. Is linux deprecating usbkbd for any reason?

---

