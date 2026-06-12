---
title: "Intel 855gm Graphics Driver Issue in 11.04"
date: 2011-09-13
forum: Hardware
---

### Post by travlemon on 2011-09-13
Hello,

I have a Dell Latitude D505 with the dreaded Intel 855gm graphics chip.  This is sort of a continuation of another problem that I thought I solved, but I thought it'd be better to re-post with an appropriate thread title and a description of the new problem. 

When I boot a live CD of any Ubuntu 11.04 based distro, the video seems to be OK.  The original problem was that I couldn't change resolutions, and I was stuck in 1400x1050 and had no other choices.  I found that generating a xorg.conf (as there is no xorg.conf by default), and moving it to the /etc/X11 folder will give me all of the resolutions.

I thought I solved the problem...but when I use xorg.conf,  the graphics are very glitchy and the desktop is unusable.  Everything on the desktop flickers and such.

Does anybody know any solutions to this problem?  I tried some fixes I found on the web, but nothing has helped me thus far.  Any help is much appreciated, as I'd like to stay away from Windows!

---

### Post by travlemon on 2011-09-29
> **travlemon said:**
> Hello,

I have a Dell Latitude D505 with the dreaded Intel 855gm graphics chip.  This is sort of a continuation of another problem that I thought I solved, but I thought it'd be better to re-post with an appropriate thread title and a description of the new problem. 

When I boot a live CD of any Ubuntu 11.04 based distro, the video seems to be OK.  The original problem was that I couldn't change resolutions, and I was stuck in 1400x1050 and had no other choices.  I found that generating a xorg.conf (as there is no xorg.conf by default), and moving it to the /etc/X11 folder will give me all of the resolutions.

I thought I solved the problem...but when I use xorg.conf,  the graphics are very glitchy and the desktop is unusable.  Everything on the desktop flickers and such.

Does anybody know any solutions to this problem?  I tried some fixes I found on the web, but nothing has helped me thus far.  Any help is much appreciated, as I'd like to stay away from Windows!


I am putting this to rest, though I never fully found a solution.  Debian seems to have a decent driver for the card, and Linux Mint Debian Edition seems to work great on that machine.  So I went with that.

---

