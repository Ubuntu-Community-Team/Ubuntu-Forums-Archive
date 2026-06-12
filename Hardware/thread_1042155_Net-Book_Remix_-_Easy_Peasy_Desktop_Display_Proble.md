---
title: "Net-Book Remix - Easy Peasy Desktop Display Problem"
date: 2009-01-17
forum: Hardware
---

### Post by dccrens on 2009-01-17
I have hardy loaded on a eeepc 1000h. I use the array kernel and the gnome desktop with compiz. I previously disabled the netbook-remix desktop. However, I just tried using the desktop switcher application to switch from the gnome desktop back to the netbook-remix desktop. Bad move on my part. Now when I boot up I get the login screen ok. Once I log in however I get no desktop; only my background wallpaper is displayed and I can't get any windows or menus. I tried restart the x server but that just takes me back to the login prompt. Also tried switching to another terminal using cntl-alt-f4 but all I get is a black screen with a flashing cursor (not login prompt). 

From the login screen I can switch the login to login in to gnome with only an xterm. And have network access. Anyone know how to either reinstall the gnome desktop or reinstall the netbook remix desktop from the command line so that I can login and get a gui?

---

### Post by dccrens on 2009-01-17
Well I partly answered my own question.

Changed the login session to gome with xterm only. Reinstall all of the required packages for netbook-remix. After that reboot and relogin. Still no go with a standard login. Next, changed login session to "Failsafe Gnome" and logged in. This brought up the Netbook Remix desktop. 

From here I was able to access "sessions" and uncheck all netbook remix related startups and recheck compiz and emerald. I then ran the  program and removed "maximus" and "ume-luancher". Making sure to check completely remove so that the config files are removed. I then rebooted and relogged in, in a failsafe session and looks like everything is working. However when I login to a regular session the same thing happens. Only the background wallpaper comes up. There must be something in my home directory config files that is causing this. Just not sure what...

---

### Post by chriseee on 2009-01-18
Hi, i had the same problemin Hardy ,after installng desktop switcher couldnt get remix ot destop mode properly. However using doing update manager and clickin on more or less everything on start up programs in session preferences remix now works. I also deletd and reinstalled desktop switcher and got rid of all the compiz stuff.

---

### Post by dccrens on 2009-01-18
Chriseee,
I finally gave up and just reloaded Intrepid. I have been wanting to do so anyway. Now I have my gnome desktop with compiz and emerald back! Also loaded adams kernel and the acpi scripts to get all of the special keys working.

---

### Post by WuChiMan on 2009-01-31
After reading Chrisee's comment, I checked Sessions and the Startup Programs tab. I found that UME-Desktop Launcher had been unchecked -- apparently by the desktop-switcher program. I certainly didn't. I enabled it again, and restarted. The Netbook-Remix desktop came up as it was supposed to do.

Incidentally, when I first had this problem, I also had dccrens' problem. I got a menu by typing ALT-F1. From there, you can get to Sessions, or, for that matter, you can launch desktop-switcher. It will bring you back to the Netbook Remix desktop.

---

### Post by remontello on 2009-02-01
I would like to install the desktop switcher and run native gnome instead of the netbook remix.  How do I find it and install it.  Not sure how to use the synaptic package manager to do this.
Russ

---

