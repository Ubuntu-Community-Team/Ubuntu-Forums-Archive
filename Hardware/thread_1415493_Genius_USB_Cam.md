---
title: "Genius USB Cam"
date: 2010-02-24
forum: Hardware
---

### Post by Axel-P on 2010-02-24
Hi all,

My family has bought a new usb camera for their computer. This camera has a little issue, it shows the image upside down.
 
I'm following [this]("http://ubuntuforums.org/showthread.php?t=838210") tutorial. Problem is this part:

> Then type:
Code:

sudo lsusb -d xxxx:yyyy -v | grep "14 Video"


If you get something like the following, your webcam is UVC capable:
Quote:
bFunctionClass 14 Video
bInterfaceClass 14 Video
bInterfaceClass 14 Video
bInterfaceClass 14 Video

If your webcam passes this test, you can go on reading. Otherwise, your camera needs to use propertary driver, because it doesn't use standard protocol/command

Well the "sudo lsusb -d xxxx:yyyy -v | grep "14 Video"" command prompts nothing. I've tried installing the driver from [this]("http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?pli=1") page. The driver installation worked but the lsusb -d command wont prompt anything.

here's the lsusb prompt:
```
Bus 001 Device 002: ID 03f0:5611 Hewlett-Packard PhotoSmart C3180
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 002: ID 093a:2624 Pixart Imaging, Inc. WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


If you need anything else just ask

Axel

---

### Post by Axel-P on 2010-02-26
Bump?

---

### Post by gordintoronto on 2010-02-26
What model webcam is it?  lsusb shows it to be a Pixart, but I suspect Pixart has produced more than one webcam.

If you get an image, you don't need to install a driver. What program shows the image upside down?

Did you try it with Cheese?

If it's an external webcam, can you turn it over to get the correct image?

This bug report might be relevant:
[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/493542](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/493542) 

It does not appear to be solved.

---

### Post by Axel-P on 2010-02-26
I know that lsusb says it is a Pixart, but the box says it's a Genius(unless Genius belong to Pixart(?)). So model would be Genius Messenger 310.

Cheese and amsn are the programs that show the image upside down though I've tested other softs and they all have the same issue.

yeah if I turn over the webcam it "fixes" the issue, but I'm trying to actually solve it :P

I'll read trough the bug report, see if I find something.

Sorry for the late response.

---

