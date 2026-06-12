---
title: "Is Force Feedback supported ?"
date: 2008-09-18
forum: Hardware
---

### Post by holmes0 on 2008-09-18
Hi,

I am a recent Linux user and have a Xubuntu Hardy Heron system. I have been trying for a while to configure my MS Sidewinder Force Feedback 2 (usb) joystick. I managed to make it work except for the force effects (tested in Bzflag). I tried different combinations of modules (joydev, sidewinder) without success. 
According to the Linux Input mailing list, I-Force joysticks (Logitech) are fully supported and MS Force feedback partially. I have no effect at all.
Has anyone succeeded in getting force effects for a joystick? Are force effects supported by Hardy Heron?

Many thanks.

---

### Post by holmes0 on 2008-09-19
It seems it is necessary to recompile the kernel with options to activate force feedback. According to the Input driver sources, a limited number of force feedback devices are supported. Logitech Joysticks and Wheels (I-force protocol) and a few others. MS Sidewinder FF2 is only partially ("EXPERIMENTAL") supported. After having activated force feedback for FF2, I tested it with ff-utils and gforce-03. The first one led to a system freeze. With gforce, I could generate a force effect into the joystick at first attempt. At the second one, I got a system freeze as well.
So I fear I won't play Freespace with my force-enabled Sidewinder on a Linux system before long. There is still the Windows solution:
- for Windows 98, the driver is OK,
- for XP,you have to install the Sidewinder FF Wheel driver (I do not know why),
- for Vista, the joystick is automatically recognized but effects are not working. Fortunately, the use of Pinacle Game Profiler enable them (I tested this myself with Beyond the Red Line and the other Freespace games).

---

### Post by holmes0 on 2009-07-23
Hi,

Since 9.04 (and kernel 2.6.28, it is no longer necessary to compile a custom kernel. Force Feeback support is from now on a standard feature. I have personnaly tested it with a Sidewinder Force Feedback 2 using ff-utils and gforce (a ff testing application with a GUI). It works perfectly. It appears Sidewinder support is no longer experimental since I don't have any more freeze as it used to happen with previous kernels.

Now we have to wait for the next SDL 2 (with a FF API) which is now the single element lacking for a FF support within Freespace SCP!

Hope it will come soon ...

---

