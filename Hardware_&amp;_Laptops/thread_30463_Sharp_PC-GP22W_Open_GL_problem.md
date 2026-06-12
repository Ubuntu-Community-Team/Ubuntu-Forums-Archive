---
title: "Sharp PC-GP22W Open GL problem"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by Staesys on 2005-04-28
I am running Ubuntu on my Sharp PC-GP22W notebook and it seems to work quite well. One thing I have noticed though is that the Open GL performance sucks big time. Whether it's an Open GL screensaver or a game like Tux Racer, the display is incredibly slow. Also, glxgears shows a FPS of about 340 - 350. This is completely unaceptible in a notebook with a 2.2 GHz processer.

Is there anyway I can boost the performance? Here's the video "card" info from xorg.conf:

**Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter** 

The display uses shared memory. Right now it's set at 16MB, would increasing that to it's max of 32MB help any?

Edit: I just changed it to 32MB and there is no change.

I'm also running Gnome at 1024x768x24bpp.

Thanks!

-Paul

---

### Post by az on 2005-04-30
[http://www.winischhofer.net/index.shtml](http://www.winischhofer.net/index.shtml)

Does this help?

---

### Post by Staesys on 2005-05-01
No, but the sisctrl program is very cool. I thank you for turning me on to it. 

The 3D performance still sucks. *sigh*

---

### Post by Staesys on 2005-05-02
Apparently my video card doesn't support DRI, so direct rendering doesn't work. That would explain the crappy open gl performance.

Oh well, nothing I can do about it I guess...

-Paul

---

### Post by leocadenas on 2007-06-25
Hello, I'am from Argentina. In this post you tell that you have UBUNTU running on your Notebook Sharp PC GP22W. Please Help me with this....
I need the recovery CD's of my Notebook Sharp, model PC-GP22W, where the operating system is inside. The problem that I have is that I had to format the machine and now I meet that the notebook does not admit another operating system.
The manual says it clearly, but I did not think that when I was installing another version of the WIndows XP Pro, I would have this kind of problems. Please, I do not find the recovery CD's, I believe that I lost them. How can I do to install another operating system? for example, "UBUNTU"???
How do you do? Do you have problems with the drivers? Where you find the drivers for this linux sistem?
Sorry for my bad english.
Thanks.
Leo

---

