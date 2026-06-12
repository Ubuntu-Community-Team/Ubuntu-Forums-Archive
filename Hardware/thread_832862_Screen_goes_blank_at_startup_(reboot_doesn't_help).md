---
title: "Screen goes blank at startup (reboot doesn't help)"
date: 2008-06-18
forum: Hardware
---

### Post by noobsalive on 2008-06-18
I am using a laptop, toshiba satellite 2403

After installing the Nvidia graphics driver required to enable desktop effects and rebooting, my screen was blank though i could hear sound effects (before login, after boot) and i could even login (familiar with login screen) and hear the login sound effects.

I solved this problem temporarily by plugging in my sisters monitor, and it could work. I changed my settings to reactivate my screen, and it surprisingly worked. Until i rebooted and the same thing happened. No amount of reboots solved this, and i did the Nvidia settings again, more thoroughly.
[U]
Steps to change screen
[/U]
*After logging in*
[http://i110.photobucket.com/albums/n89/anim4niac/Screenshot.png]("http://i110.photobucket.com/albums/n89/anim4niac/Screenshot.png")
[I]
Activating my laptop screen[/I]
[http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-1-1.png]("http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-1-1.png")

*There it is*
[http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-2.png]("http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-2.png")
[I]
Disable my sisters monitor[/I]
[http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-3.png]("http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-3.png")

*Can't directly change to an X screen by just applying, so...*
[http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-6.png]("http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-6.png")

*And save *
[http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-4.png]("http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-4.png")


**Alternatively**
I made my screen a twin, then disabled my sisters.
[http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-5.png]("http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-5.png")

Either way, it goes blank again at the login screen whenever i reboot.
Does anyone have a solution to this? Am I doing something wrong here? :confused:
Please help :(

---

### Post by noobsalive on 2008-06-18
Bump

---

### Post by noobsalive on 2008-06-19
bump

---

### Post by TubaTodd on 2008-06-19
I will admit that I have NOT looked at all of your screenshots...but...

Does this behavior persist if you boot off the Ubuntu Live CD??? If it DOES....then it sounds like you need to hit FN+F7 to toggle onboard LCD with the external VGA. OR...you may need to check your BIOS settings for video. Defaults should probably include both the internal and VGA enabled. 

If the Live CD does NOT behave the same way...then I would consider reconfiguring your X settings or doing a reinstall (last resort). BTW, I highly recommend installing Envy (if you haven't already) to automatically download and install the NVidia video drivers.

---

### Post by pietjanjaap on 2008-06-19
Compiz is proberly the problem(i had the same), your videocard is proberly blacklisted, see forum. If you do the things below, then your pc will start without compiz.
Now you can play with compiz, if fails you restart and compiz will not start.



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

---

### Post by noobsalive on 2008-06-21
@TubaTodd: I have envy, and I have absolutely no experience. Therefore I think reconfiguring X by myself would just cause my monitor to go blank permanently ;_; or worse. (also, the X config files are under /root and i have no idea how to gain acess to them) Reinstall/reformat has always been a last ditch resort for me :) Also, what's FN+f7? particularly the FN. The default settings currently only has the VGA enabled.

@pietjanjaap: Thanks so far, but your screenshot links... don't work (if they WERE meant to be links). I've got it all in, except **_Step 2: Set Metacity as your default start up window manager_** (i really don't know T^T sorry)
Here's a screenshot of the application and the editing of window_manager

[http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-7.png](http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-7.png)

Is this right?

---

### Post by pietjanjaap on 2008-06-22
I had the same problem.
Above i told you to make changes in gconf-editor so compiz won't start.
In instructions you have to make 2 buttons, 1 to start compiz en 1 to diasable compiz.

If you are playing with compiz, and it fails, then reboot, then ubuntu will start without white screen.
I did the same.

Because your screen is white, your videocard is blacklisted for compiz.
So do this:

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

### Post by noobsalive on 2008-06-22
I have no problems with your guide, it's just that i can't view your screenshots for the more specific parts, which renders me clueless on how to go around it.

Right now I just don't know how to set my default desktop manager to metactity, and since i don't know how my end result is supposed to look, i asked if this was right

Screenshot - [http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-7.png]("http://i110.photobucket.com/albums/n89/anim4niac/Screenshot-7.png")

Thanks

---

