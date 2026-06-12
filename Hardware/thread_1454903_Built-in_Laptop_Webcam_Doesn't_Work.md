---
title: "Built-in Laptop Webcam Doesn't Work"
date: 2010-04-15
forum: Hardware
---

### Post by Abbreviate on 2010-04-15
Hello all. I have recently switched over to Ubuntu 9.10 from Vista. I have a Lenovo Y530 Laptop. I never had problems before with my built-in webcam under Windows but now for some reason it doesn't seem to work. I have tried activating it on Skype, but when I go into the Options menu and then go to the Video Devices tab it doesn't even recognize that I have a webcam. How can I rectify this?

---

### Post by TBABill on 2010-04-15
I'm not sure if it's the same for webcams, but sometimes the same happens for wireless adapters. Have you done a system update since your install of Ubuntu? If you have, disregard, but if you have not, and you are able, go through the update process and see if your webcam works following the update. It could be something that has been updated since Karmic first hit the streets when the .iso was created. Just a guess, but worth a shot.

---

### Post by steveneddy on 2010-04-15
Please post the output of

```
lsusb
```

---

### Post by Abbreviate on 2010-04-15
If you mean going to the Update Manager than I have done that plenty of times. Otherwise I am not sure how to perform a system update. 

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by steveneddy on 2010-04-17
searching UF revealed:

[http://ubuntuforums.org/showthread.php?t=1020939](http://ubuntuforums.org/showthread.php?t=1020939)

---

### Post by Abbreviate on 2010-04-18
I took a look at the thread, it said that I should install Cheese and that it should work. I did that. Turned Cheese on, it said no camera found. I don't think the camera is being recognized or perhaps some drivers are missing? Also maybe gstreamer is corrupt or I need to update the ALSA drivers?

---

