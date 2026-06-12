---
title: "No 3D Acceleration, no errros though, I'm out of ideas :("
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by sneax on 2005-08-29
Hello. After installing Ubuntu I installed drivers for my graphics card and after some trial and error got them to work under Cedega. Though, when a flashbang was thrown in CS:S it would crash my game to desktop. So I decided to try some other drivers and stuff. The biggest mistake I ever made.

I installed the latest drivers for my graphics card from [http://dri.freedesktop.org/snapshots](http://dri.freedesktop.org/snapshots). Everything *seems* to be in order. Glxgears 750fps (which is ok for my graphics card - intel 855GME), direct rendering is 'yes' in glxinfo. I tryed everything in the troubleshooting page from [http://dri.freedesktop.org/](http://dri.freedesktop.org/) and indeed the drm modules should be initialised correctly, everthing set up ok, glx gears ok. BUT when I run a real 3D application, I have horrible performance (less then 1 fps). It's so weird. Tuxracer for example is excellent in the menu itself (the snow flakes fall down realy smooth, no problems) but when i start a game i have extremely slwo performance. Games in cedega don't work anymore too (very very slow performance). Still, EVERYTHING seems to be set up correctly and glxgears works and the menu in tuxracer works too!

I'm all out of ideas. I don't know at all what to do anymore. I've searched these forums and read all info regarding i810 but it's all related to getting DRI to work. DRI works! But for some reason, opengl in games simply doesn't. Please ... help?

---

### Post by pmjdebruijn on 2005-08-29
Hi,

It could just be that the latest snapshot you installed is horribly broken, try an older (or more recent) snapshot of dri, that might help.

Regards,
Pascal de Bruijn

---

### Post by sneax on 2005-08-29
There's only 2 snapshots in that directory. I just tryed the other one and it DOES fix my tuxracerproblem! Though, in Cedega I still don't seem to have any acceleration. I guess this must be a Cedega problem then?  ](*,)  :neutral:

---

### Post by Rhemat on 2005-08-29
I was wondering, since it's along the same topic, if you'd be able to help with a 3d Acceleration problem for my computer and Nvidia card.  Now I hear a lot of people have problems with Nvidia, but the problem lies solely with the 3d Accel. drivers, OpenGL, I believe.  
The problem is, I recently got Quake3 on my system, and it can be played, but the new 64meg card isn't enough to play it(w/o the drivers), and if I have the processor do the work, it is incredibly slow.
I don't know if I need to reinstall the drivers, or reconfigure.  Any suggestions would be welcome.

-Rhemat

---

### Post by sneax on 2005-08-29
What card exactly do you have? If you do
glxinfo | grep direct
is Direct rendering set to YES?

If it is set to yes, can you do glxgears and tell me FPS?
If the fps is above 1000 can you try playing tuxracer? (if it's not installed you can install it using synaptic)

If you've done all this already sorry, my bad ;)

---

### Post by Rhemat on 2005-08-30
Well, can't try anything now.  My computer had a schism last night, were every time it was on screen saver for a while, it would completely lock up.  Alt+Ctrl+Backspace and the like didn't work.  Powered it down, started it up, and it gave errors, but eventually got back to the gui.  Well, screen saver came around again, and everything froze, and restarting gave more errors, and no gui.
  One new card and a reinstall later, got 5.04 up and running again.
  So, now I'm going to try and find the drivers 1st (and find what caused the earlier problems), and reinstall the Nvidia later.  Right now, I'm temporarily using a Trident 8mb because I fried my original 32mb Savage4.
  A "TNT2 M/64" or a "geforce 1. 32 meg" as the supplier of the card said.  At least I didn't lose any important files.

-Rhemat

---

### Post by Rhemat on 2005-08-31
I was also wondering what the protocol is for switching the current card with an Nvidia card would be?  It has worked with the Nvidia card in use before, but lead to the previous errors.  Now, it gives an error and will not go to the GUI.

Anything I have to install first, or would reinstalling Ubuntu while using the card work?

-Rhemat

---

### Post by pmjdebruijn on 2005-09-02
Well, it should...

Anyway all your graphics settings can be configured from a text console using the /etc/X11/xorg.conf file...

If you're having issues, try swapping the 'nv' or 'nvidia' driver with 'vesa'.

Regards,
Pascal de Bruijn

---

### Post by Rhemat on 2005-09-10
Okay, Ubuntu 5.04 is working with a 64 Nvidia card.

I checked and Direct Rendering is set to "No."  This should be changed I bet.  I also recently downloaded nvidia-glx, but I bet I need to reboot for it to take effect.

My average of FPS is 85.4.

Also, are there any other bugs that are NVidia related?  I heard something about memory leakage when XMMS is installed and an Nvidia card is being used, but I can't seem to find the page again.

Thanks again for your help.

-Rhemat

---

### Post by Rhemat on 2005-09-27
Sorry it took me so long to post again, but I found the fix for the 3d Accel. problem.

I was just happening to look for more Nvidia drivers in Synaptic, and when I clicked on one of the files for a description, it had a small line of code.  I typed it in, and it worked.  The line is:

sudo nvidia-glx-config enable

Also, got Quake 3 to run like a dream.

Thank you all for your help.

-Rhemat

---

