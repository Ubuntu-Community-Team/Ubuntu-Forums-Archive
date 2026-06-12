---
title: "Blank White Screen"
date: 2008-08-11
forum: General Help
---

### Post by patoy on 2008-08-11
hi! fellow ubuntu users.i just got stumbled into a problem when i recently installed the driver for the video. it's an ATI integrated video. when i logged in after installing/enabling the driver, it displays blank white screen. i restarted x login and went to terminal (Ctrl+Alt F4) to reboot the machine. still the same. any recommendations? i'm currently logged in to failsafe gnome.

---

### Post by tuxxy on 2008-08-11
You could reconfigure the xorg, and follow the process through

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by patoy on 2008-08-12
still not able to get back to normal gnome.

---

### Post by Crafty Kisses on 2008-08-12
> **patoy said:**
> still not able to get back to normal gnome.

Try booting into verbose, and then do the following:
```
startx
```

---

### Post by pietjanjaap on 2008-08-12
May be your videocard is blacklisted(search forum).
When compiz is activated(and your videcard driver), then you get a white screen.

First install envy in textmode, see website envy.
Then remove your ati videocard driver.

Then start with gui.

Then do this:
Monday, April 14, 2008
Stop Compiz-Fusion From Loading Automatically

This guide will show you how to stop Compiz-Fusion from loading automatically on startup in Hardy Heron and how to setup a shortcut for launching Compiz when you want.

Step 1: Run gconf-edit
Start Run Application by pressing Alt+F2

Screenshot-Run Application

Enter gconf-editor into the box, hit enter


Step 2: Set Metacity as your default start up window manager
Once in gconf-editor navigate to desktop>gnome>applications>window_manager

Screenshot-Configuration Editor - window_manager

under current and default replace each instance of:
/usr/bin/compiz with /usr/bin/metacity
it should like this when you're done:

Screenshot-Configuration Editor - window_manager-1



Step 3: Create a shortcut for starting Compiz-Fusion
right click the Applications Places System Menu
select the Edit Menu option

Screenshot-Main Menu

pick a location for your shortcut and select New Item box

Screenshot-Launcher Properties
Type: Application
Name: Compiz
Command: compiz --replace
COmment compiz window manager



Then:
Setup Compiz Fusion with open source ati radeon drivers

Older ATI cards have been blacklisted for Compiz Fusion because of a bug in the driver, but there is an easy workaround for many cards that use the open source ati drivers. Radeon 9500 are the oldest cards to support the restricted "fglrx" drivers, so everything older requires the open source drivers to function properly.



First edit the launcher for Compiz Fusion:

gksudo gedit /usr/bin/compiz

Near the top, add the line

SKIP_CHECKS="yes"

I added it under VERBOSE="yes"

Remember that this is a workaround and may not work for everybody. If you have further problems, you should consider running a forum search and then posting on one of the main support forums if you still need help.
For the record, my card is an ATI Mobility Radeon 9000.

Then install with envy the videocard driver.


Now your pc will start without compiz(you do not get a white screen).
You can start compiz white shortcut you made, if you get a white screen, reboot and gone is the white screen.


This you do not have to do, but this is changed with 8.04:

With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by patoy on 2008-08-12
thanks for the input. was able to go back at gnome by just removing the deb package i installed for the video card xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-19.45_i386.deb was culprit. removed it the package manager. restarted and logged in back normally to gnome. kindly close this topic as its resolved already.

---

### Post by inkyfingers on 2010-03-11
The solution for me was here:
System => Preferences => Appearance => Visual Effects, Change to NONE.

---

