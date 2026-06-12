---
title: "stuck at login line"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by magnum54 on 2009-11-05
Gave up on attempting to upgrade to 9.10 and re-installed 9.04 on a freshly formatted drive. On boot up it comes to Grub and I select the recent install and then it comes to a login line. I login and don''t know what to do next to get to the desktop.

---

### Post by jjcv on 2009-11-05
> **magnum54 said:**
> Gave up on attempting to upgrade to 9.10 and re-installed 9.04 on a freshly formatted drive. On boot up it comes to Grub and I select the recent install and then it comes to a login line. I login and don''t know what to do next to get to the desktop.

Hmmm, where there any error messages as it booted?

To start X you can simply type:

**startx**

If there are problems then the programm will write a logfile where you can look for what the issue is.

---

### Post by magnum54 on 2009-11-06
Thank you. I think the problem lies in having installed Ubuntu on two different drives. I appears to be trying to use the grub menu lst from both installs. 

A history; I had installed successfully 9.04 on Drive B and completed all the updates and found all the drivers. I had been using 9.04 for about 6 months when the suggestion to upgrade to 9.10 came up in the UPDATE MANAGER. I thought it may improve my graphics driver and improve the handling of video, so I did the upgrade. But, I was unable to even get to a command prompt. So I grabbed a CD with Ubuntu written on it and ran the install on Drive B. It worked great, except the CD had Ubuntu 8.10 on it and I couldn't get any updates. So I downloaded a fresh copy of 9.04 and created a CD and formatted and partitioned Drive A and installed 9.04. That is where I am at now. The Grub shows all the installs that have been done on Drive B, but wont load the new install on Drive A. I can boot up in Live CD and see the Menu.lst and the problems but don't know how to correct them. I will try STARTX.

---

