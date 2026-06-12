---
title: "about apt-get"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2005-12-14
apt-get behaves the same in Ubuntu and Debian. Here are two nice articles to get you started :

A Concise apt-get / dpkg primer for new Debian users :

[http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html](http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html)

What to do when apt-get fails :

[http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106](http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106)

For more information about apt-get type :
$ man apt-get

For more information about dpkg type :
$ man dpkg

The key meta packages of Ubuntu are :

ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)

So after a standard ubuntu (gnome) installation ubuntu-base and ubuntu-desktop are installed which makes sure every other ubuntu package is installed.

But if you have entered an apt-get-hell dependencies problem it's good to know some important packages :

xserver-xorg - Xorg. This is the graphical server which is needed to get a GUI environment (for example gnome)

x-window-system-core - this has to be installed to get a working Xorg

gdm - gnome's login manager - needs to be installed if you want your pretty yellow Ubuntu login screen after bootup

kdm - kde's login manager - needs to be installed to get a KDE like login screen

metacity - gnome's window manager. needs to be installed (you can can change to an other window manager later if you want)

xfwm4 - xfce4's window manager. analogous to metacity. Gets installed by xubuntu-desktop

kwin - kde's window manager analogous to metacity

PS You can find my recommended breezy sources.list in my signature.

---

### Post by Herman on 2005-12-14
Thanks, ubuntu_demon, read, copied, bookmarked and saved! :D  (Herman)

---

