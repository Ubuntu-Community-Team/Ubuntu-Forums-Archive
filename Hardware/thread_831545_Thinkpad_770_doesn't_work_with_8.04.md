---
title: "Thinkpad 770 doesn't work with 8.04"
date: 2008-06-16
forum: Hardware
---

### Post by cstrrider on 2008-06-16
I have an old thinkpad 770 that I have been trying to install xubuntu on.  I have installed 7.04, 7.10, and 8.04 successfully, but my computer requires 16 bit color to run at it's full resolution of 1024 by 768. I know that I need to edit my xorg.conf  for this to work, and I got it to work in xubuntu 7.04, but not 8.04. when I run it at 16 bit color it says it's in low graphics mode and still has 800 by 600 resolution. can anyone help me?

---

### Post by phidia on 2008-06-17
What GPU does the thinkpad use, and what driver are you using?
You can post your /etc/X11/xorg.conf if you need to.
Also [this document]("https://help.ubuntu.com/community/XORGHardy") might be useful. Hope that helps.

---

### Post by TheCan on 2008-11-09
I am having the same issue on my Thinkpad 770. Just installed XUbuntu 8.10 and it doesn't switch up to 1024x768, although I have configured a DefaultDepth of 24 and an appropiate Modes "1024x768" line.

It was working fine in XUbuntu 7.10 which I had installed previously. Anybody with a Thinkpad 770 who got it working in 8.04 / 8.10 out there?

---

