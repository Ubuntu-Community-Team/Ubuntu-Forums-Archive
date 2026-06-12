---
title: "Touchscreen drivers, Keytec MagicTouch USB-XD"
date: 2009-05-21
forum: Hardware
---

### Post by quadra on 2009-05-21
Hi there

This post may help people to get Keytec MagicTouch touchscreens to work under Ubuntu 9.04.

On the website ([www.magictouch.com](www.magictouch.com)), I found the drivers for Ubuntu 7.04 and 7.10 (driver version 2.10), 8.04 (version 2.20) and 8.10 (own version). 
At the time of writing, the 9.04 (Jaunty) driver was not there, but it was e-mailed to me very quickly when I filed a support request using the web form.
(The older drivers did NOT work with Jaunty.)

There is an install script with the driver. Installation basically consists of copying the file etouch_drv.so to /usr/lib/xorg/modules/input, and adding some lines to /etc/X11/xorg.conf.

Here are the steps that got it done for me:

0) Since I had done some manual attempts with other drivers before, I deleted the corresponding driver files and cleaned stuff related to "etouch" in /etc/X11/xorg.conf just to be sure
1) Extract driver to some directory, open a terminal there
2) Run install script: **sudo ./install_Ubuntu9.04**
3) Verify xorg.conf: **sudo gedit /etc/X11/xorg.conf** - Verify entries related to etouch. The driver normally listens to /dev/usb/hiddev0, which may be wrong if there are other USB devices. To find out which device my touchscreen was, I opened /dev/usb/ and I unplugged - replugged the touchscreen, to see which of the USB devices disappeared. Then I fixed it in xorg.conf (hiddev1 instead of hiddev0 in my case - hid = human interface device)
4) After rebooting, touchscreen should work, but not precisely yet.
5) In terminal, type **Calibration** to perform calibraiton. It shold display a white screen with black circles. (This tool was installed in /usr/local/bin along with two others; it seems that it works without sudo now)

Worked on: Ubuntu 9.04 (kernel 2.6.28-11-generic).

---

### Post by SeRiAl_H on 2009-08-11
I am trying to make myself a jukebox with a touch screen and am using a MagicTouch USB-XD and have done all you have listed here but when I do the Calibration it causes a Segmentation Fault

---

