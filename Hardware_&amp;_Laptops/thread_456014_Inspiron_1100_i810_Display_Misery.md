---
title: "Inspiron 1100 i810 Display Misery"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by UncleB on 2007-05-27
Hello all,

I've searched for my problem and found answers by other people but none of the fixes I found work for me.

I'm using a Dell Inspiron 1100 with Ubuntu 7.04 and the i810 driver for the display. That results in a small portion of the screen running at 680x400. 

When I install newer Intel drivers (sudo apt-get install xserver-xorg-video-intel) I lose all display even after running dpkg-reconfigure and selecting seemingly good options. However gdm is running because I hear the little drum roll and I can drop out with CTRL+ALT+F2 to a console.

If I use 915resolution to put in 'good' resolution options again I end with failure. This time the message comes up saying that gdm had bad config and do I want to review the settings for diagnostics.

Does anyone have any other suggestions? Or better yet someone with a Dell Inspiron 1100 who has a failsafe HowTo for setting up 7.04!

Thanks in advance...

---

### Post by UncleB on 2007-05-27
2 minutes after despair it's fixed.

I loaded the Intel driver got to the black screen and then switched to console (CTRL+ALT+F2) and installed the i810 driver again.

Perhaps this could be done more elegantly if I'm really just getting a newer version of i810 but I'll leave that to someone else to test/verify.

---

