---
title: "display flicker after Jaunty upgrade on Averatec 2260-EY1 with VIA K8M890CE/K8N890CE"
date: 2009-05-02
forum: Hardware
---

### Post by librarian on 2009-05-02
After upgrading to Ubuntu 9.04 Jaunty Jackalope, my laptop display "flickers" - for a split second the display is displaced horizontally almost 800 pixels. Changing the screen resolution with "Configure display settings" does not fix the flicker. 

The laptop: Averatec 2260-EY1 (2200 series). The integrated graphics: VIA K8M890CE/K8N890CE [Chrome 9] (rev 01). It had taken me quite a while to get the display working at 1280x800 in 8.10. 

I'm poking around now, but if anyone has quick suggestions, I'd be happy to hear them.

---

### Post by MiguelMadrigal on 2009-05-06
Odd!  I have the exact same computer and have the exact same problem.  Unlike you, though, I had no trouble at all in 8.10 with the video (other than the resolution on the log-on screen, which was easy enough to solve).  I'm very new to Ubuntu (and Linux in general) and have been trying to a week to find a solution.

Help!!!

---

### Post by librarian on 2009-06-04
MiguelMadrigal, I still haven't fixed the flicker - have you had any luck?

---

### Post by pastalavista on 2009-06-04
I had this problem on one of my computers and was suggested to do this: In System > Preferences > Appearance, set Visual Effects to 'none'. Then reboot, select recovery mode, open a root termnal and enter ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and then reboot. It fixed mine, but I still can't handle any visual effects. My graphics card evidently isn't poweful enough.

---

### Post by smp1 on 2009-10-24
For what it's worth - I've just installed 9.04 on my 226,But0-EK1 with no problems. But, stalthis was a regular hard drive install. It

---

### Post by smp1 on 2009-10-24
For what it's worth - I've just installed 9.04 on my 2260-EK1 with no problems. But, this was a regular full install to my hard drive. Also I had resized the Windows partition and manually created the linux partitions when fresh installing Ubuntu.

---

