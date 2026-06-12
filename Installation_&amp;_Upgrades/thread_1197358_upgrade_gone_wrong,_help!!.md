---
title: "upgrade gone wrong, help!!"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by ShapeShifter499 on 2009-06-26
Ok I was doing a rotine update and upgrade on my system when.....I HAD A ERROR, my netbook froze, not knowing what to do I restarted. Now some packages will not configure correctly. ```
 python-wnck
 python-gnomeapplet
 python-mediaprofiles
 python-evince
 python-gtksourceview
 python-totem-plparser
 python-gnome2-desktop
 python-evolution
 python-gtop
 python-gnomeprint
 python-gnomedesktop
 python-gnomekeyring
 python-rsvg
 python-metacity
 python-nautilusburn
 python-bugbuddy

```So I ran. ```
sudo dpkg --configure -a
```And I got. ```
lance@acer-netbook:~$ sudo dpkg --configure -a
Setting up python-wnck (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-wnck (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gnomeapplet (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gnomeapplet (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-mediaprofiles (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-mediaprofiles (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-evince (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-evince (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gtksourceview (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gtksourceview (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-totem-plparser (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-totem-plparser (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python-evince (>= 2.26.0-1ubuntu2); however:
  Package python-evince is not configured yet.
 python-gnome2-desktop depends on python-gnomeapplet (>= 2.26.0-1ubuntu2); however:
  Package python-gnomeapplet is not configured yet.
 python-gnome2-desktop depends on python-gtksourceview (>= 2.26.0-1ubuntu2); however:
  Package python-gtksourceview is not configured yet.
 python-gnome2-desktop depends on python-mediaprofiles (>= 2.26.0-1ubuntu2); however:
  Package python-mediaprofiles is not configured yet.
 python-gnome2-desktop depends on python-totem-plparser (>= 2.26.0-1ubuntu2); however:
  Package python-totem-plparser is not configured yet.
 python-gnome2-desktop depends on python-wnck (>= 2.26.0-1ubuntu2); however:
  Package python-wnck is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up python-evolution (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-evolution (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gtop (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gtop (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gnomeprint (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gnomeprint (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gnomedesktop (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gnomedesktop (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-gnomekeyring (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-gnomekeyring (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-rsvg (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-rsvg (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-metacity (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-metacity (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-nautilusburn (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-nautilusburn (--configure):
 subprocess post-installation script returned error exit status 2
Setting up python-bugbuddy (2.26.0-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-bugbuddy (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python-wnck
 python-gnomeapplet
 python-mediaprofiles
 python-evince
 python-gtksourceview
 python-totem-plparser
 python-gnome2-desktop
 python-evolution
 python-gtop
 python-gnomeprint
 python-gnomedesktop
 python-gnomekeyring
 python-rsvg
 python-metacity
 python-nautilusburn
 python-bugbuddy
lance@acer-netbook:~$ 

```So now what, anyone know what to do? :confused:

I have a Acer Aspire One 8.9 model with 120 gb and built in wifi. The operating system on it is Ubuntu Karmic Koala 9.10 Alpha 2 with UNR, Ubuntu studio, Kubuntu, Xubuntu, and Super Ubuntu add-ons.

---

### Post by ShapeShifter499 on 2009-06-26
*bump*

---

### Post by ShapeShifter499 on 2009-06-26
*BUMP* Anyone?

---

### Post by Sef on 2009-06-26
Wait 24 hours with no reply before bumping your thread.  Sooner can get you an infraction or warning.   Thank you.

---

### Post by ShapeShifter499 on 2009-06-26
oh, I did not know, sorry :oops:

---

