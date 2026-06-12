---
title: "Ubuntu 11.04 Natty Install"
date: 2011-04-03
forum: Idaho Team - US
---

### Post by darinmiller on 2011-04-03
Installing 11.04 Beta 1 to a Dell m1530 laptop with NVidia 8600 GT card:

**Conditions:**
[List]
[*] Custom partitions 
[INDENT][*] 14G Root "/" partition set to format
[*] 155G /home partition set to format
[*] 4G SWAP file
[*] 63G Windows XP partition
[/INDENT][/LIST]

**Attempts:**
[LIST]
[*]Installing with Restricted Extras and Download Updates boxes checked crashed midway through install.
[*]Install with Restricted Extras **un**checked and Download Updates checked also crashed mid install.
[*]Unchecking both boxes allowed install to complete.
[/LIST]

**Post Install:**

[List]
[*] Unity would not start until the proprietary NVidia drivers were installed (driver icon in tool tray eased this effort).
[*] Installing compiz session manager nearly disabled both the gnome and unity desktops. By default, none of the compiz options were enabled including move and resize windows.  For awhile I thought the desktops were just plain unusable until I dug around in the compiz settings.  I recommend using the session specific compiz files included in this post. [ATTACH]187930[/ATTACH]
[*] The software center refused to load any .deb installs including the custom Googleearth deb install I created post 11.04B installation.  I was able to install .deb files using the sudo dpkg -i command, i.e.:
[/LIST]

```
sudo dpkg -i skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb
```

**Comments:**
[INDENT]Unity was definitely designed for mono tasking on low resolution screens where the user runs the applications maximized.  I disliked the following:[/INDENT]
[List]
[*] Top menu bar cannot be hidden.
[*] Menu items cannot moved off the top bar to the standard "in window" location.  This makes window management on high res. dual screens, with several applications running an impractical experience (and no, I do not want a 2nd menu bar on the 2nd monitor).  I will not use Unity until the menus are placed back in the window.  This has been a big pet peeve of mine since Apple initiated this layout.
[*] For desktop environments running lots of apps, the side icon bar does not allow for easy app management-especially when multiple instances of the same app are running.
[*] Side menu bar lacks customization: no sizing, renaming, adding multiple columns of icons, etc.
[*] App icons in the menus are spread out all over the place. What's wrong with the tidy list approach?  The "scattered" layout is one of the reasons I do not like KDE's default menu system.
[*] The title bar clock does not have customize-able time zones and corresponding weather conditions.
[*] I cannot add my own items to the top title bar.
[/LIST]

**What I liked about Unity:**
[LIST]
[*] "Gnome-do" like searching built in.
[*] Single "power key" press brings up icon bar and the search menu.
[/LIST]

**Conclusion:**
[INDENT]The Classic Gnome 2.32.1 session is running quite well-both stable and fast.  In previous releases, I used to crash lots of little apps during beta testing, but so far the crashes have mostly been related to installs.  Starcraft runs without a hitch, though I still have to use custom xorg.files to run SC on my external monitor in the 640x480 resolution. See the attached xorg.conf files if interested.[ATTACH]187932[/ATTACH]

A few bugs that appeared in 10.10 are fixed in 11.04 (calendar pop when clicking the clock on the bottom panel displays correctly again).

The method for re-installing packages from a previous release also worked without issue:

Create a package list on the old machine: 
```
dpkg --get-selections > ~/pkgs
```

Copy the pkgs file to the home directory of the new machine, then run:
```
dpkg --set-selections < ~/pkgs
sudo apt-get -u  dselect-upgrade

```[/INDENT]

---

### Post by vsteel on 2011-04-03
Very nice writeup Darin.  How hard is it from a fresh install to install the rest of Gnome so you can bypass Unity?

---

### Post by darinmiller on 2011-04-03
Gnome is already installed.  To enable Gnome, one must select their username from the login menu, then at the bottom of the login screen, extra login options appear.  Selecting Ubuntu Classic = Gnome.  Ubuntu remembers which UI was used and auto selects the last used interface for subsequent logins.

---

### Post by slavinzing56 on 2011-07-31
Very nice writeup Darin

---

