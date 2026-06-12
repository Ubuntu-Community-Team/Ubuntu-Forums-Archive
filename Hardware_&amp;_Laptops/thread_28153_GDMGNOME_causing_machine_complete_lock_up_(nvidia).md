---
title: "GDM/GNOME causing machine *complete* lock up (nvidia)"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by gnovos on 2005-04-19
(This seems to be a problem with the nvidia driver)

So, the basic symtomps are as follows:

At certian radomish points right before/right after startup of GDM (or sometimes it makes it as far as loading a couple Gnome panels pas GDM sign-in) the machine locks up HARD. It ceases to respond to anything, and it not reachable on the network. The only way to fix it is to reboot and remove the nvidia driver (change back to nv).

When this happens right before GDM the screen just alternated shades of black (meaning it'll go "real" black, meaning off, then go "LCD" black, which is kind of a whitish-black, but still black.  if you get my meaning), but when it happens after that it's just frozen in place.  The mouse just sticks wherever it is and no further action can take place.

This happens whether I use the nvidia driver installed via apt OR if I compile/install it myself.

I can understand gnome locking up, but how can it lock up the entire machine? I have never seen this happen when i used fc3 before.

The card is some kind of PCI-Express Nvidia card on a P4 Prescott (3.2G)

I've tried all manaer of xorg alterations, renderAccell on/off, etc.  

One interesting thing is that sometimes I can get it to start up perfectly, only to fail on reboot.

All of this seemed to start when I tried to run glxgears, which caused the first lockup I saw, but that could have been a coincidence since I had not rebooted at that time since switching to nvidia driver.

---

### Post by BobFolkerts on 2005-04-19
I'm seeing the same thing after a clean install of 5.04.  I'm configured to dual boot (with XP) and I can run in the 'recovery mode', but once gdm starts to load, my computer just locks up.  The screen is showing a single _ in the upper left corner, but it doesn't respond to keyboard input so I just have to hit the power switch.  This isn't much help yet, but missery loves company ](*,)

---

### Post by NaplesBill on 2005-04-19
You should try setting the video driver to "vesa" and if it works you will atleast have a working system to troubleshoot/test further from.  Run "recovery mode" and then edit /etc/X11/xorg.conf.  I use nano for text editing.  The command should be:

nano /etc/X11/xorg.conf.

---

### Post by Jvaldezjr on 2005-04-30
Do you have the nvidia-glx drivers installed?  It took me a while to figure out that was what was locking up my machine intermittenly.  I would be able to move my mouse, but everything else stopped responding.  It sucks because the glx drivers work nicely with my GeForce 4 card, but about 3 times a day I have to force a rebbot because it locked up.  So I just uninstalled the glx drivers- and I havent had a problem since.

**I never had a problem getting past GDM- my machine locked up after I was already logged in and doing stuff...ie surfing, gaming, coding, etc.

---

### Post by rosslaird on 2005-05-01
If you're running the latest nvidia drivers (7174, which you cancheck in nvidia-settings), there are a number of hard-lock bugs. My system, for example, works fine in gdm but locks hard in xfce. There is no way to fix these bugs (yet) except to downgrade to the 6* series drivers. The nvidia forums have a bunch of info about this.

Ross

---

### Post by Bil-E-daKid on 2005-05-02
Hey there guys,

The other way to fix this is to install the xfree86 package and start using that again. I had to do that at work on an SMP machine and now - no more hard locks at login (and then you can still use the Nvidia drivers!)

;-)

---

