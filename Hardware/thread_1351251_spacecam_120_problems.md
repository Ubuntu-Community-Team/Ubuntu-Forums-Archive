---
title: "spacecam 120 problems"
date: 2009-12-10
forum: Hardware
---

### Post by souch13 on 2009-12-10
i have a spacecam 120 and tried to install it under the sn9c102 chipset, first installing the driver, followed by a supported program sonic-snap.

after the cam not being detected i was advised to go into terminal and see if the device was successfuly installed, this is what i found, and have had no luck so far in gettting any response from the cam.


dmesg | less

[15690.933049] usb 2-2: new full speed USB device using ohci_hcd and address 3
[15691.143226] usb 2-2: configuration #1 chosen from 1 choice
[15691.374761] Linux video capture interface: v2.00
[15691.389715] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
[15691.391154] usb 2-2: SN9C10[12] PC Camera Controller detected (vid:pid 0x0C45:0x600D)
[15691.589056] usb 2-2: PAS106B image sensor detected
[15692.259265] usb 2-2: Initialization succeeded
[15692.259400] usb 2-2: V4L2 device registered as /dev/video0
[15692.259406] usb 2-2: Optional device control through 'sysfs' interface disabled
[15692.259447] usbcore: registered new interface driver sn9c102
[15692.285224] usb 2-2: usb_submit_urb() failed, error -28
[15692.358067] ohci_hcd 0000:00:0b.0: leak ed f642c100 (#81) state 2


if anyone can help please do!

---

### Post by gordintoronto on 2009-12-10
Here is a really old thread which might be relevant:

[http://ubuntuforums.org/showthread.php?t=456610&highlight=SN9C10](http://ubuntuforums.org/showthread.php?t=456610&highlight=SN9C10) 

Do you use Cheese to test the webcam?  I've found it's the simplest program for the job.

---

### Post by souch13 on 2009-12-11
yeah i have cheese both installed, but when i try the cam on it i get some bars of colour and a little box with "tv like" white noise in the bottom corner, saying no webcam detected, i'll check out the link and let you know how i get on

---

