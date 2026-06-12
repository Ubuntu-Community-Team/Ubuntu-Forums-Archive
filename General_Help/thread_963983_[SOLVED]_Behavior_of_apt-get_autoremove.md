---
title: "[SOLVED] Behavior of apt-get autoremove"
date: 2008-10-30
forum: General Help
---

### Post by jis on 2008-10-30
I have xubuntu-desktop installed (in ubuntu 8.10) and I wonder why the following command wants to remove it:

```
sudo apt-get autoremove alacarte bluez-gnome brltty brltty-x11 compiz consolekit contact-lookup-applet cups-driver-gutenprint dcraw deskbar-applet desktop-file-utils ekiga eog espeak evolution evolution-exchange evolution-plugins evolution-webcal example-content fast-user-switch-applet firefox-gnome-support f-spot gconf-editor gdm-guest-session gedit gnome-about gnome-applets gnome-control-center gnome-icon-theme gnome-mag gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-pilot-conduits gnome-session gnome-spell gnome-terminal gnome-themes gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gvfs-fuse hwtest-gtk im-switch launchpad-integration libcanberra-gnome libdeskbar-tracker libgnome2-perl libgnomevfs2-bin libgnomevfs2-extra libpam-gnome-keyring libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 metacity mousetweaks nautilus nautilus-cd-burner nautilus-sendto nautilus-share pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 rarian-compat rhythmbox rss-glx scim-bridge-agent scim-bridge-client-gtk tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds usb-creator usplash-theme-ubuntu vino xdg-user-dirs xdg-user-dirs-gtk yelp
```

---

### Post by Yellow Pasque on 2008-10-30
Use 'remove' instead of 'autoremove'

---

### Post by jis on 2008-10-30
Using remove instead of autoremove leaves a lot of unused packages that take disk space (and bandwidth when updating).

---

### Post by ajgreeny on 2008-10-30
Then there is obviously something in your list of removals that is a dependency of xubuntu-desktop.  I don't know xubuntu so can't tell you what it might be.  It really won't matter, though, unless you intend to do an online distro-version update, eg from 8.04 to 8.10.  Xubuntu-desktop is just a meta-package that tells the system what needs updating; it does not actually contain any applications itself, it just drags them in.

---

### Post by zvacet on 2008-10-30
```
 Xubuntu-desktop is just a meta-package that tells the system what needs updating; it does not actually contain any applications itself, it just drags them in.
```

But you can not perform upgrade without it.

@ **jis**

Try 

```
sudo apt-get update && sudo apt-get upgrade
```

and look if you have any packages recommended to remove.If you know that some of them you need don´t remove them.Instead of that install that packages with 

```
sudo apt-get install** packagename**
```

that way thay will not again show in list of packages recommended to remove.

---

### Post by jis on 2008-10-30
> **ajgreeny said:**
> Then there is obviously something in your list of removals that is a dependency of xubuntu-desktop.

You are right.

---

