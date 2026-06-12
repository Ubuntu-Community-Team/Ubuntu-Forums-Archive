---
title: "Trouble with Nvida video"
date: 2009-10-05
forum: Hardware
---

### Post by llwdtp on 2009-10-05
This is a re-post in a more appropriate subforum.
I have had a lot of trouble getting Ubuntu Studio to work right with audio and midi. The short version is:
  
My Nvidia card does not work with the Nvidia driver. That may not be an issue. But all of the windows on the desktop have 2 or 3 circles in the upper right corner instead of the normal symblos for minimize, maximize and close.

Please help.

Now the longer version. I am using Ubuntu studio 9.04 with a Dell desktop machine about 7 years old. It has 500 mega bytes of memory and a sound blaster live card. I think it has a built in Intel sound system according to the various responses I have gotten. I cannot use that system as it does not appear to by wired to the outside world. 

The first problem are the windows with the funny symbols in the upper right hand corner. There is either 2 or 3 circles in that corner. When there is 2 circles, clicking on the right most circle does not shut the window down, but instead maximizes it. After doing a bit of searching, I presumed the problem may be the video drover. I tried to install the Nvidia driver for my Nvidia GeForce card. It told me it failed after attempting. When I reboot, the boot stalled when it tried to load the video driver and refused to go to X. My only recourse was to reinstall the OS. This happened several times before I decided to try and live with it.

If you have ideas on how to solve this problem, I would appreciate hearing them.

---

### Post by RAKninja on 2009-10-29
those three symbols are not a bug, but the default theme.

go start menu -> system -> preferences -> appearance and select a theme with more familiar icons if you like.

to install your NVIDIA drivers, the restricted devices manager is the recommended method.  because of studio's custom kernal, you might be forced to install from synaptic package manager instead.

---

