---
title: "Three monitors with Ubuntu?"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by ScarletPimpernell on 2007-07-16
Hello chaps,

I have an Nvidia NVS 440 quad head graphics card that I happily plug my three 19" TFT's into under XP.

My question then is, somewhat predictably, can I get this 3 monitor setup working in Ubuntu, and if so, how difficult is it to achieve?

Thanks

---

### Post by Soybean on 2007-07-16
Yes you can, and it shouldn't be too hard with an Nvidia card. I believe you want to look into something called "Twinview." I've never used it with more than 2 monitors (and the name makes me a little concerned about its ability to support 3), but it would be the best place to start. 

I don't know the exact procedure on modern Ubuntu systems (it's been quite a while since I set mine up), but from what I hear it's pretty easy to configure now.

If Twinview won't do the trick for you, it's still certainly possible to get your 3 monitors working, but it'll be a fair bit trickier. In that case, you'd want to look into "Xinerama" and you'd need to edit your xorg.conf file, and... well, I just really recommend trying Twinview first. ;)

---

### Post by ScarletPimpernell on 2007-07-16
Thanks Soybean, i'll look into it and report back to this thread with my findings. :)

---

### Post by mrmcd on 2007-07-16
I would imagine that this is similar to setting up dual monitors, which i have done with nvidia cards.  
If you are just curious about how much effort it will take, i can tell you about that.  However, I cannot offer step by step instructions as I have not set up more than two monitors before.

Short answer:
This will not be an easy, 3 click operation like in Windows.  Dual-heaing is not terribly hard, but you will probably have to do some digging online to see what other people did for 3 monitors and do a bit of tweaking yourself.

Long answer:

You are probably going to need the proprietary linux LEGACY NVIDIA driver.  
Which cards and the drivers they use are here [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html)
Your card looks to be on the legacy list.

You can install your own from driver from [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html") .  There is probably an easier way to set it up on ubuntu, via using the software Automatix or Envy.

After that, you are going to have to edit the driver properties to use 3 monitors in /etc/X11/xorg.conf .
There is one example here, where someone set up 3 monitors with 2 NVIDIA cards:
[http://terrencemiao.com/Webmail/msg00928.html](http://terrencemiao.com/Webmail/msg00928.html)
You can find a lot more info on every way you can edit xorg.conf on NVIDIA's site:
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/)

Just as a disclaimer, I am not entirely sure how and if you can do what you are asking... I think you would be able to, but I have been surprised before.  The things I am mentioning are not guides but tips to help you research and give you a general idea of how to do this... with all luck you may find that someone has done this already on the forums or in another distro and has posted instrucitons.  With good googling and good luck you may find that.  Please let us know when you figure it out

---

