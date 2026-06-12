---
title: "Gnome Keyring Errors at startup"
date: 2009-03-21
forum: Hardware
---

### Post by Guus1982 on 2009-03-21
Im trying to get rid of some gnome keyring daemon errors (added below).
I also have some pulseaudio errors but i hope to have these solved with disabeling pulseaudio in the startup.

I tried a while to find a solution for this error but no luck so far. Reconfiguring the xserver in recovery mode didnt solve the problem: dpkg-reconfigure xserver-xorg

I had this errors on 32bit ubuntu as well as 64bit ubuntu (which im running now)

paste from auth.log: 

Mar 21 22:53:42 guus-laptop gdm[5714]: pam_unix(gdm:session): session opened for user guus by (uid=0)
Mar 21 22:53:42 guus-laptop gdm[5714]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Mar 21 22:53:42 guus-laptop gdm[5714]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar 21 22:53:42 guus-laptop gdm[5714]: Autolaunch error: X11 initialization failed.
Mar 21 22:53:42 guus-laptop gdm[5714]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar 21 22:53:42 guus-laptop gdm[5714]: Autolaunch error: X11 initialization failed.
Mar 21 22:53:42 guus-laptop gdm[5714]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar 21 22:53:42 guus-laptop gdm[5714]: Autolaunch error: X11 initialization failed.
Mar 21 22:53:42 guus-laptop gdm[5714]: )

---

### Post by Guus1982 on 2009-03-21
is this the right place or should i post this somewhere else in the forum?

---

### Post by Mlok on 2009-04-04
I am wondering about this too : it seems that keyrings questions are not very popular.
(mine is there : [http://ubuntuforums.org/showthread.php?t=1107094](http://ubuntuforums.org/showthread.php?t=1107094) )

Good luck.

---

