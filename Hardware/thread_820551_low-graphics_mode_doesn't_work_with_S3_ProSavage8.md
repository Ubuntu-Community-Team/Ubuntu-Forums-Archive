---
title: "low-graphics mode doesn't work with S3 ProSavage8"
date: 2008-06-06
forum: Hardware
---

### Post by Sander51 on 2008-06-06
Today, I wanted to wipe my mums computer clean from the Feisty she still runs, and install Hardy Heron. The computer is equiped with a seperate home-folder, so it wouldn't be too hard. I used the Alternate CD.

Well, installation seemed to be successfull. Booting is ok too, but when Ubuntu tries to start gdm, the screen first flickers from some boot messages to a black screen, and then tells me that Ubuntu is starting the low-graphics mode because the video chipset wasn't detected. Ok, I think, I'll sort that out later. When I click on "OK" however, the mouse pointer remains visible for a few seconds and then the monitor clicks (normally I hear that sound when switching screen resolution), and just goes black. No mouse-pointer, h/d access, CPU activity or anything that indicates the computer is doing something. Ctrl+alt+del doesn't work, I have to reset the computer.

As I said, the computer is equiped with a built-in S3 ProSavage8 video chipset. lspci tells me this:
```
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
```

I tried to edit /etc/X11/xorg.conf by hand, added
```
Driver   "savage"
```
to the right section, but it doesn't work. I also tried running dpkg-reconfigure xserver-xorg, but it doesn't even ask for video settings and only configures my keyboard.

Anyone have the same problem, or an idea how to fix it? All help is really being appreciated; otherwise I'll have install gutsy.

Thanks!
Sander

---

### Post by Sander51 on 2008-06-08
Noone has an idea?

---

