---
title: "1680x1050 resolution on Dell Studio Hybrid with x3100 graphics card"
date: 2008-09-20
forum: General Help
---

### Post by tati on 2008-09-20
No screen resolution above 1280x1024 is available on my Dell Studio Hybrid. The Hybrid has an x3100 graphics card and the monitor is a Dell SP2009W 20" Widescreen Flat Panel Monitor with Webcam. How do I increase the resolution to 1680x1050?

---

### Post by fragos on 2008-09-21
My Dell laptop has X3100 and my 1280x800 display was automatically handled. My desktp with Nvidia an Viewsonic wide screen also automatically registered my 1440x900 LCD. In years past we'd add resolution descriptions to /etc/X11/xorg.conf. You may find an answer in xorg.conf configuration. It's been so long since I had to do that I don't recall exactly how.

---

### Post by windoze87 on 2008-09-21
pop yourself open a terminal and type in ```
sudo dpkg-reconfigure xserver-xorg
``` and follow the prompts. That may help. If not, you might need to find the manual for your monitor and figure out the horizontal and vertical sync refresh rates and put them in manually. Sounds daunting, and it is, but that's what i had to do with my 19 inch Dell widescreen on my nvidia fx5500.

---

### Post by tati on 2008-09-23
I see keyboard layout instructions when I use that prompt. Should I be seeing something else?

---

### Post by mickdo on 2008-12-01
> **tati said:**
> I see keyboard layout instructions when I use that prompt. Should I be seeing something else?

Unfortunately the geniuses at Ubuntu have removed the ability to change the display settings using *dpkg-reconfigure xserver-xorg* on 8.10 so if that is what you are using it will have to be a manual edit of /etc/X11/xorg.conf I'm afraid.

What worked for me on 8.10 was the following:

1) sudo apt-get install xserver-xorg-video-intel
2) sudo vi /etc/X11/xorg.conf
3) in xorg.conf, replace the line '*Driver   "vesa"*' with '*Driver   "intel"*' and save
4) Reboot

---

