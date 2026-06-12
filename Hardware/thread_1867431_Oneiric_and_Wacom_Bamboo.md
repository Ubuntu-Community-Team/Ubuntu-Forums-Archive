---
title: "Oneiric and Wacom Bamboo"
date: 2011-10-22
forum: Hardware
---

### Post by jejones3141 on 2011-10-22
Was Oneiric tested with Wacom devices?

I've just upgraded my wife's computer to Oneiric after a week spent with my and a friend's computer, upgrading and learning how to hide the existence of GNOME 3 to the extent possible--and it is unusable, I believe because her pointing device of choice is a Wacom Bamboo.

We've observed the following:

1. Clicking on a window to move it and finding ourselves unable to release it.
2. Being unable to span the workspace with a sweep of the mouse across the pad--I think this is because the mouse acceleration was set to zero behind our backs with the upgrade.
3. Being unable to adjust sliders, such as acceleration.
4. Jerky movement of the mouse cursor.
5. Non-existent clicks being reported when simply moving the mouse around.

The tablet and hence the computer is unusable in this state, so we'll end up getting a trackball pending a fix--but then she won't be able to do graphics work in the manner to which she's become accustomed. Next stop, Launchpad.

UPDATE: for anyone else with a Wacom device, looks like this is [Bug #863154]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154").

---

### Post by Favux on 2011-10-22
That be the bug alright.

Also be aware that there are now hooks for Wacom in the gnome-settings-daemon and GNOME 3.2 has the first version of the Wacom tablet control panel applet (in System Settings) which makes partial use of them.  The daemon takes precedent over any static Options you set in a wacom.conf or xorg.conf so if you can't change it with the Wacom tablet applet or dconf-editor you need to use a xsetwacom command.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)

---

### Post by royleith on 2011-10-27
@ Favux

Just did a new install of Kubuntu. I thought I would try the Bamboo Touch. 

I am astonished! It is perfect. I can use it like a monster touchpad on my laptop, but when I rest my wrist on the pad and use the pen, it works in absolute positioning as a graphics tablet.

I need to delete my old scripts to turn touch on and off.

I tried to use the KDE tablet prefs tool (I don't know why, perhaps 'cos it was there), but it says to start the Wacom daemon. I don't think I will bother with it. It's perfect as it is.

After all the old flaky versions I was beginning to lose heart. This is such a wonderful surprise. 

Thank you so much, Favux.

Regards
Roy Leith

---

### Post by Favux on 2011-10-27
Hi Roy,

I'm happy to hear it is working well for you now!

I'd like to take the credit but it is possible there were a few other folks involved.  ;)


@ jejones3141, FYI update:

The flying window & Button 1 1 bug was found and fixed today. Should be submitted and committed shortly, with luck.  If you use a xsetwacom set command assigning Button 1 1 to stylus or eraser you are unable to left click (select things) with the stylus tip and releasing windows you've grabbed with the stylus tip fly off.  So either, since it is the driver default, don't use xsetwacom to assign Button 1 1 for now or clone xf86-input-wacom when the fix is committed.

Or you could simply fix it in the xf86-input-wacom source code and then compile it.  A button release function was missed in the switch over to valuators.  In wcmCommon.c around line #258 change:
```
						xf86PostButtonEvent(pInfo->dev,
```
to
```
						xf86PostButtonEventP(pInfo->dev,
```
So it reads like:
```
 					if (countPresses(btn_no, &keys[i], nkeys - i))
						xf86PostButtonEventP(pInfo->dev,
 								is_absolute(pInfo), btn_no,
 								0, first_val, num_val,
 								VCOPY(valuators, num_val));
```
Yep, it was a 'P' that was left out.

---

### Post by jejones3141 on 2011-10-27
That's excellent news--thanks!

---

### Post by jejones3141 on 2011-11-07
Sad to say, looking at [http://www.ubuntuupdates.org/packages/show/360056](http://www.ubuntuupdates.org/packages/show/360056) looks like the bug fix has yet to make it in.

---

### Post by jejones3141 on 2011-11-30
Hi! Since the fix was indeed committed on November 15th, if I read [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=20958f84eef0b40f91e4559099f342f28650c183](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=20958f84eef0b40f91e4559099f342f28650c183) rightly, and since the official repositories have yet to include it, I guess I will indeed have to compile it myself.

The way to go, I would think, would be to generate a .deb file that I can install on my computer, my wife's, and my sister's. Time to go look up how to do that.

---

### Post by Favux on 2011-11-30
No, you're good.  The fix is in the new xf86-input-wacom-0.12.0 tar release:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/)

See:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog)


Edit:  Oh, you meant Ubuntu repositories.  Very unlikely that will happen.  So yes you do need to compile it.  See either the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or the [LinuxWacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  To generate a deb consider using checkinstall.

---

### Post by jejones3141 on 2011-12-09
> **Favux said:**
> No, you're good.  The fix is in the new xf86-input-wacom-0.12.0 tar release:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/)
Edit:  Oh, you meant Ubuntu repositories.  Very unlikely that will happen.  So yes you do need to compile it.

Thanks much--I'll check that out. Do you really think it unlikely? It's hard for me to believe that Canonical would blow off users of what as far as I can tell are the most popular graphics tablets for six months... but then it was hard for me to believe that they'd release Oneiric with that blatant a bug, too.

---

### Post by Favux on 2011-12-09
[QUOTE=jejones3141]Do you really think it unlikely? It's hard for me to believe that Canonical would blow off users of what as far as I can tell are the most popular graphics tablets for six months... [/QUOTE]
From their point of view 6 months is no big deal.  It has to do with their release cycle and when they allow new stuff in and when they have a feature freeze so they can try and get everything working and stomp bugs.  They don't want to introduce kernel changes etc. that might cause unintended regressions in other stuff.  There's all kind of literature on their schedule and approach and what not.

---

