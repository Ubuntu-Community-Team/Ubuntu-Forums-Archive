---
title: "Problem with Ipevo usb camera"
date: 2020-02-19
forum: Hardware
---

### Post by 73sam on 2020-02-19
Hello,

I have an Ipevo usb camera and since the last kernel update the camera doesn't work...

Product: P2V Point 2 View USB Document Camera

OS:  Linux version 5.3.0-40-generic (buildd@lcy01-amd64-024) (gcc version  7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1)) #32~18.04.1-Ubuntu


usb camera well detected but uvc kernel driver not loading.
There is no /dev/video0 file created.
here is the result of "dmesg | tail" command :

[ 3390.529798] usb 1-1.4: Manufacturer: IPEVO Inc.
[  3390.531093] hid-generic 0003:1778:0214.0006: hiddev0,hidraw2: USB HID  v1.10 Device [IPEVO Inc. IPEVO Point 2 View] on  usb-0000:00:1a.0-1.4/input0
[ 3390.533871] uvcvideo: Found UVC 1.00 device IPEVO Point 2 View (1778:0214)
[ 3390.533979] uvcvideo: Failed to query (GET_INFO) UVC control 2 on unit 1: -32 (exp. 1).
[ 3390.534597] uvcvideo: Failed to query (GET_INFO) UVC control 9 on unit 1: -32 (exp. 1).
[ 3390.536351] uvcvideo: No streaming interface found for terminal 2.
[ 3390.536357] uvcvideo 1-1.4:1.1: Entity type for entity Extension 4 was not initialized!
[ 3390.536362] uvcvideo 1-1.4:1.1: Entity type for entity Processing 3 was not initialized!
[ 3390.536365] uvcvideo 1-1.4:1.1: Entity type for entity Camera 1 was not initialized!
[ 3390.536496] input: IPEVO Point 2 View: IPEVO Point as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input21


I have found someone with the same issue on opensuse here : [https://www.spinics.net/lists/linux-usb/msg189431.html](https://www.spinics.net/lists/linux-usb/msg189431.html)

thanks for helping

---

### Post by 73sam on 2020-02-19
Here is a good description of the problem and how they resolve it ( but on opensuse )
[https://bugzilla.suse.com/show_bug.cgi?id=1159811](https://bugzilla.suse.com/show_bug.cgi?id=1159811)

---

### Post by 73sam on 2020-02-20
I have made a ticket on Ipevo website and I waiting an answer...

---

### Post by 73sam on 2020-02-21
I have received an answer from Ipevo :

"Hi Samuel,
Thank you for contacting IPEVO.
After analyzing the log file you provided, our engineers believe that the issue should be related to Linux kernel.
Please let me know if you have any other questions.
Thank you and have a nice day!"

What should I do now?

---

### Post by 73sam on 2020-02-24
Up

---

### Post by 73sam on 2020-02-25
I found that :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1861344](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1861344)
I hope I understood the manipulation. I just have to test it with my version

---

