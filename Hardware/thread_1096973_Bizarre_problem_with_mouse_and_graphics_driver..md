---
title: "Bizarre problem with mouse and graphics driver."
date: 2009-03-15
forum: Hardware
---

### Post by PerryTatchett on 2009-03-15
Hi, I've been using Ubuntu for several months now, (6 months? 7 months? Time goes so fast when you're running Ubuntu!) but this is my first time posting to the help forums. So first of all, if I am in the wrong place/wrong forum/wrong anything, please tell me. I've never done this before.

Okay, next of all, I have been having two apparently unrelated problems. I'm not sure if I should start separate threads for the two problems, so I'll bundle them together.

Finally, I have placed my hardware specifications at the end of this post. If any more are needed, please ask me.

Problem 1) That blasted tap to click is on! I've tried disabling it under System->Preferences->Mouse, but that never works. A while back I managed to sort of disable it by just changing some config file somewhere to have the tap sensitivity be zero. This worked-ish. But now the "feature" is back after I disabled the touch pad and re-enabled it, and I'm not sure what to do. Is this a bug with Ubuntu somewhere, or am I doing something obviously dumb? (My default guess is the latter.)

Problem 2) I wanted to play with the fancy NVidia Cuda package, so I downloaded it and installed the graphics driver that came with it. It worked wonderfully! That is, until I rebooted: The next time I started up it offered to startup in 640x480. I then tried to re-install my original graphics drivers and succeeded, but it still tried to startup in 640x480. It simply refused to actually run in 1280x800. So then I tried re-installing the Cuda drivers and voila! It magically worked again. However, since then I have had to re-install the Cuda drivers on each startup. This brings my boot-up time from about 50 seconds to about 3 minutes. This is acceptable, as I only reboot every 1-2 days, but it is rather annoying. I'm open to solutions that involve losing the Cuda driver. To be honest, I haven't played with it since the first day I installed it.

Okay, there are my problems. Here are some more specifications in case they help:

Ubuntu 8.04.
I'm on a Compaq Presario F500. (Originally Windows Vista!)
I'm not so sure how to identify the Cuda graphics driver I'm using, but the package I invoke to install it is called: NVIDIA-Linux-x86-180.06-pkg1.run
Perhaps then the version number is 180.06?
My graphics card is the: GeForce Go 6100

Some other gunk in case it helps:
Processor: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53
/proc/version: Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008

Under /var/log/nvidia-installer.log I have a huge log from the installation of the driver. I'm not sure if it is terribly useful, however.

---

### Post by PerryTatchett on 2009-03-23
Update: The problems are getting worse. Sometimes it is on, and sometimes off. Now it is on more of the time. I simply can't disable anything about the tap-to-click touchpad under ystem->Preferences->Mouse->Touchpad. None of those settings do anything. (I really mean they don't do anything. I'll disable the touchpad there, and it continues to work.)

As for the graphics driver issue, I think I've pretty much solved that one.

---

