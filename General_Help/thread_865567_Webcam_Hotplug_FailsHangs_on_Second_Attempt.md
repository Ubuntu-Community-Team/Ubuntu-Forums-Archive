---
title: "Webcam Hotplug Fails/Hangs on Second Attempt"
date: 2008-07-20
forum: General Help
---

### Post by peacekpr on 2008-07-20
When I hotplug my Logitech webcam the first time, it is recognized, and dmesg shows the following information indicating that the webcam is recognized:
> 
usb 6-3: new high speed USB device using ehci_hcd and address 9
uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:13.5/usb6/6-3/6-3:1.0/input/input10
usbcore: registered new interface driver uvcvideo
USB Video Class driver (SVN r232)
I am able to use the webcam with Ekiga and Skype with no problems.  The problem arises when the webcam is hotplugged a second time.  When it's hotplugged the second time, the lsusb command hangs without showing any information until I unplug the webcam.  Ekiga and other software cannot detect the webcam at this point either.  The dmesg command only results in the following:
> 
usb 6-3: new high speed USB device using ehci_hcd and address 9
In order for me to be able to use the webcam upon the second "hotplug," I have to reboot the machine, which is obviously undesirable.   I've spent a couple of days tinkering to see if I can get it the machine to recognize the webcam on the second hotplug but to no avail.  Does anyone know how to correct this problem?

My machine: Dell Inspiron 1501 with Ubuntu 8.04 i386 with the 2.6.24-19-generic kernel.

Jason

---

### Post by Polygon on 2008-07-21
i have experienced something similiar with my webcam, which  is a logitech quickcam 3000, it seems that if i fire up cheese, it works fine but then after a while it stops working , and i have to reboot cheese in order for it to start working again

im thinking its just a bug in the underlying code for webcams or something

i followed the instructions here to get my webcam working, 

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

maybe that will help

---

### Post by peacekpr on 2008-07-23
Well, the webcam works just fine on the first "hotplug."  But if I want to use it anytime later on, I have to reboot Ubuntu altogether, which is quite annoying.

Thanks.

---

