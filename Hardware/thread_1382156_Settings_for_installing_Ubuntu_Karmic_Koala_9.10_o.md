---
title: "Settings for installing Ubuntu Karmic Koala 9.10 on a HP Compaq EVO with intel 845 gr"
date: 2010-01-15
forum: Hardware
---

### Post by SilverBug on 2010-01-15
As a complete newbie, I installed Karmic Koala 9.10 on two identical HP Compaq EVO desktop computers.  Everything worked except that the screen would freeze sporadically. By freezing, I mean only the mouse moved but no mouse keys or keyboard buttons worked.  The only way to recover was to power down the computer.  This usually happened when surfing in Firefox and scrolling up and down in the browser window.

Since, much to my surprise and relief, I eventually  found what I needed to do, it seemed only fair to post the results. I am sure some profi can explain this in detail but for those of you with the same computer and the same novice level, here goes.......

After much googling, my first attempt was to create an xorg.conf file with the following content

Section "Device"
 Identifier "Configured Video Device"
 Driver "vesa"
EndSection

This had the effect of stopping the screen freezing but when I logged out or tried to switch user, the screen went black and again the only way to recover was with a power down/power up.

I then googled some more and eventually created an xorg.conf file with the following content

Section "Device"
 Identifier "Configured Video Device"
 Driver  "intel"
 Option "AccelMethod" "EXA"
 Option "MigrationHeuristic"  "greedy"
EndSection

This works perfectly and has been for nearly a week with no problems.  You can't activate any of the special desktop effects but these are not really necessary for a simple office workhorse like the EVO.

A few additional notes:-  

This is the info regarding the graphics driver....

administrator@Compaq:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I read somewhere that this might also be useful to know....

administrator@Compaq:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 845G GEM 20090712 2009Q2 RC3 x86/MMX/SSE2

And for the other newbies, this is what you have to enter to create the xorg.conf file in Karmic Koala Ubuntu 9.10 because it is not automatically created in this version of Ubuntu.

administrator@Compaq:~$ sudo gedit /etc/X11/xorg.conf

Hope this helps somebody.

---

