---
title: "[SOLVED] Webcam not detected, yet seen in lsusb"
date: 2008-06-10
forum: Hardware
---

### Post by dapps2k on 2008-06-10
I'm trying to get my webcam, Rosewill RCAM-100 to work with Ubuntu.  I'm really confused why it doesn't work now since it worked on the LiveCD.  The lsusb command gives this for the webcam:
```
Bus 002 Device 007: ID 0c45:602c Microdia Clas Ohlson TWC-30XOP WebCam
Bus 002 Device 006: ID 045e:00f0 Microsoft Corp. 
Bus 002 Device 005: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 002 Device 004: ID 056a:0013 Wacom Co., Ltd 
Bus 002 Device 003: ID 04ca:0020 Lite-On Technology Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
Bus 001 Device 006: ID 0bda:0103 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000 
```

And I assume the webcam is under the Microdia Clas name.  Though with the LiveCD, it worked in Exiga using the V4L driver under the Videocam Messenger sn9c101 Ov76 name.

The dmesg output is also giving out a lot of these messages:
```
[ 5105.643465] ohci_hcd 0000:00:0b.0: leak ed df8358c0 (#81) state 2
[ 5105.643899] usb 2-1: usb_submit_urb() failed, error -28
```

Any ideas how I can get this working?

---

### Post by dapps2k on 2008-06-10
I got it to work.  I found out that I had two webcam drivers installed and were conflicting with each other.  I had to remove the sn9c102 driver and keep the gspca driver.

---

### Post by Joentokyo on 2010-10-23
> **dapps2k said:**
> I got it to work.  I found out that I had two webcam drivers installed and were conflicting with each other.  I had to remove the sn9c102 driver and keep the gspca driver.

Could you please tell me how to remove the sn9c102 driver

---

### Post by kwacka on 2011-05-30
Late I know, but thanks for the tip, dapps2k, just found an old webcam in a drawer and working fine.

Joentokyo (and anybody else who might want to know)

Open terminal (or hit Alt + F2) and enter: 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and add```
 blacklist sn9c102
``` to the list.

Probably best to restart computer.

---

