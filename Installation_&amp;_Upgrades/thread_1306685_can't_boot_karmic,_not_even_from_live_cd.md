---
title: "can't boot karmic, not even from live cd"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by gsch on 2009-10-30
Hi. Upgraded from jaunty to karmic a few hours ago. Buggered up everything. Can't boot without pressing escape and choosing an older kernel. After boot from the older kernel, my mouse does not work. You can imagine the mission just to get to write this message. I downloaded the iso-image (without using the mouse) in the hope that I can save the system through the live cd ... same problem, won't boot. Seems like a dead end street. Please help. I'm not a linux geek, so don't use a bunch of jargon. I know what a terminal is though.
Acer Travelmate 2450 with ATI 200M if that matters.

Can I get the mouse going? Everything else seems to work. After that, I can remove the latest kernel with synaptic? Heeelp

---

### Post by gsch on 2009-10-30
sorry, I do not have a mouse. It is the touchpad that's not working. I repeat: heeelp

---

### Post by peabrane on 2009-10-30
I have the same problem with xubuntu on an ancient hp omnibook.

I haven't solved the boot problem but have managed to get the touchpad working. Using the keys, access settings>mouse and reset defaults. This is an icon but you should be able to tab to it and hit enter.

---

### Post by jhenager on 2009-10-30
> **gsch said:**
> sorry, I do not have a mouse. It is the touchpad that's not working. I repeat: heeelp

I could only suggest trying an older live CD. I don't work with laptops, but this machine is an Athlon 64 3200 on an old Winfast motherboard. No problems at all to speak of.

Have you tried using the Alternative CD? That might be something to try as well.

Best of luck getting it squared away.

---

### Post by gsch on 2009-10-30
I do not see any "reset defaults" icon under preferences>mouse. Checked in both tabs. Remember, this is karmic now. New gnome? New menus? Thanks for the replies.

---

### Post by gsch on 2009-10-31
No worries. I gave up on Karmic and went back to Jaunty. Took the opportunity to go over to ext4 and put my /home directory on a separate partition. I'll wait for the next LTS and stick with that, that would be 10.04, right? It is disappointing though that ubuntu would release a product with lots of fanfare that is not ready for the big time.

---

### Post by kfsorensen on 2009-11-13
I have the same problem, Karmic won't boot at all, not even in recovery mode.  But neither the Karmic nor the Jaunty CD work anymore, so even trying to roll back to Jaunty doesn't work.  Any suggestions?  I have Karmic installed on two other machines without this problem.  One installed the alpha version in early October, the other was a fresh install of Karmic a few days after release.  Both appear to be fine.  The one that's borked (and the one I really need to get working) had Jaunty and then auto-upgraded to Karmic on Oct.29.

---

### Post by gsch on 2009-11-24
I think it has something to do with grub2. I am not willing to hack my way out of this one. I'm tired of hacking. I see there is a daily build of Lucid Lynx. Would it be an option to install that?

---

### Post by dhavalbbhatt on 2009-11-24
> **gsch said:**
> I think it has something to do with grub2. I am not willing to hack my way out of this one. I'm tired of hacking. I see there is a daily build of Lucid Lynx. Would it be an option to install that?

I am sorry if I missed this - but have you tried doing a fresh install of Karmic? A fresh install is a better way to "upgrade" than the normal upgrade process.

---

