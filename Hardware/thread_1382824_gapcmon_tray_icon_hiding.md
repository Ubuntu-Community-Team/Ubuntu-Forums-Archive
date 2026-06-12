---
title: "gapcmon tray icon hiding"
date: 2010-01-16
forum: Hardware
---

### Post by Timothy Taylor on 2010-01-16
I have an APC UPS running with apcupsd and the gapcmon GUI.

Although gapcmon is running, the icon no longer appears in the "notification area" of the top panel.  If I hover the mouse pointer over the left end of the notification area, the gapcmon status box appears and if I click there, the gapcmon information window opens.  It seems as though gapcmon is no longer displaying the tray icon.  I notice that the other icons (network, audio) "twitch" when I open apcupsd, or change the state of gapcmon's "show tray icon" checkbox.

I tried removing the top panel and deleting the hidden .gconf and .gconfd folders to reset this, but the hidden icon problem persists.

Any ideas?

---

### Post by DonAtConnServe on 2010-01-23
For what it's worth, when I start gapcmon from a terminal I get the following message.
[INDENT]** Message: gapc_util_load_icons(Unable to find icons) emsg=--load failed!
[/INDENT]System Monitor (or ps -eaf | grep gapcmon) indicates that it's running, so it appears to have misplaced its icons. It's in the notification tray (once that option has been selected), but it's just a blank space. Kind of stealthy, really.

---

### Post by DonAtConnServe on 2010-01-23
I poked around a bit more and found that if you build from the source instead of using the package, the icons show up. The thread below gives more details.

[http://sourceforge.net/projects/gapcmon/forums/forum/531517/topic/2638364](http://sourceforge.net/projects/gapcmon/forums/forum/531517/topic/2638364)

I had to install the libgtk2.0-dev and the libgconf2-dev packages for the configure script to complete successfully, but that was the only hiccup. I now have the icons showing up in the notification tray (and in the app windows, too, for that matter).

---

### Post by crunch256 on 2010-11-22
Thanks for posting your resolution.

I was having a similar problem with a new install of gapcmon (Lucid, amd64)... I couldn't start the app after enabling the TrayIcon option. Running from the command line  gave several error, starting with:
** Message: gapc_util_load_icons(Unable to find icons) emsg=--load failed!

I built/installed version 0.8.9 (after installing the "-dev" versions of gconf and gtk2.0) like you suggested, and everything is working great.

---

### Post by deadite66 on 2011-01-15
if you convert the rpm on sourceforge with alien i get they show up in the tray ok.

---

### Post by sinned72 on 2011-02-26
I noticed this issue and the error mentioned under Debian Squeeze as well. I solved this a slightly different way since I noticed the icons are already made before compilation.

Under Debian they are installed in /usr/share/icons/gapcmon however the INSTALL file with the source tarball indicate ${_datadir}/pixmaps. I then created hard links for each file in the /usr/share/icons/gapcmon folder inside /usr/share/pixmaps:

```

ln ../icons/gapcmon/apcupsd.png apcupsd.png
ln ../icons/gapcmon/charging.png charging.png
ln ../icons/gapcmon/gapc_prefs.png gapc_prefs.png
ln ../icons/gapcmon/onbatt.png onbatt.png
ln ../icons/gapcmon/online.png online.png
ln ../icons/gapcmon/unplugged.png unplugged.png

```Those commands were executed in /usr/share/pixmaps as the root user.

I know this is a slightly older topic but this seemed like a useful alternative to add. Also, it solved a different problem I was having related to the program not display after launch as a normal user (apparently it was launching but no icons meant I could not see it.)

Cheers.

Dennis

---

### Post by Thad E Ginathom on 2011-05-09
sinned72, thank you very much for that fix. I have just used it under 10.04, and I have icons now.

Excellent --- and so easy to do. Thanks.

---

