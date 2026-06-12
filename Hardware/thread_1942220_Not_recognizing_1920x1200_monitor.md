---
title: "Not recognizing 1920x1200 monitor"
date: 2012-03-17
forum: Hardware
---

### Post by pderocco on 2012-03-17
OS: Ubuntu 11.10, all updates
Mobo: Intel D2700MUD (Atom) with GMA3650 graphics
Monitor: Eizo CE240W 1920x1200 via DVI
 
On a different Windows system, the monitor is properly recognized, but on Ubuntu, the system doesn't identify the monitor. In Displays, it shows up as Unknown, and it chooses a 1600x1200 max resolution. Questions:
 
1) Is the fact that it's not identifying the monitor the cause of my problem? If I could get it to know what the monitor is, would it automatically enable the higher resolution?
 
 
2) If it's flying blind, where does it come up with 1600x1200 for the max resolution, as opposed to, say, 640x480?
 
3) Is there a way to know if it's using an Intel-specific driver, as opposed to, say, some Vesa or vanilla VGA driver?
 
4) Is there a way to blindly force it to support 1920x1200? My "xrandr" experiments manage to create such a mode, but it won't enter that mode because something is still enforcing a 1600x1200 limit. And my experimental creation of a minimal xorg.conf file (there was none) also ended in boot failure.

---

### Post by Helen McCall on 2012-03-17
I am having the same problem with my HP w2216 monitor.

On my old (now broken down) computer which ran Ubuntu 9.04 64bit with a nVida graphics card and nVidia driver it recognised this monitor as 1920x1200.

My new computer I built a few weeks ago running Ubuntu 11.10 64bit with an onboard Radeon HD6410 graphics adapter, the AMD driver only recognises my HP w2216 as 1680x1050

---

