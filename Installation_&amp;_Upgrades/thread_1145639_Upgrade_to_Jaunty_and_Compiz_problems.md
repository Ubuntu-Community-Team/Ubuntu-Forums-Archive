---
title: "Upgrade to Jaunty and Compiz problems"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by jlbr21 on 2009-05-01
OK, so I spent all day yesterday upgrading to Jaunty, I spent all day today trying to fix all the issues that came with it. Anyhow, one of the last problems I got is compiz, everytime I start the computer, I get the message that the display is not composited, and that I need to enable compiz. When I run compiz in the terminal, it gets stuck and does nothing. Output here:

juanluis@juanluis-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png


I heard also something about Intel graphic cards and Jaunty not working very well due to some bugs. Anybody know something about that?

---

### Post by DracoJesi on 2009-05-01
no, I haven't, but try this, it's a diagnostics tool for Compiz...

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by jlbr21 on 2009-05-01
OK; thanks but according to that little application, compiz is running fine, still, I get that message everytime I start my computer, and when i run compiz on the terminal, it gets stuck. I must add that compiz runs fine when i run it on the terminal, however, I have to terminate the terminal and the process it is performing.

Strange.

---

### Post by MickS on 2009-05-04
I have the same problem it gets stuck at the same point. I just close the terminal on the little cross and compiz runs fine until next boot when I have to do the same again.
I looked in the folder /usr/share/gdm/themes/Human/ubuntu.png and ubuntu.png doesn't exist, could that be the problem? If so how to get and install ubuntu.png?

Mick

---

### Post by jlbr21 on 2009-05-04
What I do now is run compiz by way of F2+Alt, then there is no terminal hanging. I added it to the start-up applications as well. Let's see if it runs smoothly next time I start the computer.

Cheers.

---

### Post by MickS on 2009-05-14
Any body got a proper fix yet?

Mick

---

### Post by RavanH on 2009-05-14
Just some thoughts: what if you switch to a completely different theme and icon set? What happens when you disable Desktop Effects then log out and back in again? And what if you install Fusion-Icon?

---

