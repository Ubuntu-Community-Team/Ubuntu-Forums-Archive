---
title: "Setting up media center on older pc: x hangs after post-install updates"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by damacy on 2009-10-14
Hello all,

I'm trying to set up an old computer as a media center in my living room. It has an Asus A7N8X motherboard, GeForce 5200 FX graphics card, 75gb hard disk space and 512mb ram. 

I've installed xubuntu successfully, but upon installing the updates afterwards, I lose the panel and cannot retrieve it. After rebooting, x seems to hang and I can't use anything desktop-related like the right-click menu. I've checked my xorg.conf file and changed the line in the device section to "nv" just in case it was using some proprietary drivers, but that doesn't seem to do anything.

Any thoughts? I'm not sure what the problem might be, so I'm having trouble diagnosing it, much less fixing it.

---

### Post by hal10000 on 2009-10-14
Try
[COLOR="Red"]sudo apt-get update[/COLOR] and [COLOR="Red"]sudo apt-get upgrade[/COLOR] fron the console, maybe the upgrade process was interrupted by strange reasons.

If X hangs the next time, gp to a console (STRG-ALT-F2) and do
[COLOR="Red"]sudo less /var/log/Xorg.0.log[/COLOR] and 
[COLOR="Red"]less ~/.xsession-errors[/COLOR] to see if you can find errors.

---

### Post by damacy on 2009-10-14
Hello again,

I ran apt-get and looked for updates/upgrades, but there were none.


When I ran "sudo less /var/log/Xorg.0.log" it returned a long list of actions, but none of them were warnings (except one about Cyrillic fonts) or errors.

The output I got from the command, "less ~/.xsession-errors" is attached in the corresponding file. It seems to be warning me that the Xserver is already running, and SELinux was found but is not enabled. There are also a couple of vague DEBUG statements. If anyone wants I can copy it inline, but I assume that everyone who's willing to help is a member here.


As an update, on my most recent reboot I get the following error:

[] Kernel panic -- not syncing: Attempted to kill init!

I had to hard shutdown and boot back in. It brought me back to the light-blue screen I get after xubuntu loads.

I should also note that any applications I managed to launch in the previous session eventually load when I restart the computer.

---

