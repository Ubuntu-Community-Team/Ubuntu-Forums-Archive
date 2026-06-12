---
title: "wacom bamboo fun buttons"
date: 2013-05-28
forum: Hardware
---

### Post by LowFidelity on 2013-05-28
I have a rather old wacom bamboo fun cte-450 that I've recently been using with MyPaint. I've been trying to figure out how to get the buttons on the tablet to work so I can use them instead of having to undo, redo and such on the keyboard. I looked around at a lot of different places that talk about wacom mapping but I can't seem to get it to work still. Can anyone help?

---

### Post by ShadWolf on 2013-06-04
I'm having similar situation too! I have **Wacom Bamboo Fun and Touch CTE-450/W** but the button mapping isn't shown under **Settings > Wacom Graphics Tablet** as all it shows is blank and no way to add or configure button mappings for the tablet to use. I've tried installing Wacom Express Keys by writing out the script for putting under **/etc/init.d/** and even made it into a startup application then did a reboot, but to no effect it didn't work.

[ATTACH=CONFIG]243492[/ATTACH]

---

### Post by Favux on 2013-06-05
Hi,

What do they have?  Two buttons, one on each side of a scroll wheel?

I don't think there is a data file for those tablets in libwacom:  /usr/share/libwacom

I think I had one to submit somewhere but never did because the datafiles I submitted for the current Bamboo's have been pending for close to a year now.  The Gnome Wacom tablet configuration applet couldn't handle out of order buttons and Chris had made changes to the kernel driver a while back making the Bamboo Pen and Touch ExpressKeys out of order for what seemed like good reasons to him.

So you'll need to use a xsetwacom script and do it from the command line.  See:
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562) or [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

---

