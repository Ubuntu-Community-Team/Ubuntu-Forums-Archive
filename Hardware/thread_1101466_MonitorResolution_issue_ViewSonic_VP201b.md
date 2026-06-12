---
title: "Monitor/Resolution issue ViewSonic VP201b"
date: 2009-03-20
forum: Hardware
---

### Post by jumpoutofatree on 2009-03-20
Hey folks,
I just recently found my old vp201b and was going to run dual monitors with it as my secondary. My main problem is that ubuntu hardly recognizes my monitor it has issues with it at installation and when i enable it for my secondary i can never get the right resolution... The native is 1600x1200 @ 60hz... i can only seem to get around 1024 at best. I tried: editing the xorg, using ubuntu and nvidia drivers, played around for a while with nvidia settings i just can't find a solution. Would using a kde desktop as opposed to a gnome desktop change anything?... i'd be down. Any help is much appreciated.

---

### Post by cheaka on 2009-10-08
I was having same problem with my VP201b running as a second monitor from my ATI Mobility X1300, on a thinkpad t60. xrandr was also not reporting any resolution above 1280x1024. A simple 
```
sudo dpkg-reconfigure xserver-xorg
``` fixed it for me (as suggested at [http://ubuntuforums.org/showthread.php?t=51151](http://ubuntuforums.org/showthread.php?t=51151) ).

---

