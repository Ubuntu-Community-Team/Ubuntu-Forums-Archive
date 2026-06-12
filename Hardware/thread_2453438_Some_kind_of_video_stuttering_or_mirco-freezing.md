---
title: "Some kind of video stuttering or mirco-freezing?"
date: 2020-11-10
forum: Hardware
---

### Post by zebutron on 2020-11-10
First off, a big thanks to everyone in the community. I often come here to read about possible solutions and it really means a lot of me that people put so much effort into helping each other. 

The problem:

I have a Lenovo T430 with 3rd gen integrated Intel graphics card and I sometimes have various freezeups and microstuttering with videos. I was experiencing some Youtube video stuttering while using Firefox but that turns out to be a google problem and the work around was to use the Enhancer for Youtube extension which mimics Youtube's faux full-screen. That is great but a similar problem happens when I am using multiple resources, e.g.multiple Firefox tabs and VLC playing a video. Things start getting a bit jittery or laggy. I then quit programs and free up resources except even after quitting all programs and reopening just one, the problem persists. The only way I've been able to work around it is to log out and log back in or reboot. This problem doesn't make things unuseable but I'd love to figure out what is happening. I'm not sure if it has gotten worse over time but I feel like it has. The only thing I haven't tried yet is rolling back to an earlier kernel. I was hoping someone has some experience with this. 


```
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1600x900@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 4000 (IVB GT2)
           version: 4.2 Mesa 20.0.8
```

---

### Post by SeijiSensei on 2020-11-10
How much memory do you have? Have you set up a [swap file]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F")? Does this happen while watching local video files or only over the Internet?

---

### Post by zebutron on 2020-11-11
Hi. Thanks for the response. 

I have 8 GB memory and another 2 GB swap. It happens with both local and streaming files. What is strange to me is that even after closing programs e.g. Firefox, VLC, and reopening just one, the problems persists until I logout and log in again. Are there any specific logs I can check or diagnostics I can run?

---

### Post by SeijiSensei on 2020-11-11
Just to humor me, can you install mpv and see if you have the same problems playing local files? If you want a GUI, install SMPlayer as well.

```
sudo apt install mpv smplayer
```

If that doesn't help, try installing the Intel VA-API driver to enable hardware acceleration of video.  
```
sudo apt install intel-media-va-driver
```

See [https://wiki.debian.org/HardwareVideoAcceleration#VA-API](https://wiki.debian.org/HardwareVideoAcceleration#VA-API) which gives instructions for modifying $HOME/.config/mpv.conf to utilize VA-API. It also discusses the browsers that support VA-API.

---

### Post by zebutron on 2020-11-16
Thanks again. 

I do not know what has happened but I can't trigger the problem anymore. When I try to tirgger it by running too much, it just lags like normal until I quit/stop something and then it runs fine. 

Perhaps there has been some update in the last week, IDK. If it starts again, I'll try your suggestion. 

Thanks  again!

---

