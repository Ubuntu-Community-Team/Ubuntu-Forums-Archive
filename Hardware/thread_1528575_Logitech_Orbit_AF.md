---
title: "Logitech Orbit AF"
date: 2010-07-10
forum: Hardware
---

### Post by Tullyamo on 2010-07-10
Hello, I have recently decided yet again to get off the Windows horse and board the linux train.  I of course am a newer user of linux but somewhat familiar with in from the past.  There is a small list however, that I need linux to do in order to keep interest.

Empathy to do video conversing 
Itunes to update firmware and backup iPhone 

With Empathy though, I am running into an issue.  I am using Lucid Lynx 64-bit.  I have a logitech orbit af webcam.  I have plugged it into all usb ports and there was no detection.  I have used the lsusb command in the terminal and got the following:

```
jeremy@jeremy-desktop:~$ lsusb
Bus 006 Device 002: ID 04b8:0818 Seiko Epson Corp. Stylus CX3700/CX3800/DX3800
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04f2:0112 Chicony Electronics Co., Ltd KU-8933 Keyboard with PS/2 Mouse port
Bus 003 Device 002: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 05ac:1294 Apple, Inc. iPhone 3GS
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have gotten the iPhone to be recognized by lucid but, it obviously won't be getting updates anytime soon without iTunes.  I working on baby steps in this approach with first and foremost priority is the webcam fix.  I have installed cheese and received the "No Device Found" msg.  Is there a fix for this or have I simply overlooked the obvious?

---

### Post by Tullyamo on 2010-07-10
For what its worth, here is the lsusb while running lucid live
```
Bus 001 Device 004: ID 046d:0994 Logitech, Inc. QuickCam Orbit/Sphere AF

```

---

