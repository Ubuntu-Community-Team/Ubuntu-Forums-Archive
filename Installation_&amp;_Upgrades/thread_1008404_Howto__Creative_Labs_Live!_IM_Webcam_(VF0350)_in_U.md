---
title: "Howto:  Creative Labs Live! IM Webcam (VF0350) in Ubuntu Intrepid"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by mocha on 2008-12-11
In case someone needs this for the future, this is how I got my Creative VF0350 webcam/mic working in Ubuntu Intrepid.  Note that I use this device only for Skype, I can't vouch for these instructions if you are using the device with some other application.

Using "lsusb" gives me a Device ID 041e:4067 Creative Technology, Ltd

[http://www.ubuntuhcl.org/browse/product+creative-labs-live-cam-video-im-vf0350?id=4929]("http://www.ubuntuhcl.org/browse/product+creative-labs-live-cam-video-im-vf0350?id=4929")

Follow the procedure linked above for compiling and installing the hacked ov51x_jpeg driver.

If using only for Skype, DO NOT add "options ov51x_jpeg force_rgb=1" to /etc/modprobe.d/options as explained in the procedure, the red-blue color issue is not a problem in Skype, only in other applicatons.  If the cam is needed outside of Skype, then using "force_rgb=1" when loading the module will be necessary.

To manually load the module and test the camera use "modprobe ov51x_jpeg forceblock=1"

"lsmod | grep ov" shows:

ov51x_jpeg            159224  0 
videodev               41344  5 ov51x_jpeg,msp3400,tuner,ivtv,bttv
usbcore               149360  10 ov51x_jpeg,snd_usb_audio,snd_usb_lib,usbhid,usblp,usb_storage,libusual,uhci_hcd,ehci_hcd

For automated loading of the module during bootup (with the correct options for Skype), edit /etc/modprobe.d/options to include "options ov51x_jpeg forceblock=1" and edit /etc/modules with "ov51x_jpeg".

Replace "forceblock=1" with "force_rgb=1" in the /etc/modprobe.d/options file if NOT using with Skype.

---

