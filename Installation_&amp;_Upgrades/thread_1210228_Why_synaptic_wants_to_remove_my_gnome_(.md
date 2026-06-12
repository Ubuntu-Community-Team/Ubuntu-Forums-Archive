---
title: "Why synaptic wants to remove my gnome :("
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by renbla on 2009-07-11
I use sudo dpkg -i python-support_0.8.4_all.deb to install python-support. Then it tell me i need a newer version of dpkg. I attemp to remove that python-support 0.8.4 by synap tic and it tell me that these packages will be remove :
  alacarte apport apport-gtk apturl deskbar-applet displayconfig-gtk
  fast-user-switch-applet foomatic-db-hpijs gdebi gedit gimp-python
  gnome-app-install gnome-applets gnome-applets-data gnome-control-center
  gnome-doc-utils gnome-games gnome-games-data gnome-menus gnome-orca
  gnome-panel gnome-terminal gnome-user-guide guidance-backends hal-cups-utils
  hpijs hplip hwtest-gtk jockey-common jockey-gtk language-selector
  libdeskbar-tracker nautilus nautilus-cd-burner nautilus-sendto
  nautilus-share onboard python-apport python-brlapi python-cups python-dbus
  python-gconf python-gdata python-glade2 python-gmenu python-gnome2
  python-gnome2-desktop python-gnomecanvas python-gnupginterface
  python-gobject python-gst0.10 python-gtk2 python-gtkhtml2
  python-gtksourceview2 python-launchpad-bugs python-libxml2 python-notify
  python-pyatspi python-pyorbit python-sexy python-software-properties
  python-support python-vte python-xdg rhythmbox software-properties-gtk
  startupmanager system-config-printer-common system-config-printer-gnome
  totem totem-plugins ubufox ubuntu-desktop ubuntu-docs update-manager
  update-manager-core update-notifier yelp

:( :(

Actually, now whatever i do w/ synaptic, it tell me that those packages will be removed :( :( :(. So i can't do anything :(
Can smb help me ???

---

### Post by renbla on 2009-07-11
Any one ???? :(:(:(:(

---

### Post by Partyboi2 on 2009-07-11
Hi, what version of Ubuntu are you using?

---

### Post by renbla on 2009-07-13
I'm using ubuntu hardy... But now every thing is OK. It turns out that when i try to install new version of python support, it did something w the old one so it's not usable anymore. And the new version could not continue to install bcoz the old version of dpkg doesn't support it. I think the reason that synaptic wants to remove gnome is bcoz all of those packages need python-support to work :lolflag:. Now new dpkg installed, python support installed. It's ok now :guitar:

---

