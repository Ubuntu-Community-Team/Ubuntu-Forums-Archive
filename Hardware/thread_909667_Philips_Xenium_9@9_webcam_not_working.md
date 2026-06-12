---
title: "Philips Xenium 9@9 webcam not working"
date: 2008-09-03
forum: Hardware
---

### Post by stingx on 2008-09-03
Hi all.

I have a problem getting Xenium 9@9u to work as WebCam on Ubuntu 8.04 (kernel 2.6.24-21-generic)

**$> dmesg|tail**
```
...
[ 4290.656942] usb 2-1: new full speed USB device using uhci_hcd and address 11
[ 4289.258503] usb 2-1: configuration #1 chosen from 7 choices
[ 4289.405056] uvcvideo: Found UVC 1.00 device 9@9U    (0e8d:0004)
[ 4290.404565] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[ 4290.406560] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -71 (exp. 26).
[ 4290.406572] uvcvideo: Failed to initialize the device (-5).
[ 4292.266570] usbcore: registered new interface driver uvcvideo
[ 4292.266581] USB Video Class driver (SVN r246)
```
(This output with latest SVN *uvcvideo* driver. Original ubuntu driver gives same results)

*/dev/video0* device wasn't created.

Even, removing *uvcvideo.ko* from */lib/modules/* and loading via *insmod uvcvideo.ko* manually after replugging USB wont work (same results).

Any ideas?

---

### Post by IntuitiveNipple on 2008-09-03
I'm afraid it means the device isn't fully UVC (USN Video Class) standard compatible, as you can see from the kernel messages.

The only possibility is if someone has/is created/ing a driver for the chipset that is in the device. If you can find out what that is (maybe from examining or posting the Windows driver installer .inf file for the camera) it might give some clues.

---

