---
title: "Laptop VGA output resolution"
date: 2013-03-09
forum: Hardware
---

### Post by dldeskins on 2013-03-09
I have an old laptop that has outlived its usfulness (at least for my wife) as a laptop. It is a Lenova 3000 N100. I am trying to set it up as a media server. I have a video and audio converter that converts to HDMI input on the TV.  It works well, EXCEPT the default and maximum resolution is 1024x768. The problem is not the output on the VGA output (Intel), I have tested on another external monitor. The problem is not the converter, I have used my wife's new laptop to connect up at much more compatiable resolutions.

I have tried everything that I have read and nothing seems to work.

Thanks in advance.

---

### Post by tgalati4 on 2013-03-09
Open a terminal and post the output of:

```
lspci | grep VGA
```

It's possible that the video RAM is shared with regular RAM, so perhaps bump it up in BIOS.

Most business-grade laptops have poor sound and video for multimedia.  So don't get your hopes up.  They do handle spreadsheets though.

---

### Post by dldeskins on 2013-03-10
With my understanding, this seems to be a config problem because it will drive an external Acer 23" monitor at an exceptable resolution, is that not right? But here is what you asked for:

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by dldeskins on 2013-03-13
Here is the answer that I was looking for:
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")

I got it working, but I had to use a Windows machine to get the exact resolution for the larger screen. 1280x768 was working, but 1280x800 was crashing.  The final display was 1368x768. To get a movie to fullscreen, I had to turn off the laptop display and use the TV as the primary display. I can now view movies, etc at fullscreen.

Now, to make this permanent... the above link show how to make permanent on ubuntu, but how do I do it on Xubuntu? There isn't any /etc/gdm/Init/Default . 

Thanks in advance.

---

