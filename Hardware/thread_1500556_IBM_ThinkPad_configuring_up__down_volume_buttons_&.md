---
title: "IBM ThinkPad: configuring up / down volume buttons &amp; TrackPoint center scroll button"
date: 2010-06-03
forum: Hardware
---

### Post by RayJohns on 2010-06-03
I wanted to post this information for anyone who has installed Ubuntu 10.04 LTS on their Thinkpad and is attempting to get the on screen display (OSD) working for the volume up, down & mute buttons and/or for anyone who is attempting to get the middle scroll button on the IBM trackpoint to work for scrolling websites, etc.

I had a heck of a time getting it to work, but after a few attempts, I was able to track down some helpful websites and finally get everything working as I wanted.  This posting is for anyone who is facing the same issues.  I'll try to make these instructions as clear as possible, so that they are helpful for the novice (as well as advanced) user of Ubuntu.

Please note: I'm using Ubuntu version 10.04 LTS i386 on a ThinkPad R51.  I believe these instructions will work for most ThinkPad models, but I have only tested it on my laptop.

**TRACKPOINT SCROLL BUTTON:**

First, in order to get the center trackpoint button to function as a scroll button, I installed the program called "gpointing-device-settings", which is outlined here on this website:

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#GPointing_Device_Settings](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#GPointing_Device_Settings)

From a terminal window, it can be installed as root (or using sudo) with the following command line:

$ sudo apt-get install gpointing-device-settings

This should install the gpointing-device-settings in /usr/bin.  It should also create a menu option called "Pointing Devices" under the System/Preferences menu (you may need to reboot).  

Once you find this menu option, click it and you can configure the trackpointer.  It allows you to configure the touch pad, as well as the IBM TrackPoint.  In order to get the center button to function for scrolling webpages, etc. you need to select the trackpoint area (the picture on the left) and then check the "Use wheel emulation" button and select "button:" so that it has the #2 in the pull down menu.  Also enable vertical scroll.  Note, if you also enable "use middle button emulation", this will cause you to lose the ability to drag around windows using the left mouse button on the trackpoint.  Once these settings have been configured, fire up your browser and you should once again be able to scroll the pages using the center mouse button and the track point (i.e. the red eraser in the middle of the keyboard)

NOTE: As I discovered later (and outlined below), it appears that (at least in my case) using gpointer-device-settings only configured the trackpoint center scroll buttons until the next reboot.  I ultimately had to add a file (see my subsequent post below) so that the configuration would persist between reboots.

-------------------------------------------------

**ON-SCREEN DISPLAY - VOLUME UP/DOWN & MUTE BUTTONS:**

To enable the on screen display for the up/down volume buttons (as well as the mute button and the contrast control function keys - and even the lid LED), I installed a program called tpb (e.g. "Think Pad Buttons")

tpb can be installed via the Ubuntu software center.  Just search for "tpb" and it should show up.  Click install and it should install a binary called "tpb" in /usr/bin

You can test to see if it's working by opening a terminal window and running it directly (by typing /usr/bin/tpb as root).  BTW, if you are tired of using sudo and wish to su - to root, just use sudo to install a root password like this:

sudo passwd root

that should allow you to select a password for root.  From there, you can use:

su - root

Whichever method you use, you need to run tpb as root, because it needs access to the /dev/nvram device.  I had a little trouble getting tpb to start up automatically.  I presume the issue was that when it started during my gnome session, it didn't have root privileges.  What I finally ended up doing was adding an entry to the start up applications control panel (in system/preferences).  I created an entry called "tpb" with this command:

sudo /usr/bin/tpb -d --config=/home/ray/.tpbrc

This runs tpb as a daemon and loads a specific .tpbrc configuration file (you'll want to replace the directory above with the location of wherever your file is).  Here's a link to the tpb manual:

[http://manpages.ubuntu.com/manpages/lucid/man1/tpb.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/tpb.1.html)

And on this page, there is even more information:

[http://www.thinkwiki.org/wiki/Tpb](http://www.thinkwiki.org/wiki/Tpb)

The link below is a sample .tpbrc configuration, which you can edit (and which gives information as to what each parameter does):

[http://www.nongnu.org/tpb/doc/tpbrc.html](http://www.nongnu.org/tpb/doc/tpbrc.html)

Copy this file to your .tpbrc file and then you can start editing.  In my case, the default appearance of the tpb config file was so bad that, at first, I thought tpb wasn't even working.  It was only after making some modifications that I realized it was working, but the default colors were just not very visible.  Here are some of the specific parameters I used, which produce a very nice green display (similar to how the OSD looks when run under Windows, etc.)

Here is my config file if you want to use it.  It should produce a nice green volume control bar long the bottom of your desktop when you use the up/down volume & mute keys.  It should also show the screen contrast level (when adjusted) as well.  And, if you change the "OSDTINKLIGHT" to ON, it will show the state of the LED light on the lid also:

```

#### TPB CONFIGURATION FILE

OSD             ON
#OSDZOOM        OFF
OSDTHINKLIGHT   OFF
#OSDDISPLAY     OFF
#OSDFONT        -*-lucidatypewriter-*-*-*-*-*-240-*-*-*-*-*-*
OSDCOLOR        Green
#OSDTIMEOUT     3
#OSDOFFSET      25
OSDSHADOW       0
OSDSHADOWCOLOR  Green
OSDOUTLINE      1
OSDOUTLINECOLOR Black
#OSDVERTICAL    25
#OSDHORIZONTAL  25
OSDPOS          BOTTOM
OSDALIGN        CENTER

```

As mentioned, I wanted to have it load as part of the startup applications in system/preferences.  However, in order to do that, you need to either make /dev/nvram writable by your user (at least I think that will work), or you need to give yourself more global root access when running sudo.  If you look at the command above for the start up, you'll notice I'm using sudo to start it (since my gnome session is under my non-root user account).  The method I used for that was to edit the /etc/sudoers file and add this line:

ray           ALL = (ALL) NOPASSWD: ALL

From what I can see from the sudoers documentation, that is supposed to allow my user account (in this case, user "ray") to issue any command via sudo and not be prompted for a password.  As far as I know, I have the above command correct.  Keep in mind, that can be viewed as a security risk (since you are giving your user account full root access via sudo).  In any event, that's how I did it and it works okay now.  I had previously attempted to add my user account to the group relating to the /deve/nvram device, but that didn't seem to work.  I also tried using /etc/rc.local, but that didn't work (probably because the X server wasn't started at that stage of the boot process).

Anyway, once you configure a startup application for tbp and grant the needed privileges, you should be able to reboot and it will load when your GNOME desktop fires up.  This can be confirmed with something like this command in a terminal window:

ps - aux | grep tpb

For debugging, you can also manually run tpb in a terminal window and then use CTRL+C to abort it (just run tpb).  While it's running, the on-screen display for the buttons should work.  From there, the trick is just to get it to load as a daemon via the startup applications control panel in system/preferences.

Anyway, I believe everything above is accurate as I recall doing it.  If anyone has any questions, feel free to post them here.  Hopefully this information will help other ThinkPad users get their keys & trackpoint working under Ubuntu again.

Enjoy!

Ray

---

### Post by timosha on 2010-06-03
Thanks a lot :P

To get the OSD working on my Thinkpad R51I added the following line 

```
cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

```

to /etc/rc.local. This gives me a nice black transparent OSD.

---

### Post by RayJohns on 2010-06-04
I noticed today that the gpointer-device-settings seems to conflict with the compiz fusion desktop manager.  The gpointer enabled the two button scrolling (using button #2) for scrolling websites.  However, this seems to conflict with the compiz use of button #2 to zoom the cube out and rotate it (via the viewport switcher's "initiate plugin action" setting).

I found this website:

[http://www.linuxquestions.org/questions/linux-hardware-18/gpointing-device-settings-settings-will-not-stay-after-reboot-762801/](http://www.linuxquestions.org/questions/linux-hardware-18/gpointing-device-settings-settings-will-not-stay-after-reboot-762801/)

It seems to describe the same problem (or similar problem) that I'm having - specifically problems with the ability to scroll websites using the trackpoint and middle scroll button between reboots.  If you go into gpoint-device-settings and change around the settings, then you can get that everything working again.  However, this causes the viewport switcher to die.  However, even if you change the binding keys in the viewport switch to different keys, upon reboot, the gpointer-device-settings seems to not hold its settings. (EDIT: see below - this loss of settings (after reboot) turned out to be related to the lack of a configuration file, not the confliction between key bindings).

Ray

---

### Post by RayJohns on 2010-06-05
Some good news!

After posting the original message, I noticed that the trackpoint settings, which are configured using the gpointer-device-settings panel, did not persist after rebooting.  

I also noticed that, when you configure the center scroll button for scrolling websites, this seems to conflict with the settings in the CompizConfig Settings Manager (specifically the key combination in the Viewport Switcher" called "initiate plugin action" that allows you to use the same key combination to pan out & spin the desktop cube).

For now, the biggest issue (for me) is getting the settings that allow me to scroll websites (using the center trackpoint button) to persist.  I was finally able to accomplish that, after a little hunting around, when I discovered this page:

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Scrolling](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Scrolling)

I followed the suggestions in the link above to create a file called **/usr/lib/X11/xorg.conf.d/20-thinkpad.conf** (as root).  I then added the following configuration section into that file:

```

Section "InputClass"
	Identifier	"Trackpoint Wheel Emulation"
	MatchProduct	"TPPS/2 IBM TrackPoint|DualPoint Stick|Synaptics Inc. Composite TouchPad / TrackPoint|ThinkPad USB Keyboard with TrackPoint|USB Trackpoint pointing device"
	MatchDevicePath	"/dev/input/event*"
	Option		"EmulateWheel"		"true"
	Option		"EmulateWheelButton"	"2"
	Option		"Emulate3Buttons"	"false"
	Option		"XAxisMapping"		"6 7"
	Option		"YAxisMapping"		"4 5"
EndSection

```

After rebooting, the scrolling for the websites worked.  The only issue was that this still had the effect of disabling the key combination in compiz fusion that controls the viewport switcher.  However, at this stage, being able to scroll websites, etc. using the center button is more important than being able to pan out and spin the cube in fusion.

Moving forward, I'm going to experiment around with changing the key combo for the viewport switcher in fusion and see if that resolves the conflicts.  If anyone has any comments, please feel free to post them here.  

Anyway, at least the above configuration file for X seems to address the issue with the gpointer-device-settings persisting between reboots.

Ray

---

### Post by RayJohns on 2010-06-05
Okay... success! :-)

Here is the latest: I ended up re-mapping the key combination in compiz fusion (in the compizconfig manager) for the viewport switcher, since both the scrolling and viewport switching couldn't be mapped to the same key combination (which is totally understandable).  What I did was to change the viewport switcher over to <control>+button #1, instead of just button #2 (which is the trackpoint center mouse button).  So now, to invoke the viewport switcher, I use the red rubber eraser button (i.e. mouse button) on the trackpoint and then press <control> along with the left trackpoint mouse button.  This allows me to spin the desktop cube and zoom in/out while selecting the desktop I want to view.

And, now, after adding the **/usr/lib/X11/xorg.conf.d/20-thinkpad.conf** file (as outlined above), I am able to use the center trackpoint button to scroll up/down on websites (and other applications) as I used to do under Windows XP - and this configuration persists between reboots as well.

So, everything is working great now!  Scrolling with the trackpoint and also full on-screen display for volume changing, etc.  

Ray

---

### Post by _Mark_ on 2010-06-05
> **timosha said:**
> Thanks a lot :P

To get the OSD working on my Thinkpad R51I added the following line 

```
cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

```

to /etc/rc.local. This gives me a nice black transparent OSD.

Thanks for that I always got the OSD for the screen brightness Fn home and End but never for the volume keys, but now works a treat

You're a :KS

---

### Post by JHolmes763 on 2010-11-05
> **RayJohns said:**
> The method I used for that was to edit the /etc/sudoers file and add this line:

ray           ALL = (ALL) NOPASSWD: ALL

From what I can see from the sudoers documentation, that is supposed to allow my user account (in this case, user "ray") to issue any command via sudo and not be prompted for a password.  As far as I know, I have the above command correct.  Keep in mind, that can be viewed as a security risk (since you are giving your user account full root access via sudo).

Have you, or anyone, found a way around having to edit /etc/sudoers? I followed your instructions and everything works so long as I run tpb as root, like you said. I've got accounts on this machine for my kids and wife, though, and I don't want to do the above with /sudoers on their accounts. I guess they don't get OSD unless there's another workaround for this. :)

Thank you for this post, btw. Got scrolling and OSD display working after switching over to Ubuntu a few days ago. 

-John

---

### Post by me_loco on 2011-05-31
Howdy all,
Sorry to resurrect an old post.
I'm having a problem with volume buttons not working in ubuntu 11.4, would the solution given above still valid?

Thank you.
P.S. i'm in love with 11.4 :wink:

---

