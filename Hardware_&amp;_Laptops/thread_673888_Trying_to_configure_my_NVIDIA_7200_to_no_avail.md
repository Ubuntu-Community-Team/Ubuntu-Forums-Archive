---
title: "Trying to configure my NVIDIA 7200 to no avail"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by yiorgos on 2008-01-21
Last two days I'm trying to configure my NVIDIA 7200 to no avail.
What's getting on my nerves at most is that it has worked the first time!
Anyway let me explain you in detail my problem.

After installing** Ubuntu 7.10** with the default settings I tried to install the NVidia drivers to get the most of my graphics card. So I download the official drivers from NVidia's page (.run file) and run it. Installer said that no precompiled version found and I was prompted to autocompile one etc. etc.
After the installer successfully finished I started gdm and I gladly figure out that I could use all the Compiz effects. I continued using my new eye-candies until two days before that I reboot my system.

After the Ubuntu logo I got the Screen and Graphics Preferences dialog box saying that my monitor has low resolution etc. I tried to use the configure button but in the dialog box appeared just next no NVidia drivers were present. From that moment I have tried every possible solution I found either in this forum or in others but I still get the same dialog box informing me about the low resolution (like I didn't know that! ).

I tried installing the nvidia-glx-new drivers, reinstalling the official NVidia, reconfiguring X (dpkg-reconfigure Xserver-Xorg ) setting **vesa **drivers, nothing! And, as I'm writhing at the 2nd line of my post, I can't say that there's something wrong with my card or the drivers because it had perfectly worked before the reboot!!

Please any idea or suggestion would be far more that just helpful!
Thank you in advance 

I attach below my latest xconfig (one of my many unsuccessful ones) to have it a look. 

I forgot to mention that hitting glxgears at terminals I get

```

yiorgos@yiorgos-pc:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
yiorgos@yiorgos-pc:~$ 
```

```
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
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
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "LG 1900R"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72 [GeForce 7300 SE]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72 [GeForce 7300 SE]"
    Monitor        "LG 1900R"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

```


**And one last small question because I am confused.**
In the Restrictive Drivers section should the NVidia drivers be enabled or not?
I read in a relative thread that this choice is referred to the oped source drivers not to the NVidia one's.
Is that correct?

---

### Post by c0met on 2008-01-21
Have you had a look in System >> Administration >> Restricted Drivers Manager to see if you have a restricted driver that is not fully installed?

You need to make sure that the "restricted driver" repository sources are enable (and reloaded) under System >> Administration >> Software Sources

---

### Post by dreadlord_chris on 2008-01-21
Hi - I also have been using an NVIDIA 7200 - and I found the easiest way to deal with the drivers for this card was with [Envy]("http://albertomilone.com/nvidia_scripts1.html")
I would recommend first using Synaptic and **purging** all the NVIDIA drivers from your system...
Also, I can only speak for my system, but:
```
Option            "UseFBDev" "true"
```
causes problems on my system, YMMV

And, for NVIDIA cards, this should be in your xorg.conf:
```

Section "Extensions"
        Option     "Composite"  "True"
EndSection

```

---

### Post by yiorgos on 2008-01-21
> **c0met said:**
> Have you had a look in System >> Administration >> Restricted Drivers Manager to see if you have a restricted driver that is not fully installed?

You need to make sure that the "restricted driver" repository sources are enable (and reloaded) under System >> Administration >> Software Sources

First thanks for the replies guys.

I don't think this may be solution because, as I wrote at my first post, the installed driver worked at the first time so the correct repositories should be enabled.

> **dreadlord_chris said:**
> Hi - I also have been using an NVIDIA 7200 - and I found the easiest way to deal with the drivers for this card was with [Envy]("http://albertomilone.com/nvidia_scripts1.html") 
I'll give it a try (I'm away for a couple of days) and I will come back again with feedback, hope this envy tool do the trick. 

I just want to ask you to provide with the very steps to completely remove any NVidia installed drivers, because I want to be sure that I'll do the complete procedure of  cleaning my system correct before trying Envy.
The nvidia-glx-new drivers I would remove it from Synaptic, right?
What's the procedure when it comes to the official drivers that I installed through NVivia.run script package?
Or is there any aptitude command that removes drivers?

---

### Post by c0met on 2008-01-21
Hi Yiorgos,

I'm pretty sure there would be commands for what you seek, but I do not know them. I'm still working on learning this stuff.

---

### Post by cdtech on 2008-01-21
I had the same problem. I went into the recovery mode to install...

```
apt-get install nvidia-glx-new
```

Everything seems to be ok now. This method did uninstall the old version automatically.

---

### Post by jerrykenny on 2008-01-21
cdtechs response above loks good  . . . . 

We had an update to xorg-x11 2 days ago, and i had to reinstall my nvidia drivers after that as well. . . . . 

try cdtechs solution, also after that type

nvidia-xconfig

then  

gdm


let us know how you get on

---

### Post by oni5115 on 2008-01-21
Yeah, definitely install the restricted drivers, either using the the restricted drivers manager or
sudo apt-get install nvidia-glx-new
sudo -s nvidia-xconfig

(Reboot PC, or at least log out.)
nvidia-settings

If you get an error about not having the driver installed properly when running nvidia-settings try to manually uninstall XGL.  
sudo apt-get remove --purge xserver-xgl

That seemed to work for me, and a couple of other people as well in this thread:
[http://ubuntuforums.org/showthread.php?t=656093](http://ubuntuforums.org/showthread.php?t=656093)

---

### Post by yiorgos on 2008-02-01
I have tried all the above but without any result.
I'm still getting the message of the "running at low resolution" at startup.

Everything seems correct, why isn't working?
From the restricted drivers manager, the latest Nvidia drivers are enabled.
I also followed the process described [here]("http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver") step by step and after hitting 
"sudo nvidia-glx-config enable" I get no errors showing again that the process completed successfully.
On the other hand when I/m trying to use
nvidia-settings I get 
*You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.*
I do that also, but the same again.

Please help, any ideas would be helpful!
I now count only on you guys, I don't want to result using vesa drivers when I
can take the most of my card by using the nvidia drivers.

I quote you also my xorg.conf in case you can see anything faulty.
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

Section "Module"
    Load           "glx"
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
	Identifier	"nVidia Corporation G72 [GeForce 7300 SE]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"LG 1900R"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72 [GeForce 7300 SE]"
	Monitor		"LG 1900R"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

---

### Post by yiorgos on 2008-02-03
Waiting for some help I come with feedback.
I've noticed something that may be a good clue of what is 
really going wrong on my system.
Making only one change in xorg.conf, specifically in *Device Section* from
 driver "nvidia"
to 
diver "vesa"

everything goes back to normal but the 3D effects obviously.

Changing back to "nvidia" I again get the message of running at low resolution.
So, I guess there's something wrong with the driver itself, 
but nothing particular.
Any ideas of you guys that you are more experienced?

EDIT: Forgot to mention Envy failed to do the job also

---

### Post by yiorgos on 2008-02-10
Well, after all this failure, I removed all glx-nvidia drivers along with both dependencies and restricted drivers manager module and then installed the latest official NVIDIA drivers.
The installation process went smoothly and after restarting gdm I resulted with a full support of 3D effects and eye candies.
Unfortunately my pleasure last until the next reboot when I got the known dialog box informing me about my low resolution screen.
So, since the NVIDIA drivers worked absolutely fine until reboot, I figure out that something goes wrong during the start up process and Ubuntu looses the drivers configuration. It must be something with the drivers path because Xorg has no change (under Device Section still says "nvidia" drivers, as configured by the NVIDIA scrict).

Does anyone know which startup process I have to edit so as not to check for drivers and keep the last settings I set?

---

### Post by cdtech on 2008-02-10
Did you perform this in console mode? And do you not need to set xorg.conf to see it?

Section "Module"
...
# Load "glx" (rather than this)
Load "dri" (shouldn't you have these)
Load "GLcore" (and this one)

I'm not sure but I think something like that should work.

---

### Post by yiorgos on 2008-02-11
> **cdtech said:**
> Did you perform this in console mode? And do you not need to set xorg.conf to see it?

I have tried all possible ways. Both automated from scripts (glx-new and nvidia) 
and manually (editing Xorg by hand).

> 
Section "Module"
...
# Load "glx" (rather than this)
Load "dri" (shouldn't you have these)
Load "GLcore" (and this one)


Sorry but I didn't quite understand which of the three you suggest that I have under Section Module indeed.

---

