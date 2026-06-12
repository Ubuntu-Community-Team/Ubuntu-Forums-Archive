---
title: "Graphical environment doesn't start before, after install"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by PacSci on 2009-03-03
I am trying to install Intrepid onto a Dell OptiPlex GX260 desktop, that was already running WinXP with no more problems than any Windows computer has. When I tried to boot from the Live CD to install, I simply received a black screen on which I could move a mouse pointer, but that was it. (I had used the CD to install Ubuntu on another computer just a few days beforehand, and it worked perfectly.)

So, after that, I decided to just directly install Ubuntu from the option that says "Install Ubuntu" (or something like that), and the installation worked fine - the background appeared, the GUI installer worked, and Ubuntu was apparently installed. I restarted, and was able to log in using GDM. After that, though, I only got the same black screen. I rebooted again, but didn't even get to GDM.

Does anyone have an idea of what might be going on? It's probably a computer issue, but I'm not sure what the nature of the problem is (probably related to GNOME, though, because it could start the GUI installer but not the GNOME desktop). Do you think that installing Xubuntu might work?

---

### Post by overdrank on 2009-03-03
Hi and it would appear that you have a ATI graphics card. You may try and boot into recovery mode and use the xfix option to help with the graphics. Recovery mode is usually the second choice from the grub when booting. After the xfix is complete you should be given the option to boot normally.
How much memory does the system have?

---

### Post by PacSci on 2009-03-03
Okay, I ran xfix. Now, I can log in with GDM, and I don't get a black screen. Problem is, now I'm stuck on a *beige* screen on which I can move the mouse cursor, and GNOME's still not starting. Any suggestions?

---

### Post by Hockey21 on 2009-03-05
Any resolution for this problem? 

I also have a Dell OptiPlex GX260 desktop with 1 GB memory. I ran 8.04LTS for some time now on this machine. I performed a new install of 8.10 instead of doing an upgrade. I'm only running Ubuntu on the desktop.  

I have the exact same problem as described in the original post.

Thanks for any help!

---

### Post by yjcho on 2009-03-05
Unfortunately, I am having the same problem. I even posted my question, but no answer was given.
I think it must be a big problem.  Even though GRUB works fine, after login, nothing is shown except that I can move my mouse!!! Please give us an answer!!!:(

---

### Post by IsmailBhai on 2009-03-06
there are alot of graphics problems with intrepid.  what kind of errors are you getting in the xorg log?  if it's error setting mtrr you can follow this guide: [http://hydtech.wordpress.com/2009/02/26/gnome-display-manager-problems-error-setting-mtrr-in-ubuntu-intrepid-810/]("http://hydtech.wordpress.com/2009/02/26/gnome-display-manager-problems-error-setting-mtrr-in-ubuntu-intrepid-810/")

---

### Post by Hockey21 on 2009-03-06
Thanks for the reply. I took a look at my Xorg log file and found the following 2 lines repeated hundreds of times on the tail end. 

[mi] mieqEnequeue: out-of-order valuator event; droping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.

---

