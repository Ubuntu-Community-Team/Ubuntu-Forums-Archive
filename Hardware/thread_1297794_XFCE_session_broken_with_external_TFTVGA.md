---
title: "XFCE session broken with external TFT/VGA?"
date: 2009-10-22
forum: Hardware
---

### Post by kawazu on 2009-10-22
Folks;

running Ubuntu 9.10 beta, GNOME and XFCE installed, on a Toshiba Tecra notebook, partly working with the machine "standalone", partly (at the office) having it attached to a docking station with an external TFT / VGA display.

The external display seems a little flaky relating to Linux compatiblilty, needed to add a custom modeline to xorg.conf to have it working using the desired resolution (1280x1024 @ 75Hz), plus this resolution never was automatically restored when rebooting the machine into X. So far, using 9.04 I merrily used a bash script wrapping xrandr to, after logging in to XFCE, fix this problem and restore the desired resolution.

After upgrading to 9.10, I saw a few problems about that:

(a) Initially, my xrandr wrapper script didn't work anymore. Resolution wasn't switched. 

(b) However, for the first time using my hardware, I was capable of setting the "right" resolution (in both GNOME and XFCE) using the screen properties configuration panel. Good.

(c) By now, the machine boots into a bad default resolution when connected to the external VGA, but as soon as I log in to GNOME, the "right" resolution is correctly restored. Good.

(d) Bad, however: as soon as I log in to XFCE, there are two things that could possibly happen: Either the external TFT goes "No signal" followed by an "Out of range" message, blacking out, leaving my only choice to reboot the machine and try again. Or, it goes "no signal" for a few seconds to then fall back to GDM, leaving (according to .xsession-errors) me with the impression that the X server died all of a sudden, leaving none of the XFCE apps capable of connecting to it.


So to ask:

- Is XFCE in Xubuntu 9.10 also trying to restore its screen resolution on login?

- If so, how to fix this behaviour in my situation (given it works pretty flawless in GNOME, I assume my display generally works, but I don't want to work with GNOME full time :) ).

TIA and all the best,
Kristian

---

### Post by s.jegen on 2009-11-04
Hey ho!

I'm running Xubuntu and was just upgrading to the official version 9.10 from 9.04 when I run into some problems with my XFCE-sessions.

At first everything ran smoothly it just happened sometimes, that my screen resolution didn't correctly fit the screen. A short correction to the Display Settings solved the problem though.

But then, suddenly after starting 9.10 for the 15th time or so, gdm did not let me log into my usual XFCE-session anymore. I would put in my PW as always and after a short loading time (with the nice new splash screen) it just fell back to the graphical gdm login. A look at the .xsession-errors showed me the following:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/silvan/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/scim-bridge.
Smart Common Input Method 1.4.9

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
/usr/bin/startxfce4: X server already running on display :0
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.9

xfdesktop[2139]: starting up
Starting SCIM as daemon ...
SCIM has been successfully launched.

(xfce4-panel:2141): xfce4-panel-WARNING **: xfce4-panel is not running
Failed to init the UI: Unknown option --sm-config-prefix

** (evince:2153): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

(xfce4-mixer-plugin:2171): Gtk-WARNING **: cannot open display: :0.0
xfce4-settings-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfwm4: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-session: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfsettingsd: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Thunar: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfdesktop: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-power-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-menu-plugin: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
xfce4-places-plugin: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
evince: ../../src/xcb_io.c:378: _XAllocID: Assertion `ret != inval_id' failed.
libnotify-Message: GetServerInformation call failed: Connection was disconnected before a reply was received
libnotify-Message: Error getting spec version
The application 'pidgin' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

Since I didn't shut down any programs there seems to be a connection problem with the X-Server. Because I'm able to start an lxde-session without problems though, the XFCE-session configuration seems to be the culprit. Seeing that I didn't change any configs prior to this problem occurring I think it fits this topic even though I'm not using an externel TFT/VGA.

Does anyone have an idea to get my XFCE-session working again? :-)

---

### Post by ioulianos on 2009-11-11
from console start  xcfc-session and it will start your session
If you have checked automatic login in apps/settings/login win , uncheck it
Try it, it worked for me
Theo

---

### Post by s.jegen on 2009-11-12
I can start a working xfce-session by going through tty1 and starting it with 'startxfce4', but I can't find the login settings under the Applications/Settings Menu? Is there a console command I could use instead?

Thaanks for your reply anyway!

---

### Post by seagullsaregreat on 2009-12-22
I have the same problem.
i cant log into my computer via gdm. but heres a new twist: if i add a new user from tty, that user _can_ login..
and the other actions that helped above don't work for me.
> apps/settings/login
for me its apps/system/login

---

