---
title: "install kubuntu 9.10 on samsung Q1 ultra (UMPC)"
date: 2009-11-24
forum: Hardware
---

### Post by edkwok on 2009-11-24
Hi,
    Has anyone out there installed Kubuntu 9.10 on a Samsung Q1 Ultra?

   I have download both version (netbook and regular Kubuntu 9.10) and tried to install on Samsung Q1 ultra but it kill my screen from the get go.

   Using a CD install, it boot up the mini root and probed around for hardware, and the screen went green and then red! and switch to blank.  Do not see any images at all to input and start the selection setting to install.

  The Spec of Q1 is:

    7" wsVGA touch screen.
    2 GB memories
    Intel Solo 1500 CPU
    the unit has a split mini keyboard
    Pressure mouse and joystick.
    80 GB Hardrive.

   I install 9.04 but have to use the text mode install, when I try to use the GUI install, I get a PartMan error.  With 9.04, I have to apt-get Kubuntu-desktop and apt-get x-window package to make it to work, even then, the mouse and touch do not work.

   I found couple list on successful install Ubuntu 7.10, and I even went and download 7.10 but couldn't get it to install.

   Any help is great appreciated. thanks.

//ed

---

### Post by undesigned on 2009-12-10
I didn't have any problems installing the 9.10 netbook remix on a Q1 Ultra, so I'm not sure what to suggest...

But to get the touchscreen working, I had to install xserver-xorg-input-evtouch and reboot.

---

### Post by undesigned on 2009-12-10
Almost forgot...

There was actually one problem with the display, it would flicker with an error, "Failed to restore crtc configuration: -22":
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404421)

Adding i915.modeset=0 to kernel args solved the problem.

---

