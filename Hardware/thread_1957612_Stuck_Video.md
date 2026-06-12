---
title: "Stuck Video"
date: 2012-04-12
forum: Hardware
---

### Post by sparks40 on 2012-04-12
I'm using the most current beta version of Skype with a Logitech QuickCam Communicate STX external camera. Incoming audio and video are fine and I have a good connection to the internet. My outgoing transmission (as seen in the thumbnail at the bottom of the screen), works for a few seconds, showing full motion, but then it locks up completely. 

My own video looks good in Skype test mode as well as in Cheese. But once I link up with someone it's almost as if a buffer fills and the video can not stream any longer. I've been working on this problem for several weeks and have not made much in the way of progress. 

dmesg yields the following:

1734.298471] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 3783.438239] WARNING! power/level is deprecated; use power/control instead
[ 3783.519080] usb 1-9: USB disconnect, device number 6
[ 3783.964022] usb 2-9: new full-speed USB device number 6 using ohci_hcd
[ 3784.676897] usb 2-9: not running at top speed; connect to a high speed hub
[ 3784.699453] scsi7 : usb-storage 2-9:1.0
[ 3784.813616] usb 2-9: USB disconnect, device number 6

I have no idea what "power control" means and I'm pretty much in the dark as to the meaning of the rest of the message. 

Although Skype is a mystery wrapped up in an enigma, it's the best we have for now. I would appreciate any suggestions.

TNX
QRZ K2OSP

---

### Post by yankeeDDL on 2012-09-02
Hi, were you able to fix the problem?
I have the same webcam and a similar problem.
In Cheese the video starts and works fine for few seconds (about 8~10), and then it freezes.
In Skype it seems the same: if I go in the Options menu, I can see my video fine, till it locks up. During a call though, the video does not work from the every beginning: it takes a while to start, and when it does, the bottom half of the image is garbled and the top part is frozen.

I have a clean installation of Ubuntu 12.04.1 and I did not have this problem with 11.04.

I checked with lsusb that the webcam is ID'd properly:
Bus 001 Device 004: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX

Best regards,
Yankee

EDIT: I am using Skype 4.0.0.8 from the repos (but as I mentioned, I don't think the issue is Skype for me)

---

### Post by yankeeDDL on 2012-09-08
Nobody?

---

### Post by samwilhide on 2012-09-11
I have the same problem, have tried for a long time to find an answer. I'm just a beginner, but I think it has to do with a kernel update in the recent past and USB port hardware on some computers, including Dell Inspirons. Here's a bug report.

[https://bugzilla.redhat.com/show_bug.cgi?id=746914](https://bugzilla.redhat.com/show_bug.cgi?id=746914)

Apparently they were able to get their webcam working by replacing the USB port hardware with USB 3.0 hardware. This is the only thing that I've read so far that has worked, although I haven't tried it myself yet.

---

