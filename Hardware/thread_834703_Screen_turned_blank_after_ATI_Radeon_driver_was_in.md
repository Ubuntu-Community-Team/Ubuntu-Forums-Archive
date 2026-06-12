---
title: "Screen turned blank after ATI Radeon driver was installed and enabled."
date: 2008-06-19
forum: Hardware
---

### Post by trengen on 2008-06-19
Someone please help me with my ATI Radeon problem.
After installing the ATI Radeon driver, I am getting a white blank screen after the computer restarted.  I have tried the recovery mode and used the all the options in the recovery mode, and still could not get my Ubuntu to recover the desktop screen.  

Please show me how to restore default video driver so that it might work again? I don't want to reinstall Ubuntu again.  Your help is greatly appreciated!! :) :guitar:

System Config:

Pent D 2.6
ATI Radeon X1650
ECS P4M800PRO-M
2GB PC3200 DDR2
Maxtor 160GB SATA HD
Onboard ethernet, sound
Toshiba DVDRW 16X

---

### Post by pietjanjaap on 2008-06-22
1 do this then compiz does not start with ubuntu, and you don't get the white screen.

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

3

/etc/modprobe.d/blacklist

hier in kopieren

blacklist i82875p_edac
blacklist edac_mc

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

### Post by trengen on 2008-06-22
[QUOTE=pietjanjaap;5236846]1 do this then compiz does not start with ubuntu, and you don't get the white screen.

Thanks for your reply.

I've tried your very detailed instructions, but it did not work.  I guess that I will stay with "very limited default" video driver.  I was able to log back in the Ubuntu desktop in the failsafe mode, then un-installed the ATI video driver.

Cheers!

:guitar:  Rock On!

---

