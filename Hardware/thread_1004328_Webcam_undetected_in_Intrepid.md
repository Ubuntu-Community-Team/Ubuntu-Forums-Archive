---
title: "Webcam undetected in Intrepid"
date: 2008-12-07
forum: Hardware
---

### Post by Ashmadai on 2008-12-07
Ok, so here's the thing. I need my webcam to talk to people back home. Now, the problem is, ubuntu doesn't recognize my webcam(which is built in).
If I run any program that lists the connected video devices, all of them say none, or something. I installed EasyCam2 and it is the only thing that recognizes my webcam. It is "Sony Visual Communication Camera VGP-VCC4". I ran through the process, clicked the install drivers thing, but still it doesn't show up anywhere. I've been through the web but I can't seem to find a solution.

Help, please.

Key points:

-Ubuntu Intrepid Ibex
-Sony Visual Communication Camera VGP-VCC4(integrated)
-Webcam does not show up in any program
-Shows up only in EasyCam2
-Ran EasyCam2, to no avail


PROBLEM SOLVED:

Reinstall Cheese, it detected my camera and enabled recognition.

---

### Post by picturefreedom on 2008-12-07
can you post the device ID?

```
lsusb
```

---

### Post by sayantandas on 2008-12-07
> **Ashmadai said:**
> Ok, so here's the thing. I need my webcam to talk to people back home. Now, the problem is, ubuntu doesn't recognize my webcam(which is built in).
If I run any program that lists the connected video devices, all of them say none, or something. I installed EasyCam2 and it is the only thing that recognizes my webcam. It is "Sony Visual Communication Camera VGP-VCC4". I ran through the process, clicked the install drivers thing, but still it doesn't show up anywhere. I've been through the web but I can't seem to find a solution.

Help, please.

Key points:

-Ubuntu Intrepid Ibex
-Sony Visual Communication Camera VGP-VCC4(integrated)
-Webcam does not show up in any program
-Shows up only in EasyCam2
-Ran EasyCam2, to no avail

hi,

if u want ubuntu to work out of the box, try installing ubuntu ultimate edition 2.0.
u just dont need to install anything. everything is pre installed except the restricted extra codecs. and all webcams that i have used gets detected. i have tried it in dell, hp, acer , and an assembled desktop. all have perfect running conditions.

---

### Post by picturefreedom on 2008-12-07
multimedia codecs have nothing to do with webcam detection.

---

### Post by sayantandas on 2008-12-07
well , i definitely agree. what i meant to say was, ubuntu ultimate edition somehow was able to recognize all the webcams on all the computers that i have installed it. be it an inbuilt webcam on a laptop , be it a normal pc webcam on a desktop. and all of these installations have worked out of the box.

---

### Post by Ashmadai on 2008-12-08
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05ca:1837 Ricoh Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

There is nothing pluged in the usb ports, if that matters at all...which it shouldn't

(sorry I took so long to respond. Busy guy)

---

