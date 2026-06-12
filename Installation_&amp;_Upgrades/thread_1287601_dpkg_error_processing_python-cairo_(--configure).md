---
title: "dpkg: error processing python-cairo (--configure)"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by ronaldv on 2009-10-10
I did an 8.10 to 9.04 ubuntu upgrade via the upgrade manager but it failed on me somehere midway with this message (and lots more after this):

```
2009-10-08 18:38:48,912 ERROR got an error from dpkg for pkg: 'ufw': 'subprocess post-installation script returned error exit status 1
'
2009-10-08 18:38:48,952 DEBUG running apport_pkgfailure() ufw: subprocess post-installation script returned error exit status 1

2009-10-08 18:38:49,028 ERROR got an error from dpkg for pkg: 'ufw': 'subprocess post-installation script returned error exit status 1
'
2009-10-08 18:39:39,585 ERROR got an error from dpkg for pkg: 'python-cairo': 'subprocess post-installation script returned error exit status 1
'
2009-10-08 18:39:39,586 DEBUG running apport_pkgfailure() python-cairo: subprocess post-installation script returned error exit status 1

2009-10-08 18:39:39,612 ERROR got an error from dpkg for pkg: 'python-cairo': 'subprocess post-installation script returned error exit status 1

```

Now when I boot the upgrade system the gnome-gui is completely a mess. When I try to fix this by booting into recovery mode I get these errors:

- when auto-fixing the gui:

```
package xserver-xorg is incomplete or not installed
```

- when running dkpg-reconfigure:

```
Setting up python-cairo (1.4.12-1.2ubuntu1) ...
file does not exist: /usr/lib/python2.5/site-packages/cairo/__init__.py
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-cairo (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-cairo (>= 1.0.2-1.1); however:
  Package python-cairo is not configured yet.

.......[lot more]......

dpkg: too many errors, stopping
Errors were encountered while processing:
 python-cairo
 python-gtk2
 python-gnome2
 python-glade2
 python-gnome2-desktop
 deskbar-applet
 libdeskbar-tracker
 python-gmenu
 gnome-menus
 python-apt
 ubuntu-system-service
 gnome-control-center
 gnome-session
 gnome-about
 gnome-panel
 gnome-applets
 python-imaging
 hplip
 gnome-applets-dbg
 command-not-found
 python-newt
 ufw
 update-manager-core
 alacarte
 python-launchpad-bugs
 python-problem-report
 python-apport
 apport
 apport-gtk
 python-xapian
 apt-xapian-index
 python-gst0.10
 python-gtkhtml2
 python-sexy
 gnome-app-install
 python-vte
 apturl
 checkbox-gtk
 computer-janitor
 computer-janitor-gtk
 devede
 epiphany-extensions
 fast-user-switch-applet
 hpijs
 foomatic-db-hpijs
 gcompris
 gdebi-core
 gdebi
 python-qt4-common
 python-qt4
 python-kde4
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I tried to re-start the upgrade by running 'apt-get upgrade' with the 9.04-cd in the drive but this has no result.

How to proceed on this?
How can I force apt-get to continue where it failed?

Hope to hear from you, Ronald

---

### Post by Partyboi2 on 2009-10-11
Hi, boot into recovery mode and try
```
dpkg --configure -a
apt-get -f install
```
then if that clears the problem
```
apt-get update
apt-get upgrade
```

---

### Post by ronaldv on 2009-10-11
I tried 'dpkg --configure -a'; that runs fine but does not solve anything.

'apt-get -f install' give the same errors as listed above:

Setting up python-cairo (1.4.12-1.2ubuntu1) ...
file does not exist: /usr/lib/python2.5/site-packages/cairo/__init__.py
pycentral: pycentral pkginstall: error byte-compiling files (1)
...........

---

