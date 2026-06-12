---
title: "Acer 5920(G) - tweaks for Intrepid"
date: 2008-11-30
forum: Hardware
---

### Post by FokkerCharlie on 2008-11-30
Please note:  New thread created for Karmic Koala [here]("http://ubuntuforums.org/showthread.php?t=1313893").  It seems that our methods need changing!

Intrepid works generally very nicely on the Acer Aspire 5920 series laptops that I am familiar with.  There are one or two glitches, however, including the media keys (on the right hand side) being mapped as mouse buttons, the hotkeys (fn+blue symbols) not being quite right, and the &#8364; and $ keys adjacent to the arrow keys not working.

All the guidance below is what works for me.  I am not an expert, and all advice comes with the usual disclaimers!

Anyway, here goes the fixes:

[FONT="Arial Black"]Part 1a:  Media Keys (Intrepid)[/FONT]  See part 1b for a method that works for Jaunty and Karmic.

Go to System > Preferences > Sessions.  Then under 'Startup Programs' press the 'Add' button.  Make the fields thus:
Name:  Remap media keys
Command: xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
Comment:  Whatever you like!

Then save.  Quick explanation:  the media keys are identified as a touchpad, device 4 (on my PC), the xinput command swaps the mapping of buttons 1-4 to 17-20.

[FONT="Arial Black"]Part 1b:  Media Keys (Jaunty / Karmic)[/FONT]

Unfortunately, in Jaunty this no longer works.  We need a couple of extra steps here.  Instead of the above command in sessions, we need to call a script, eg:

Command: sh /home/username/script_location/jauntymediakeys.sh

And save.  Then, create a text file for you script, eg:

gedit /home/username/script_location/jauntymediakeys.sh

And put this in it:

```
#!/bin/sh

#Remaps the second Synaptics touchpad entry.

xinput set-button-map "`xinput list | grep Synaptics | tail -1 | grep -o id=. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16

#Note- to remap the first entry, replace tail with head.
```

And save.  Thanks to StuartN for his help on [this]("http://ubuntuforums.org/showthread.php?p=715168") thread.

Now back to the instructions that work for Intrepid and Jaunty:

If you have not yet done so, install xbindkeys and xvkbd, and open the configuration file for editing:

```
sudo apt-get install xbindkeys
sudo apt-get install xvkbd
gedit .xbindkeysrc
```

Copy this text into the file:

#Mutlimedia control keys:
```

"xvkbd  -text "\[XF86AudioPlay]""
    b:17

"xvkbd  -text "\[XF86AudioStop]""
   b:18:

"xvkbd  -text "\[XF86AudioPrev]""
    b:19

"xvkbd  -text "\[XF86AudioNext]""
    b:20
```

This works perfectly with Exaile, I am sure that it can be made to work with other players!  While you're here, you can map your blue 'e' key to run Exaile, or whatever else you want:

```
#Map 'e' key to launch exaile
"exaile %f"
    c:219
```

If you're using Jaunty (not sure about Intrepid), you will need to create a .fdi file to enable adjustment of the touchpad:

```
gksu gedit /etc/hal/fdi/policy/touchpad.fdi
```

put this in the new file:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input">
        <merge key="input.x11_options.SHMConfig" type="string">True</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
    </match>
  </device>
</deviceinfo>
```

(thanks to Mohr Tutchy for that one)

And you're done.  Restart for the changes to take effect.  **NOTE:  THE BLUE E-KEY WILL ONLY WORK AFTER YOU HAVE COMPLETED PART 4 BELOW**

[FONT="Arial Black"]Part 2: The Hotkeys[/FONT]

With thanks to Alkis and Percy for the work on [this]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/281951") bug.

Download a new fdi file from [here]("http://launchpadlibrarian.net/23227355/30-keymap-acer.fdi").  Now you need to replace your old /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi file with the one you just downloaded.  The steps below assume that you have downloaded the file to your home folder.

**THIS IS RISKY.  PLEASE ONLY FOLLOW THESE STEPS IF YOU UNDERSTAND THEM, AND ARE ABLE TO UNDO THEM.  DO THIS AT YOUR OWN RISK!**

```
sudo mv /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi /home/<yourusername>/30-keymap-acer-old.fdi
sudo cp 30-keymap-acer.fdi /usr/share/hal/fdi/information/10freedesktop/
```

That should fix any issues with your fn keys.  It also sets us up for part 3.

[FONT="Arial Black"]Part 3:  Enable the &#8364; and $ keys[/FONT]

We need to make a script that will run every time you log in.  In this example, I will make a hidden folder in your home folder and put it in there.

Open a terminal, and type:
```
mkdir .startscripts
cd .startscripts
gedit eurodollar.sh
```

And paste this code:
```
#!/bin/sh
echo 'keycode 186 = dollar dollar dollar dollar dollar' | xmodmap -
echo 'keycode 185 = EuroSign EuroSign EuroSign EuroSign EuroSign' | xmodmap -
```

Now, to set this script to run on every login, go to System > Prefs > Sessions, and under Startup Programs, add again:
Name:  EuroDollar
Command: sh /home/<username>/.startscripts/eurodollar.sh
Description: Enables &#8364; and $ keys.

And close.  You should see this come into effect when you next restart X, or log out/in.

[FONT="Arial Black"]Part 4:  Fix the glitchy brightness adjustment.[/FONT]

You may have noticed that the brightness control keys (fn+ left/right arrow) control the brightness erratically. You can fix this by blacklisting the video module:

```
gksu gedit /etc/modprobe.d/blacklist
```

And insert the following lines at the end of the file:
```

# fix keyboard brightness control
blacklist video
```

Save and close the file.

I am unaware of any side effects of blacklisting video in this way.  I see no problems here with compiz, video playback etc, but please report if you have a problem.  I believe that this issue is properly fixed in Jaunty.

If this doesn't fix your brightness control, try adding a parameter to your menu.lst:
```

gksu gedit /boot/grub/menu.lst
```

And find the line that you are using to boot Ubuntu, it will look something like:

```
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=918db6e7-1f3c-4eed-8ceb-2bd05de3ca0c ro quiet splash vga=792
```

and add ```
acpi_backlight=vendor
``` to the end of the line, eg:

```
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=918db6e7-1f3c-4eed-8ceb-2bd05de3ca0c ro quiet splash vga=792 acpi_backlight=vendor
```

Please note that if you have multiple users on your system, you will need to follow parts 1 and 3 for each user.

I hope that this is of some help.  If you find any bugs, or have suggestions, please post them or pm me.  If it works for you, I'd also appreciate knowing that it works for you.

Cheerio
Charlie

---

### Post by iggykoopa on 2008-11-30
one thing you may want to try for the backlight is the app xbacklight, it's in the repos. It lets you manually set the backlight, and tells you what it is set at now. It shouldn't be to hard to make a script that see's what your backlight is at now and drop it 5 or 10 percent.

---

### Post by FokkerCharlie on 2008-12-04
Just added the fix for brightness keys- with thanks to Alkis and Percy, again!

Charlie

---

### Post by 3poD on 2008-12-10
thanks for posting all your tweaks ;) brightness control is still not perfect but its better than before

i appreciate your time and sharing this how-to, thanks again

---

### Post by FokkerCharlie on 2008-12-11
Glad it helped, 3poD.

I notice, however, that the media keys are back to 4,5,6,7 again after a suspend/resume.  Anyone know how to get a script run on every resume?

I would like this to happen:

```
#!/bin/sh

#Set media touchpad keys to 17 18 19 20
xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```

I have put this script in /etc/acpi/resume.d, but it doesn't seem to work!

Charlie

Cheers
Charlie

---

### Post by 3poD on 2008-12-18
I have a working solution for suspend/resume issue.. 

1. create script 01media_keys.sh in /etc/pm/sleep.d:
```

#!/bin/sh

set_media_keys() {
sleep 10
DISPLAY=:0.0 su *your_username* -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
}

case "$1" in
	thaw|resume)
		set_media_keys &
		;;
	*)
		;;
esac

```

---

### Post by 3poD on 2008-12-24
let me know if it works for you

---

### Post by FokkerCharlie on 2008-12-24
Hi 3poD

Thanks for this, unfortunately, it did not work for me.  I also created a new thread for this issue [here]("http://ubuntuforums.org/showthread.php?p=6429044#post6429044"), but am still struggling!

I wonder if I have broken something without realising it...

Cheers
Charlie

---

### Post by 3poD on 2008-12-24
try to change sleep to 15 secs... or you can try to move the script to /usr/lib/pm-utils/sleep.d, or.. 

but it should work.. if it works for me.. (did you mean sleep or hibernation, hibernation takes longer, so that could be a problem)

---

### Post by FokkerCharlie on 2008-12-27
Hmmmm

Still doesn't work for me.  I now suspect that I have done something odd to my setup here that makes it subtly different to others'!

Not to worry.

Charlie

---

### Post by 3poD on 2008-12-28
try to change the command after "-c " to something else (i.e. gnome-terminal) to see if it works.. or, replace the whole line with just gnome-terminal

---

### Post by Harmshi on 2008-12-28
You state in the howto that this command is used to map the euro and dollar keys:

> Now, to set this script to run on every login, go to System > Prefs > Sessions, and under Startup Programs, add again:
Name: EuroDollar
Command: sudo /home/<username>/.startscripts/eurodollar.sh
Description: Enables € and $ keys.


However, the euro and dollar keys only work for me when using this command:
sh /home/<username>/.startscripts/eurodollar.sh

is this only me? I always have to use the sh command to run scripts.

---

### Post by 3poD on 2008-12-29
i think it's just a mistake in the how-to.. i didn't try it as i dont use these characters/keys, but i think you can just replace "sudo" with "sh" and everything will work ;)

---

### Post by FokkerCharlie on 2008-12-29
Yes, you are right- my mistake.  I will update the howto with the new info in a tick!

Thanks for flagging this up.

Charlie

---

### Post by errenay on 2009-01-04
@FokkerCharlie - thank you for tweaks. I have added link to your thread in my old one.

---

### Post by SawmSawn on 2009-02-06
First of all thank u for these how to's. unfortunately neither my media keys nor $ and € keys still don't work. please have a look on my xorg.conf and udev-rules, cause i got no reaction on xev with the media-keys

xorg.conf

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Scroll"
	Driver		"evdev"
	Option		"Device"		"/dev/input/vscroll"
	Option		"SendCoreEvents"	"true"
EndSection

Section "InputDevice"
	Identifier	"Touch"
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/vtouch"
	Option		"Protocol"	"event"
	Option		"SHMConfig"	"true"
	Option		"UseSHM"	"true"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option 		"SendCoreEvents" "true"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
Identifier "nVidia Corporation G80 [GeForce 8600M GT]"
Boardname "nv"
Busid "PCI:1:0:0"
Driver "nvidia"
Screen 0
Option "NoLogo" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1280x800"
Horizsync 30 - 75
Option "DPMS"
Vertrefresh 60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation G80 [GeForce 8600M GT]"
Monitor "Generic Monitor"
Defaultdepth 24
DefaultDepth 24
Option "metamodes" "1280x800_60 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 	"Default Screen" 0 0
	Inputdevice 	"Generic Keyboard"
	InputDevice	"Touch"
	InputDevice	"Scroll"
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
EndSection
```

udev-rule

```
SUBSYSTEMS=="input", ATTRS{phys}=="isa0060/serio4/input0", KERNEL=="event*", NAME="input/vtouch"
SUBSYSTEMS=="input", ATTRS{phys}=="isa0060/serio3/input0", KERNEL=="event*", NAME="input/vscroll"
```

PS: I did all tweaks, except the las cause my brightness control works fine for me

---

### Post by FokkerCharlie on 2009-02-07
Hi Sawm

A couple of notes- the udev files no longer have any impact on Intrepid.  They were a fix that worked for Hardy (and possibly before) only, so you can get rid of them.

Your xorg.conf file is much longer than mine, have you modified it yourself?  Here is mine:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildd@palmer)  Thu Jun 26 06:22:40 UTC 2008

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

Are your illuminated media keys not working, is it just the € and $ keys you are having a problem with?

Please post the output of:

xinput list

Cheers
Charile

---

### Post by SawmSawn on 2009-02-11
Hey thanks for reply. I have copied some parts of my xorg.conf out of other acer 5920g owners xorg.conf and followed the howto for the 2. touchpad of the german ubuntuusers wiki.[http://wiki.ubuntuusers.de/Baustelle/Acer_Aspire_5920G?highlight=acer]("http://wiki.ubuntuusers.de/Baustelle/Acer_Aspire_5920G?highlight=acer")

the xinput list output is:
```
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Generic Keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Touch"	id=3	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"Scroll"	id=4	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 10000
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 10000
"Configured Mouse"	id=5	[XExtensionPointer]
	Num_buttons is 9
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=8	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255

```

---

### Post by SawmSawn on 2009-02-11
ahh forgot to say: both dont work, neither iluminated keys nor $and€ keys

---

### Post by FokkerCharlie on 2009-02-12
Sawm, that guide is for Hardy and before.  It won't work with Intrepid.

You need to follow the steps at the top of this thread, and can undo the other stuff.

Charlie

---

### Post by FokkerCharlie on 2009-02-28
Bumping this thread, as we now have backlight brightness control working perfectly- see the top post for the changes (adding acpi_backlight=vendor) to the kernel line in menu.lst.

Works fine in Intrepid, feedback appreciated.

Charlie

---

### Post by Shooree on 2009-03-21
First of all, thank you for sharing your experiences. Unfortunately, the how-to doesn't resolve my problems in the slightest.

I've got a 5920G, running Xubuntu 8.10 and following your how-to to the letter. Absolutely no results. Maybe I'm doing something wrong when creating the startup scripts? I use Settings Manager>Autostarted apps>new. 

Unfortunately, I'm very new to customising. To recap, tried the media keys (step 1) and EuroDOllar (step 2) thing, none work. Restarted X many, many times whilst following the how-to on a vanilla system.
 
should I post any terminal outputs? Also hibernation doesn't seem to work, but that's another issue. :(

Really would appreciate any sort of a meaningful answer, even if it was to switch to Ubuntu from Xubuntu or GNOME from Xfce4.

---

### Post by FokkerCharlie on 2009-03-22
Hi Shoree

Sorry it doesn't work for you.  I'm not an xcfe expert, but I would have thought that it should work as per Gnome in these respects.  Perhaps someone will correct me if I'm wrong about this?  If you're able to have a go at a gnome setup in parallel to your xcfe setup, it's worth a go.

I'm also not great at keymapping, so let's have a look at your media keys first.  Please post the output from:

xinput list

That might give us a clue as to what is going on in your setup.  And, while we're at it, post your xorg.conf here.  Remember to use the [code] tags!

Cheers
Charlie

---

### Post by Shooree on 2009-03-22
oh, lovely! Thanks for deciding to help. Here goes nothing:

xinput list:

```
shooree@shooree-laptop:~$ xinput list
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"Keyboard0"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Mouse0"	id=3	[XExtensionPointer]
	Num_buttons is 9
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=5	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=6	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=8	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech USB Receiver"	id=9	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
shooree@shooree-laptop:~$ 


```

xorg.conf 

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Thu Feb  5 00:18:17 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Thanks again for looking into this. I should probably add that I followed your instructions, the first two steps at least (eurodollar and trying to remap mediakeys), so that you have that in mind. I'm anxious to see what we can do. I'm also on #xubuntu with the same nick, feel free to poke me there.

---

### Post by FokkerCharlie on 2009-03-22
No probs, Shoree

The xinput command that you will have added to your sessions refers to device 4.  From your xinput list, device 4 on your machine is Macintosh button emulation.  The root cause of that is a problem in your Xorg.conf.

So, here's what I suggest:  edit your xorg.conf, and comment out all the references to mouse0 and keyboard0.  Alternatively, use mine as a replacement:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildd@palmer)  Thu Jun 26 06:22:40 UTC 2008

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
#    InputDevice    "Keyboard0" "CoreKeyboard"
#    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

#Section "InputDevice"
#    Identifier     "Keyboard0"
#    Driver         "keyboard"
#EndSection

#Section "InputDevice"
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

Whatever you do, make sure that you make a backup that you can restore from the terminal first.

Let us know how that works for you.  Anyone an expert on key mapping to help shoree?  I don't have a great understanding.

Cheers
Charlie

---

### Post by Shooree on 2009-03-23
Meh, no luck. Tried both editing my own and pasting your xorg.conf and I haven't noticed any changes. i.e. my "play" and "stop" media keys still act as if they're mousewheel up/down and rewind buttons as if they are mousewheel tilt left/right... 

Did manage to run the EuroDollar script at startup, though. I guess it was just me, in the end. Read up a bit on correctly addressing stuff and now it works. So thanks for that, Charlie, you're the guy.

The hotkeys work, and the brightness thing with blacklisting the video, as well.

Can we try anything else for media keys? Thanks for your continued help.

Also, being that you presumably run the same hardware setup as me, could you tell me if your hibernation works correctly? Noone seems to be answering my plea for help in the thread I made to try and get the answer> 

[http://ubuntuforums.org/showthread.php?t=1103205]("http://ubuntuforums.org/showthread.php?t=1103205")

---

### Post by FokkerCharlie on 2009-03-23
Hi Shoree

What you can do is, in a terminal, type   xinput list    again.  Look for "SynPS/2 Synaptics TouchPad".  You should see two instances of this.  Look at the second one, and then type:

xinput set-button-map "n" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16

But replace n with the id number that is written next to "SynPS/2 Synaptics TouchPad".  If that doesn't work, try using the other instance that you saw from xinput list.  The one that works, you can put in your sessions.

Sorry, but hibernation is a dark art, and not something I really use.  Good luck!

Charlie

---

### Post by Shooree on 2009-03-23
cheers, Charlie, I'll try it immediately. 

What I just realised is that the "suspend" option actually works! Which is better than not having anything. :) 

Anyway, I'll edit this post with an update. Thanks, man.

Right, so I substituted n=4, which is the second one in the list. The good news is that it doesn't seem to equalise media keys with the mousewheel anymore. I still can't get it to operate in exaile, though. I'll try putting the xinput command in autostart and restarting X.

---

### Post by FokkerCharlie on 2009-03-23
Ensure that you have followed the steps relating to xbindkeys.  Then set up your keys using System > Prefs > Keyboard Shortcuts.

---

### Post by gmclean on 2009-03-25
Thanks to everyone for the tips in this thread.  I now have my media keys working.

I had trouble initially because where you recommended adding the xinput command to the session startup with the name "Remap media keys", I used the name "Acer 5920 Media Keys" and it didn't work.  Maybe because the name starts with 'A' it gets run first.  I ended up combining the xinput command in with the xmodmap script and as long as it has a sleep at the beginning it seems to work.

My euro and $ keys don't seem to do anything.  xev shows no event at all when I press them.  meh.

Also I took the suggestion from another thread of adding --no-start to the rhythmbox-client commands in the .xbindkeysrc.  If I want rhythymbox I start it with the 'e' key.  If I don't then it doesn't start when I bump the media keys.

Thanks again.

---

### Post by Shooree on 2009-03-26
stupid RL chores... anyway, I'm back and still trying. I just realized that, in my keyboard prefs window, I unchecked the box next to "use X configuration", because I couldn't find any other way to easily switch keyboard layouts (I need regular US and SR). Could that be the reason why all of this wasn't working?

Also, under the keyboard model menu, I found an "Acer laptop" choice, which I selected instead of the "generic" thing - but when I turn X configuration on, it all becomes locked and I believe unusable. Am I correct? I need someone to explain to me how this works. :(

@gmclean what do you mean by xmodmap script? I believe Charlie referred to it only in the context of... omg! my euro and dollar aren't working now. I was about to use them. Must have made a mess with ticking that X config thing. Damn. This will take so much experimenting for me. Please explain exactly what you did, if you can.

EDIT: &#8364;$ working, but layout switching completely went bonkers. US gives me Serbian letters, and RS doesn´t have them.. jeez.

---

### Post by gmclean on 2009-03-26
> **Shooree said:**
> @gmclean what do you mean by xmodmap script?

In the original post of this thread, 'Part 3' involves making a script containing xmodmap commands and then setting it up to be run at session startup.  This is the 'xmodmap script' I referred to.

I noticed that 'Part 1' describes running an xinput command in session startup.  I thought it was a bit untidy to have two different things set up to run in session startup, so what I did was put that xinput command in the same script file as the xmodmap commands.

But it's a bit irrelevant because as I said, the only thing that doesn't work for me is the € and $ keys.

---

### Post by Shooree on 2009-03-27
@gmclean> right, I understand what you did. What I don't understand is why your eurodollar keys aren't working, and yet you've got the mediakeys up and running flawlessly. Would you be so kind as to go a bit further into the details of where EXACTLY you diverged from the manual?

Also, if the mediakeys and the eurodollar scripts are one and the same file for you, how come that one of them does work and the other doesn't? Or am I misunderstanding?  

Anyway, I'm starting to believe I messed up my keyboard mapping entirely. There's just too much info to juggle by a novice who needs to be able to switch language layouts on a media-key laptop. Everyday I try something new, to the effect that I forget what I already did, and all teh varables that may be influencing what I do. I'm actually thinking of reinstalling the entire system in order to start again (which I already did once).

---

### Post by edgar83 on 2009-04-03
Hi, I have a question slightly different...

I'm not interested in Acer media keys but I would like to tune the sensibility of the "real" touchpad... As I try to set it in the touchpad panel, nothing happens, I think that I'm just setting the sensibility for the media keys.

Do you know how to solve that problem? Can you help me?

Ciao :)

---

### Post by FokkerCharlie on 2009-04-04
Edgar

That's a really good question, and a problem that I haven't solved yet.  I think that you are correct to say that configuration changes seem to affect the media keys rather than the touchpad, I have no idea how to fix it.

Sorry!
Charlie

---

### Post by FokkerCharlie on 2009-04-25
Hello!

Well, the media keys fix doesn't work so well after the upgrade to Jaunty.  The problem is that the ids of the touchpads change depending on whether a USB mouse is plugged in on startup- for me that's quite a snag.

For instance, here's my cat /proc/bus/input/devices with a USB mouse:

```
I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=10000 200 0 0 0 0 0 700f 2000003 3862078 f870f401 febfffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c508 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=20017
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10
B: LED=ff00

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=064e Product=a101 Version=0100
N: Name="Acer CrystalEye webcam"
P: Phys=usb-0000:00:1a.7-2
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input8
U: Uniq=
H: Handlers=event8 
B: EV=3
B: KEY=1 0 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio3/input0
S: Sysfs=/devices/platform/i8042/serio3/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=b
B: KEY=6420 0 7001f 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0011 Vendor=0002 Product=0007 Version=81b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse3 event10 
B: EV=b
B: KEY=6420 0 7000f 0 0 0 0 0 0 0 0
B: ABS=11000003
```

If I don't have it plugged in at start, the 'USB Receiver' section disappears, and the touchpads become mice 1 and 2 instead of 2 and 3.

Anyone know how to get around this?

Charlie

---

### Post by p3y on 2009-04-26
Hi Charlie,

I was just going to ask you this myself. ;-)

Lets see what I can find out. Another problem I experience on the 5920 is that on shutdown the screen goes black after usplash finished and then I get some white vertical line all over the screen just before the machine powers down. Not a real problem but looks a bit amateurish... Do you have the same problem? It only happens with the current NVidia driver and with the current beta.

Percy

---

### Post by FokkerCharlie on 2009-04-26
Hi Percy

I haven't noticed that, but I do see a lot of text flashing past between Gnome stopping and the shutdown-usplash display.  Like you say, it's a bit untidy.

I haven't seen any improvement in boot time, bootmap reporting 29s, longer than Intrepid!  I have converted my HDD to EXT3, but I realise that this doesn't make all the difference immediately.

I have asked a question on the Hardware and Laptops forum:
[URL="http://ubuntuforums.org/showthread.php?t=1138200"]
http://ubuntuforums.org/showthread.php?t=1138200[/URL]

If you have anything to add to my ideas, or are interested in a bit of scripting, please go on!

Cheers
Charlie

---

### Post by FokkerCharlie on 2009-04-26
StuartN has solved this for us!

See this thread:

[http://ubuntuforums.org/showthread.php?p=7151684]("http://ubuntuforums.org/showthread.php?p=7151684#post7151684")

This is the terminal command that works for me:

```
xinput set-button-map "`xinput list | grep Synaptics | tail -1 | grep -o id=. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```

Be careful with the ` marks- don't use ' !

I couldn't get it to work just by putting that line in the 'Startup Applications', I had to create this script:

```
#!/bin/sh

#Remaps the second Synaptics touchpad entry.

xinput set-button-map "`xinput list | grep Synaptics | tail -1 | grep -o id=. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16

#Note- to remap the first entry, replace tail with head.
```

And call it from Startup Apps.

Could someone test this out, to check it's not just my setup it's working on?

Cheers
Charlie

---

### Post by p3y on 2009-04-26
Hi Charlie,

thanks for finding out about the new xinput-commandline. I successfully tested your script once with an usb-mouse plugged in and once without the usb-mouse. In both cases mediakeys worked.

About the boot time: For me it takes about 45 seconds from grub to desktop (with auto login). I think this is around 15-20 seconds faster than with intrepid.

Again thank you for your work on the Acer 5920. :-)

Percy

---

### Post by FokkerCharlie on 2009-04-26
Good, I will put it at the top of the thread.

I think my boot-up is longer than that, will time the whole thing, but it's about 1 min.  Did you upgrade or fresh install?

Charlie

---

### Post by p3y on 2009-04-27
I made a clean install only keeping my home partition.

---

### Post by FokkerCharlie on 2009-05-06
Hmmm.

I have now made a clean install, keeping my /home partition, and am seeing the same problem that you've been having- the fine vertical lines on shutdown.

In fact, quite often, the computer won't fully shut down, and just sits displaying the corrupted screen.  If I ctrl+alt+del, it reboots!  That ain't much good.

Charlie

---

### Post by p3y on 2009-05-06
Hi Charlie,

I found out, that the vertical lines come from usplash quitting or exiting. You can try this by going to a console outside of X and typing

sudo /etc/init.d/usplash stop

Then try to switch to a different console and you will see the vertical lines. At the moment I gave up on this one as I can live with it. Just close the laptop before the shutdown has finished... ;-)

I don't have a problem with the shutdown like you have. But interestingly my wife had this problem - the machine did not power down until any key was pressed or the lid was closed - with Mint6 (Intrepid) on an Acer 7720. I did some research and found out that I could reduce - but not completely solve - the problem by removing the link /etc/rc0.d/S20sendsigs. No idea why this made it better, maybe you want to try it for yourself.

Cheers, 
Percy

---

### Post by edgar83 on 2009-05-06
> **edgar83 said:**
> Hi, I have a question slightly different...

I'm not interested in Acer media keys but I would like to tune the sensibility of the "real" touchpad... As I try to set it in the touchpad panel, nothing happens, I think that I'm just setting the sensibility for the media keys.

Do you know how to solve that problem? Can you help me?

Ciao :)

Has this problem been solved yet?

Bye :)

---

### Post by FokkerCharlie on 2009-05-07
Cheers, Percy.

Tried it, doesn't seem to work here!

Not to worry...

Charlie

---

### Post by Dao984 on 2009-05-14
hi charlie thx u very much for your good job :)
im sry but i have a problem whit € and $ key. I follow up your guide step by step but my euro and dollar key dont work. i dont understand :(

---

### Post by edgar83 on 2009-06-03
> **edgar83 said:**
> Hi, I have a question slightly different...

I'm not interested in Acer media keys but I would like to tune the sensibility of the "real" touchpad... As I try to set it in the touchpad panel, nothing happens, I think that I'm just setting the sensibility for the media keys.

Do you know how to solve that problem? Can you help me?

Ciao :)

any progress?

---

### Post by FokkerCharlie on 2009-06-03
Not here.

I can't even get syndaemon to work under Jaunty.

---

### Post by edgar83 on 2009-06-03
whoa!

I'm seriously thinking about disassembling the pc and just disconnect the media keys, I really care more about a usable (not with super high sensitivity!) touchpad than the multimedia touch keys... :(

---

### Post by mohr tutchy on 2009-06-29
> **edgar83 said:**
> whoa!

I'm seriously thinking about disassembling the pc and just disconnect the media keys, I really care more about a usable (not with super high sensitivity!) touchpad than the multimedia touch keys... :(

See here :)
[http://ubuntuforums.org/showthread.php?p=7535907#post7535907](http://ubuntuforums.org/showthread.php?p=7535907#post7535907)

One love

---

### Post by Pott on 2009-10-24
Hey, great thread, thanks for the help!

Everything worked for me except part one (using Jaunty). Not sure why, I did exactly as it said I think. I have Exaile now but the media buttons don't work...

Exaile is actually pretty slow though, I have 10,000 songs and it doesn't seem to be the right software for it. I do miss media monkey...

---

### Post by Pott on 2009-10-30
Any ideas..? I'm actually considering upgrading to KK to see if it'd recognize those damn things!

---

### Post by dadodadodado on 2009-10-31
I have modified this script like this:
```
#!/bin/sh

#Remaps the second Synaptics touchpad entry.

xinput set-button-map "`xinput list | grep Synaptics | tail -1 | grep -o id=.. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16

#Note- to remap the first entry, replace tail with head.
```

was necessary the double dot here ```
grep -o id=..
``` cause my secondary touchpad have number "10" as event, with only a dot have 1 as event found.. you understand? i don't speak english... thanks a lot

---

### Post by Pott on 2009-11-03
Mhmm how do you know about your touchpad's event..?

---

### Post by Shooree on 2009-11-03
I'm on KK with my Acer 5920G now and as far as I can tell, none of the issues dealt with here have been addressed by default. What's more, trying these hacks in KK resulted in utter fail for me. :(

Anyone up to figuring out the proper way to do it?

---

### Post by Pott on 2009-11-03
> **dadodadodado said:**
> I have modified this script like this:
```
#!/bin/sh

#Remaps the second Synaptics touchpad entry.

xinput set-button-map "`xinput list | grep Synaptics | tail -1 | grep -o id=.. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16

#Note- to remap the first entry, replace tail with head.
```was necessary the double dot here ```
grep -o id=..
``` cause my secondary touchpad have number "10" as event, with only a dot have 1 as event found.. you understand? i don't speak english... thanks a lot

Hey I tried this, but it still doesn't work for me...

EDIT:

I tried to map the blue e key to Exaile. It worked. But then I restarted and it didn't work anymore... I didn't change anything to xbindkeys.
Using xbindkey-config I can run Exaile with the blue key. I also had to edit the copied text from the first post to include spaces after each command (or else xbindkeys won't recognize them!). But it tells me it doesn't recognize the xvkbd command...

EDIT two:

the second synaptic on my xinput list is listed as being id=6, so I replaced the script by its original version with "6", it didn't work.
I used the keyboard shortcuts to map the first media key on the right to launch exaile, that works just fine right now. I could use it to lauch gmusicbrowser as well, I think it'd be ok. 
Everything else works except those media keys and it's doing my head in! I have music running 100% of the time I'm at my PC without any other media on. 
Here's my xinput list:
> "Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=3    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Microsoft Microsoft Basic Optical Mouse"    id=4    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=5    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=6    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1


And here is my xorg:
> Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

The scripts and xbindkeysrc files are both exactly as in the first page of this thread.

---

### Post by FokkerCharlie on 2009-11-04
OK, let's try a little bit of troubleshooting on these media keys.

Open a terminal, and type:

```
killall xbindkeys
```

Then:

```
xev | grep button
```

Now try the media keys.  You should see buttons 17-20 mentioned.  Anyone having trouble with the touch-sensitive buttons, please report back here what you see.

You can re-start xbindkeys by using alt+f2, and typing:

```
xbindkeys
```

Also interested in anyone's experience with installing Karmic on their 5920... I have not had the opportunity yet.

Charlie

---

### Post by errenay on 2009-11-04
@FokkerCharlie I have just upgraded to Kubuntu 9.10. The media keys do not work. For example, "play" button changes the screen (as Ctrl+Fn). I have also strange problems with sound - there are sometimes loud cracks from speakers apart from normal sound.
BTW - maybe it's time to start new thread "Acer 5920(G) - tweaks for Karmic"?

---

### Post by FokkerCharlie on 2009-11-04
Good idea, Errenay.

[New thread here.]("http://ubuntuforums.org/showthread.php?t=1313893")

Please could you go there and post the output from the xev method above?

We'll get this fixed!

Charlie

---

### Post by Pott on 2009-11-04
Thanks Fokker. That all worked ok for me actually. Then I tried it again just for kicks and now my media keys work :s go figure...

I did change the Jauntymediakeys script to id=6, I'll try again with the original values...


I also realised that xvkbd isn't included in Jaunty, I had to install it. Whihc explains why it wouldn't work. Doh :lolflag:


EDIT:
I have accidentally disabled the Gnome shortcut for next track, and it wouldn't let me pick the media key. Anyone knows how to re-set these to default..? Thanks!

---

### Post by FokkerCharlie on 2009-11-04
Ah!

That's good news- so is everything working now, or are there still glitches?

Charlie

---

### Post by Pott on 2009-11-04
Well there are glitches:

The Next song button doesn't work, I accidentally got rid of it in Gnome shortcuts. Doh.
Also xbindkeys doesn't seem to start at each session and I'm not sure how to enable it at log on. Do I do a sh on the xbindkeysrc file in the Startup Application?

Otherwise it's all good. I used the shortcuts to map gmusicbrowser with the big blue button (BBB) and the mediakeys work fine with it!

All three other bits (&#8364; and $, brightness, hotkeys) seem to have worked 100% as well :)

---

### Post by FokkerCharlie on 2009-11-04
Good news.

To get xbindkeys working every time you log on, ensure that it is installed (sudo apt-get install xbindkeys), then just add 'xbindkeys' to your startup apps.  Might be worth making a copy of your .xbindkeysrc file, I don't know whether installing the program will overwrite it!

Charlie

---

### Post by Pott on 2009-11-04
Aye it was already installed... The file seems right. I made a backup in my Documents called xbindkeysbackup which hopefully won't clash with the original. 

I still can't figure out how to get the Next Song working. I tried creating a new shortcut with command Next track and XF86AudioNext as key but to no avail. It's a bit frustrating as it's the key I use the most...

To make xbindkeys startup, do I just type xbindkeys in the command or do I need to explore and find the software and link it from there...? I don't know where it is...

---

### Post by FokkerCharlie on 2009-11-04
To start xbindkeys, just type xbindkeys .  That's it.

Does Fn+End work for the next song?  If it does, then it suggests a problem with the button mapping or xbindkeys setup.  If not, then it might be an issue with the shortcut you have (I think that in Jaunty, the system for this might be different- here I click on the shortcut I want to change, then tap the media key, and it's done).

If the problem persists, please post the output from the xev troubleshooting method from my post earlier today.

Cheers
Charlie

---

### Post by Pott on 2009-11-04
Nope fn +end doesn't work. All the other fn + do however.

And yeah I can't configure the shortcut. The other shortcuts were preset. I accidentally messed up the NextTrack one, and it doesn't recognize the mediakey when I press on it.

WAAAIT. You sir are THE MAN!

Since I didn't know those two sets (fn + and mediakeys) were now remapped to essentially be interchangeable, I hadn't realised I could use as shortcut fn + end and it would remap the mediakey correct :D

AND IT WORKS!!


Wooooot. 
Thank you good sir. 

And xbindkeys started up just fine at startup too, I could see it on my conky.

Just two things if you would like to edit the first post:

Specify that you need to install xvkbd.
You need to edit the xbindkeysrc bit I think, I had to change mine to this:
"xvkbd  -text "\[XF86AudioPlay]""
   b:17

"xvkbd  -text "\[XF86AudioStop]""
   b:18

"xvkbd  -text "\[XF86AudioPrev]""
   b:19

"xvkbd  -text "\[XF86AudioNext]""
   b:20

You need to skip lines between each, or else xbindkeys didn't recognize them properly in the config.

---

### Post by FokkerCharlie on 2009-11-09
Thanks, Pott.

Changes made to the first post.

---

