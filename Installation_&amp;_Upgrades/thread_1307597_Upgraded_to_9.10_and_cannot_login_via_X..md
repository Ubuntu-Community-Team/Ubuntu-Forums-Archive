---
title: "Upgraded to 9.10 and cannot login via X."
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by cloverprince on 2009-10-31
I upgraded to 9.10 from Xubuntu 9.04 using the Update Manager.  It installed many new packages and removed some packages which is no longer officially supported.

After rebooting, I entered my username and password in the login screen (GUI).  The authentication was successful.  But then none of the panels, desktop and so on showed up. X seems restarted and it went back to the login screen again.

However, login via command line was possible by pressing ctrl+alt+f2.

I found a file named .xsession-error in my home directory.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=zh_CN.
Start IM through /etc/X11/xinit/xinput.d/zh_CN linked to /etc/X11/xinit/xinput.d/ibus.
current session already has an ibus-daemon.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7

** (gnome-screensaver:1831): WARNING **: Failed to get session presence proxy: Could not get owner of name 'org.gnome.SessionManager': no such name

(xfce4-panel:1849): xfce4-panel-WARNING **: xfce4-panel is not running
xfdesktop[1851]: starting up
Failed to init the UI: &#26410;&#30693;&#36873;&#39033; --sm-config-prefix
gnome-screensaver: Fatal IO error 104 (&#36830;&#25509;&#34987;&#23545;&#31471;&#37325;&#32622;) on X server :0.0.
xfce4-session: Fatal IO error 104 (&#36830;&#25509;&#34987;&#23545;&#31471;&#37325;&#32622;) on X server :0.0.
xfsettingsd: Fatal IO error 104 (&#36830;&#25509;&#34987;&#23545;&#31471;&#37325;&#32622;) on X server :0.0.
xfwm4: Fatal IO error 104 (&#36830;&#25509;&#34987;&#23545;&#31471;&#37325;&#32622;) on X server :0.0.
Thunar: Fatal IO error 104 (&#36830;&#25509;&#34987;&#23545;&#31471;&#37325;&#32622;) on X server :0.0.
xfce4-settings-helper: Fatal IO error 11 (&#36164;&#28304;&#20020;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
gnome-power-manager: Fatal IO error 104 (&#36830;&#25509;&#34987;&#23545;&#31471;&#37325;&#32622;) on X server :0.0.
xfce4-menu-plugin: Fatal IO error 104 (&#36830;&#25509;&#34987;&#23545;&#31471;&#37325;&#32622;) on X server :0.0.
The application 'xfce4-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'pidgin' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
linux-fetion: Fatal IO error: client killed
The application 'xfdesktop' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
```In case there are people who can't read Chinese:

In the line: Failed to init the UI: &#26410;&#30693;&#36873;&#39033; --sm-config-prefix
it is "unrecognized option" in English.

The message of Fatal IO error 104 is "connection reset by peer" in English.
And Fatal IO error 11 is "resources temporarily  unavailable"

The attachment is the output of "dpkg --get-selections" in case it may help.

What is wrong with it and how to fix it?

---

