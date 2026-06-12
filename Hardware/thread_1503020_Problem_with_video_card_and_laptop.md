---
title: "Problem with video card and laptop"
date: 2010-06-06
forum: Hardware
---

### Post by Str82DHeaD on 2010-06-06
Hello everyone! I have a Fujitsu Siemens AMILO pro V2030 laptop and I've installed ubuntu 10.04 on it. But there's a problem with the video card. It detects 1600x1200 default dimensions and when I try to make it 1024x768, the monitor becomes blurry. I can see just a part of my desktop screen. I've tried dpkg-reconfigure xserver-xorg but there's no xorg!?!? + there's no xorg.conf anywhere....
Please help me

---

### Post by Str82DHeaD on 2010-06-08
anyone???

---

### Post by TheDuph on 2010-06-23
I have the same problem, still searching...

---

### Post by dave_man137 on 2010-06-23
you can try this driver ...if it can be installed with 10.04, hope it works for you.






[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by bayr00t on 2010-11-23
on a friend's AmiloPro a2030 I created a new xorg.conf file and that solved the issue!

```
sudo gedit /etc/X11/xorg.conf
```

the file was empty, but I copy/pasted the following:

```
Section "Device"
   Identifier   "Configured Video Device"
EndSection

Section "Monitor"
   Identifier   "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
   DefaultDepth     24
   SubSection "Display"
      Viewport 0 0
      Depth    24
      Modes    "1024x768" "800x600" "640x480"
   EndSubSection
EndSection
```

...saved the changes and rebooted the computer. And now Gnome works in 1024x768 instead in 1600x1200!

---

