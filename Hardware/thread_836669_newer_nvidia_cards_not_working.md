---
title: "newer nvidia cards not working"
date: 2008-06-21
forum: Hardware
---

### Post by mthode on 2008-06-21
I have a 7800gt that works until you do anything 3d on it.
I also have a 8600gt to be used as a replacement.
the 7800 boots up fine
as soon a the 8600 boots up and tries to enter X (gdm whatever) it dies
the screens stop receiving input and I get the error on both of them stating that no signal is detected
I thought that my power supply was not beffy enough so I upgraded it to a 750 watt single rail (previous one had 2 split rails), that didn't help

I have reinstalled both the beta nvidia driver the current one, the ones frome envyng and the ones in the base ubuntu repos
none of them work for the 8600 all of them work for the 7800
I also have the same issue on a 9600gt so it probably is not related to the card itself

did some new kernel update mess everything up?

---

### Post by pietjanjaap on 2008-06-22
1 do this then compiz does not start with ubuntu, and you don't get the whitw screen.

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


2 try this:
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).



4

Setup Compiz Fusion with open source ati radeon drivers

Older ATI cards have been blacklisted for Compiz Fusion because of a bug in the driver, but there is an easy workaround for many cards that use the open source ati drivers. Radeon 9500 are the oldest cards to support the restricted "fglrx" drivers, so everything older requires the open source drivers to function properly.



First edit the launcher for Compiz Fusion:

gksudo gedit /usr/bin/compiz

Near the top, add the line

SKIP_CHECKS="yes"

I added it under VERBOSE="yes"

You may also need to install the Compiz settings manager program that you can access from System->Preferences->Advanced Desktop Effect Settings | 1-click install or:

sudo apt-get install compizconfig-settings-manager

You can now load Compiz Fusion with

compiz --replace

and revert to Metacity (the basic window manager) with

metacity --replace

I suggest making launchers in a panel for this.

Remember that this is a workaround and may not work for everybody. If you have further problems, you should consider running a forum search and then posting on one of the main support forums if you still need help.
For the record, my card is an ATI Mobility Radeon 9000.

---

### Post by mthode on 2008-06-22
thanks for the help but the doesn't have to do with compiz but with the drive itself.

It seems like the video card powers down after X starts (no video signal is being sent)

---

