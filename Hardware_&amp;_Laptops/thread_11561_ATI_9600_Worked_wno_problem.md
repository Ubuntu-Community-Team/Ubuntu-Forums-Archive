---
title: "ATI 9600 Worked w/no problem"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by coolbreeze on 2005-01-17
I just installed Ubuntu and have greate news!

I have an ATI Radeon 9600.  Linspire recognized the card and loaded driver during installation with 3d working.  For Debian I had to compile the driver into the system including downloading headers and working with kernel.  I followed some instructions I found on the web.  I think I was re-building kernel? Heck allI know it took me several hours!  However, neither in Linspire nor Debian did fireglcontrol work.  This wasn't the case with Ubuntu.  The card was recognized. I ran glxinfo and saw Mesa so I knew something was wrong.  I saw in Synaptic that fglrx-dev and fglrx-control weren't loaded.  So, I marked them for installation.  And presto after re-booting, everything works great!  It was that simple!  Here are my numbers from glxgears.  I have never gotten numbers this great in other distros.  Oh yea I see that fglrx-control is the name of the package but the command to use the panel it loads is fireglcontrol.  I know in the "HOW-TO" section it says you you have to edit fglrxconfig but I didn't have to! That's my news! It's working out the box, just install the remaining packages in Synaptic.

18304 frames in 5.0 seconds = 3660.800 FPS
17159 frames in 5.0 seconds = 3431.800 FPS
18232 frames in 5.0 seconds = 3646.400 FPS
18729 frames in 5.0 seconds = 3745.800 FPS
18843 frames in 5.0 seconds = 3768.600 FPS
18847 frames in 5.0 seconds = 3769.400 FPS

 :) coolbreeze

---

### Post by coolbreeze on 2005-01-17
Oh wow!! I just loaded KDE and it placed the ATI Control Panel on the menu!!

---

