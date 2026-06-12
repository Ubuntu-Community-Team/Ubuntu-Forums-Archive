---
title: "Changing the Menu Bar to 3 Icons"
date: 2008-09-13
forum: General Help
---

### Post by aaaantoine on 2008-09-13
This is likely a rare request, but I'd like to put it out there anyway.  I will preface it with the fact that I know there exists a "Main Menu" gnome panel applet that kinda does what I want, but it's not exactly what I'm looking for.

**I want to change the Menu Bar so that Applications, Places, and System are each represented by an icon instead of text.**

I don't want the single menu icon, because it nests Places and System as sub menus, and requires an extra click for each of them.  I want to get rid of the text because it's somewhat disorienting on a vertical panel.

1. Does this feature exist in the preinstalled software, maybe in gconf somewhere?
2. Failing that, has a third party programmed such a feature for the menu bar?
3. If not, where do I find the source code for the Menu Bar applet, so that I can try to tweak it myself?

I appreciate any help I receive on this matter.

On reading the help file (pff, who reads help files anyway? :-P), I found the following instructions:
> System menus: System menus contain the standard applications
and tools that you can use in the GNOME Desktop. The Applications menu and Actions menu are system menus. To add
a system menu to a panel, right-click on a launcher in the menu, then choose Entire menu &#9656; Add this as menu to panel. From these instructions, I figured out how to add Preferences and Administration menus to the panel... but not the entire System or Places menus.  Nevertheless, this is a step closer to what I had in mind.

---

### Post by aaaantoine on 2008-09-16
I put this in the completely wrong forum.  This should be in General Help and/or Programming.

I would really like to put in iconified menus for Applications, Places, and System.  I've created a compromise that's sort of a mess because it consists of icons for the Main Menu, Home, Pictures, Computer, a remote site, Preferences, and Administration.  I would still prefer the three icon idea I posted in the OP.

By the way: I checked the source code for gnome-panel.  The Menu Bar applet code isn't there.  In fact, the source code for only one or two applets can be found there.

Also, it doesn't appear to be in gnome-applets, either.  Unless one of these is it:
```
gnome-applets-2.22.2$ ls
accessx-status  COPYING                gswitchit            Makefile.am     omf.make
aclocal.m4      COPYING-DOCS           gweather             Makefile.in     po
AUTHORS         cpufreq                INSTALL              man             py-compile
battstat        debian                 install-sh           mini-commander  README
ChangeLog       depcomp                intltool-extract.in  missing         stickynotes
charpick        drivemount             intltool-merge.in    mixer           trashapplet
config.guess    geyes                  intltool-update.in   mkinstalldirs   xmldocs.make
config.h.in     gkb-new                invest-applet        modemlights
config.sub      gnome-applets.spec     ltmain.sh            multiload
configure       gnome-applets.spec.in  m4                   NEWS
configure.in    gnome-doc-utils.make   MAINTAINERS          null_applet

```

---

