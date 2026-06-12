---
title: "Trackpad issues after hibernate/resume cycle"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by APU on 2006-09-03
Hello, I already posted this in the Apple/PCC Forums because the laptop in question is a PowerBook but I think the question is fundamental enough to be applied to many laptops.

The PowerBook has an Synaptics USB trackpad which is driven by the "appletouch" kernel module (not compiled directly into the kernel). It is important to note that I am currently running a self compiled vanilla 2.6.17.11 kernel from kernel.org. The reason for this is that I want to get hibernation to work on this PowerBook (12" Model 1.5 GHz), a task that no one in the ubutu forums seems to have completed up to now.

The good message is that hibernation is possible when using this current kernel and the in-kernel "swsusp" module. After resuming virually everything seems to work fine again with the exception of the trackpad where I have encountered some oddities. Here are my ovservations:

* The Trackpad is still driven by the "appletouch" kernel module (naturally), so unloading this module deacitvates the trackpad. I was not able to unload the "evdev" module though, which might also to have something to do with the trackpad.

* It seems that some low-level X11 functions are capturing and processing all input that comes from the trackpad and don´t pay attention to the X11 synaptics driver. The trackpad is perfectly usable for moving the cursor around - even better than I have yet got it to work _with_ the synaptics driver. But it is impossible to disable tapping or to emulate 2nd and 3rd mouse button or even to use scrolling.

* Synclient, which can normally be used to tune the trackpad settings while in X11, has absolutely no effect. This adds to the theory that some low level X11 mouse routines are actually driving the trackpad and not the synaptics driver.

Now comes the question: Does anyone have an idea on how to reload the synaptics driver without reloading X11 completely? Or any other hint on how to correctly unload/reload some kernel modules to get everything working again after a hibernate-resume cycle?

I did not yet test suspend2 on this laptop because of two reasons. I would like to stay with the in-kernel solution if anyhow possible. And second, the current suspend 2.2.7 for kernel 2.6.17 does not patch the current sources without warnings/problems. So I did not go down that road for now but I will if it is really necessary to get hibernation to work. (btw: supsend to ram is no option on this machine because of the Nvidia graphics chipset and the nonexistant support from Nvidia for Linux PPC)

Thank you very much!
APU

---

