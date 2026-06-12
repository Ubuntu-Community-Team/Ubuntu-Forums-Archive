---
title: "HP built-in laptop webcam has stopped working"
date: 2008-12-13
forum: Hardware
---

### Post by Potters Son on 2008-12-13
Hello, all. For the past semester, I have relied on the webcam built-into my HP Pavilion dv6985se laptop. It functioned perfectly in Cheese under Ubuntu 8.04.1 x86, Ubuntu 8.10 x86, and Ubuntu 8.10 x86_64 (which was the order of my upgrades).

However, after the last upgrade, I noticed Cheese beginning to act up: whenever I tried to take a picture with another application running, the screen would flash white - but STAY WHITE. I could access the GNOME panels by dragging the mouse over the space where they used to be (and they would somehow popup until the mouse left them), but the other windows were inaccessible. As a result, I had to log off using the user switcher applet and log back on, thus killing Cheese. But at the very least, the picture was saved to the computer.

Now, it appears that I have a new problem: Cheese will not show the video stream from the camera at all; in the space where the video SHOULD be, it is just the same gray as the background of all GNOME windows. In other words, it doesn't appear to be able to communicate with the webcam at all.

Testing Camorama affirms this. When I try to open it, Camorama complains that it can't communicate with /dev/video0, which is what Cheese says is my webcam.

This is very frustrating. I upgraded my computer in hopes of achieving better performance, but each time, it seems as if it got worse. I'll appreciate any help to get this webcam up and running again. Until then, I'm going to try and test it with LiveCD versions of Ubuntu, if Cheese is installed on it.

---

### Post by stefanadelbert on 2008-12-26
I'm having some issues with my built-in webcam on my HP Pavilion dv6836TX on 8.10 since my most recent kernel update (2.6.27-7 to 2.6.27-9). As far as I remember, it was working fine on the earlier kernel, but I don't actually use the webcam, so couldn't be sure. I first noticed the problem it when starting XSane Image Scanner and got the error:
```
Failed to open device'v4l:/dev/video0': Invalid argument.
```
XSane will go no further.
I then tried Cheese and got no picture from the webcam although the webcam's blue light does turn on. If I click Record (in video mode), Cheese exits.
'lsusb' does not seem to show up the webcam (it should be on the USB bus, right?).
```
stefan@stefan-laptop:~$ lsusb
Bus 007 Device 002: ID 05c8:010c Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
I think the "Cheng Uei" device also has to do with the wireless card.
So, I'm a little stumped. Anyone having similar problems?
Stef

Corrections:
The first device listed in 'lsusb' is actually the webcam:
```
Bus 007 Device 002: ID 05c8:010c Cheng Uei Precision Industry Co., Ltd (Foxlink)
```

'dmesg' has the following line regarding the error:
```
[  181.125677] cheese[6369] general protection ip:7fa1448aea5a sp:42f377e0 error:0 in libpthread-2.8.90.so[7fa1448a6000+17000]
```

I'm seeing this behaviour in both kernels mentioned earlier (2.6.27-7 and 2.6.27-9).

Skype lists "HP Webcam /dev/video0" and does display Video when clicking "Test". Cheese displays the same webcam under Settings, but crashes when trying to use it.

---

### Post by xouhcoatl on 2008-12-26
I am having the same problem with a HP laptop DV9910us. (After the new apgrade)

---

### Post by skiwithpete on 2009-01-14
same problem for me on the dv6934ca.

Any indications how to fix this yet?

---

### Post by myddewji13 on 2009-05-03
same problem on hp pavilion dv2708ca ... used to work...im guessing the new updates screwed it up ...

Edit: nvm.. im referring to jaunty.. pls disregard this post

---

### Post by Potters Son on 2009-05-03
Since the first post, I downgraded to Hardy, and then went up to Jaunty.

Jaunty gives no problems, at least yet.

---

### Post by njsanders1 on 2009-05-16
BUMP for HP DV7.  (Specifically, the DV7-1267CL.)

As I saw above in another quote, the camera is recognized by Skype and displays video in "test" mode.  However, it will not work on a call in Skype, nor will it work in Camorama.

---

