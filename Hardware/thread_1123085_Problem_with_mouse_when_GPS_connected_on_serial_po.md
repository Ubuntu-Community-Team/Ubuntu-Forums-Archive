---
title: "Problem with mouse when GPS connected on serial port"
date: 2009-04-11
forum: Hardware
---

### Post by aloknrao on 2009-04-11
Hello

Here's the thing. I have a Garmin eTrex GPS handheld device from which I want to capture data using my laptop. I am running Ubuntu 8.10 on an IBM Thinkpad T61p. As the laptop does not have a serial port, I am connecting the GPS through a Serial Port to USB adapter. Now when I plug the USB into the laptop, the mouse pointer goes crazy and starts jumping around the screen. This stops as soon as I unplug the USB cable.
I did some googling or this and found out that the problem happens because the serial device I am connecting is being treated as a serial mouse. But almost all the problems were reported in Windows and I did not come across anybody facing the same problem in linux. Hence I am posting this question here. Does anybody know the solution to this problem?

Thanks
Aloknath

---

### Post by prahs rozar on 2009-04-11
Does the same problem ever happen with Windows? Find out why it happens there and tell us what you find. There is probably a parallel somewhere if it does.

---

### Post by aloknrao on 2009-04-11
Well I seem have to fixed it for now. Although I dont know how it got fixed, but its working fine. Here's what I did
1. Connect the Serial port to USB adapter into the USB port of the laptop, but leave the serial connector free.
2. Open the terminal and run lsusb.
3. Now connect the serial device to the adapter and turn it on.
4. Works like a charm.

I tried it out on Windows, doesn't happen there.

---

### Post by prahs rozar on 2009-04-11
I'm glad to hear that it works. I have no idea why it does that, but maybe someone else here will.

---

