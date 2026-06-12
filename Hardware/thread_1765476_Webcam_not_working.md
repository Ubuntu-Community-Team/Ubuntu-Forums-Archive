---
title: "Webcam not working"
date: 2011-05-23
forum: Hardware
---

### Post by GlobalServant on 2011-05-23
Hello everyone,

I have a webcam I used in the past that was working just fine. It still works in Windoze. However, since I upgraded to Natty, it won't work more than 15-30 seconds. This is what I'm getting in dmesg:

```

[  948.308071] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  948.631391] Linux video capture interface: v2.00
[  948.664368] uvcvideo: Found UVC 1.00 device USB2.0_Camera (093a:2800)
[  948.673110] input: USB2.0_Camera as /devices/pci0000:00/0000:00:13.5/usb1/1-1/1-1:1.0/input/input11
[  948.675578] usbcore: registered new interface driver uvcvideo
[  948.675589] USB Video Class driver (v1.0.0)
[ 1025.021071] usb 1-1: USB disconnect, address 3
[ 1028.252066] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1031.368044] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1034.472068] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1037.564061] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1037.564099] hub 2-0:1.0: unable to enumerate USB device on port 1

```

So what's going on? How can I fix that? :confused:

---

