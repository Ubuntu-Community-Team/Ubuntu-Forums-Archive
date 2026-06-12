---
title: "hauppauge USB-live model 600 and edgy"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by larryk335 on 2007-03-07
I have a telescope with a electronic eyepiece and I am trying to figure a way to get images onto my computor. I bought that video sampler so I could hookup my eyepiece with a RCA connection to a USB port.  I checked the hauppauge website and could find no drivers for Edgy or linux period.  Anyone who could help would be greatly appreciated:KS

---

### Post by jeremybear on 2008-01-18
I got this device working (after a fashion) in Gutsy 7.10 by following these steps; prefixed with "sudo" where necessary:

1. Unplug the Hauppauge "USB Live" from the USB port.
2. modprobe bttv
3. modprobe usbvision
4. Plug the "USB Live" back in again
5. dmesg (to check that the device is recognized correctly)
6. apt-get install xawtv motv
7. xawtv -nodga 

If this works, you can try the command "motv" - this launches xawtv with the correct options.

For some reason, it does not work with VLC or TVtime. The latter thinks the device is a low-res webcam and refuses to open it. The results you get with xawtv are certainly low-res, but watchable.

If you are still on Edgy, you may have to dist-upgrade to Feisty then Gutsy to get the latest drivers.

---

