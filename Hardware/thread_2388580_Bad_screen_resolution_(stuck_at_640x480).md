---
title: "Bad screen resolution (stuck at 640x480)"
date: 2018-04-04
forum: Hardware
---

### Post by turb03 on 2018-04-04
Hello everyone,
I recently installed lubuntu on my old HP mini 2140 because it says it is designed for old systems, and so far is going great! But I encountered a few problems after the installation. Even though after I finished installing Lubuntu i rebooted my machine and on start up i had a black screen on the top left corner, that covered 2/3 of the screen. After reading some other posts about solution I managed to boot the system in "nomodeset" mode and it worked fine, but the resolution was pretty bad. I made is so it boots up that way everytime, and now I don't have to worry about the black box, but the resolution is really bad and when I try to do something it is very blurry. I tried installing drivers for my integrated intel video card (intel GMA 950) and I think I did something, but I still do not have the option the increase the resolution. I also tried adding new resolution (1024 x 576, which is the maximum for my laptop) using 'cvt 1024 576' and then xrendr to add it as a mode, and I make it available. But when I type 'xrandr -s 1024x576' it says it cannot change it, and also once I reboot the machine the whole thing is gone, so only the 640x480 is available. I'm pretty new with linux, so I would really appreciate it if anyone can help me.

Thank you very much,
- turb0

---

### Post by mörgæs on 2018-04-05
Hi, welcome to the fora.

There is a workaround for Lubuntu 17.10 (if that's what you are using) but first I suggest that you try a fresh install of Lubuntu 18.04 though it's not released yet. Just follow the defaults without adding boot options and the like.

---

### Post by turb03 on 2018-04-05
Yes, I am using lubuntu 17.10. Where can I download Lubuntu 18.04 for 32bit pc? And also if it is not released yet do you think that going back to lubuntu 16.04 would fix my issue? 
Thank you very much :D

---

### Post by mörgæs on 2018-04-06
[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

Chances are good that the bug is fixed here.

---

### Post by turb03 on 2018-04-06
Thanks for the link!

I found a solution to the problem that I think is easier. I updated my Kernel to the newest version that was available for download from the Ubuntu website and then I install it on my laptop. I restarted the laptop and removed the 'nomodeset' command and the laptop booted up automatically in the maximum possible resolution without any problem!

Thank you anyways for helping me, have a good day :D

- turb0

---

