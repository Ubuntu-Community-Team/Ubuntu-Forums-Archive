---
title: "Update manager issue"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by SpitfireSMS on 2009-06-13
Alright so, I have a custom version of wallpaper-tray installed, and every time update manager comes up, it tries to update it.
Its not a huge inconvenience to deselect it every time, but it does get annoying.
Is there any way to keep it from appearing?
For reference(idk if this will even help) its under "Distribution updates"

I have gone into synaptics and told it to lock version, but that didnt seem to do anything.
Any ideas?

---

### Post by jenkinbr on 2009-06-14
You *could* possably edit the /var/lib/dpkg/status file, but it may be risky.  Back it up first.
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak
```
Now run;
```
gksu gedit /var/lib/dpkg/status
```
That will open up a root gedit session.

Find the section for wallpaper-tray, which should look like;
```
Package: wallpaper-tray
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 372
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.5.5-0ubuntu2
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libboost-filesystem1.34.1 (>= 1.34.1-8), libboost-regex1.34.1 (>= 1.34.1-8), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libcairomm-1.0-1 (>= 1.6.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libgconf2-4 (>= 2.13.5), libgconfmm-2.6-1c2 (>= 2.22.0), libglade2-0 (>= 1:2.6.1), libglademm-2.4-1c2a (>= 2.6.0), libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.19.3), libgnome-vfsmm-2.6-1c2a (>= 2.22.0), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomecanvasmm-2.6-1c2a (>= 2.23.1), libgnomemm-2.6-1c2 (>= 2.16.0), libgnomeui-0 (>= 2.22.0), libgnomeuimm-2.6-1c2a (>= 2.16.0), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.16.0), libgtkmm-2.4-1c2a (>= 1:2.16.0), libice6 (>= 1:1.0.0), libnotify1 (>= 0.4.4), libnotify1-gtk2.10, liborbit2 (>= 1:2.14.10), libpanel-applet2-0 (>= 2.19.3), libpango1.0-0 (>= 1.22.0), libpangomm-1.4-1 (>= 2.14.0), libpixman-1-0, libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.14), libsigc++-2.0-0c2a (>= 2.0.2), libsm6, libstdc++6 (>= 4.2.1), libx11-6, libxcb-render-util0 (>= 0.2.1+git1), libxcb-render0, libxcb1 (>= 1.1.92), libxml++2.6-2 (>= 2.24.0), libxml2 (>= 2.6.27), libxrender1, zlib1g (>= 1:1.1.4)

```

I would try editing the status line to a higher version number than the one that is installed.
Mine reads:
Version: 0.5.5-0ubuntu2

I might change it to:
Version: 1.5.5

Save the file, then exit the terminal

Try updating again

Note that I am not sure if this is the greatest idea, but it should work.

---

### Post by SpitfireSMS on 2009-06-14
Alright so I take this is going to trick update manager into thinking the version I have is newer than the ones its checking against to update?
If it doesnt work, should I overwrite with the backup just to ensure nothing goes awry?

---

### Post by jenkinbr on 2009-06-14
Correct and correct.

---

### Post by SpitfireSMS on 2009-06-14
Ok thanks.
Update manager is acting kind of odd now.

[IMG]http://i42.tinypic.com/mlbq1.png[/IMG]

I assume the 96kb is wallpaper tray.
Clicking install does absolutely nothing, so I think its doing what you intended.
But I will have to wait for more updates to become available to make sure that those actually update.

---

### Post by jenkinbr on 2009-06-14
Post back when you find out - I've subscribed to this thread, and I am on frequently.

---

### Post by SpitfireSMS on 2009-06-14
Alright thank you so much.

Iv also been wondering if theres a way to get update manager to come up like it did on 8.10?
I remember it popping up in the notification area saying updates are available.
Now it just brings up the window behind everything else, and my occasional alt-tab brings it up by surprise.

---

### Post by jenkinbr on 2009-06-15
Your welcome

as for your second issue, I have no idea.  I don't use Update Manager personally, as I use apt-get for updating and upgrading packages.

---

### Post by SpitfireSMS on 2009-06-16
Just updated, and it works perfectly.
Thanks again

---

