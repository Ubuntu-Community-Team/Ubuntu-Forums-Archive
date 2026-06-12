---
title: "Top and bottom bars not displayed"
date: 2008-10-07
forum: General Help
---

### Post by manoka on 2008-10-07
The top bar with the "Applications", "Places", "System" etc. and the bottom bar with the trash and the "Hide all windows and show the desktop" signs etc. do not appear, on Ubuntu 7.10.
Thanks in advance for any infos.
manoka

---

### Post by mixmaster on 2008-10-07
> **manoka said:**
> The top bar with the "Applications", "Places", "System" etc. and the bottom bar with the trash and the "Hide all windows and show the desktop" signs etc. do not appear, on Ubuntu 7.10.
Thanks in advance for any infos.
manoka
I had something like that when xfce4-panel didn't run (on Xubuntu).  I think on standard Ubuntu you should check to see if gnome-panel is running.

---

### Post by manoka on 2008-10-07
Thanks, but how can I - as a newbie - do this without the bar for the access to the "System" and "Administration" etc.?

---

### Post by geirha on 2008-10-07
Hit Alt+F2 and run "gnome-system-monitor"

If gnome-panel is not in the list under the processes tab, hit Alt+F2 again and run "gnome-panel" and see if they come back.

If they don't come back, I suggest resetting the panels to how they were when your user was created. Again Alt+F2, run "gnome-terminal", and in the terminal-window:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by manoka on 2008-10-07
Nothing happens when I hit Alt+F2.

When I run: 

"gconftool --recursive-unset /apps/panel && killall gnome-panel" 

in a terminal window, then the response is:

"gnome-panel: no process killed"

---

### Post by geirha on 2008-10-07
Then use the terminal window instead. gnome-panel obviously wasn't running then, so run ```
gnome-panel
``` in the terminal window.

---

### Post by manoka on 2008-10-07
That worked, at least for now.
Though the response was:

"Unable to open desktop file file:///usr/share/applications/yelp.desktop for panel launcher: No such file or directory"

Thanks again!

---

### Post by geirha on 2008-10-07
That warning suggests that you've uninstalled yelp. Have you uninstalled any packages lately? It may be the cause of this problem. Try ```
sudo aptitude install ubuntu-desktop
``` Does it install anything?

---

### Post by manoka on 2008-10-07
This is the response:

> "Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  gimp wicd 
The following packages are unused and will be REMOVED:
  libavcodec0d libavformat0d libboost-program-options1.33.1 
  libboost-regex1.33.1 libboost-signals1.33.1 libboost-thread1.33.1 
  libflac++5c2 libjack0.100.0-0 liboggflac3 libportaudio2 libpostproc0d 
  libquicktime0 libssl0.9.7 libswfdec0.3 libwxgtk2.4-1 
  linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic python-qt3 
  python-sip4 
The following NEW packages will be automatically installed:
  apturl bogofilter-bdb bogofilter-common compiz-fusion-plugins-extra 
  compiz-fusion-plugins-main compiz-gnome discover1-data 
  libcompizconfig-backend-gconf libcompizconfig0 libdiscover1 libgsl0 
  libpaper-utils libtracker-gtk0 libwv-1.2-3 network-manager o3read tracker 
  tracker-search-tool tracker-utils untex wv 
The following packages have been kept back:
  gnome-orca 
The following NEW packages will be installed:
  apturl bluez-gnome bogofilter bogofilter-bdb bogofilter-common compiz 
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome 
  cups-pdf discover1 discover1-data displayconfig-gtk firefox-gnome-support 
  gimp-print gnome-user-guide hal-cups-utils libcompizconfig-backend-gconf 
  libcompizconfig0 libdeskbar-tracker libdiscover1 libgsl0 
  libpam-gnome-keyring libpaper-utils libtracker-gtk0 libwv-1.2-3 
  network-manager network-manager-gnome o3read pxljr splix tracker 
  tracker-search-tool tracker-utils ttf-unfonts-core ubufox ubuntu-desktop 
  ubuntu-docs untex wv xresprobe yelp 
0 packages upgraded, 42 newly installed, 19 to remove and 1 not upgraded.
Need to get 26.9MB of archives. After unpacking 75.4MB will be used.
The following packages have unmet dependencies:
  wicd: Conflicts: network-manager but 0.6.5-0ubuntu16.7.10.0 is to be installed.
  gimp: Conflicts: gimp-print (<= 5.0.1-3) but 5.0.1-0ubuntu8 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
wicd

Keep the following packages at their current version:
gimp-print [Not Installed]

Leave the following dependencies unresolved:
ubuntu-desktop recommends gimp-print
Score is -12

Accept this solution? [Y/n/q/?]"


Should I accept this solution?

---

### Post by semitone36 on 2008-10-07
If you press "y" it will just install a lot of software that works with your desktop.  Nothing bad will happen to your computer but it is just a bunch of stuff you may or may not want, such as compiz, and that takes up memory (75 MB in this case).

Based on what Ive read in this thread, I agree that it appears you dont have Yelp.  If when you reboot your computer your panels dont appear again until you start them through the terminal you might want to try this:

```
sudo apt-get install yelp
```

---

### Post by semitone36 on 2008-10-07
> The following NEW packages will be installed:
apturl bluez-gnome bogofilter bogofilter-bdb bogofilter-common compiz 
compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome 
cups-pdf discover1 discover1-data displayconfig-gtk firefox-gnome-support 
gimp-print gnome-user-guide hal-cups-utils libcompizconfig-backend-gconf 
libcompizconfig0 libdeskbar-tracker libdiscover1 libgsl0 
libpam-gnome-keyring libpaper-utils libtracker-gtk0 libwv-1.2-3 
network-manager network-manager-gnome o3read pxljr splix tracker 
tracker-search-tool tracker-utils ttf-unfonts-core ubufox ubuntu-desktop 
ubuntu-docs untex wv xresprobe **[COLOR="Blue"]yelp[/COLOR] **

Aha! yeah all you need is to install yelp.  If your panels still dont work after installing yelp, THEN install all these other packages.

---

