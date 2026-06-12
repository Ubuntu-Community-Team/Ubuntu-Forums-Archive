---
title: "Purge packages using dpkg --get-selections"
date: 2008-09-25
forum: General Help
---

### Post by gladstone on 2008-09-25
I know I can make a list of all installed packages and reinstall them with something like:
```

dpkg --get-selections > packages
dpkg --set-selections <packages && apt-get dselect-upgrade

```
but is there a way of doing the same but to **purge** packages instead of installing them?

I've made a file with:
```

oclock                      purge
xeyes                       purge
xlogo                       purge
xclock                      purge

```
and tried:
```

dpkg --set-selections <packages && apt-get dselect-upgrade

```
but it returns "*0 packages to remove*"

---

### Post by sisco311 on 2008-09-25
try:
```
sudo aptitude purge `sed 's/purge$//' packages`
```

---

### Post by gladstone on 2008-09-25
Hmm, something strange has happened (before trying your suggestion). apt-get is saying the *xclock* (one from my purge list) isn't installed even though it is:
```

sudo apt-get purge xclock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xclock is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```
Running *xclock* starts it as normal. Looks like I've deleted it from the package list but not actually uninstalled it?

---

### Post by sisco311 on 2008-09-25
> **gladstone said:**
> Hmm, something strange has happened (before trying your suggestion). apt-get is saying the *xclock* (one from my purge list) isn't installed even though it is:
```

sudo apt-get purge xclock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xclock is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```
Running *xclock* starts it as normal. Looks like I've deleted it from the package list but not actually uninstalled it?

xclock is not a real package.
```
aptitude show x11-apps
```
> Package: x11-apps
State: installed
Automatically installed: no
Version: 7.3+1
Priority: optional
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1905k
Depends: libc6 (>= 2.6.1-1), libfontconfig1 (>= 2.4.0), libice6 (>= 1:1.0.0),
         libpng12-0 (>= 1.2.13-4), libsm6, libx11-6, libxaw7, libxcursor1 (>
         1.1.2), libxext6, libxft2 (> 2.1.1), libxkbfile1, libxmu6, libxmuu1,
         libxrender1, libxt6, cpp
PreDepends: x11-common (>= 1:7.0.0)
Suggests: mesa-utils
Conflicts: oclock, x11perf, xbiff, xcalc, xclipboard, xclock, xconsole,
           xcursorgen, xditview, xedit, xeyes, xload, xlogo, xmag, xman, xmore,
           xwd, xwud
Replaces: xbase-clients (<= 1:7.2.ds2-3), oclock, x11perf, xbiff, xcalc,
          xclipboard, xclock, xconsole, xcursorgen, xditview, xedit, xeyes,
          xload, xlogo, xmag, xman, xmore, xwd, xwud
Description: X applications
 An X client is a program that interfaces with an X server (almost always via
 the X libraries), and thus with some input and output hardware like a graphics
 card, monitor, keyboard, and pointing device (such as a mouse). 
 
 This package provides a miscellaneous assortment of X applications that ship
 with the X Window System, including: 
 *** oclock and xclock, graphical clocks; **
 * xbiff, a tool which tells you when you have new email; 
 * xcalc, a scientific calculator desktop accessory; 
 * xclipboard, a tool to manage cut-and-pasted text selections; 
 * xconsole, which monitors system console messages; 
 * xcursorgen; 
 * xditview, a viewer for ditroff output; 
 * xedit, a text editor; 
 * xeyes, a demo program in which a pair of eyes track the pointer; 
 * xload, a monitor for the system load average; 
 * xlogo, a demo program that displays the X logo; 
 * xmag, which magnifies parts of the X screen; 
 * xman, a manual page browser; 
 * xmore; 
 * xwd, a utility for taking window dumps ("screenshots") of the X session; 
 * xwud, a viewer for window dumps created by xwd; 
 * Xmark, x11perf, and x11perfcomp, tools for benchmarking graphical operations
   under the X Window System; 
   
 The xbiff, xcalc, xconsole, xedit and xman programs use bitmap images provided
 by the xbitmaps package.


---

### Post by gladstone on 2008-09-25
> **sisco311 said:**
> xclock is not a real package.
```
aptitude show x11-apps
```

:oops: Thanks

I tried: ```
sudo aptitude purge `sed 's/purge$//' packages`
``` but aptitude wants to remove all *these*, instead of just ```
x11-apps
``` that I have specified :confused:
```

Remove the following packages:
amarok
amarok-xine
apport-gtk
gdebi
gksu
gnome-system-monitor
gparted
jockey-gtk
kdelibs4c2a
language-selector
libgksu2-0
network-manager
network-manager-gnome
software-properties-gtk
synaptic
ubuntu-standard
update-manager
update-notifier
xbase-clients
xfce4-session
xorg

```

---

