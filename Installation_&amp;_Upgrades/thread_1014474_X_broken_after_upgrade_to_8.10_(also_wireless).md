---
title: "X broken after upgrade to 8.10 (also wireless)"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by Ben Branch on 2008-12-17
Upgraded my laptop (generic with ATI radeon 350 video) from 8.04 to
8.10. Now I get the notorious "kinit can't find image" message. If I
try "startx", the X server core dumps (signal 11) inside radeon.o.
Can't go back to glfrx unless I go back to 8.04. I have tried
various suggestions, including

dpkg-reconfigure -phigh xserver-xorg
apt-get install gnome
apt-get install ubuntu-desktop

Nothing changes the behavior.

Oh, and my wireless stopped working, only ethernet works.
(Atheros chipset).

:confused:

---

### Post by Ben Branch on 2008-12-17
The "live CD" works OK, so something in the upgrade didn't work.

---

### Post by Ben Branch on 2008-12-17
I had to do a complete remove and re-install:

sudo apt-get remove xserver-xorg ubuntu-desktop
sudo apt-get install xserver-xorg ubuntu-desktop

Now my GDM/X11 is working OK (although it seems a little slow).
I'll test other things, including wireless, tomorrow.

---

### Post by luoenzhen on 2008-12-18
Backup all home folder and any files you don't want to reinstall;
Fresh install 8.10 and copy back the home folder.

---

### Post by Ben Branch on 2008-12-18
Well, everything is working now, but all things considered, being forced
to use the "radeon" driver feels like a step backwards. As I reported
earlier, using apt-get to remove & install xserver-xorg (which forced a
remove and install of ubuntu-desktop as a dependency) allowed X to start.

Issues:
1) video is slower. Yes, the upgrade script warned me that it might be.
   (Didn't warn me that it wouldn't function at all!). Of course, my
   350 chip wasn't fast enough for gaming anyway, but now long scroll
   lists can react choppily. It's usable, though.
2) After boot and before painting the login screen the video paints the
   top third of the screen in noise and bottom two-thirds with my previous
   session's wallpaper/desktop. This lasts for about a second.
3) My previous xorg.conf had been customized so that pressure on the
   touchpad would *not* be interpreted as a button click (the touchpad
   has two buttons already and the touchpad was way too sensitive). Well,
   the sufficient-pressure-is-a-click is back, and my old method to
   remove it does not work. (synaptics touchpad). The touchpad is less
   sensitive than before so I may be able to live with this, but it was
   another unexpected shock.
4) Bringing up gnome (panels, applets, etc.) is noticeably slower.

Side effects of the fix: I was using wicd to manage the network
connections, but the reinstall of ubuntu-desktop blew that away. I've
got it working again, but the interactions between the Network Manager
applet, Administration > Network, and Preferences > Network Configuration
is confusing to say the least (wicd seems much cleaner, but NM is working
for now and I have other things to do.)

---

