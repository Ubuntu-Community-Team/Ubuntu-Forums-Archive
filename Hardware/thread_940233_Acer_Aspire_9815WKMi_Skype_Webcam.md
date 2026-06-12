---
title: "Acer Aspire 9815WKMi Skype Webcam"
date: 2008-10-06
forum: Hardware
---

### Post by skotos on 2008-10-06
On my laptop there is no way to get the webcam working other than with Skype.
Skype shows me the **UVC Camera (046d:09b0) (/dev/video0)**, switches on the led and I can see myself correctly in the options panel.
If I run *luvcview*, instead, I get the following:
```

luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 16.
 Init v4L2 failed !! exit fatal

```*caminfo* returns the following:```
CVideoCollector::VideoCollector()
>> CVideoDevice::CVideoDevice()
<< CVideoDevice::CVideoDevice()
>> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video0)
CVideoDeviceInput: Warning: no channel info available.
<< CVideoDeviceLinux::CVideoDeviceLinux()
>> CVideoDevice::CVideoDevice()
<< CVideoDevice::CVideoDevice()
>> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video1)
<< CVideoDeviceLinux::CVideoDeviceLinux()
```Is there a way to merge the received feedback and have a definitely working webcam with the other apps ?

---

### Post by skotos on 2009-02-26
FYI
Upgrading to Intrepid Ibex automatically solved the problem. The Intrepid Ibex increased hardware detection functionalities made it work just out of the box. The same happened to the wireless nic.

---

