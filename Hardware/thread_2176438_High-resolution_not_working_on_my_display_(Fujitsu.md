---
title: "High-resolution not working on my display (Fujitsu Siemens AMILO LL 3220T)"
date: 2013-09-24
forum: Hardware
---

### Post by voh9Noom on 2013-09-24
Hi guys,

I have a Fujitsu Siemens AMILO LL 3220T display, but it is not being correctly detected by Ubuntu. The display is capable for 1920x1080 resolution, but currently in System Settings / Displays it says "Unknown" and available resolutions are 1027x768 and 800x600.

How can I get it detected properly and the get to enjoy of the full capacity of this screen?

---

### Post by Arjunanda on 2013-09-24
Adding to my post above (the account was duplicate due to SSE login confusion), the screen has a VGA plug, connected via an adaptor to a DVI connector.

Can this cause the issue of the screen not getting recognized?

---

### Post by Arjunanda on 2013-09-24
Aha,

It seems it might be due to this VGA-DVI adapter. As when I run xrandr command, it says "DVI1 disconnected". But is there any way to solve this?

$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)

---

### Post by Arjunanda on 2013-09-24
Ah, found a post in ubuntu questions, and now my screen has the resolution I was wishing for. Though so far it is not persistent after reboot, working on that.

Here is the link:
[http://askubuntu.com/questions/139947/why-cant-ubuntu-12-04-detect-my-screen-resolution](http://askubuntu.com/questions/139947/why-cant-ubuntu-12-04-detect-my-screen-resolution)

---

