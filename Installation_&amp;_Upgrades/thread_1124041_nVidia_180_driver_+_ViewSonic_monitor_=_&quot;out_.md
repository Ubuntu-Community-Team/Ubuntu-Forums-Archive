---
title: "nVidia 180 driver + ViewSonic monitor = &quot;out of range&quot; error on reboot (blank screen)"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by blue carrot on 2009-04-12
Hi people,
I just got a new computer and I'm running only Ubuntu 8.10 on it (no dual boot). For a first time linux user I think things are going allright, my system is set up pretty well apart from one thing that is really frustrating! And that is that installing my graphics driver overloads the screen making it blank!

HARDWARE:
nVidia GeForce 7 Series Shader model 3.0
ViewSonic VE710b (about 4 years old 17 inch non-widescreen)

Okay so basically when I installed and set up ubuntu, the highest screen resolution I can get is 800x600 (which I'm still using now). 

I figured that installing the restricted graphics driver listed in the hardware drivers menu would give me higher resolution options. So I installed the most recent nVidia graphics driver, 180 (although I have since tried it with 177 and 173 as well with the same outcome). 

When I reboot my system after installing the driver, right about the time that the opening noise plays, the whole screen goes blank and displays a monitor-generated message saying "out of range".

The only way that I've found to fix it is to reboot in recovery mode, and select 'Try to fix X server'. This fixes it, but it also uninstalls the driver, leaving me with a measley 800x600 screen resolution again. 

It has been suggested to me to run gksu gedit /etc/X11/xorg.conf and then edit my HorizSync and VertRefresh lines into the correct values. But for some reason now when I run gksu gedit /etc/X11/xorg.conf all I can see is this:

> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

There are no values there which I can alter. Although I did used to be able to see them.

I think that this might be the fix but I need to be able to know how to edit the full version of xorg.conf. Also what would the process be. e.g. Install driver, reboot, edit xorg.conf somehow from boot menu? I'm just not sure. 

Any help greatly appreciated.

---

### Post by blue carrot on 2009-04-13
bump

---

### Post by blue carrot on 2009-04-14
bump again...can someone please help? i suppose the crux of the problem is that i cannot edit xorg.conf to the extent that i need to. someone must know how to do this?

---

### Post by Mark Phelps on 2009-04-15
Ubuntu with 8.10 change to lessen the reliance on details in the xorg.conf file.  You can now edit your display parms directly doing "sudo display-config.gtk". See if that helps.

---

### Post by saradisn on 2009-04-15
Have same problem with geforce 7300 gt and viewsonic va1903wb 19' monitor.
Tried 
sudo display-config.gtk  and returned  

sudo: display-config.gtk: command not found.

---

### Post by blue carrot on 2009-04-15
yes, i got the same message of command not found. 

the weird thing is that one time when i typed in the command gksu gedit /etc/X11/xorg.conf i could see things under the monitor section like 'HorizSync' and 'VertRefresh' which are apparently the values that I need to change. but now i can't see those anymore.

---

### Post by Mark Phelps on 2009-04-16
Sorry -- typo on my part.  Try "sudo displayconfig-gtk".

---

### Post by blue carrot on 2009-04-16
command not found

---

### Post by Mark Phelps on 2009-04-16
Just tried it in 8.04 (not sure if it was only available in 8.10) -- works for me!

---

### Post by blue carrot on 2009-04-17
doesn't work for me...not sure if its because im on 8.10, or if there is some other problem with my system. pleeease someone help its been 2 weeks that ive been trying to fix this and im getting damn sick of 800x600 resolution.

---

### Post by saradisn on 2009-04-17
I've installed 9.04 on USB flash drive and the monitor with the 800x600 problem is at work. We in Easter holidays now , so I'll try the solution from Tuesday and tell you what happened.

---

### Post by blue carrot on 2009-04-20
that would be great, saradisn. im still having the problem, and as you can see there doesn't seem to be anyone able to help as yet!

---

### Post by upchucky on 2009-04-20
You do realize that 8.10 has issues with 3d graphic and is not a long term release 8.04 is a long term release and has better support for graphics.

with the above said, you can try this on 8.10 it may or may not work, but it is the best solution for 8.04.

Set up Nvidia driver

Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     [http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)


I am including my xorg.conf from long ago, it has some settings you may be able to copy to yours as experiments. remember to backup your presently working xorg first, and note that mine has some other settings you will not be able to use so an exact copy will not work.

you must be able to switch from a command line to the GDM and back again for each experiment you try.

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
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
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
#    Load           "type1"
    Load           "vbe"
    Load           "dri"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
#    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV41.9 [GeForce Go 6800 Ultra]"
    Driver         "vesa"
    BusID          "PCI:1:0:0"
    Option         "UseFBDev"              "true"
    Option         "RenderAccel"	   "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "backingstore"          "true"
    Option         "AddARGBGLXVisuals"     "true"
    Option         "TripleBuffer"          "true"    
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV41.9 [GeForce Go 6800 Ultra]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1024x678" "960x600" "840x600" "1280x960" "800x600"
    EndSubSection
Endsection
#    SubSection     "Display"
#        Depth       4
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       8
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       15
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       16
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1920x1200"
#    EndSubSection
#    SubSection     "Display"
#        Depth       16
#        Modes      "1024x678"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "960x600"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "840x525"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "800x600"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1024x768"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1280x800"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1400x1050"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "640x480"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1280x1024"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1280x960"
#    EndSubSection
#    SubSection     "Display"
#        Depth       24
#        Modes      "1280x960"
#    EndSubSection
#Endsection
Section "DRI"
        Mode     0666
EndSection

---

### Post by saradisn on 2009-04-22
Tried every step to 12.a). The nvidia logo didn't appear but the login screen seemed to be in the right resolution. I could hear ubuntu start , but couldn't see anything , just a black screen.

---

### Post by blue carrot on 2009-05-16
i tried this and not only did it not work but now, when i go system>administration>hardware drivers, the list of restricted drivers is blank where it used to show the different options of drivers to enable / disable. 

can anyone help out here? ive had ubuntu for a couple of months now and im still stuck on 800x600 screen resolution!! it is starting to tick me off

---

