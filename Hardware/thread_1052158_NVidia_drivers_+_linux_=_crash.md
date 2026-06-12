---
title: "NVidia drivers + linux = crash? :/"
date: 2009-01-27
forum: Hardware
---

### Post by linuxguru1 on 2009-01-27
This is probably the quadrillionth topic you're reading about NVidia drivers + any linux distro not working. I've had this problem about 3-4 years ago. I was running Fedora, and every time when I tried installing the NVidia drivers something went wrong. That's when I swapped from a dual boot back to an operatingsystem-wannabe: Windows XP.

2 days ago I really felt like giving linux a shot again (my nickname is LINUXGURU after all ;)), so I installed Ubuntu 8.10 from the live CD. I upgraded the whole thing, installed some softwares (gtkpod, wine,...) and tried some games. I really like chess, so when I saw "chess" in the gamesmenu I was like "yay!" Everything went fine until I checked out the preferences and saw there was an option "run in 3D". I was like "OMG!! LET'S TRY!!" I did, but it failed. Some error about opengl.

I assumed it was the NVidiadrivers that weren't (properly) installed so I went to the NVidiawebsite, got myself the latest driver for the 8800GT, killed the X, logged on as root, ran the installer (with plenty of errors like before :/ [click to read the install-log](http://pastebin.com/m6335388c)), rebooted my computer and got an error.

I can't recall what it was exactly, but it was something about me having to make sure I have an actual NVidia videocard or having installed the drivers properly.

I must've went through about 30 topics concerning this matter, but still haven't found a solution. That's why I made my own.

Anyone willing to help out this "linuxguru"? :)

---

### Post by Squid Spectre on 2009-01-27
Thats surprising, I've been using nVidia cards and Ubuntu for some time now, and they usually play nice even with a manual install of the drivers. What architecture are you using? Also can you post whatever message X server throw up when you reboot?

Also try Envy, it usually works the first time without having to muck about with the manual install. The latest build is for 8.04 but it might just work. Be sure to use the uninstall option first, reboot, then reinstall.

 [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by utnubuuser on 2009-01-27
I've seen many posts about Nvidea drivers in 8.10/9.04,  not so many for 8.04.

---

### Post by linuxguru1 on 2009-01-27
I tried the envy thing... After reboot I got something about "input, monitor, videocard weren't detected properly --> low resolution. What do you wanna do? reconfigure -> new configuration (failed) --> generic config.

---

### Post by Squid Spectre on 2009-01-27
I can't be sure but it sounds like you got through the uninstall alright. Choose the generic config and continue forward, it'll be ugly. Use Envy once more to reinstall the drivers, if all went well you should have a reasonible display upon boot, if not re-post.

---

### Post by linuxguru1 on 2009-01-27
I've got a normal display with standard graphics... the default stuff... No OpenGL or GLX or 3Daccelleration or anything else that can fancy stuff a bit >.<

EDIT:
oh use the uninstall version first, then reboot, then install? Just a sec... I think I forgot the uninstall part (doh! -.-)

EDIT2:
I removed the old drivers, rebooted, installed the recommended + compatible one from envy and now I'm stuck with a quarter of a screen visible and divided into 2 parts. Also I got some message saying "New restricted hardware drivers are now in use." 

Any ideas? :?

---

### Post by Squid Spectre on 2009-01-27
That sounds...unsettling. Try going to the nVidia setting manager under the Administration (?) menu and mess with the display settings there. The good news it that it sounds like you have the nVidia drivers and they are in use.

Edit:
If possible post your xorg.conf file

---

### Post by stchman on 2009-01-27
> **linuxguru1 said:**
> This is probably the quadrillionth topic you're reading about NVidia drivers + any linux distro not working. I've had this problem about 3-4 years ago. I was running Fedora, and every time when I tried installing the NVidia drivers something went wrong. That's when I swapped from a dual boot back to an operatingsystem-wannabe: Windows XP.

2 days ago I really felt like giving linux a shot again (my nickname is LINUXGURU after all ;)), so I installed Ubuntu 8.10 from the live CD. I upgraded the whole thing, installed some softwares (gtkpod, wine,...) and tried some games. I really like chess, so when I saw "chess" in the gamesmenu I was like "yay!" Everything went fine until I checked out the preferences and saw there was an option "run in 3D". I was like "OMG!! LET'S TRY!!" I did, but it failed. Some error about opengl.

I assumed it was the NVidiadrivers that weren't (properly) installed so I went to the NVidiawebsite, got myself the latest driver for the 8800GT, killed the X, logged on as root, ran the installer (with plenty of errors like before :/ [click to read the install-log](http://pastebin.com/m6335388c)), rebooted my computer and got an error.

I can't recall what it was exactly, but it was something about me having to make sure I have an actual NVidia videocard or having installed the drivers properly.

I must've went through about 30 topics concerning this matter, but still haven't found a solution. That's why I made my own.

Anyone willing to help out this "linuxguru"? :)

All you needed to do was enable the restricted driver and it would work excellent.

---

### Post by Squid Spectre on 2009-01-27
Well sure, if we wanted to make the whole process "simple."

---

### Post by linuxguru1 on 2009-01-27
I tried enabling the restricted driver. It made some fancy stuff happen, but no OpenGL or anything like that... I did that before I installed the NVidiawebsite drivers.

Xorg.conf:
```

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

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by Squid Spectre on 2009-01-27
Try running this in the console:

sudo dpkg-reconfigure xserver-xorg

Then reboot and repost the xorg.conf

---

### Post by linuxguru1 on 2009-01-27
```
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

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Driver	"nvidia"
EndSection


```

---

### Post by Squid Spectre on 2009-01-27
Well, that looks like its using the nvidia drivers. I'd have to double check againt my Ubuntu machine at home (which I will in about an hour or so.) Is 3d acceleration still not working for you?

---

### Post by linuxguru1 on 2009-01-28
[Don't think so...](http://www.imgdumper.nl/uploads/49805f69e4bcf/49805f69cffc7-screenshot1.png)

What's even weirder still is the way my monitor looks... KSnapshot didn't show the problem, so I used a digital camera: [1](http://www.imgdumper.nl/uploads/49806746a0982/49806746a01b6-DSC02438.JPG)  [2](http://www.imgdumper.nl/uploads/4980678b06441/4980678b05c74-DSC02439.JPG)

---

### Post by Squid Spectre on 2009-01-28
Sorry about the delay, I wasn't able to check your xorg.conf against my own yesterday. I got caught up in another folly.

Just a quick thought based off your first screen shot, it would seem to my that you need to install the "python-opengl" package. It would seem to me that you aren't missing the capability for 3D rendering, rather you are missing the python binding to the OpenGL engine, which would explain your 3D chess woes. Hopefully you haven't changed anything since yesterday and you are still using the restricted driver. Try running:

     *sudo apt-get install python-opengl*

Install that package and all the dependencies it asks for, they are listed [here]("http://packages.ubuntu.com/gutsy/python-opengl").

I saw the pictures you took with your camera and had a chance to think for a bit about them. It's just a wild guess but it would seem the nVidia card may be kicking an unsupported output to your monitor and as a consequence you are getting that odd feedback. Did you try adjusting the screen resolution and refreshrate?

---

### Post by linuxguru1 on 2009-01-28
Uh... I just opened the "resolution"program... It said "unkown" all over the place, but I ignored that and changed the resolution to the only thing possible... from 800x600 to 600xsomethingelse. It's looking even worse now >.< should I swap back to the default driver? this is really starting to annoy me :/

I did manage to install the OpenGL thing though... now the chessgame says it still needs Python GTKGLext. I googled it, and it's downloading as I type... Hope things'll look normal again soon o_O

You're gonna get lots of thanks when this all turns out okay xD

EDIT:
... I'm not quite familiar anymore with these install/make/configure things >.<  Isn't there a way to install that last package with the default installerprogram (I'd say YAST, but that's openSUSE's updatemanager :P)

---

### Post by Squid Spectre on 2009-01-28
Run this to get Python GTKGLext

*sudo apt-get install python-gtkglext1*

Also, do you still have the nVidia Administration Tool in your Administration menu?

---

### Post by linuxguru1 on 2009-01-29
I'll install the python package on my computer as soon as I get back home. I still have the administration tool in my menu, but when I run it it says I need to install/enable the nvidia drivers o_O

---

### Post by Squid Spectre on 2009-01-29
They launched some kernel/drivers for nVidia today, run those. Then post your xorg.conf once more. I checked you old one against what I have and acording to that you are using the nvidia driver. I'll check back later to see what it says and hopefully have a solution for you.

---

### Post by linuxguru1 on 2009-01-29
hmm... I updated my system (40+ updates), but I can't remember seeing any nvidia stuff, so I tried searching with the updatemanager... Just old packages.
From the list with search "nvidia" I have these installed:
* Hardware Drivers
* NVIDIA X Server Settings
* NVIDIA X.Org driver ('version 177' driver)

Xorgfile:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Tue Nov  4 14:07:17 PST 2008

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
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

### Post by Squid Spectre on 2009-01-29
Well now THAT looks like a good xorg.conf file. I know for a fact you're using the nVidia driver by looking at the "Screen" configuration and then to the "Device" section describing your video card.

> Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection


The one thing that seems off is that there are no meta-modes specified in the subsection of "Screen" for the display, its currently set to "nvidia-auto-select." 

Coupled with the fact X11 wasn't able to produce anything useful from the probe it did on your monitor and that option is select this may very explain the terrible trouble with your display. I think I can give an additional line to add to this file that should help fix the issue, but I need to know what is the resolution and refresh rate for that monitor?

---

### Post by linuxguru1 on 2009-01-30
So you're saying all that was causing this displayproblem is a line telling the computer what resolutions the monitor can display?
Well currently it's 800x600 and 61Hz(=low gfx mode + output fail)which quite sux -.-', but it's perfectly capable of displaying 1280x1024... (my fav resolution lol :P)

EDIT:
I added a line in the xorg.conf file to fix the above problem, but... no change...
My xorg.conf now looks like this:

```

stefaan@Stefaan-Ubuntu:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Tue Nov  4 14:07:17 PST 2008

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
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by linuxguru1 on 2009-02-04
Any ideas...? :?

---

### Post by linuxguru1 on 2009-02-24
Problem solved!
I got a bit angry with ubuntu and reinstalled it. Then, for the first time in my whole life, the nvidia installer from nvidia.com actually did what it was supposed to do. Everything runs fine and smooth now :D
Thanks for the help anyways ;)

---

