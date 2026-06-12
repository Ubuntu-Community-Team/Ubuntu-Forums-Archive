---
title: "Optiplex 7400 AIO wmi hotkeys drivers?"
date: 2022-12-20
forum: Hardware
---

### Post by saturation on 2022-12-20
Hello everyone! I've been dabbing in various linux distros for about a year now, so not overly competent but not a complete newbie either, though this is my first time using plain Ubuntu.

The problem:
Last month I upgraded my PC with a Dell Optiplex 7400 all-in-one. This came with Windows 11, but the machine is Ubuntu-certified, so I promptly added another nvme drive and installed Kinetic Kudu in a dual-boot configuration. Unfortunately, I ignored the fact that this particular PC is only tested for 20.04, which apparently means that any of Dell's own drivers are bundled to that release. That isn't a huge problem, except that the WMI hotkey that changes the HDMI inputs doesn't work on 5.19 kernels. 

So I poked around and found Dell's oem kernel that supposedly includes the driver, which is this: [https://packages.ubuntu.com/focal-updates/linux-image-5.14.0-1007-oem](https://packages.ubuntu.com/focal-updates/linux-image-5.14.0-1007-oem) Of course, this is for focal fossa, and for 'not a complete newbie' I still have no idea how to proceed from here. Can I install the custom oem kernel and modules and see what happens (how?)? Should I wipe my current installation and install 20.04, see if the drivers get automatically downloaded? Should I try to map the button myself somehow? Or, just maybe, leave it all and use Windows if I need HDMI intput? Are other workarounds available?

So far I tried looking for this kernel via Ubuntu mainline, but it's not there, probably because it's an oem kernel. I have set up 22.10 the way I wanted it now, so am a bit reluctant to wipe it and install 20.04. Plus, I do like sticking to newer releases.

If anyone happens to have any experience with that machine, or any recent AIO Optiplex models, I'd appreciate your input. Thanks for your help in advance!

P. S. You probably wonder, why would you need a driver to change inputs?  Don't know, but on Windows, Dell has its own 'osd buttons' firmware  application that's responsible for that tiny bit of hardware, and I  suppose it needs a similar solution on ubuntu as well. :(

---

