---
title: "Suspend and resume issues"
date: 2009-11-05
forum: Hardware
---

### Post by glennric on 2009-11-05
I am having two issues with suspend and resume.

First, I have an AGP NVidia video card that I have set up to use NvAGP instead of AGPGART, and have enabled AGP fast writes and AGP SBA.  This all works fine on a fresh boot.  However when the computer resumes from suspend if I type "cat /proc/driver/nvidia/agp/status" it says that fast writes are disabled and sba is still enabled.  Although, if I type "cat /proc/driver/nvidia/registry" it shows "EnableAGPSBA: 1" and "EnableAGPFW: 1".  On a fresh boot both methods report SBA and FW are enabled.  So are fast writes enabled after I resume or not?  If not then how do I get the fast writes to remain enabled after resuming?

Second, I have a usb webcam with a microphone, and I have pulseaudio's default source set to that mic.  However, when I resume from suspend it always reverts to the internal mic.  I don't actually have a mic plugged into the sound cards jack so this is useless.  I was having this problem every time I rebooted, but after using padevchooser I was able to get the setting to persist some of the time when I reboot.  How do I get pulseaudio to stay on the webcam's mic when I resume from suspend (and the other times when I reboot)?

---

