---
title: "Wacom Volito 2 not working properly"
date: 2011-10-25
forum: Hardware
---

### Post by ClaraMFerreira on 2011-10-25
Hello all!
First of all sorry if this issue has already popped up before, I'm afraid I might be repeating a thread like this. If there's a similar issue in a thread and it was solved, I don't mind being redirected. :)

My problem with my Wacom Volito 2 is that when I'm just hovering the pen over the tablet, without touching on it yet, it starts clicking a lot in the interface, sometimes it even shakes the cursor a bit while clicking on whatever option/window that is beneath it.
I tried to change manually the pressure over the System configuration, but in all pressure levels the result is always the same.

I use Ubuntu 11.10 currently, but back when I tried previous versions of Ubuntu (I think it was the 9), the tablet worked just fine so I'm guessing I'm missing a configuration here?

Thanks in advance for any help. :)

---

### Post by Favux on 2011-10-25
Hi ClaraMFerreira,

Welcome to Ubuntu forums!

With Oneiric you get GNOME 3.2 which has the initial Wacom tablet applet in System Settings.  It works through hooks that were added to the gnome-settings-daemon, but currently it only uses some of them.  The thing is the gnome-settings-daemon defaults will override any Options you set in an xorg.conf.d wacom.conf file or in xorg.conf.  So you need to install dconf-editor if it isn't already installed.  Then open it and go to org.gnome.settings-daemon.peripherals.wacom.  Under wacom you'll see the box for the tablet-pc-button isn't checked.  Check it.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)

Of course you could do the same thing with a xsetwacom command:
```
xsetwacom set "stylus device name" TabletPCButton on
```
Where you get the <device name> from *xinput list*.   See *man xsetwacom* in a terminal.

Hopefully the Wacom tablet applet will see some rapid development and soon will use all of the current hooks and hopefully more hooks are added.  Right now for example the pressure slider actually only works in increments of 25 (move it when you are also looking at the pressure in dconf-editor) which is pretty crude when you have the Wacom Bezier pressure curve available, see the demo here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#PressureCurve](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#PressureCurve)

---

### Post by ClaraMFerreira on 2011-10-26
Thanks for the help! :)

I can't confirm yet if it worked because I need to assure myself of something. I do not have the dconf-editor installed, going to the application center I found it under the package dconf-tools. Since it says it's not related to the older debian dconf, I just want to ask if it's the same thing?

---

### Post by Favux on 2011-10-26
I'm not sure because I don't know what the old Debian dconf package was.

I think the dconf configuration database that dconf-editor views is basically new with GNOME 3 and is replacing gconf and gconf-editor.

---

### Post by ClaraMFerreira on 2011-10-26
Well, installed it and my tablet is working pretty well now! Thanks! :D
The supposedly new dconf might have a newer interface then, but I guess it pretty much works the same way.

Again, thank you. :)

---

