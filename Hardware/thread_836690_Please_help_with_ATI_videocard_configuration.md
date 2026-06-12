---
title: "Please help with ATI videocard configuration"
date: 2008-06-21
forum: Hardware
---

### Post by ranchero on 2008-06-21
(Ubuntu 8.04)

I'm trying to make ATI x600 All-in-Wonder work properly with CRT monitor for about a week and totally pissed off. I've tried everything I could find, but no luck.
I had all kind of s**t - from 640x480 screen to white screen when Ubuntu starts.
I've installed ATI hardware driver (System-Administration-Hardware drivers)
and ATI Catalyst control driver.

I need 1152x864x85Hz resolution (Once again, it's CRT, Hitachi CM751). I'm changing it in ATI Catalist. After restart -
What I'm having - login/password screen displayed full screen, 1600x1200.
Then Main desktop appears at 1152x864 but not full screen, moved to the left. No matter what I do, after restart it does exact same thing, or doesn't work at all. Without ATI driver system becomes slow as pentium I.
 xvidtune gives me error when I'm pushing Test even if I'm not changing anything.

 Is there any way I can make it stick to the 1152x864 and keep t full screen?
Thanks

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

### Post by ranchero on 2008-06-23
I don't have Compiz or any other fancy stuff installed.
Any other suggestions how to make my wideocard work properly?
Is there any other place where I can ask for help?

---

### Post by jocko on 2008-06-23
> **ranchero said:**
> I don't have Compiz or any other fancy stuff installed.
Any other suggestions how to make my wideocard work properly?

Compiz is installed by default, and I think it will be used if you have a driver that supports it. The white screen you get may be related to compiz (I had something similar on my my laptop with an nvidia card, don't remember how I solved it...).

First, set up your xorg.conf to use the correct driver (if you haven't already done it):
```
sudo aticonfig --initial
```Then make sure you have your monitor properly set up in xorg.conf.
```
sudo gedit /etc/X11/xorg.conf
```In the "Monitor" section, set the horizontal sync and vertical refresh rates according to your monitor's specifications (find it in your monitor manual or on the manufacturers homepage). Make sure you use the correct values, otherwise you may get problems.
```
Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Q910"
    Option        "DPMS" "true"
    [COLOR=Red]HorizSync    30-110
    VertRefresh  50-150[/COLOR]
EndSection
```In the "Screen" section, make a subsection "Display" with the modes you want to be able to use (with the default first, in my example 1600x1200).
```
Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device     "aticonfig-Device[0]"
    Monitor    "aticonfig-Monitor[0]"
    DefaultDepth     24
    [COLOR=Red]SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes        "1600x1200" "1280x1024" "1152x864" "1024x768"
    EndSubSection[/COLOR]
EndSection

```> **ranchero said:**
> Is there any other place where I can ask for help?
There are plenty of other places, but this is probably the best.

---

### Post by ranchero on 2008-06-24
I only getting white screen only when things totally messed up.
Right now is as described in my original post:

Then Main desktop appears at 1152x864x85Hz (that's what I need, specified by me in Catalist center), but not full screen, moved to the left. No matter what changes I do, after restart it does exact same thing, or doesn't work at all (and in worst case the white screen may appear). Without ATI driver system becomes slow as pentium I.
xvidtune gives me error when I'm pushing "Test" button, even if I'm not changing anything.

I'll try to make ajustments which you've sujjested (I'm using XP right now as Ubuntu is useless the way it is right now)

---

