---
title: "broke graphics with nvidia's cuda"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by fazza on 2009-04-08
hey, it's the fiddler

and the fiddler broke his graphics. Again.

I was looking into the BOINC projects, when I saw something about cuda, an extended graphics driver for nvidia cards, to allow BOINC to use the GPU. So I _had_ to download it.

The installer wouldn't let me install it while X was running, so I had to boot into recovery mode - it was the only way I could stop X starting itself.
I installed it, all seemed fine. Til I rebooted and it complained about something being wrong (can't remember what, sorry, though I think it might not matter), and used ubuntu's low graphics mode (which ironically is a higher but non-widescreen resolution than my normal one :p). I removed the graphics driver from the hardware drivers window, and rebooted, and the graphics were all the right resolution with no complaints. Except that the nvidia driver wasn't installed.

So then I installed the recommended one, 180.22 I think, instead of the upstream cuda version, 180.44. Rebooted. And now I'm stuck with the same issue again. Compiz doesn't work, and I live for compiz, and my resolution is a nasty 1280x1024 squashed into a 1440x900.

Help please?!

and while we're on graphics and drivers and resolutions, can someone direct me properly on how to set my boot screen up to a widescreen one please?

Cheers :D Sorry to be a massive pain :p though that's what I'm here for hehe

---

### Post by fazza on 2009-04-09
well again this is serious (as are many other people's problems, I'm not being selfish, there's just no other way to bring my post back to attention)
so sorry but bump :p

---

### Post by fazza on 2009-04-09
bump

---

### Post by fazza on 2009-04-09
bump

---

### Post by Claus7 on 2009-04-27
Hello,

while tampering with all these things that you made, have you any backup of your original xorg.conf file so as to put it back?

Yes, in order to change such things in your graphical environment you have to do it either from recovery mode or just to stop your x server. 

In order to put back everything as it was, one thing you should try is to remove everything from synaptic that has to do with nvidia and put back the glx version which supports your graphics card and then after a reboot to enable the driver that the system will find. 

I just came accross your post looking about cuda. Where you able to run applications in your gpu? And if you did so, how you were able to accomplish such a task?

Regards!

---

### Post by Claus7 on 2009-04-27
Hello,

searching a little bit more about the subject I do not think that you have to install anything specifically for cuda to work. If you have ge force 8 and on then it is supposed to be included in your graphics card driver (the cuda thing, that is). Now, I suppose that you went there:
[http://forums.nvidia.com/index.php?showtopic=85832](http://forums.nvidia.com/index.php?showtopic=85832)

and you downloaded the 32 version of linux. It is nice to give this specs if you expect in general any help. Also it would be nice to provide the model of your graphics card. 

There:
[http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)
it sais that this driver supports the cuda architecture. Now, I do not know whereas ubuntu devs are supporting this or not. You have either to install the nvidia graphics driver or the driver from the ubuntu repos. Not both. Having done that for jaunty lately, I have to tell you that it depends on your computer whereas the first or the latter will be the best choices for you. 

From here:
[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002757.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002757.html)
I can see that the cuda architecture is implemented, so it is supported.

Maybe a fresh install of the drivers is highly recommended.

Regards!

---

