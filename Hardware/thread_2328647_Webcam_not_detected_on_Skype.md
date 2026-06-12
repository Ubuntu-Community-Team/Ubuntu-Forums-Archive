---
title: "Webcam not detected on Skype"
date: 2016-06-23
forum: Hardware
---

### Post by Kev-inc on 2016-06-23
Hello!
I have installed Xubuntu 14.04 in a laptop and there are some problems with the built-in webcam.
I was able to use it only after installing Cheese: it was not in the original installation, but it correctly shows the video. The webcam is mapped as /dev/video0. When using Skype (v. 4.3.0.37) instead, it does not detect any webcam. What can be the problem?
Thank you anyway!

Kevin

---

### Post by mörgæs on 2016-06-25
Hi, welcome to the fora.

Please post the output from **lsusb** in CODE tags.

---

### Post by Kev-inc on 2016-06-27
> **mörgæs said:**
> Hi, welcome to the fora.

Hi :)! Thank you!

> **mörgæs said:**
> Please post the output from **lsusb** in CODE tags.

Here it is:

```
Bus 002 Device 002: ID 04f2:b064 Chicony Electronics Co., Ltd CNA7137 Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 008 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

The webcam is obviously the first item.

---

### Post by mörgæs on 2016-06-28
Hi, I don't know this particular webcam. The best I can suggest is searching for the ID number **04f2:b064** to see if other people have had the same problem. 

Another option which may or may not work is a fresh install of 16.04. Hardware support is in general better here than in 14.04.

---

### Post by coldraven on 2016-06-28
Is the camera view just  black in Skype? If so, shine a flash-light at it, do you see anything?
If so then install guvcview
```
sudo apt-get install guvcview
```
Then uncheck any "Auto level".
Adjust the brightness
Quit guvcview.
Try Skype again

---

### Post by mastablasta on 2016-06-29
Copy and paste this command into terminal:
```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

if you get an error then try to run this one:

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

if you have 64 bit then you may need to install the library before these would work so:

```
sudo apt-get install libv4l-dev
```

if the above commands launch skype and make the camera work, then you can create the launcher and add them to it.

more here: [ [SIZE=2]https://help.ubuntu.com/community/Webcam/Troubleshooting [/SIZE]]("https://help.ubuntu.com/community/Webcam/Troubleshooting")

---

