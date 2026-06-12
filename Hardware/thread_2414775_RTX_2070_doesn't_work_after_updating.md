---
title: "RTX 2070 doesn't work after updating"
date: 2019-03-14
forum: Hardware
---

### Post by mthartley on 2019-03-14
Hey, I have an NVIDIA RTX 2070, that I was running just fine on nvidia-driver-410. However, after my last update, it no longer works with the nvidia driver. If I don't have any nvidia packages installed, the gui works, but doesn't properly determine the size of the monitor. If I have nvidia drivers installed, whether it be 410, 415, or 418, the booting process hangs the moment that the gui is turned on, since the driver is unable to initialize the gpu, according to what I've seen trying to run startx in recovery mode. I tried to use the live version, and it had the same problem, as has the live version of every linux distribution I've tried.

The gpu outputs stuff to the screen without drivers, so I assume that the gpu isn't broken. How can I get the gpu to go back to working with the nvidia driver that was working without incident until yesterday?

Thank you in advance

---

### Post by Autodave on 2019-03-14
Where are you getting the drivers from?

---

### Post by mthartley on 2019-03-14
When I run apt install nvidia-driver-410, the download message says: 

[http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main amd64 libnvidia-cfg1-410 amd64 410.104-0ubuntu0~18.04.1 [69.9 kB]

---

### Post by Autodave on 2019-03-14
[https://ubuntuforums.org/showthread.php?t=2414359&highlight=rtx+2070](https://ubuntuforums.org/showthread.php?t=2414359&highlight=rtx+2070)

Take a look at that and follow the instructions in the last post.

---

### Post by mthartley on 2019-03-14
I already had that ppa installed, but I re added it, and verified that it did not solve my problem.

---

### Post by CatKiller on 2019-03-15
> **mthartley said:**
> If I have nvidia drivers installed, whether it be 410, 415, or 418,

You need to purge the drivers between versions. They don't upgrade, and certainly don't downgrade, cleanly.

>  the booting process hangs the moment that the gui is turned on, since the driver is unable to initialize the gpu, according to what I've seen trying to run startx in recovery mode. 

Without more information, that doesn't narrow it down at all.

> I tried to use the live version, and it had the same problem, as has the live version of every linux distribution I've tried.

That's not indicative of anything, either. No live version will have any version of the proprietary driver, only very recent versions of the proprietary driver support that card anyway, and nouveau support for a card that new is very spotty.

> The gpu outputs stuff to the screen without drivers, so I assume that the gpu isn't broken. How can I get the gpu to go back to working with the nvidia driver that was working without incident until yesterday?

Well, that depends on why it's broken, doesn't it?

The scenario that seems most likely to me is that you've got a version mismatch between the driver and the kernel module for the driver. Purge all the nvidia stuff, and then try to install a version of the proprietary driver. Do it from the command line so that you can post the output here.

If it's still hanging after that, if it's at the point that the login screen shows, it'll be /var/log/Xorg.0.log that you want to look at. If it's hanging before that point, it's dmesg that you'll want to look at.

---

