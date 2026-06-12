---
title: "[SOLVED] Graphics card settings cant save to file"
date: 2008-08-22
forum: General Help
---

### Post by Tony_photoplus on 2008-08-22
Great I have managed to get the Nvidia loaded.  But, now it is not stable.  When I re-boot Nvidia drivers do not load and I have to Systems > Admin Nvidia server settings and reset to 1024x768 resolution.  I tried to sav e config to file it sates it cant backup.  What is the answer to this please.

Thank you

Tony

---

### Post by livestockPimp on 2008-08-22
you can edit your resolution in the "xorg.conf" and put in here the default modes you want your pc to load.

The xorg.conf is located in /etc/X11/xorg.conf.

If you look in here there will be a line towards the end that will have:


        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1024x768"
        EndSubSection

you can modify the "Modes" line and change the resolution.

---

### Post by Tony_photoplus on 2008-08-22
> **livestockPimp said:**
> you can edit your resolution in the "xorg.conf" and put in here the default modes you want your pc to load.

The xorg.conf is located in /etc/X11/xorg.conf.

If you look in here there will be a line towards the end that will have:


        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1024x768"
        EndSubSection

you can modify the "Modes" line and change the resolution.

It doesnt have this config at all in the script:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "Module"
	Load		"glx"
EndSection

And thats it.  Cant see anything there, I even looked at the backup and again nothing.

So do I add something in?

Tony

---

### Post by livestockPimp on 2008-08-22
Add this to the bottom, it should work.
(just change the resolution to what you want it to be!)

SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection

You can also use "sudo dpkg-reconfigure xserver-xorg"
This will go through a basic wizard on configuring your display and generate your xorg.conf for you!

---

### Post by nikobor on 2008-08-22
Why don't you install nvidia-settings?
sudo apt-get install nvidia-settings
Then you just start nvidia-settings by:
sudo nvidia-settings
and then open the section X Server Display Configuration. When you make the changes, use the Save-to-Configuration-File option. For me, nvidia-settings is a really helpful tool.

---

### Post by Tony_photoplus on 2008-08-22
Just logged in and thank you for your replies.  The problem has worsened - I have no Nvidia access, all I get now is:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

All this sounds double dutch and looking at a load of script and told what to take off and what to load is confusing.  Mind you on my third morphine tablet today doesn't help.  So ABC please if can bare with me I need to sort this out.  I really thought I had cracked it, but with my luck I always get the bum end of the deal!

Just to say there are no Nvidia setting to be able to work on now its blank.

Next move please

Tony

---

### Post by livestockPimp on 2008-08-22
if you are at a console have you run as the prompt suggested "sudo nvidia-xconfig"

---

### Post by Tony_photoplus on 2008-08-22
Thanks did that and got this:
photoclub@photoclub-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first CorePointer in the config input list.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

photoclub@photoclub-desktop:~$ 

Doesn't look good.

---

### Post by nikobor on 2008-08-22
sudo apt-get install envyng-gtk
Start it and remove the nvidia driver and then install it again. I think this is the easiest way.

---

### Post by Tony_photoplus on 2008-08-22
Funny enough Nikobor I have just done that.  But the problem still exists with trying to save the setting using Nvidia's software.  When I try and save the setting it states:

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'

However there is a preview before you save and I did copy this to text file

See below.  Now if all this is text controlled would it be ok to paste this in?  ..................

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Jan 22 19:53:46 PST 2008
# xorg.conf (X.Org X Window System server configuration file)
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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Proview"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX Integrated GPU"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by nikobor on 2008-08-22
I suppose you didn't start nvidia-settings with "sudo nvidia-settings" in the terminal. You need sudo to save the changes.

---

### Post by Tony_photoplus on 2008-08-22
Many thanks it is now saved.  So hoping it will be resolved.  Thank you so much

Tony

---

### Post by livestockPimp on 2008-08-23
yes, you should just be able to use that config file and paste it into the new xorg.conf, just make sure you back it up first.

from a command prompt:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
sudo nano /etc/X11/xorg.conf
(make changes necessary here and then "ctrl + x" to exit, this will prompt to save)

if this works after you reboot then all is good, if there is a problem you can revert back by:

sudo mv /etc/X11/xorg.conf.orig /etc/X11/xorg.conf

---

### Post by Tony_photoplus on 2008-08-23
Ah, thats interesting thanks.  I have another 3 computers to tackle and will ensure I use it if necessary

Tony

---

