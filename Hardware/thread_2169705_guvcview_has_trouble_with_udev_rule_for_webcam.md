---
title: "guvcview has trouble with udev rule for webcam"
date: 2013-08-23
forum: Hardware
---

### Post by josvanr on 2013-08-23
hello I use the udev rules

SUBSYSTEM=="video4linux", ATTRS{serial}=="BA9550EC", SYMLINK+="webcam1"
SUBSYSTEM=="video4linux", ATTRS{serial}=="029D8ED4", SYMLINK+="webcam2"
SUBSYSTEM=="video4linux", ATTRS{serial}=="HF1014-P80A-OV05-VH-R01.01.01", SYMLINK+="webcam0"


for my webcams. The symlinks get created:

jos@hpux:/var/log$ ls -l /dev/webcam*
lrwxrwxrwx 1 root root 6 aug 23 11:50 /dev/webcam0 -> video0
lrwxrwxrwx 1 root root 6 aug 23 11:50 /dev/webcam1 -> video1
lrwxrwxrwx 1 root root 6 aug 23 11:50 /dev/webcam2 -> video2

but if I try to view with guvcview 

jos@hpux:/var/log$ guvcview -d /dev/webcam1 
guvcview 1.6.0
webcam1 not a valid video device name

and defaults to video0

(after 3 hours of debuggin :-S)


???

---

### Post by FooTheBar on 2013-09-24
Have you found a solution? I experience exactly the same problem..

---

### Post by dannyboy79 on 2013-09-24
hmm, when I use the GUI for guvcviewer, it asks me which input i'd like to choose. i have a webcam via usb as well as a hd-pvr via usb so there's a video0 as well as a video1

---

### Post by FooTheBar on 2013-09-24
But does it also shows you the additional links created by the udev-rules?

---

### Post by dannyboy79 on 2013-09-24
i don't use the udev rules. i just know that it brings up a dialog box to choose either the logitech webcam or the hd-pvr.

---

