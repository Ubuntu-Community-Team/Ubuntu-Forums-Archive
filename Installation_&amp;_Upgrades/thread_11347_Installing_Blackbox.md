---
title: "Installing Blackbox"
date: 2005-01-16
forum: Installation &amp; Upgrades
---

### Post by Sham on 2005-01-16
Hi all,

I've just made the jump from Fedora Core 3 to Ubuntu. So far its been great. I was a KDE user, but playing about with GNOME has inspired me to try other windows manager.

I used synaptic to install Blackbox, but it doesn't appear as a session option on the login screen. Could someone please tell me how to get around this?

Cheers

---

### Post by Ricapar on 2005-02-28
I would like to know this as well.

---

### Post by 471v3 on 2005-08-02
Damn, I got the same problem. Lol

---

### Post by GnuBee on 2005-08-06
The following is the blakbox.desktop located in /usr/share/xsessions it should apear in gdm sessions list now.


[Desktop Entry]
Encoding=UTF-8
Name=Blackbox
Comment=Highly configurable and low resource X11 Window manager
Exec=blackbox
Terminal=False
TryExec=blackbox
Icon=blackbox.xpm
Type=Application

[Window Manager]
SessionManaged=true

---

### Post by blu.gecko on 2005-08-06
I installed flux box by going to a term and typing in sudo apt-get install fluxbox
                                                                                password ***********
you might try "sudo apt-get install blackbox"

uninstall any blackbox packages prior to this! [-X 

(remember you have to reboot for all the gui setting to initallize)

but if I were you I would update your ubuntu to 5.0.4

hope this helps

---

### Post by blu.gecko on 2005-08-06
try this

sudo dpkg -r blackbox

sudo apt-get install blackbox

when it prompts you hit Y

reboot your pc

post results please. ;-) 







when it prompts you hit Y

---

### Post by n3trunner on 2005-08-16
here's what i got:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "netrunner"
/etc/gdm/Xsession: Beginning session setup...

(x-session-manager:7893): Gdk-WARNING **: locale not supported by Xlib

(x-session-manager:7893): Gdk-WARNING **: cannot set locale modifiers
SESSION_MANAGER=local/netrunner:/tmp/.ICE-unix/7893
/home/netrunner/.themes/Digital-Harmony/gtk-2.0/icons/iconrc:23: Unable to locate image file in pixmap_path: "gtk-bookmarks.png"
/home/netrunner/.themes/Digital-Harmony/gtk-2.0/icons/iconrc:24: Unable to locate image file in pixmap_path: "gtk-bookmarks.png"

i think the first 5 lines are the ones important/displayed in the error box....

---

### Post by Nelson Munz on 2007-03-09
I installed the blackbox 1-70-1.1ubuntu1 package with Synaptic.

You don't seem to need to create a configuration file to start up blackbox - You can start up the blackbox session by clicking the options button at the bottom left of the login screen and selecting a blackbox session... However....

When I started the x-terminal, I started getting a Cyrillic font (ie Russian font or Bulgarian font) instead of the western european ASCII type font.  This is probably a bug, (I'm not sure how to report bugs on the forums yet), So I followed GnuBee's post above and created a blakbox.desktop file located in /usr/share/xsessions with the following text in it


[Desktop Entry]
Encoding=UTF-8
Name=Blackbox
Comment=Highly configurable and low resource X11 Window manager
Exec=blackbox
Terminal=False
TryExec=blackbox
Icon=blackbox.xpm
Type=Application

[Window Manager]
SessionManaged=true

---

