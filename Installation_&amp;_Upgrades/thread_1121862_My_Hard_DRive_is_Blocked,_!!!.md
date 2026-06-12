---
title: "My Hard DRive is Blocked, !!!"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by raeoh7 on 2009-04-10
I'm not sure with other Linux OSs but when i tried to install Ubuntu on my Hard Drive, there were something like

"I/O Buffer , somethign something (numbers) blocked

This Hard Drive is about 10 years old, the company is Barracuda.

Please HELP<, SOS!!! :(:(

---

### Post by cariboo on 2009-04-10
I suspect that you error has something to do with /dev/sr0. The error you're getting is a cdrom error, the drive can't read the CD.

Boot from the LiveCD and at the menu select the verify cdrom option to make sure your burn was OK.

I frequenty got that error when I burned the cd at to high a speed, I now burn iso's at 4X and have zero problems.

Jim

---

### Post by cariboo on 2009-04-11
Double-click the speaker icon in the top panel, and make sure the mic level is turned up. Then go to System-->Preferences-->Sound and try different settings for the capture device. In my case, the mic in my webcam (which isn't detected in Windows) is a usb device, so I select the usb id number for a capture device. BTW the webcam is a Logitec Quickcam Messanger, so the mic should work in Windows.

Jim

---

