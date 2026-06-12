---
title: "ATI Radeon Xpress 200M doesn't function properly"
date: 2010-09-06
forum: Hardware
---

### Post by Martificiam on 2010-09-06
I have ATI Radeon Xpress 200M integrated video card on my Fujitsu Siemens Amilo L series laptop and it works with Windows perfectly. When I installed Ubuntu it appears that the driver isn't functioning as it should be. Whenever I try to watch a video, it has some strange horizontal lines appearing randomly. Or when I use special effects on desktop environment the computer lags very much. Which DIDN'T happen when I installed Ubuntu previously with Wubi. As I wanted an independent Ubuntu install, I got rid of the Wubi thing and installed Ubuntu on unallocated space that I left for it when installing XP.

Anyway, I have the highest resolution possible on my machine, but everything that's in 3D (even those primitive 3D flash animations) lags a lot. In fact, everything that takes up my integrated video processor's usage lags or doesn't function properly (the video doesn't lag, but they just have some sort of refreshing failure or something, I don't know).

I don't understand why did it work with Wubi, but doesn't work with the real Ubuntu thing.

How do I fix this?

---

### Post by androiddev on 2010-09-06
I'm fairly new to Ubuntu (used on/off for a few years) but have you tried going to System > Administration > Hardware Drivers and checking to see if there are any restricted drivers available for your card?

---

### Post by Martificiam on 2010-09-08
Yes, I've tried that, but with no luck.

---

### Post by JHCKX on 2010-09-09
I've had problems with the Xpress 200M as well. Apparently, there's a propietary driver available for Ubuntu 8.04. From 9.04 on, ATI stopped providing the propietary driver for older cards such as the the Xpress 200M and open source drivers were you're only option. I did find that 10.04 had poorer graphics performance than 9.04 (9.10 was unstable on my computer). What worked for me was to install the Xorg-edgers PPA, which gives you advance access to newer drivers. Be aware though that others have reported the Xorg-edgers PPA froze their system.

To install Xorg-edgers, use the following commands:

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get install ppa-purge
sudo apt-get update
 
Then run update-manager to update your system and restart.

If you have problems, run ppa-purge:

sudo ppa-purge xorg-edgers

That will remove the xorg-edgers version. After a reboot, the standard drivers will be re-installed, with the known performance issues. But at least your system will be stable.

See also 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125)
[http://ubuntuforums.org/showthread.php?t=1537994](http://ubuntuforums.org/showthread.php?t=1537994)

---

### Post by Fafler on 2010-09-09
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get install ppa-purge
sudo apt-get update

```

Fix for [email]John2.Hendrickx@gmail.com[/email]

---

### Post by Martificiam on 2010-09-12
My ATI drivers still don't work correctly with 10.04. I'm downloading Ubuntu 8.04 at the moment, hope it works.

---

### Post by Martificiam on 2010-09-12
How do I make those drivers work on 10.04?

---

### Post by avi58 on 2010-09-20
I'm quite interested in the continuation of this post. I have the same graphics card but the rest of the computer is different, I haven't got my laptop at hand so I can't remember the model.

In ubuntu 9.04, in the startup process, the screen could either work perfectly or change and stuck to a white screen with some vertical light colored lines.

Yesterday I tried to install ubuntu 10.04 and the only way I could manage to work with my laptop was connecting an exterior monitor.

Any suggestions?

---

### Post by Fafler on 2010-09-20
avi58: Look into kernel mode setting and try disabling it from your /etc/default/grub

---

### Post by avi58 on 2010-09-21
@fafler: It worked! I had to search a few to know how to do what you said '^^

Although I have faith in linux I'll wait until I reboot the computer few more times to be sure that everything it's ok ;)

---

### Post by efflandt on 2010-09-22
What Fafler is referring to is **nomodeset** or **radeon.modeset=0** kernel boot parameters to disable the new kernel mode setting drivers, and use the older user space modules instead.

I have an old Compaq laptop w/200M that could not hardly run 9.10 because there was some sort of system lag that would often drop characters (making sudo difficult), the mouse would lag and jump, and it could not suspend/hibernate at all.  For 10.04 I used nomodeset because I had trouble with kms for other legacy ATI cards (X1300 desktop or mobile in particular).  In 10.04 this laptop rarely has keyboard or mousepad lag, and suspend/hibernate work.

The video is still not exactly fast, and may glitch if you try to do any gaming (like supertuxkart), but maybe that depends upon shared video RAM.  It was a really low end laptop originally and I just inherited it when I got someone a better laptop.

---

### Post by ademey on 2010-11-14
I am experiencing similar problems with Radeon Xpress 200M integrated motherboard graphics on a Dell Vostro 1000 laptop. This is since 9.10, I think.

At start-up I saw vertical color line instead of the login screen. Or, (text-based) tty1 login was prompted for about a minute before normal graphical login screen came up.

It was solved by a local linux store using radeon.modeset=0 in boot options However, no desktop effects could be enabled, and after a while the tty1 login prompt returned (september 2010). Alternatively, the xforcevesa in boot options also eliminated the color lines, but resolution was poor.

Now, in 10.10, I tried again radeon.modeset=1 in boot options. vertical color lines re-appear (no tty1 login). When closing the lid of the laptop and reopening it, login screen is shown properly and the system runs fine, with desktop effects enabled.

Really hope to get this fully solved soon.

---

### Post by Jarcon on 2011-01-05
I'm having the same issue, it's not just Ubuntu, other newer distros seem to have the same problem.

---

### Post by Bucic on 2011-01-27
Explain this then: **Ubuntu LiveCD provides multiple of installed Ubuntu performance!**

Same card, same system. By multiple I mean the performance is more than 3 times better. It's like with proper drivers!

---

### Post by Nattydread69 on 2011-06-04
I managed to double my FPS on the benchmarks by disabling the kernel driver for my laptop with a ATI Radeon Xpress 200M (ubuntu 10.04).

type:

```
sudo gedit /etc/modprobe.d/radeon-kms.conf
```

then enter into the empty file:

```
options radeon modeset=0
```

save then restart.

---

### Post by Bucic on 2011-06-09
Nattydread69,

Unity won't  rub after such a modification. Besides, I'm more after stability rather than performance. Performance on my system seems fine anyway. Recently even crashes stopped for no apparent reason - I didn't do any updates or config alterations recently. Plus after my recent fresh reinstallation of 11.04 I stayed with Unity 3D!

Please note however that I totally confirm that KMS was behind crawling performance on 10.x. At least on 10.10 I used. You can read about it [**Ubuntu LiveCD provides MULTIPLE of my installed ubuntu performance!**]("http://ubuntuforums.org/showthread.php?p=10403240#post10403240")

---

