---
title: "s-video output thinkpad t41p?"
date: 2008-09-21
forum: Hardware
---

### Post by jemonic on 2008-09-21
I have installed Hardy Heron on a Thinkpad T41p and would like to configure for S-Video output to a TV if possible. Much searching has yielded a variety of inconclusive answers regarding i855crt, xorg settings, and nvidia settings. Anybody have any information regarding this? I would like to setup the laptop to connect to the TV with XBMC or VLC or Myth TV.  Thanks.

---

### Post by armin_sadeghi on 2008-11-18
I just recently had this exact issue while trying to get video output working on my Thinkpad T41. I posted a full solution on my blog here:
[http://www.arminsadeghi.com/?q=node/40](http://www.arminsadeghi.com/?q=node/40)

---

### Post by yoel.koenka on 2008-12-06
Hello,
I have the same problem with my T41p S-video output (my other output works fine).
I tried what is written here but when I run:
xvattr -a XV_CRTC -v 1
I get:
Found Xv 2.2
No adaptor

Generally, it seems that this solution isn't for S-video problems.
Does anyone have a clue how to make the S-video on T41p work?
Even when I boot my computer when the cable is connected, it doesn't work.

---

