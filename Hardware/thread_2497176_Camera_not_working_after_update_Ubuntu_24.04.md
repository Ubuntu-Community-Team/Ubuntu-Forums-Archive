---
title: "Camera not working after update Ubuntu 24.04"
date: 2024-04-25
forum: Hardware
---

### Post by eduardostevens on 2024-04-25
My Camera is not working after I updated from Ubuntu 23.10 (Mantic Minotaur) to 24.04 (Noble Numbat). I purchased one of those cheap laptops Gateway GWNR7151-7BK Ryzen 7.
Do I need to install new drivers?

---

### Post by ian-weisser on 2024-04-25
Try the much simpler step of rebooting into an older kernel at GRUB,

---

### Post by nickholaswh on 2024-04-26
Make sure your camera is enabled in your system settings. Updates can sometimes reset settings. Additionally, there might be an issue with the drivers. You can check for additional drivers by navigating to the "Software & Updates" application and then selecting the "Additional Drivers" tab. If you see any camera-related drivers listed there, try selecting and installing them to see if it resolves the issue with your camera.

---

### Post by Liakoni on 2024-04-27
I have the same problem, camera stopped working after upgrade to 24.04 from 23.10. I installed cheese and I get this error:
> [0:12:52.893088367] [10599]  WARN IPAManager ipa_manager.cpp:154 No IPA found in '/usr/lib/x86_64-linux-gnu/libcamera'
[0:12:52.893149182] [10599]  INFO Camera camera_manager.cpp:284 libcamera v0.2.0

(cheese:10599): GStreamer-CRITICAL **: 15:37:32.012: gst_structure_get_value: assertion 'structure != NULL' failed
[0:12:52.980798780] [10599]  WARN IPAManager ipa_manager.cpp:154 No IPA found in '/usr/lib/x86_64-linux-gnu/libcamera'
[0:12:52.980836762] [10599]  INFO Camera camera_manager.cpp:284 libcamera v0.2.0
[0:12:53.137196513] [10634]  INFO Camera camera.cpp:1183 configuring streams: (0) 1280x720-MJPEG
[0:12:53.137262839] [10625] ERROR V4L2 v4l2_videodevice.cpp:1047 /dev/video0[50:cap]: Unable to set format: Device or resource busy
[0:12:53.138771179] [10634]  WARN IPAManager ipa_manager.cpp:154 No IPA found in '/usr/lib/x86_64-linux-gnu/libcamera'
[0:12:53.138797769] [10634]  INFO Camera camera_manager.cpp:284 libcamera v0.2.0
[0:12:53.256097013] [10633]  INFO Camera camera.cpp:1183 configuring streams: (0) 1280x720-MJPEG
[0:12:53.256174510] [10635] ERROR V4L2 v4l2_videodevice.cpp:1047 /dev/video0[50:cap]: Unable to set format: Device or resource busy

(cheese:10599): cheese-WARNING **: 15:37:32.320: Failed to configure camera: Device or resource busy: ../src/gstreamer/gstlibcamerasrc.cpp(446): gst_libcamera_src_negotiate (): /GstCameraBin:camerabin/GstWrapperCameraBinSrc:camera_source/GstBin:bin18/GstLibcameraSrc:libcamerasrc1:
Camera::configure() failed with error code -16


I tried the old kernel 6.5, but the same.

---

### Post by niamotullah99 on 2024-05-01
After installing Ubuntu 24.04 default camera apps says there's no camera found. So i installed `Cheese` and it just worked fine. But i wanted defaults to work, so i searched up on internet and got [this]("https://ubuntuhandbook.org/index.php/2024/01/install-gnomes-camera-app-ubuntu/"). and after doing `systemctl --user restart pipewire` dafault Camera app working fine.

---

### Post by Claus7 on 2024-05-02
Hello and welcome to the forums,

> **niamotullah99 said:**
> After installing Ubuntu 24.04 default camera apps says there's no camera found. So i installed `Cheese` and it just worked fine. But i wanted defaults to work, so i searched up on internet and got [this]("https://ubuntuhandbook.org/index.php/2024/01/install-gnomes-camera-app-ubuntu/"). and after doing `systemctl --user restart pipewire` dafault Camera app working fine.

thank you for posting this. I faced exactly the same issue and your solution is working fine. The only thing is that the command provided as a solution should be issued after every reboot.

Regards!

---

### Post by rob.cranfill on 2024-05-05
> **Claus7 said:**
> Hello and welcome to the forums,

thank you for posting this. I faced exactly the same issue and your solution is working fine. The only thing is that the command provided as a solution should be issued after every reboot.

Regards!

Yes, I too find that this solves my problem (with the camera built in to my Lenovo laptop).

Does anyone know how do we make this survive reboot?

---

### Post by #&amp;thj^% on 2024-05-05
I'm using Xubuntu, but should not matter, I add this to ".bashrc"
```
bash -c "sleep 10 && systemctl --user restart pipewire"
```

So far So Good...

EDIT: I feel I also need to add, once I'm logged in I open a Terminal and keep it open, That's just how i run.

---

### Post by Claus7 on 2024-05-05
Hello,

I have tested also this alternative option [https://ubuntuforums.org/showthread.php?t=2496736](https://ubuntuforums.org/showthread.php?t=2496736) in another machine, so I will keep things as is at the moment, since a fix is about to take place, which might make all these solutions redundant. If on the other hand someone can't wait, the solution *1fallen* proposes is what someone has to follow.

Regards!

---

### Post by timatgca on 2024-05-09
> **niamotullah99 said:**
> After installing Ubuntu 24.04 default camera apps says there's no camera found. So i installed `Cheese` and it just worked fine. But i wanted defaults to work, so i searched up on internet and got [this]("https://ubuntuhandbook.org/index.php/2024/01/install-gnomes-camera-app-ubuntu/"). and after doing `systemctl --user restart pipewire` dafault Camera app working fine.

works for me too

---

### Post by timatgca on 2024-05-09
did anyone create a bug report for this?

---

### Post by artifactis on 2024-05-24
I also have run  into this problem but from a fresh install.
although i have cheese and camera working, some of my other applications still point to the dud camera in 24.04, uninstalling it is also not working

---

### Post by BeachNerd on 2024-05-27
> **niamotullah99 said:**
> After installing Ubuntu 24.04 default camera apps says there's no camera found. So i installed `Cheese` and it just worked fine. But i wanted defaults to work, so i searched up on internet and got [this]("https://ubuntuhandbook.org/index.php/2024/01/install-gnomes-camera-app-ubuntu/"). and after doing `systemctl --user restart pipewire` dafault Camera app working fine.

Thanks for posting that link - I was able to fix my camera with that info. :o

---

### Post by ozcarrago on 2024-05-29
Installing cheese solved my problem. Thanks.

---

### Post by pawanpawar1 on 2024-06-01
Thank you so much, writing `systemctl --user restart pipewire` command solved the problem.

---

### Post by Jonners59 on 2024-07-11
This worked for me for a while, but now I can't find my built in or attached cameras.  Not happy.

---

### Post by nsingh289 on 2024-08-28
> **eduardostevens said:**
> My Camera is not working after I updated from Ubuntu 23.10 (Mantic Minotaur) to 24.04 (Noble Numbat). I purchased one of those cheap laptops Gateway GWNR7151-7BK Ryzen 7.
Do I need to install new drivers?

I had the same issue, then I found this app [https://github.com/degville/snap-cameractrls](https://github.com/degville/snap-cameractrls)

You can follow the instructions, once done you should have the access to your camera.  Mine is working fine now.

---

### Post by juksu66 on 2024-12-08
> **niamotullah99 said:**
> After installing Ubuntu 24.04 default camera apps says there's no camera found. So i installed `Cheese` and it just worked fine. But i wanted defaults to work, so i searched up on internet and got [this]("https://ubuntuhandbook.org/index.php/2024/01/install-gnomes-camera-app-ubuntu/"). and after doing `systemctl --user restart pipewire` dafault Camera app working fine.

Thanks, this works for me on Lenovo T14s Gen 4 AMD. The only thing is, whenever I need the camera that command has to be run. So not a long-term solution. I have not yet found anything permanent that would work.

---

