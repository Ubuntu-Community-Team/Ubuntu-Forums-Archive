---
title: "Safe to install different video drivers (AMD and NVIDIA) before move to new PC?"
date: 2017-08-26
forum: Hardware
---

### Post by marseille2 on 2017-08-26
Dunno how to phrase the title... I just want to prepare to build a new system, but I'm worried I'll break something.

I'm getting some new components and will start building a new computer in a couple days. I need to transfer my current hard drive into the new build, but I'm currently using an AMD card (Trusty 14.04 LTS with 4.x kernel).

The new build will have an NVIDIA Geforce GTX 750ti and run an i9 core. Can I go ahead and install the drivers now, so I won't have a black screen when I boot into the new system? (BTW... I think I stripped out some of the stock drivers I didn't need, so I'm worried I'm going to break something if I don't get it right).

So far I see this thread:

[URL="https://askubuntu.com/questions/653592/nvidia-geforce-gtx-750-ti-doesnt-work-in-ubuntu"]https://askubuntu.com/questions/653592/nvidia-geforce-gtx-750-ti-doesnt-work-in-ubuntu
[/URL]
But it doesn't answer my question... just tells me what to install...

---

### Post by Yellow Pasque on 2017-08-27
Are you using proprietary AMD drivers? If so, you should purge them before you shut down the old system for the last time.

> Can I go ahead and install the drivers now, so I won't have a black screen when I boot into the new system?

You could, but it's not a big deal. Throw the hard disk into the new system, and if it doesn't at least boot to a safe mode, then you can boot with 'nomodeset' parameter to use a generic video driver. The resolution will be low, but once there, you can add this PPA and install nvidia 375 or 384 driver:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=trusty)

> (BTW... I think I stripped out some of the stock drivers I didn't need, so I'm worried I'm going to break something if I don't get it right).
For the most part, "drivers" are part of the kernel package, either as modules or built into the kernel itself. You're going to need to give a lot more detail about what you did if you want anyone to know what you're talking about.

---

### Post by marseille2 on 2017-08-29
Thank-you so much! This is very helpful info. Unfortunately, video drivers are my weak point and it's been so long that I can't recall what I did exactly. I do know that I'm not using proprietary drivers. Is there a way where I can post the output of the drivers still installed?

---

### Post by mastablasta on 2017-08-30
yes you can see the drivers you are usign by CLI output or using various applications that provide system information.

to do the move the best way is to remove any proprietary drivers and then boot with new configuration. you shouldn't get black screen. at minimum you should be able to force the VGA mode (the very basic graphics) or if that fails text mode is enough to install nvidia drivers (add the PPA and install or the recomended way install using available ones in the repos). the text based install is easy enough to do (enable repos - if necessary) and then sudo apt-get install *package*

if you manage to boot to vGA then system will offer you any additional drivers.

---

