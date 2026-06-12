---
title: "Screen Flashes (fresh install 8.10) and cannot activate ati Driver."
date: 2008-11-02
forum: General Help
---

### Post by zhenka11230 on 2008-11-02
Hello!

I just installed Kubuntu 8.10.  It works fine except the screen flashes every 5 seconds or so as if the refresh rate is messed up.  My resolution is 1024/768 with 85 refresh rate(my monitor does support it and that is what i always used with no problems in Ubuntu, including 8.10 ubuntu).

When i open hardware driver manager and click activate ATI driver - it doesn't seem to do anything  : (.  It remains unactivated. 

Help please!

---

### Post by drinian on 2008-11-02
I am having the same problem. However, I am using the intel driver, and only my secondary screen (which is mirroring my laptop's builtin screen) flashes.

I installed Kubuntu through Ubuntu and can confirm that the GNOME desktop works fine. I can also confirm that KDE 4.1 under Gentoo works fine with this setup.

---

### Post by lordmyth on 2008-11-07
same problem here... I'm using an old SiS pci card, when i type it's even worse, it's like the monitor is constantly restarting

i'm using 1024x768, 16bit and 70Hz or so, but using the same xorg.conf (properly set up) i used on gnome

happens with any resolution btw

also, kdm doesn't show the problem

---

### Post by lordmyth on 2008-11-07
i discovered that the problems disappear if you kill krunner

kindof silly because you're left without alt-f2 to run your programs :D

---

### Post by bitseeker on 2008-11-12
I had the same [screen flashing problem in Kubuntu]("http://blog.turbulentsky.com/2008/11/kubuntu-810-video-flashing-flickering.html") and solved it by disabling the monitor detection service, "Detecting RANDR (monitor) changes", in the Service Manager. Some people have experienced the same problem but as flickering of the screen rather than flashing.

Screen is fine now and hotkeys aren't negatively affected by this workaround.

---

### Post by wirechief on 2008-11-23
I have ATI X1300 pro it has always failed with the proprietary driver.
This flashing problem was resolved for me too, this
fix works well in stopping the annouying flashing.

---

