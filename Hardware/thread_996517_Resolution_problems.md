---
title: "Resolution problems"
date: 2008-11-28
forum: Hardware
---

### Post by walkingbeard on 2008-11-28
Hi,

My problem is that when I install versions 7.10-8.10, I get a high resolution picture (1152x864), but when I install the Nvidia proprietary driver (1.73 or 1.77), the resolution is reset to 1024x768 and the refresh rate is stuck on 60Hz.

When I first install Ubuntu, the applet System->Preferences->Screen Resolution correctly detects my monitor as being a 17" LG flatscreen, but after I have installed the protected driver, it doesn't recognise my monitor any more.

Can I just choose my monitor from a list, like with Windows?

---

### Post by tommcd on 2008-11-29
First, make sure you have the correct nvidia driver. What nvidia card do you have?
Second, try running **nvidia-settings** from terminal. Then click on **X Server Display Configuration**. On the resolution drop down list on the right side, see if you can choose your monitor's correct resolution and refresh rate from the list.

If this doesn't work, you can try adding the correct resolution to /etc/X11/xorg.conf. On a default 8.10 install there is no xorg.conf, since the newest X server does not need one. The nvidia driver may have created one for you though. If not, you can create one yourself and add the resolutions to it. Try nvidia-settings first though.

---

### Post by doas777 on 2008-11-29
be sure to run nvidia-settings with sudo or gksu
```

sudo nvidia-settings &

```

have fun

---

