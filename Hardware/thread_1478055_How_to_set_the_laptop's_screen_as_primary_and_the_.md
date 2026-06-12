---
title: "How to set the laptop's screen as primary and the projector's secondary?"
date: 2010-05-09
forum: Hardware
---

### Post by AlexZaim on 2010-05-09
Hello. I'm using a toshiba t135 with GMA4500M V-card, running Ubuntu 9.10.

The problem is that all programs start on the monitor screen after i launch them. It's not a problem to drag them back on the laptop's screen, but some programs like lyricue get "confused" and projects the fullscreen image on my laptop, in stead of the projectors.

So any ideas on how to make laptop's screen primary?

I tried playing with the "System> Preferences >Monitor Preferences" but nothing is working.

---

### Post by AlexZaim on 2010-05-09
up

---

### Post by AlexZaim on 2010-05-10
up

---

### Post by AlexZaim on 2010-05-11
Help,pls?

---

### Post by AlexZaim on 2010-05-17
i discovered that intel v-cards set the projector as primary by default. Is there a way to configure it via soft?
Last chance. Any help yet?
```
$ xrandr -q
Screen 0: minimum 320 x 200, current 2166 x 768, maximum 4096 x 4096
VGA connected 800x600+1366+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3*+   85.1     72.2     75.0     60.3     56.2 
   1280x1024      85.0     75.0 
   1280x960       85.0 
   1152x864       75.0 
   1280x720       60.0 
   1024x768       85.0     75.0     70.1     60.0     43.5 
   832x624        74.6 
   640x480        85.0     75.0     72.8     66.7     59.9 
   720x400        70.1 
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0*+
   1360x768       59.8 
   1024x768       85.0     75.0     70.1     60.0 
   832x624        74.6 
   800x600        85.1     72.2     75.0     60.3     56.2 
   640x480        85.0     72.8     75.0     59.9 
   720x400        85.0 
   640x400        85.1 
   640x350        85.1 
HDMI-1 disconnected (normal left inverted right x axis y axis)
```

---

