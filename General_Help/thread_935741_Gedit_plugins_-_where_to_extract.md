---
title: "Gedit plugins - where to extract?"
date: 2008-10-02
forum: General Help
---

### Post by pdubs on 2008-10-02
I'm at a total loss on this one.  I'm hoping to add regex search and replace to gedit.  I've found this [helpful list of gedit plugins for gnome]("http://live.gnome.org/Gedit/Plugins"), which includes a link to[ a search and replace module in python]("http://vaem.googlecode.com/files/gedit2_regex_replace_plugin.tar.gz") - but after downloading, I've run into a snag.

A few of the sites I've gone to indicate "Unpack the files in ~/.gnome2/gedit/plugins", but I don't have a gnome2 directory (I'm assuming this is because I'm using Ubuntu and not Gnome).  I've unpacked the plugin into what I thought was the gedit directory using gksudo nautilus:

/usr/share/gedit-2/plugins/

In theory, according to several websites, once I have extracted this into my "plugins" directory, I should be able to find it as one of the options in gedit - Edit-> Preferences -> Plugins.  However, it's not showing up there.

Anyone know what I'm doing wrong?  I'm new to linux and the file structure used in Ubuntu.  I assume I have the wrong path for gedit, but searching my system for gedit folders returns several folders, so I'm not sure which is the right one (thought I had it).

---

### Post by Ms_Angel_D on 2008-10-02
Search for Gedit in synaptic, there are some plugins there, for other plugins [try this post]("http://ubuntuforums.org/showpost.php?p=4424711&postcount=2").

---

### Post by ad_267 on 2008-10-02
Ubuntu uses Gnome, Gnome is a desktop environment ([http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)). In the file browser go to View - Show Hidden Files and there should be a directory called .gnome2. Put the extracted plugin in ~/.gnome2/gedit/plugins

The "." in front means the directory is hidden.

---

