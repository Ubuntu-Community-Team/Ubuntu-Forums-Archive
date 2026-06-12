---
title: "Nvida 660M Cannot Correctly Install Drivers"
date: 2018-02-02
forum: Hardware
---

### Post by ben.holland on 2018-02-02
Hello!
Specs first: I'm on a Lenovo Y580 with an nvidia 660M, 8G ram and an 8-Core processor.
So I started out with Ubuntu 17.10. When attempting to install the nvidia supplied 384 drivers for the graphics card, the computer failed to boot. So I did troubleshooting:
Many places online suggested that I change the grub options.
I used nomodeset: Didn't help.
I used nvidia-drm.modeset=1: Didn't help
I used modeset=0: Didn't help.
I disabled Wayland: Didn't work.
I attempted to install the drivers with the alternate ppa:graphics-drivers source: Didn't work
I reinstalled the OS and did all these things in combination: Didn't work.
All of these failed at different steps. nomodeset would occasionally get me to the login screen, which would immediately freeze. Many of the others didn't even get that far.

Looking around, I found that a lot of people had been having issues with 17.10, so I made the decision to downgrade to 16.04.
Didn't. Work.
I've tried all the troubleshooting steps again. Using nomodeset at LEAST gets me through the login screen, but dumps me into a blank orange screen. It's gotten to the point where I'm thinking my video card is burnt out, but there doesn't seem to be any way to test this without installing a working driver. I've reinstalled both version of the OS multiple times to make sure nothing is interfering with the install process, and I can't figure it out. I've been working on this for the last 16 hours. If I could get some help, that would be great.

---

### Post by Autodave on 2018-02-02
I am assuming that you have video when going through the install process, so I wouldn't think that your video card is going out.

When you first install 16.04, are you then going to Settings -> Additional Drivers and allowing it to chose the recommended one? Never install the drivers from the Nvidia site!

---

### Post by Yellow Pasque on 2018-02-02
It's an Optimus (intel+nvidia hybrid graphics) laptop. Do you have a switch in the BIOS for the graphics?

---

