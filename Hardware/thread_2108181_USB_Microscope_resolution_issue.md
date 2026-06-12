---
title: "USB Microscope resolution issue"
date: 2013-01-24
forum: Hardware
---

### Post by nathandetroit on 2013-01-24
I have a DigiMicro 2.0 Mega-pixel USB Digital Microscope (it shows up in lsusb as "Z-Star Microelectronics Corp." The camera is recognized by Linux, and I get an image in either Camorama or Cheese. 

Camorama identifies the device as: Vimicro USB2.0 UVC PC Camera

The problem is that the maximum image resolution I can get is 640x480. In a test with Windows 7, I was able to get 1600x1200 resolution. Comparing snapshots taken at the two resolutions shows that the 1600x1200 image definitely has higher resolution.

Now, lsusb shows a max resolution for the device of 640x480, yet Windows is able to get higher resolution. Somehow the Windows driver is getting the full resolution (2 mega-pixels) out of the device.

My question is this: How can I get Ubuntu to "over-ride" lsusb and get the full device resolution?

---

