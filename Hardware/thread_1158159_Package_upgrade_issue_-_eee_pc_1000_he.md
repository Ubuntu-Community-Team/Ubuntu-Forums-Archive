---
title: "Package upgrade issue - eee pc 1000 he"
date: 2009-05-13
forum: Hardware
---

### Post by lukenz on 2009-05-13
Hi All

Just installed netbook remix onto my eee pc 1000 he.  All worked well until i performed an upgrade with Synaptic.  From then on after GDM login it would only boot to a blank desktop with no panel, netbook-launcher or anything.  The only thing i could get was the right click menu on the desktop.  My mate has the 1000 he, upgraded with Synaptic and the same thing happended to him.

I have done a reinstall because I hadn't done much configuring anyway, so I am about to look through the packages marked for upgrade to see what could have broken.

Has anyone seen this issue before, or know how to get around it if it happens again?  Tried reconfiguring x, didn't know what else to do.

Luke

---

### Post by lukenz on 2009-05-13
Here is the list of packages marked for upgrade:

bluez-alsa        install
update-manager        install
gnome-desktop-data        install
nautilus        install
bluez-gstreamer        install
ubuntu-docs        install
bluetooth        install
libwmf0.2-7        install
gnome-settings-daemon        install
update-manager-core        install
xulrunner-1.9        install
system-config-printer-gnome        install
bluez-cups        install
libevview1        install
cups-client        install
compizconfig-backend-gconf        install
screen-profiles        install
checkbox        install
apport        install
nautilus-data        install
bluez        
hwtest-gtk        
libsoup2.4-1        
libgweather1        
libck-connector0        
acpid        
udev        
bluez-utils        
checkbox-gtk        
firefox        
cups-common        
gnome-about        
libcups2        
splix        
libgweather-common        
system-config-printer-common        
cups        
python-problem-report        
evince        
libbluetooth3        
libevdocument1        
gnome-app-        
apturl        
libsoup-gnome2.4-1        
firefox-3.0        
cups-bsd        
libmpfr1ldbl        
libudev0        
libvolume-id1        
synaptic        
libpam-ck-connector        
libfreetype6        
libcupsimage2        
gnome-applets        
gnome-system-tools        
libgnome-desktop-2-11        
python-apport        
libnautilus-extension1        
python-cupshelpers        
firefox-3.0-branding        
gnome-applets-data        
apport-gtk        
consolekit

---

### Post by lukenz on 2009-05-15
Think it was the Compiz packages.

---

### Post by Zuuted on 2009-05-23
I recently got an eee pc 1000he also and am preparing to install ubuntu netbook remix... I will test and post results. 

Any updates in the mean time???
Thanks!

---

### Post by lukenz on 2009-05-24
Hello Zuuted

Thought it was the package update at first. After the reinstall ended up removing compiz and allowing the other upgrades to complete.

Turns out the same thing happened again.  Other people have had the same issue.  I think it is a bug (reported) with the desktop switcher and/or launcher.  I ended up removing netbook-launcher, maximus, desktop-switcher and compiz.  It is now running really well (and quick).  I don't miss the netbook-launcher either, gnome looks great on the small screen.

If you want to keep the netbook-launcher stuff, have a search on launchpad because a few people have workarounds.  This is only required of course if you have the missing panel problem.

Even with this issue I still highly recommend ubuntu netbook remix:p

Luke

---

### Post by Zuuted on 2009-05-29
Hey lukenz! 
I have actually updated eveything and all is running mighty fine & fast with the 2GB RAM upgrade in my 1000HE. Incrediby pleased so far... The Netbook Remix rocks! 
Many thanks for your updates and suggestions. I'll post in this thread with any further updates.

Thanks Again!

---

