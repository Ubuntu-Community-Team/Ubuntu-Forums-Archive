---
title: "eeepc &quot;low graphics mode&quot; dpkg-reconfigure doesnt fix it"
date: 2009-04-12
forum: Hardware
---

### Post by theboredone on 2009-04-12
I have an 1000H eeepc with eeebuntu nbr(updated as of today) installed. It ran great till after some updates(I'm guessing) and a restart my graphics drivers no longer works. It just boots up and throws the "Running in low graphics mode" dialogue. No matter what I do in that, it wont save it, or work, or anything(I tried just selecting the i810 driver, and tried selecting by model>intel>915.) 

I shutdown gdm, and ran:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
as indicated in this thread: [http://forum.eeeuser.com/viewtopic.php?id=49753]("http://forum.eeeuser.com/viewtopic.php?id=49753")
I started gdm, and had the same low graphics prompt. Running in low graphics mode is a waste of time and unacceptably slow in changing from menu to apps, and from window to window. How can I unfoobar this without reinstalling everything? At this junction in my life I have only one usb drive(512mb) which is too small to load the installer on(unless theres a way around maybe? bootstrapper maybe?), so until I buy another usb drive my netbook went from being my most useful computer, to being worthless. Or is there a way to get out of this low graphics hell short of a re-install? ](*,)

---

### Post by neu2buntu on 2009-04-12
you should have a backup/backups of your /etc/X11/xorg.conf file since this update that broke it.. do code ```
gedit /etc/X11/xorg.conf*
``` in terminal and it should have more than 1 tab.. you could compare the present 1 with the backup to see changes made by this update to x. i think you can rename/remove the latest xorg.conf and the last 1 will be used .and hopefully this should set things right..  paste the output of the command (the latest xorg.conf and the closest to date backup)   you may also have to rename the backup as xorg.conf, i havnt done this myself so im not 100% sure....   go with the rename of the latest xorg.conf file for now as a safety net...ok

---

### Post by theboredone on 2009-04-13
I already looked at my X.org backups, and none of them appeared to be older than the update. I tried replacing it with the one's I did have(two from running the dpkg-reconfigure, and a .1, .2, and .3, as well as .failsafe and failsafe.bak) and they all did the same thing(low graphics mode).

All the .confs have what look like default settings for "Device"("Configured Video Device"), "Monitor", etc.

---

### Post by theboredone on 2009-04-13
I replaced my xorg.conf with:

```
Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Driver        "intel"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Modes        "800x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection
```
(from [http://forum.eeeuser.com/viewtopic.php?id=688]("http://forum.eeeuser.com/viewtopic.php?id=688") )
which didnt work. So I restored the old one dpkg made and I changed the 
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection
```
section to show:

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
EndSection
```

which after a reboot gave me the same "low graphics" prompt with vesa drivers selected.

---

### Post by neu2buntu on 2009-04-13
things to try/look at maybe ```
lspci -vvv
``` (this will show the drivers in use for the all of hardware including display) [cant seem to "grep" this whilst being verbose]

```
dmesg
``` this will show whats going on when the kernel boots (possibly show errors about x)

```
gedit /var/log/Xorg.*
```  (this seems to be what is happening in xorg.conf)

```
gedit /etc/modprobe.d/blacklist*
``` (look for anything resembling your intel driver)

also wonder what would happen if you blacklisted the vesa module that is driving your display and booted,would it default to your proper driver or would it break x 

maybe add "intel" to your /etc/modules file and reboot (not sure if "intel" will do it but worth a try at least)


another thought........if you can find the exact name of the driver your display is supposed to use insert it into the kernel ```
sudo modprobe NAMEOFMODULE
``` and remove the low graphics driver ```
sudo modprobe -r NAMEOFMODULE
```     i might be a long way off track with all of these but worth a try!!!!!

---

### Post by theboredone on 2009-04-15
neu2buntu: These seem like some great leads, and just the kind of commands I need. 
Thanks for your help.

I'll go ahead and play with this for a while. I've discovered from lspci my graphics card is a different version than one described in the xorg.conf i was using. 
Once I figure out a solution to this, I'll post my xorg.conf and whatever steps/things to look for, for eeepc 1000h's.

---

### Post by neu2buntu on 2009-04-15
hope u get it sorted....also ```
lsmod
``` shows all modules that are loaded into the kernel and i have found this command from searching the net ```
sudo dexconf
``` (reset xorg.conf configuration), 
    dont know if this is a variant of the initial command you ran 
> sudo dpkg-reconfigure -phigh xserver-xorg .read up on this command before executing it to be safe...

---

### Post by Galata on 2009-04-15
Have you try to reboot -> select "recovery mode" -> fix x server-> reboot again?

This Fixes automatically the X server (graphics). If this doesn't work, then try to configure xorg.conf and generally your graphics settings.

I suggest you to install "nvidia-settings"(if you haven't already install). It is an app (gui), which help you to configure your graphics!

For installation open a terminal and run: ```
sudo apt-get install nvidia-settings
```

---

