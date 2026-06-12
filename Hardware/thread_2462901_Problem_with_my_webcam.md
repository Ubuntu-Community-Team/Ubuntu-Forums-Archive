---
title: "Problem with my webcam"
date: 2021-05-29
forum: Hardware
---

### Post by gratus2 on 2021-05-29
Hello,

I have a webcam which is ok in Windows but is not recognized by ubuntu's software (cheese or Skype).

When I do dmesg, I have:

```
[   55.466644] usb 1-13: new high-speed USB device number 6 using xhci_hcd
[   55.616933] usb 1-13: New USB device found, idVendor=0711, idProduct=3108, bcdDevice= 0.10
[   55.616938] usb 1-13: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   55.616942] usb 1-13: Product: j5 WebCam JVCU100
[   55.616944] usb 1-13: Manufacturer: HD 2MP WEBCAM
[   55.616947] usb 1-13: SerialNumber: V20201016003RSJXF23
[   66.042836] videodev: Linux video capture interface: v2.00
[   76.318882] uvcvideo: Found UVC 1.00 device j5 WebCam JVCU100 (0711:3108)
[   76.318885] uvcvideo: Forcing device quirks to 0x100 by module parameter for testing purpose.
[   76.318886] uvcvideo: Please report required quirks to the linux-uvc-devel mailing list.
[   76.830854] uvcvideo: Failed to query (GET_INFO) UVC control 2 on unit 1: -110 (exp. 1).
[   77.342758] uvcvideo: Failed to query (GET_INFO) UVC control 3 on unit 1: -110 (exp. 1).
[   77.854839] uvcvideo: Failed to query (GET_INFO) UVC control 4 on unit 1: -110 (exp. 1).
[   78.366827] uvcvideo: Failed to query (GET_INFO) UVC control 2 on unit 2: -110 (exp. 1).
[   78.878831] uvcvideo: Failed to query (GET_INFO) UVC control 3 on unit 2: -110 (exp. 1).
[   79.390835] uvcvideo: Failed to query (GET_INFO) UVC control 7 on unit 2: -110 (exp. 1).
[   79.902978] uvcvideo: Failed to query (GET_INFO) UVC control 8 on unit 2: -110 (exp. 1). 
[   80.414949] uvcvideo: Failed to query (GET_INFO) UVC control 10 on unit 2: -110 (exp. 1).
[   80.926998] uvcvideo: Failed to query (GET_INFO) UVC control 4 on unit 2: -110 (exp. 1).
[   81.438982] uvcvideo: Failed to query (GET_INFO) UVC control 5 on unit 2: -110 (exp. 1).
[   81.950692] uvcvideo: Failed to query (GET_INFO) UVC control 11 on unit 2: -110 (exp. 1).
[   92.190919] uvcvideo: Failed to query (129) UVC probe control : -110 (exp. 26).
[   92.190926] uvcvideo: Failed to initialize the device (-5).
[   92.191100] usbcore: registered new interface driver uvcvideo
[   92.191102] USB Video Class driver (1.1.1)
[   97.311194] usb 1-13: 3:1: usb_set_interface failed (-110)

```

The product use standard UVC/UAV protocol. What should I do?

Thanks for your help.

---

### Post by TheFu on 2021-05-30
I can't say what you should do. I know what I would do.  I'd buy a well-supported webcam that "just works" with Linux.  Webcam prices have dropped to well below the pre-COVID prices.  Last month, I saw a Logitech C920 for $55, which is about half the price I paid for mine 6 yrs ago.  

If you don't need 1080i @ 30Hz, you can get a well-supported Logitech C270. This is a 720p webcam, also "just works" with Linux. Think it was $30 last month.

Of course, you could fight with this webcam too.  For that, I'd begin with looking up the USB identifier (0711:3108) in the supported USB device list.  That webcam isn't in the list of supported USB devices. 
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) might have other tidbits.

You could try to contact the vendor directly and ask about Linux support.  Most vendors never test their hardware with Linux, unless you get someone inside the company who is a Linux fan and does it on her own time.  That person might have knowledge for driver options to make it work, a little, if not completely. 

I wouldn't hold my breath for this webcam to work well. Sorry.
[https://www.reddit.com/r/linuxquestions/comments/lsm7uy/linux_driver_helpj5_webcam_jvcu100/gosbsgo/](https://www.reddit.com/r/linuxquestions/comments/lsm7uy/linux_driver_helpj5_webcam_jvcu100/gosbsgo/) has someone trying to figure out the same webcam. They didn't get very far.

---

