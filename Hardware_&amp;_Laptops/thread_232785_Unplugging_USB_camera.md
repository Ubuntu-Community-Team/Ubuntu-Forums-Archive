---
title: "Unplugging USB camera"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by hadders on 2006-08-09
Hello
I'm using a sony cybershot dsc-s600 over USB with Ubuntu 6.06, and it seems to be messing up my usb devices - Basically if I unplug or turn off the camera once connected, it causes my USB wireless device to turn off (ZD-1211).

Am I doing this right by just unplugging the camera? I can't find anyway of disconnecting within the OS (as you can in Windoz)

Is there a way I can re initialize the USB wireless dongle?

Thanks
Hade

---

### Post by huygens on 2006-08-09
Very weird problem...
I have a Canon Powershot A70 and I can turn off the camera without problems. However, one should notice that the camera is not seen as an hard disk by Ubuntu.
I have a friend who has one of this small Sony camera (pocket-party type). To connect it to Linux we had to set the protocol to be PTP if I recall. Thus, Linux (aka Ubuntu) would sees it as a hard drive.
Before turning off the camera, we then ejected it. On the desktop, there was a new icon that appeared after the connection. By right-clicking this icon we were able to choose 'Eject' and properly disconnect the camera.

Do you see this icon on your desktop?

I cannot help you about reinitialising the USB dongle. Try unplugging it and plugging it back...

Huygens

---

### Post by hadders on 2006-08-09
Hi 
I have the camera set to PTP, and am able to access it - on turning on, I'm asked if I want to import the images using gThumb veiwer. And can import the pictures without any problems.

I don't get a drive on the desktop, nor can I see a removeable drive anywhere.

If I do lsusb in terminal I get:
> Bus 004 Device 004: ID 054c:004e Sony Corp. DSC-xxx (ptp)
Bus 004 Device 002: ID 07b8:6001 D-Link Corp.
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000

When I turn off the camera, the USB wireless stops working, but still appears in the lsusb list! I tried unplugging and plugging in but still needed a restart to get it working..

---

### Post by hadders on 2006-08-09
Bizzare, If i unplug the USB wireless, turn off the camera, then plug the wireless USB in, all is ok!

---

### Post by huygens on 2006-08-10
sorry, I have no idea why you have such a problem... Perhaps you could try to file a bug report...

---

