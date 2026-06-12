---
title: "I got Desktop Effects working on an X3100 (965 GMA). Here's how."
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by fd9_ on 2007-07-22
So far everything is working - the cube, the wobbly windows....the whole works. Note that this is NOT Compiz Fusion, this is simply how to enable Desktop Effects in Feisty with an Intel card...I don't know if this works with other cards, I just know it's working with an X3100.

Go to System --> Administration --> Synaptic Package Manager
Then go to Settings --> repositories
Then go to the "Third-Party Software" tab

Click "Add"
Copy and paste the following line and then click "Add Source"
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse

Add this line as well using the same procedure:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy main restricted universe multiverse

Now click "Reload" or go to Edit --> Reload package information

Now, open a terminal to install the following:

```

sudo apt-get install xserver-xorg-video-intel
sudo apt-get install xserver-xorg
sudo apt-get install ibgl1-mesa-dri
sudo apt-get install  libgl1-mesa-glx
sudo apt-get install libglu1-mesa
sudo apt-get install mesa-utils

```

Note that the libglu1-mesa package might not work, that's OK, don't worry.

Now, the last step. Enter in terminal:

```

sudo gedit /etc/X11/xorg.conf

```

Edit the "Generic Video Card" section to look like this:

```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option "monitor-TV" "TVOutput"
        Option  "CacheLines"    "32768"
        Option  "DRI"   "true"
        Option  "PageFlip"      "true"
        Option  "TripleBuffer"  "true"
EndSection

```

Then add this to the bottom:

```

Section "Monitor"
    Identifier "TVOutput"
    Option "Disable" "true"
EndSection

```

Reboot your computer, and go to the screensavers (just to make sure this works first):

System-->Preferences-->Screensaver

Preview a few of the screensavers in full screen, and if your system doesn't hang/crash after a minute, then this is a good sign! If your system does hang/freeze, then do NOT, I repeat, do NOT enable Desktop Effects!

However, if this is not the case, then you can go to System->Preferences->Desktop Effects and click "Enable Desktop Effects"

**Where's my cube?**

If alt+ctrl+arrow key does not work for you, enter the following in a terminal:

```

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

```

Most of this guide was taken from the following:
[http://wiki.debian.org/Installing_Debian_On/SantaRosa](http://wiki.debian.org/Installing_Debian_On/SantaRosa)

Good luck....

---

### Post by notwen on 2007-07-24
Any idea if this works w/ Beryl instead of the older Compiz?  I prefer Beryl over Compiz and as far as I have read her eon the forums, the X3100/965 chipset is not working w/ Compiz-Fusion.

---

### Post by sciurus on 2007-07-24
For reference, here is what this will do.

```

The following NEW packages will be installed:
  gcc-4.2-base xserver-xorg-video-intel 
The following packages will be upgraded:
  libgcc1 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libstdc++6 
  libxdamage1 mesa-utils xserver-xorg xserver-xorg-core 
10 packages upgraded, 2 newly installed, 0 to remove and 1008 not upgraded.
Need to get 22.5MB of archives. After unpacking 45.1kB will be freed.
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.5-0ubuntu14) but 2.6-3ubuntu1 is to be installed.
  libc6-dev: Depends: libc6 (= 2.5-0ubuntu14) but 2.6-3ubuntu1 is to be installed.
  libc6: Conflicts: tzdata (< 2007e-2) but 2007e-0ubuntu0.7.04 is installed and it is kept back.
Resolving dependencies...
The following actions will resolve these dependencies:

Upgrade the following packages:
libc6-dev [2.5-0ubuntu14 (feisty, now) -> 2.6-3ubuntu1 (gutsy)]
libc6-i686 [2.5-0ubuntu14 (feisty, now) -> 2.6-3ubuntu1 (gutsy)]
tzdata [2007e-0ubuntu0.7.04 (feisty-updates, now) -> 2007f-3ubuntu1 (gutsy)]

Score is -100

Accept this solution? [Y/n/q/?] Y

```

Edit: I had to remove xserver-xorg-video-i810 before I could install the new intel driver. Afterwards, everything worked as it should. It's nice to see that G965 will be supported in Gutsy.

---

### Post by WHiZZi on 2007-07-30
Wow. It works without problems on my Dell D830 with the X3100 videocard. I installed Beryl instead of Compiz and now the themes are also working. Very nice!

Perhaps some kind of bug, but when you select the optimal resolution 1920x1200 @ 24bit color, the screen will turn white when you start Beryl, Desktop Effects or Compiz. The color depth must be 16bit in order to activate the compiz/beryl/desktop effects!

---

### Post by ghindo on 2007-07-31
I followed your directions, and upon restarting, X is no longer working for me.

I get the following error messages:```
(EE)  Failed to load module "intel" (module does not exist, 0)
(EE)  No drivers available
```Is there any way for me to solve this through the command line?

**EDIT:**  I think it may be a result of a botched installation.  When I try```
sudo apt-get install xserver-xorg-video-intel
```I get an error message, which reads ```
dpkg: error processing /var/cache/apt/archives/xserver-xorg-video-intel_2%3a2.1.0-1ubuntu1_i386.deb (--unpack):
trying to overwrite '/usr/lib/libI810XvMC.so.1.0.0', which is also in package xserver-xorg-video-i810
Errors were encountered while processing:
/var/cache/apt/archives/xserver-xorg-video-intel_2%3a2.1.0-1ubuntu1_i386.deb
E:  Sub-process /usr/bin/dpgk returned an error code (1)
```

---

### Post by ghindo on 2007-07-31
Bump?  I'm really anxious to get my computer back up and running.

**EDIT:**  Nevermind.  After seeing scirus' post, I just typed ```
sudo apt-get remove xserver-xorg-video-i810
```Ran```
sudo apt-get install xserver-xorg-video-intel
```And everything was fine.

---

### Post by Syke on 2007-08-01
Now try out the screensavers and some heavy 3D games like Nexuiz and let us know how they work.

---

### Post by ghindo on 2007-08-01
> **Syke said:**
> Now try out the screensavers and some heavy 3D games like Nexuiz and let us know how they work.Not sure about games, but screensavers and Compiz work fine now.

---

### Post by WHiZZi on 2007-08-01
> **Syke said:**
> Now try out the screensavers and some heavy 3D games like Nexuiz and let us know how they work.


I installed Nexuiz on my laptop (that Dell D830 with x3100 videocard) and it worked. Even on the highest resolution (1920x1600x32bit) the game worked without any problems! And Beryl/Emerald were running when I started the game, Whoohoo

Only when there is much to do on the screen AND i'm firing things that produce lots of fire, the framerate dropped to 5. But normally it is on 98 fps on the highest res and texture quality GOOD.

---

### Post by Syke on 2007-08-01
Excellent! Which method did you use to upgrade the drivers?

---

### Post by ghindo on 2007-08-01
For some reason, I'm having difficulty playing video of any sort now, whereas before I installed the driver, it was no problem.  I also noticed that in the install process, "ibgl1-mesa-dri" wasn't installed because it couldn't be found.

Also, as an alternate way of configuring Compiz to fd9_'s method, you can always go to Synaptic and install the package "gnome-compiz-manager," if you're running GNOME.  After it's installed, just type the package name into the terminal and you can mess around with your Compiz settings!

**EDIT:**  Would it be safe to install all the updates that pop up when I add those two lines to my software sources?

---

### Post by Syke on 2007-08-01
> **ghindo said:**
> **EDIT:**  Would it be safe to install all the updates that pop up when I add those two lines to my software sources?

I think those updates will upgrade your whole system to Gutsy - probably something you don't want to do.

---

### Post by WHiZZi on 2007-08-01
> **ghindo said:**
> 
**EDIT:**  Would it be safe to install all the updates that pop up when I add those two lines to my software sources?


It will update all packages to the Gusty-version.

For those with problems, this was my exact apt-get install:

> 
sudo aptitude install xserver-xorg-video-intel xserver-xorg libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa mesa-utils mesa libdrm2 libxdamage libgl1-mesa libglu1-mesa mesa-utils x11proto-print xorg-server xnest xprint xserver-xorg-video-intel beryl beryl-manager
You can leave beryl and beryl-manager out of the line if you don't want that..

Next to that, I set the color depth to 16bit (don't worry, you won't see any difference)

---

### Post by ghindo on 2007-08-01
How do you configure color depth?

---

### Post by WHiZZi on 2007-08-01
The easiest way is to edit /etc/X11/xorg.conf

Hit ALT-F2 and type 
> 
gksudo gedit /etc/X11/xorg.conf


Search for the line that says:
DefaultDepth
(It's in the Screen Section)

and change the number to 16. Then, save it and press CTRL-ALT-BACKSPACE to reload X

---

### Post by ghindo on 2007-08-01
> **WHiZZi said:**
> The easiest way is to edit /etc/X11/xorg.conf

Hit ALT-F2 and type 


Search for the line that says:
DefaultDepth
(It's in the Screen Section)

and change the number to 16. Then, save it and press CTRL-ALT-BACKSPACE to reload XThis just messed up my display - I had to change it back to 24.

---

### Post by victorgreen on 2007-08-01
On a Lenovo X61 with the same graphics chip everyone else here has, changing the monitor section of the xorg.conf file from "generic moniitor" to "tv out" toastered X on my computer. Thank god I had thought to put the original entries in a text file on my desktop so I knew what to change back in nano in the conf file. 

Any sort of graphical anything- screen savers, full screen glx gears, and google earth crash X on my computer so badly that it cannot restart as much as it tries and I must hard reboot.

---

### Post by notwen on 2007-08-02
Recieved my Dellbuntu Inspiron 1420n yesterday.  I got Beryl working on it simply by enabling "Pre-Released Updates" in System->Administration->Software Sources->Updates and then running the Update Manager.  Installed Beryl using this [guide]("https://wiki.ubuntu.com/BerylOnFeisty").  Haven't gotten a chance to play w/ all of Beryl's configs, but wobbly windows and 3d cube work w/o a hitch so far.  The X3100 seems to be more than enough to run it smoothly.  Once reports of Compiz-Fusion running on it start appearing then I'll give it a try. Anyone else having luck w/ the X3100 on the Insipron 1420n?  =]

---

### Post by benry on 2007-08-02
> **ghindo said:**
> For some reason, I'm having difficulty playing video of any sort now, whereas before I installed the driver, it was no problem.  I also noticed that in the install process, "ibgl1-mesa-dri" wasn't installed because it couldn't be found.

Also, as an alternate way of configuring Compiz to fd9_'s method, you can always go to Synaptic and install the package "gnome-compiz-manager," if you're running GNOME.  After it's installed, just type the package name into the terminal and you can mess around with your Compiz settings!

**EDIT:**  Would it be safe to install all the updates that pop up when I add those two lines to my software sources?

Hi Ghindo,

The line with "sudo apt-get install ibgl1-mesa-dri" should be "sudo apt-get install libgl1-mesa-dri".

The L just got left off for some reason.

Don't apt-get update if you have these lines in your sources.list! You'll install all updates from gutsy, and you don't want that just yet.

---

### Post by benry on 2007-08-02
Hey WHiZZi,

I changed my DefaultDepth in my xorg.conf to 16, but I'm getting these huge banding display issues.

Could you attach your xorg.conf?

Thanks!

---

### Post by Syke on 2007-08-03
This solution is pretty good. I still have some performance issues. Some screensavers, like Helios, are horribly slow (not even 1 fps).

---

### Post by phynix on 2007-08-04
nvm

---

### Post by kuja on 2007-08-08
I tried this tutorial and it seemed to work at first (ie: after restarting X), but after a reboot, or some such, I started running into problems where X wouldn't start, so I reconfigured it to use the Vesa driver and it seems to be performing much better than I anticipated! I'm sure the performance isn't quite as good as the cards potential, but it seems to be a quick, easy, and stable solution (to instabilities in the i810) (at least for me, on my 1420n). Not sure if it'd cut it for a 3d window manager or not though ... but at least it's enough to play crack-attack :)

---

### Post by ghindo on 2007-08-08
I'm having trouble doing something I was able to do without trouble before installing these drivers - playing a game.  Specifically, playing Starcraft through WINE.  Before configuring x.org, this was no problem, but now I can't get it to work - when I launch the program, I get huge bands down my screen, and it freezes up.  How can I solve this?

---

### Post by lynchman on 2007-08-08
Thanks for this - it worked for me.  Now I can pick a screensaver without crashing X.  How nice. :)

Also the Wobbly windows works fine (I don't like it though - the blurriness freaks my eyes out), but the desktop on the cube has issues - when I switch workspaces the bottom and top taskbars on the desktop disappear and then the desktop is totally blank (I just see the background) and I cannot do anything.  I can still CTL-ALT-BACKSPACE out of X though.  Disabling the desktop effects gets the workspace switching working again.

---

### Post by victorgreen on 2007-08-10
X refused to start when i added the monitor information to xorg conf file. Desktop effects dont work, in fact nothing 3d works on my x61 with intel x3100gpu. google earth crashes, screensavers crash, and desktop effects still crash the computer

---

### Post by kdub432 on 2007-08-11
Do not perform the modifications to the xorg configuration file as described in the first post. I found that it breaks some X server types of programming tools that I use to do Xlib stuff. The optimal way I have found (thanks to an intel driver bug report) to fix the odd screen resolution issues without messing up xserver things is to do the apt-gets as instructed and then procede like this


modify the device section to look like this

```
 
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option "monitor-TV" "TVOutput"
        Option  "CacheLines"    "32768"
        Option  "DRI"   "true"
        Option  "PageFlip"      "true"
        Option  "TripleBuffer"  "true"
EndSection

```

do not add the second part to your xorg.conf


after modifying, reboot. Your screen will look a little funny, as the X server will have a hard time determining the screen resolution. Don't worry though, its still usable. Open up a command line and type

```

xrandr --output TV --off

```

This is a temporary fix, so watch be aware.


As an aside, you will need to leave the gutsy repos open, i think, or run the risk of hitting dependancy problems. 

Hope that helps :-D

---

### Post by zorkerz on 2007-08-11
I have an x61 with the x3100 card runny gutsy gibbon.
I performed the whole procedure from the first post. 

My system is not crashing. However when I try to turn desktop effects on I get this error "nvidia hardware not available" then all but the desktop background blanks for a sec and it asks if i want to keep the new settings. At this point it seems as of desktop effects are working except for the wobbly windows. Im not sure what all the effects are supposed to be.
There is no difference between normal and extra effects.

Any ideas?

Update: my brightness keys also no longer work. Before they did not actually change the brightness but did show the little icon with a brightness bar moving up and down.

---

### Post by everettattebury on 2007-08-19
I have the Dell 1420n with intel x3100 card, and had no problems installing compiz-fusion and getting it to run.

The only thing is, the water effect and blur effect do not work.  When I type <shift><F9> to start the rain, I get raindrops, but all of the windows on the desktop turn blank.  Same thing when I enable the blur effect.

Has anyone been able to make the rain or blur effects work on their 1420n, or on other systems using the x3100?

---

### Post by andywang603 on 2007-08-27
great one, It works for me.

---

### Post by thefekete on 2007-09-14
When updating package lists, I get the following:
```
E: Dynamic MMap ran out of room
E: Error occurred while processing libfaad2-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_multiverse_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

This is pretty much a fresh install of Fiesty (amd64) on an IBM/Lenovo R61i.

Please advise.

***UPDATE***
Problem was fixed by adding
```
APT::Cache-Limit "118388608";
```
in /etc/apt/apt.conf.d/70debconf

found in [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/113424]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/113424")

Also see [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61") for instructions on doing above with "apt pinning". This makes it possible to add repositories for specific packages, but not including them in standard apt-get procedures. This page explains the process of apt pinning in more detail: [http://jaqque.sbih.org/kplug/apt-pinning.html]("http://jaqque.sbih.org/kplug/apt-pinning.html")

---

### Post by keith11 on 2007-10-09
Hi,

I have Lenovo X61 tablet and I followed everything as suggested in the first post of this thread by fd9_. I modified my xorg.conf file and added the configuration script for the monitor too but when I rebooted it couldn't find an recover image and it pointed to the xorg.conf file. So I replaced the modified xorg.conf file with the original one and it booted again. This time, I uninstalled compiz and all it's components and configuration setting manager too and reinstalled all of them. I again modified the xorg.conf file as suggested and rebooted again but this time too, the same problem occurred. I don't understand why this would be happening but I am providing my modified xorg.conf file and if someone can please take a look at it and suggest a solution, that would be great.

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
        Option    "EmulateWheel"          "true"
        Option    "EmulateWheelButton"    "2"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option "monitor-TV" "TVOutput"
        Option  "CacheLines"    "32768"
        Option  "DRI"   "true"
        Option  "PageFlip"      "true"
        Option  "TripleBuffer"  "true"
EndSection

Section "Monitor"
    Identifier "TVOutput"
    Option "Disable" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

I would also appreciate if someone has any information on enabling the tablet functionality of my Lenovo X61t. Thanks.

UPDATE: I got the xorg.conf file working. I had "Generic Monitor" instead of "TVOutput" for the "Monitor" of the "Screen" section. I changed the "Generic Monitor" entry to "TVOutput" and the xorg.conf file loaded smoothly. I also found out how to enable the tablet functionality. All I had to do was to uncomment the last section of the xorg.conf file (the xorg.conf file I have posted here has that section already uncommented) where it asked to uncomment if it was a tablet. I am glad I can write in Xournal now. I am looking for other functions for Lenovo X61t now, like autorotate, functional tablet buttons, configuring the pen buttons, etc. Any ideas anyone?

---

### Post by keith11 on 2007-10-09
A quick update: The xorg.conf file is working but with compiz and the compiz settings manager installed, I don't see any effects when I press the key combinations. The tablet functionality is working but just in Xournal or such note-taking software, not like Vista where I can input text in any text box in any application. The third thing that is bothering me is even after installing win32 codecs and non-free codecs I am not able to play any movies/videos in Kaffeine. Totem and VLC just crash as soon as they attempt to open a video file. Any help regarding all these issues is greatly appreciated. Thanks.

Keith.

---

### Post by ghindo on 2007-10-10
> **keith11 said:**
> A quick update: The xorg.conf file is working but with compiz and the compiz settings manager installed, I don't see any effects when I press the key combinations. The tablet functionality is working but just in Xournal or such note-taking software, not like Vista where I can input text in any text box in any application. The third thing that is bothering me is even after installing win32 codecs and non-free codecs I am not able to play any movies/videos in Kaffeine. Totem and VLC just crash as soon as they attempt to open a video file. Any help regarding all these issues is greatly appreciated. Thanks.

Keith.I had similar troubles earlier this year, [as you can see]("http://ubuntuforums.org/showthread.php?t=514675").

I managed to solve them with the help of [this post]("http://ubuntuforums.org/showpost.php?p=3118766&postcount=14").

---

### Post by sixstorm on 2007-10-19
I needed to bump this thread now that Gutsy is officially out.  My Compaq C714NR has the X3100 graphics chip in it but nothing on the forums work.  My GLXGears works and fullscreen screensavers work just fine, just Desktop Effects won't enable.  Any clue guys?

---

### Post by elyk on 2007-10-20
Due to issues with video playback, the devs have decided to blacklist compiz on intel 965 chipsets (which the x3100 GMA is), but without providing any indication as to why the advertised "composite by default" is not working. Luckily, a workaround is present that provides both compiz and video. What you have to do is sudo nano /usr/bin/compiz , look for a line like this [code]T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:29a12" # intel 965 (xv video problem)[/url]
Comment it out, then save and exit nano.
You will now need to modify your player settings for video to continue to work : see this thread: [http://ubuntuforums.org/showpost.php?p=3118766&postcount=14](http://ubuntuforums.org/showpost.php?p=3118766&postcount=14)

---

### Post by sixstorm on 2007-10-20
Turns out I didn't have xserver-xorg installed . . . After I installed it, Desktop Effects WORK GREAT ON THE X3100!!!!  Just DON'T enable "Reflection" or else it will freeze.  Hopefully it will stay stable . . . I'm gone to do more testing.

---

### Post by ghindo on 2007-10-21
Is there any indication as to when this chipset will be properly supported by Ubuntu?

---

### Post by doppis on 2007-10-25
thanks it worked for me, great info guys.

---

### Post by noxxle on 2007-10-27
Does anybody know why the x3100 is blacklisted by default?

---

### Post by ghindo on 2007-10-28
> **noxxle said:**
> Does anybody know why the x3100 is blacklisted by default?Blacklisted?  What do you mean?

---

### Post by Toufas on 2007-10-28
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)
this worked for me.

---

### Post by ghindo on 2007-10-28
> **Toufas said:**
> [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)
this worked for me.This did not work for me.  I used ```
 sudo gedit /etc/xdg/compiz/compiz-manager
```, added ```
SKIP_CHECKS=yes
``` to the end of the file, restarted X, and it still did not work.  Any ideas?

---

### Post by BlueEight on 2007-11-01
When I got to Synaptic Packag manager, I got 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

And then I went to the terminal, and typed in:

"sudo dpkg --configure -a"

But it started trying to install Flash Player.Anyone know why?

---

### Post by juanbretti on 2007-11-03
Hi,
When I try to add the:
```
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
```
I get nothing.


When I try to run in the console
```
sudo apt-get install xserver-xorg-video-intel
sudo apt-get install xserver-xorg
sudo apt-get install ibgl1-mesa-dri
sudo apt-get install  libgl1-mesa-glx
sudo apt-get install libglu1-mesa
sudo apt-get install mesa-utils
```
Got some installation.

But no "Extra Visual Effects" :(

I try the Ctrl+Alt+BackSpace and error! The Safe system start.

I am trying the Ubuntu from the **LiveCD.**
Is any way to make it work from the **LiveCD**? The problem is that "I cannot reboot"

---

### Post by inchaos on 2007-11-05
I also used the SKIP_CHECKS="yes" to no avail, however, this morning I got a Compiz update and it magically works, quite perfectly, I might add.

However, I am no longer able to play video...I get the following error in Totem:
 
```
~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Please note that Totem itself opens fine, it just quits when I attempt to play video.
I also tried VLC, it froze for a bit and then quit.

I thought it was strange because it says 'insufficient resources', but I have 2 gigs of ram and my processor useage is at 0% and 1% for both processors (dual core).

Any ideas, other than disabling Effects?

---

### Post by inchaos on 2007-11-05
Oh.
And I have an Intel Integrated Graphics Controller that was blacklisted and it is allotted 512 MB of ram.

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

^^ This.

---

### Post by roktiw on 2007-11-25
got the same problem as mentioned above. didn't help changing resolution to 16, trying to switch off as many desktop effects, as possible, trying with totem, vlc with diffrent file formats.. is always the same: the window with movie simply shuts down. only flash films in browser works.

any idea how to solve it?

(i got Gutsy x64, but i don't think it's a x64 problem)

---

### Post by Yellow Pasque on 2007-12-06
BTW, for anyone following this guide, I would suggest double-checking your BusID. It may be different than the OP's (0:2:0)

```
sudo update-pciids
lspci | grep "VGA"
```

---

### Post by bro on 2007-12-09
I used this [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility") link to succesfully enable desktop effects. After that i ```
gstreamer-properties 
``` and on the window that pops up selected the video tab and changed it to X windows (no xv) so I could play video. 
No that I see it mentioned here, the rain gives grey windows indeed. Couldn't care less about that.

---

### Post by juanbretti on 2007-12-09
> **Temüjin said:**
> BTW, for anyone following this guide, I would suggest double-checking your BusID. It may be different than the OP's (0:2:0)

```
sudo update-pciids
lspci | grep "VGA"
```
Sorry, but I don't understand what is this for?
What are this codes for? :S

Thanks!

---

### Post by juanbretti on 2007-12-09
> **bro said:**
> I used this [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility") link to succesfully enable desktop effects. After that i ```
gstreamer-properties 
``` and on the window that pops up selected the video tab and changed it to X windows (no xv) so I could play video. 
No that I see it mentioned here, the rain gives grey windows indeed. Couldn't care less about that.

Hello, where is the "*the window that pops up selected the video tab*"?
Thanks!

Ups! I get it... forget my question :)

---

### Post by juanbretti on 2007-12-09
OK, now I have a different problem:

[[IMG]http://img388.imageshack.us/img388/3843/shadowsw7.th.png[/IMG]](http://img388.imageshack.us/my.php?image=shadowsw7.png)

Look at these shadows... are terrible.

Any ideas?

In the other hand: How do I install the **compizconfig-settings-manager**?
(I'm checking this out [http://despuesdegoogle.com/2007/08/06/despues-de-beryl-compiz-fusion/](http://despuesdegoogle.com/2007/08/06/despues-de-beryl-compiz-fusion/), but with no luck :()

---

### Post by iza_ciekawa20 on 2007-12-10
> **fd9_ said:**
> So far everything is working - the cube, the wobbly windows....the whole works. Note that this is NOT Compiz Fusion, this is simply how to enable Desktop Effects in Feisty with an Intel card...I don't know if this works with other cards, I just know it's working with an X3100.

Go to System --> Administration --> Synaptic Package Manager
Then go to Settings --> repositories
Then go to the "Third-Party Software" tab

Click "Add"
Copy and paste the following line and then click "Add Source"
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse

Add this line as well using the same procedure:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy main restricted universe multiverse

Now click "Reload" or go to Edit --> Reload package information

Now, open a terminal to install the following:

```

sudo apt-get install xserver-xorg-video-intel
sudo apt-get install xserver-xorg
sudo apt-get install ibgl1-mesa-dri
sudo apt-get install  libgl1-mesa-glx
sudo apt-get install libglu1-mesa
sudo apt-get install mesa-utils

```

Note that the libglu1-mesa package might not work, that's OK, don't worry.

Now, the last step. Enter in terminal:

```

sudo gedit /etc/X11/xorg.conf

```

Edit the "Generic Video Card" section to look like this:

```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option "monitor-TV" "TVOutput"
        Option  "CacheLines"    "32768"
        Option  "DRI"   "true"
        Option  "PageFlip"      "true"
        Option  "TripleBuffer"  "true"
EndSection

```

Then add this to the bottom:

```

Section "Monitor"
    Identifier "TVOutput"
    Option "Disable" "true"
EndSection

```

Reboot your computer, and go to the screensavers (just to make sure this works first):

System-->Preferences-->Screensaver

Preview a few of the screensavers in full screen, and if your system doesn't hang/crash after a minute, then this is a good sign! If your system does hang/freeze, then do NOT, I repeat, do NOT enable Desktop Effects!

However, if this is not the case, then you can go to System->Preferences->Desktop Effects and click "Enable Desktop Effects"

**Where's my cube?**

If alt+ctrl+arrow key does not work for you, enter the following in a terminal:

```

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

```

Most of this guide was taken from the following:
[http://wiki.debian.org/Installing_Debian_On/SantaRosa](http://wiki.debian.org/Installing_Debian_On/SantaRosa)

Good luck....

-----------------------------------------------------------------------------------------------------------------------

I have a problem with it , when I was doing this:  "Go to System --> Administration --> Synaptic Package Manager
Then go to Settings --> repositories
Then go to the "Third-Party Software" tab
Click "Add"
Copy and paste the following line and then click "Add Source"
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse
Add this line as well using the same procedure:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy main restricted universe multiverse
Now click "Reload" or go to Edit --> Reload package information", ubuntu show me the problems: 

- when I try to update informations of Ubuntu:

" Doesn't initiate informations about the packet/pack. 
Appear an insoluble problem during initiate informations about the pack.
Please to report pack's error 'update-manager' and add this informations of error '
E: Incorrect line 61 in the list of sources /etc/apt/sources.list (analysys distribution).
E: Can't to read sources list"

I don't know where I have a mistake and the second problem, when I try to open a manager packet od Synaptic:

"Error !.
E: Incorrect line 61 in the list of sources /etc/apt/sources.list (analysys distribution).
E: Can't to read  to the list.
Go to the configurations of repositories, then repair this problem.
E: _cache->open() failed, please report."

I don't know when I have a problem, maybe I did something wrong, please HELP, I am a begginer user of Ubuntu and I'm wondering if in terminal I can to repair this problem, remove some wrong repositories ?

---

### Post by bro on 2007-12-10
If you want to make changes via the terminal you can use a text editor that works in the terminal. To edit your sources.list you can do:
```
 sudo nano /etc/apt/sources.list
```

I didn't quite understand your problem but did you close other programs like synaptic while trying to update via commandline? Also the commandline is a wonderfull thing but you can just 'tick' on  the multiverse repos in a graphical window as well. which avoids mis spellings.

---

### Post by juanbretti on 2007-12-10
> **bro said:**
> ```
 sudo nano /etc/apt/sources.list
```


**nano**, is like **gedit**?

---

### Post by bro on 2007-12-10
nano is like gedit but you don't need xwindows to use it.

---

### Post by juanbretti on 2007-12-10
> **bro said:**
> nano is like gedit but you don't need xwindows to use it.
Cool, thanks!

---

### Post by push_harder on 2008-01-18
Hi.
When i enter 'sudo apt-get install ibgl1-mesa-dri'
It returns saying 'Couldn't find package ibgl1-mesa-dri'
Everything else was already up to date.
Although when i go to edit xorg.conf, there's nothing there at all...just a black page ready to write in...

Any help would be greatly appreciated :)

---

### Post by roktiw on 2008-01-28
hi,

with this guide i can run compiz on 7.10 and it works fine on 8.04 (hardy runs X3100) out of the box!

but still while i've desktop effects enabled i have **scroll very slow and laggy.** it uses lots of cpu resources. but while switching for example firefox into fullscreen there are no lags while scrolling at all.

maybe giving more VideoRAM to the X3100 will help?

any ideas how to make scroll faster while working in normal window (apart of turning compiz off)?

---

### Post by sledgeas on 2008-02-06
Hi,

I confirm slow scrolling persists with current compiz-fusion-0.6.0 and latest xf86-video-intel drivers (2.2.1 -- yes, NOT the older 2.1.1).

Does anyone has any updates on slow scrolling? I cannot even find a thread for that, regarding exactly the X3100 (965 GMA).

-- 
sledge

---

### Post by roktiw on 2008-02-16
intel drivers 2.2.2
compiz 0,7

still lags while scrolling

---

### Post by sledgeas on 2008-02-18
Looks like this is the driver aspect, as the still most stable i810 driver is **2.1.1**, has a nice scrolling.

This driver (2.1.1) I find even more fast!, whilst drawing primitives (try to change workspaces with Ctrl+Alt+Arrow Keys and then it slowly redraws e.g. your firefox window contents) even that without compiz and/or composite. 2.1.1 does it fast.

As further drivers (>=2.2.0) again showed a degraded performance in graphics

---

### Post by w3me on 2008-03-19
Hi.. everything was going fine until I reboot. 
I reboot then It tells xserver can't load, so I had to reconfigure the xserver-xorg
So it didn't work for me..  :mad:

now xorg file looks as before..

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

any idea..

---

### Post by sledgeas on 2008-04-02
INFORMATION TO EVERYONE: the new Intel Driver 2.2.99.901 still did not solve all problems for me, neither Firefox scrolling.. :/ What also still remains is low speed window repaint when without effects. I'd switch to effects now, but I notice now the shadows of windows borked :( Maybe I will switch with a new driver, but I'll first try the current SVN version lurking for other fixes I am concerned (like [http://forum.compiz-fusion.org/showthread.php?t=6679&page=2#17](http://forum.compiz-fusion.org/showthread.php?t=6679&page=2#17) :))

edit: compiz-9999 fixed the shadows problem (instead of my prev used old 0.6.2) (the latest git version [http://compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository](http://compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository))

in reply to w3me:
Sorry I quite don't get what you are talking about.
Did you upgrade to a newer intel driver? What do you mean xorg.conf looks `as before'. As the one you pasted is configured to work with an intel card OK.
So you did not change it?

cheers

-- 
sledge

---

### Post by leandromartinez98 on 2008-05-22
Desktops effects worked well for me (VAIO VGN-NR11Z, GMA X3100) simply
by putting the "option DRI true" in the xorg.conf file. The other options
didn't make much difference. The packages were installed by default in 
Hardy. However, some Open-GL applications (Pymol and VMD) have problems
running while the effects are habilitated. The screenservers work fine.

---

### Post by kmb`` on 2008-05-22
hey i did everything, screensaver works, when i go to enable the visual effects to extra effects it seems to work, but when i close the window and reopen its back to none any clue?
im a hp dv6626ca

---

### Post by sledgeas on 2008-05-22
> **kmb`` said:**
> but when i close the window and reopen its back to none any clue?
im a hp dv6626ca

Hi, Ubuntu Hoary still has general frequent issues with closing lid..

For all the others info on recent intel driver (xf86-intel-i810) v2.3.1:

Desktop Effects work (glxgears flickers a bit, cannot properly handle move, gives 851 FPS), but Firefox (3 Beta 5) still scrolls slowly. And “playing with fire“ results in totally white cube

Without desktop effects:
* redrawing of windows (when switching workspaces) is still not as effective compared to all-time-winner xf86-intel-i810 v2.1.1, but way faster then 2.3.0!
* external VGA or TV still does not work (works with 2.1.1)
* glxgears now works smoothly and correctly reports 831 FPS

ATTENTION: All-time-winner 2.1.1 now scrolls Firefox 3 Beta 5 OK under desktop effects! (note my mesa and drm versions below) Can someone reconfirm please?

(My system HP 6710b, X.org 1.4.0.90-r3, mesa 7.0.3, libdrm 2.3.0, x11-drm 20060608:
[https://wiki.ubuntu.com/LaptopTestingTeam/HP6710b](https://wiki.ubuntu.com/LaptopTestingTeam/HP6710b)
[http://gentoo-wiki.com/HARDWARE_HP_Compaq_6710b#Video_.28Intel_X3100.29](http://gentoo-wiki.com/HARDWARE_HP_Compaq_6710b#Video_.28Intel_X3100.29))

-- 
sledge

---

### Post by leandromartinez98 on 2008-05-22
I have all desktop effects working, but 3D applications do not work if
compiz is working. I have installed the packages and put the "DRI true"
option in xorg.conf. (Vaio with GMA X3100)

When I enable desktop effects, glxgears run, but if I try to move its windows
it starts to behave oddly, like the gears stay where they were, for example.
Furthermore, I cannot even play the chess game in 3D mode. Everything works
perfectly without the desktop effects.

I searched the forums and it seems something relativelly common, but nobody
didn't get an answer yet. Any help would be appreciated.

---

### Post by leandromartinez98 on 2008-05-22
Ok, I found this bug report, it is my problem, and apparently it has
no solution yet and will not have so soon.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/96991](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/96991)

Nothing to be done for now.

Good explanation here:

[http://hoegsberg.blogspot.com/2007/08/redirected-direct-rendering.html](http://hoegsberg.blogspot.com/2007/08/redirected-direct-rendering.html)

---

### Post by kmb`` on 2008-05-23
i found a usefull tip, and my desktop effects are finnaly working, the video card was blacklisted and to unblacklist it you have to :


1. sudo apt-get install xserver-xgl .
2. Ctrl+Alt+Backspace .
3. remove SKIP_CHECKS from ~/.config/compiz/compiz-manager OR /etc/xdg/compiz/compiz-manager (only if you added it)
4. enable compiz in System->Preferences->Appearences->Visual Effects.

And thats it!

* note: video playback will have issues.

[http://ubuntuforums.org/showthread.php?t=674123](http://ubuntuforums.org/showthread.php?t=674123)

---

