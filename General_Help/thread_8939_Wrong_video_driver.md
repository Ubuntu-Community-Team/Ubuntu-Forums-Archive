---
title: "Wrong video driver?"
date: 2004-12-22
forum: General Help
---

### Post by BillDrew on 2004-12-22
I just installed Ubuntu onto a IBM 300GL.  It did not find a driver for my video  which is a TRIO 64 3D pci video.  The problem is I want to increase the rsoltuion and the only one I have now is 640 x 480.  How do I find the correct driver so I can get higher resolution that I know this monitor is capable of?

Bill Drew
[email]drewwe@morrisville.edu[/email]

---

### Post by pelle.k on 2005-11-06
I've been batteling this problem recently and thought i would fill in on what might be the solution. I have a ibm 300gl with a trio 64 3D on board. I dont know how much ram it has got, but it could vary from 512kb up to 4mb in most cases.

To configure Xorg do "sudo dpkg-reconfigure xserver-xorg" at the command prompt (or a terminal). (If screen is locked in som less readable mode, press ctrl + alt +f2 to get a new "prompt").

This card will not start if you choose s3 as driver! i don't know why, but s3virge as driver seems to work fine though! xorg should autodetect most settings, and default values should be fine. IF you know you have LESS than 2 mb graphics ram, 1024*768 in 16 bit probably wont be an option for you. Lower either resolution or bit depth.
Good luck.

---

