---
title: "Orbicam problem"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by walkero on 2007-12-13
Since the last Ubuntu updates a problem occurred on my AcerAspire 5685 WLMI. There is an error message from the begin of the boot, about the camera of my notebook. the funny think is that the last 10 months that I use the computer, I never had a problem with it. Ubuntu recognizes the camera and uses it from the first installation. But yesterday, the problem that occurred made the DUO Core CPU to work at full speed 100%. then, I don't know why, the computer powered off. Just like that. 

I made a format and a clean installation and everything was ok, the camera was working just fine. Until I made all the updates.... The problem occurred again after a reboot...

from the kernel log gives me the following all the time.

> 
Dec 14 02:14:01 ubuntu kernel: [ 6893.808000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
Dec 14 02:14:01 ubuntu kernel: [ 6894.040000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
Dec 14 02:14:01 ubuntu kernel: [ 6894.040000] gspca: probe of 2-2:1.0 failed with error -5
Dec 14 02:14:01 ubuntu kernel: [ 6894.040000] usb 2-2: USB disconnect, address 125
Dec 14 02:14:01 ubuntu kernel: [ 6894.280000] usb 2-2: new full speed USB device using uhci_hcd and address 126
Dec 14 02:14:02 ubuntu kernel: [ 6894.456000] usb 2-2: configuration #1 chosen from 1 choice
Dec 14 02:14:02 ubuntu kernel: [ 6894.460000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
Dec 14 02:14:02 ubuntu kernel: [ 6894.692000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
Dec 14 02:14:02 ubuntu kernel: [ 6894.692000] gspca: probe of 2-2:1.0 failed with error -5
Dec 14 02:14:02 ubuntu kernel: [ 6894.900000] usb 2-2: USB disconnect, address 126
Dec 14 02:14:02 ubuntu kernel: [ 6895.140000] usb 2-2: new full speed USB device using uhci_hcd and address 127
Dec 14 02:14:02 ubuntu kernel: [ 6895.316000] usb 2-2: configuration #1 chosen from 1 choice
Dec 14 02:14:02 ubuntu kernel: [ 6895.316000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 


---

### Post by homburg on 2008-03-31
I have this problem as well on my Acer TravelMate 4220

Using hardy, kernel 2.6.24-12-generic

---

### Post by doobydave on 2008-04-12
I have been noticing my ubuntu install failing to boot a number of times - hanging in a 'cant configure camera' loop.

I too have an acer 5685 and I'm wondering if the camera has an intermittent fault or whether windows and linux don't play fair with it.

Regardless of whether the camera is faulty or not, this error should not be a showstopper.

---

