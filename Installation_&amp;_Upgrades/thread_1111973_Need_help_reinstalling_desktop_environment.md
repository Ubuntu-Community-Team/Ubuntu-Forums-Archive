---
title: "Need help reinstalling desktop environment"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by xaos on 2009-03-31
I have a dual boot with WinXP and what used to Kubuntu. Because my laptop is getting old and KDE4 is kind of heavy I decided to migrate to ubuntu 8.10 and chose to do a fresh install over my kubuntu partiton.

see also:
[[COLOR="Blue"]_this topic_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1110926")
To keep a long story short: I ran into some problems because my CDROM drive is apparently not working very well. I can boot to WinXP without problem, when I boot to Ubuntu, screen resolution is 800x600, and when I shutdown the laptop, the screen just goes black and becomes non-responsive, I have to manually shutdown. If I boot from live CD everything seems to work fine and I have my native resolution (1280x800), but often the CD hangs when trying to boot... I checked the CD, it's fine, I even used it to install ubuntu on my old PC without problems.

I would like to reinstall the desktop environment, but want to avoid reinstalling ubuntu from CD because of previous issues. How can I achieve this from commandline? What exactly do I need to reinstall, Gnome? X11? something else?

Please of you reply can you provide the commands I should give? Thanks a lot in advance...

---

### Post by lindsay7 on 2009-03-31
Maybe you could try the 9.04 beta?

Upgrading from Ubuntu 8.10

To upgrade from Ubuntu 8.10, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.04' is available. Click Upgrade and follow the on-screen instructions.

---

### Post by xaos on 2009-03-31
Thanks for the reply, I will give it a shot. I don't need to add repositories to enable the upgrade to 9.04beta?

---

### Post by lindsay7 on 2009-03-31
no

---

### Post by xaos on 2009-04-01
Ok, I upgraded successfully to 9.04beta, which got rid of the shutdown problem. My resolution is still at 800x600 though. I tried editing my /etc/X11/xorg.conf file, but so far it either doesn't do anything or it results in a nonfunctional file.

Any ideas? I have a compaq presario r3000, the screen is a widescreen with native resolution 1280x800, according to the label on the laptop my graphics card is ATI mobility radeon 9000 IGP

Any help would be greatly appreciated...

---

