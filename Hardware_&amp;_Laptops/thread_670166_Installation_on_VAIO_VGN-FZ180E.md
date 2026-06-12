---
title: "Installation on VAIO VGN-FZ180E"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by sammydadams on 2008-01-17
i'm new to ubuntu and running on a sony vaio vgn-fz180e and these settings might work for others running similar configurations...this is written for noobs by a noob but it took a long time for me to find all the necessary tutorials to get my desktop beautiful and all the things that i paid for on my compy workin!

i finally have everything working relatively well and i wanted to share to those of you out there who have a VAIO and are having problems...the only things i haven't checked throughly are the blueray player, mic and a few other things that i have not used
what works:
N-vidia Driver
cd player/burner
media controls (above keyboard)
mute button (Fn F2)
headphone jack (including mute upon insertion)
s-video (must be inserted before logon or insert and press ctrl-alt-backspace)

what doesn't so far:
brightness (Fn F5, F6 & F7...I have tried a few fixes that broke Ubuntu... unfortunately i have given up)
the "wireless" light
the AV & S buttons above keyboard (for all i know these work but i just dont know how to configure them...i'm over it tho)

other nice things that are included...
AWN + Applets (using BZRs)
presession color fix (so the presession matches your theme)
grub GFX boot 
advanced desktop settings manager (controls compiz-fusion)

i take no responsibility for any of this stuff, it is things i found all around the net written by other people and i just wanted to store it all in one place...remember to backup EVERYTHING you change!!!!!!!

this is all the stuff that has worked for me:



AWN using BZRs


IMPORTANT!!! must have emerald installed through synaptic...this could be added below, ie emerald libemeraldengine0 libemeraldengine-dev, this will allow you to add some nice themes and such...i believe it also needs to be restarted...it wont tell you, but if it doesnt seem to work, give it a restart.

run in terminal
```

sudo apt-get install build-essential automake1.9 autotools-dev bzr libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf gnome-common python-dev python-gtk2-dev python-cairo-dev python-gnome2-dev emerald libemeraldengine0 libemeraldengine-dev

bzr co http://bazaar.launchpad.net/~awn-core/awn/trunk avant-window-navigator

```
Now you have avant-window-navigator directory
```

cd avant-window-navigator

./autogen.sh

make

sudo make install

```
This will complete the installation.

Install Avant Window Navigator Applets

Preparing Your system
```

sudo apt-get install libgnome-menu-dev librsvg2-dev libgtop2-dev libvte-dev libsexy-dev libnotify-dev python-alsaaudio python-libgmail

```
it may require more dependencies as the list of applets is updated, but these are what was required for me.

Download the source
```

bzr co http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk awn-extras

```
Install Avant Window Navigator Applets
```

cd awn-extras/awn-applets/awn-extras-applets/

```
./autogen.sh

make

sudo make install

This will complete the Avant Window Navigator Applets installation.

/**************************************************************/
GFX-Boot GRUB

REMOVE OLD GRUB
Code:
```

sudo apt-get remove grub

```
DOWNLOAD & INSTALL GRUB-GFXBOOT
Code:

wget [http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)

Code:

sudo dpkg -i grub-gfxboot_0.97-5_i386.deb

GET THE ANIMATED IMAGE & COPY IT TO YOUR GRUB DIRECTORY
(You can also get some from gnome-look.org or from the bottom of post #1 in this thread)
Code:

wget [http://quasarfreak.googlepages.com/message.suse](http://quasarfreak.googlepages.com/message.suse)

Code:

sudo cp message.suse /boot/grub/

EDIT YOUR GRUB MENU TO USE THE ANIMATED IMAGE
(good practice to backup the file first and then edit)
Code:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

Code:

sudo gedit /boot/grub/menu.lst

ADD THE FOLLOWING LINE  TO THE TOP OF THE FILE SO IT LOOKS LIKE THIS...
Code:
_____________________________________________________
|gfxmenu /boot/grub/message.suse                                                 
|                                                                                                         
|# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )             
|#            grub-install( 8 ), grub-floppy( 8 ),                                   
|#            grub-md5-crypt, /usr/share/doc/grub                                
|#            and /usr/share/doc/grub-doc/.                                         

THEN, INSTALL THE BOOT-LOADER

sudo grub-install /dev/sda


/**************************************************************/
Change Presession Color:

edit:
/etc/gdm/PreSession/Default as root (sudo)
look for
# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#dab082"
near the bottom
and change the value "#------" to the hex value of your choice 
("#000000" for black)


/**************************************************************/
Install Advanced Desktop Settings Manager:

run:
$ sudo aptitude install compizconfig-settings-manager
in terminal.
(make sure all compiz-fusion packages are fully updated through synaptic)


/***************************************************************/
Audio/Headphone Fix (VAIO):

IMPORTANT!!
make sure in software sources "pre-release updates" is NOT selected! (i did this once and made a mess of things)
...to simplify this, run automatix (i know some hate automatix, but it has never let me down =) ) first which will configure the software sources for you then IMMEDIATELY fix the ALSA driver as below!!!!!!!!!!!!!

reinstall ALSA driver
run:
$ sudo apt-get install module-assistant
$ sudo m-a update
$ sudo m-a prepare
$ sudo m-a a-i alsa
in terminal

add line:
options snd-hda-intel model=vaio
to
/etc/modprobe.d/alsa-base

not sure if this was needed...try above first along with modprobe.d fix and reboot/check

run:
$ sudo apt-get install linux-backports-modules-generic
in terminal


reboot

i also have xorg.conf settings that work very nicely and allow the use of the s-video cable...i'll share these soon, but for now i'll tell you to open up the terminal and type "nvidia-settings" and play around with some of the settings in there...


you might also be able to let it detect the screen if the s-video is connected to a TV and select detect displays in X Server Display Configuration...

the only reason i am not posting now is that i have recently reinstalled Ubuntu and i actually haven't recently tried out the s-video port so i want to make sure it still works after the reinstall before posting something that may not work after the reinstall...if steps are needed to get it working, of course i'll post those too

hope this helps someone as much as it would have helped me =)

---

### Post by sammydadams on 2008-01-17
here's my xorg.conf (make sure to back up your own):

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

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

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"

 #Primary display
    Identifier     "Monitor[0]"
    HorizSync       28.0 - 90.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"

 #TV
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

 #adjust using 'lspci' or cat /proc/pci 
    Identifier     "Device[1]"
    Driver         "nvidia"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"
    Option         "ConnectedMonitor" "Monitor[1]"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GT"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x1280"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_50"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "TV: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
EndSection

```

This creates a screen to the right of the main desktop, so if you move the cursor or drag a program window (say...VLC) over to the right it will show up over the s-video cable...because of this it will look like your background is stretched.

one odd thing about this is that in a program like VLC (the one i use) if i set it to go full screen it does it at the TV resolution but orients it on the "left"...i'm going to try to make the TV the left screen and see what that does, but you can move VLC over and under settings:switch interface select wxWidgets and you can maximize the video window on the TV side and either move the controller to the computer screen or minimize it all together...

i'm also playing with a driver for the webcam which may or may not be available here:
[HTML]http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/2.6.22-14-generic/[/HTML]
for the ricoh cam...for some reason i cant seem to get XawTV running to test it out...

and just cause i didnt state it before, the buttons over the keyboard seem to work out of the box, and i use the media controllers on Exaile music player (available through synaptic) and it works perfectly...

---

### Post by sammydadams on 2008-01-17
better be safe and send anyone looking here for info about the webcam:
[HTML]http://ubuntuforums.org/showthread.php?t=289836&highlight=vaio[/HTML]

---

