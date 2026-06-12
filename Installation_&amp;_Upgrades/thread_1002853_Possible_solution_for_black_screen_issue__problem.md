---
title: "Possible solution for black screen issue / problem"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by mpadams on 2008-12-05
Based on reading forum posts and my own difficulty with Intel video chipsets, as well as using some scripts to standardize an install, the following should get a lot of people going, I hope.

1. Get into failsafe mode: hit ESC at boot and choose a failsafe kernel; go to the root prompt when able. 
2, Get rid of Compiz, completely: **sudo apt-get -y remove compiz***
3. 8.10 seems to default to a blank xorg.conf: run **Xorg -configure** and move the file it creates to **/etc/X11/xorg.conf**
4. Make sure you have a .gnome2 directory in your home folder: r**m -fr /home/(username)/.gnome2** ; **mkdir /home/(username)/.gnome2** ; [B]chown (username):(username) /home/(username).gnome2
[/B]
5. Reboot normally, then make sure you've chosen a GNOME session in the bottom-left corner menu (set as default if asked).

---

