---
title: "Nvidia GeForce 9600M - looking for proper driver/installation guide"
date: 2008-08-04
forum: Hardware
---

### Post by mad_prince on 2008-08-04
Hello :) at first, I'd like to sorry for my english, but I think I can speak english better then you speak polish :)

And now my question.

Where I can find driver for GF9600M? I found only for 8700M. Besides I don't know how to install it. I have to completly quit X, but I've tried all ways that I found on this forum, but they didn't work :/
I ran recovery mode in GRUB, and everything was ok untill request about kernell appeared. I chosed 'yes', but in recovery m. there is no internet conection. 

I hope you know, what I mean :) thx for any respons.

---

### Post by phidia on 2008-08-04
You don't want to get out of X by using recovery mode. 
There are other ways to install the nvidia driver but perhaps your card model doesn't support those?

To stop X do this in terminal: > sudo /etc/init.d/gdm stop
 And then run the nvidia installer.

---

### Post by mad_prince on 2008-08-04
I have already try it, but it doesn' work, it doesn't "turn off" X completly.

edit// there is no problem any more :) I used Envy and **manually** (I have polish ver. so I don't know how it is in english ver.) and everything is ok (auto didn't recognize my video card)

Edit2// it was ok until restert :/ X didn't run, I have to set default options.

---

### Post by phidia on 2008-08-04
That should work but try > sudo telinit 2
See runlevels [here]("http://www.debian-administration.org/articles/212"), and maybe [this thread]("http://ge.ubuntuforums.com/showthread.php?t=815636")?

---

### Post by mad_prince on 2008-08-04
ok, I manage to install new driver, but i can't set higher resolution then 640x480:/

---

### Post by phidia on 2008-08-04
> **mad_prince said:**
> ok, I manage to install new driver, but i can't set higher resolution then 640x480:/

Sorry you're having these problems. You're using Hardy (8.10) right?
Try entering > sudo nvidia-xconfig in a terminal and letting that update your X then restart X (Alt+Ctrl+Backspace).

If that doesn't work post your /etc/X11/xorg.conf

---

### Post by jimv on 2008-08-04
EASIEST WAY TO GET NVIDIA CARDS WORKING:

Install EnvyNG and run it.  Here are the console commands:

```
sudo apt-get install envyng-gtk
envyng -t

```
Press 1 to install the driver.
Reboot when it's finished.

---

### Post by phidia on 2008-08-04
jimv, do you have a 9600 card that envy works on?
I don't think envy works on that card model-I could be wrong though.

Added: BTW I'm not just dreaming this stuff up there are posts [like this]("ttp://ubuntuforums.org/showthread.php?t=863205&highlight=nvidia+9600") that suggest there are problems getting the 9 series card to work using envy or the ubuntu hardware driver way. The manual way (using the [nvidia installer]("http://www.nvidia.com/object/unix.html") does apparently work).

---

### Post by jimv on 2008-08-04
The only way to know is to try and see if it works.  If it can't find the driver for that card, it will tell you.

---

### Post by phidia on 2008-08-04
Seems the driver is installed > ok, I manage to install new driver, but i can't set higher resolution then 640x480:/
but the rez isn't correct.

As I said earlier "sudo nvidia-xconfig" may fix that and if not posting the xorg.conf file could provide information to work with.

---

### Post by hotweiss on 2008-08-05
> **mad_prince said:**
> ok, I manage to install new driver, but i can't set higher resolution then 640x480:/

1. sudo apt-get remove nvidia* (will also remove any other restricted modules (e.g.-madwifi), so watch out)
2. sudo apt-get install envyng-gtk
3. enable the proposed repositories
4. sudo apt-get update
5. sudo envyng -g
6. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
7. Once the installation is completed, reboot and you will once again have a crisp screen.

---

### Post by mad_prince on 2008-08-05
It works :) but I don't know for how long ;) I removed driver from nvidia website and installed envy driver (like before) but this time I didn't use NVIDIA accelerated graphics driver in "hardware drivers". Is this option important or can I ignore it?

---

### Post by phidia on 2008-08-05
mad_price, Open a terminal and enter > glxgears you should see an animation running, or you'll get an error message. You may also want to run glxgears with the -printfps flag.
If the gears run _and_ run smoothly then the driver is likely working.
You should also have a nvidia setting menu item in System > Administration.

---

### Post by mad_prince on 2008-08-05
```
Error: API mismatch: the NVIDIA kernel module has version 173.14.09,
but this NVIDIA driver component has version 173.14.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
16616 frames in 5.0 seconds = 3319.019 FPS
16675 frames in 5.0 seconds = 3330.260 FPS
16960 frames in 5.0 seconds = 3389.376 FPS
17147 frames in 5.0 seconds = 3428.439 FPS

``` but gears move smooth

---

### Post by phidia on 2008-08-05
I think the previously installed nvidia left something behind.
If it works for you and works after a reboot then don't mess with success.

If you want to clean up the previous install see the thread [here]("http://ubuntuforums.org/showthread.php?t=481887").

---

### Post by phidia on 2008-08-06
mad_prince, How is the resolution now? If you are still stuck at the low res look at the [thread here]("http://ubuntuforums.org/showthread.php?t=881314").
There seems to be a problem with 8 & 9 series cards getting the correct resolution set.
Try that runfile and hope that's a good fix!

---

### Post by mad_prince on 2008-08-06
1024x760 so it's OK

---

### Post by mad_prince on 2008-08-12
same problem again :/ everythink was ok until today. I installed driver, but I can't set higher rez then 640x480. My X11:```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Jul 17 18:39:00 PDT 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "pl"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"

	# 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

	# 
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection

Section "Screen"

	# 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by blazercist on 2008-08-12
I have a suggestion, lets do a hard clean of all the crap that you've screwed up already.

This will remove the old driver packages 
```
sudo apt-get remove nvidia-glx nvidia-glx-new nvidia-kernel-common
```

This will remove the actual driver file from its directory.
```
sudo rm /lib/modules/`uname -r`/kernel/drivers/video/nvidia.ko
```

Now lets blacklist all the bad stuff.

```
sudo gedit /etc/modprobe.d/blacklist
```
add "nv" to the list there.


Now its time to install the driver the PROPER way.
*Download the driver from NVIDIA.com to your home folder.

This installs the files needed to build the driver file with the installer and also makes the driver file executable.
```
sudo apt-get install build-essential
sudo chmod +x NV*
```
CTRL+ALT+F1 (This will drop you to virtual terminal.)

This stops X-server and runs the installer, the NVIDIA driver cannot be installed while the X-server is running.
```
sudo /etc/init.d/gdm stop
sudo sh NV*
```
Accept, yes, yes yes.

This restarts X-server
```
sudo /etc/init.d/gdm start
```

Now everything should work just fine.  Keep in mind that when there is a Kernel update you will need to reinstall the driver.  Don't panic, this is easy.


Instructions for reinstall after kernel update.
Leave the installer as is in your home directory.
CTRL+ALT+F1
```
sudo /etc/init.d/gdm stop
sudo sh NV*
Accept, yes yes yes.
sudo /etc/init.d/gdm start
```

---

### Post by mad_prince on 2008-08-12
Thanks but I've already solved my problem. It's strange, I reinstalled my driver 3 times and it didn't work, but when did it fourth time (in the same way) it's working properly.
**blazercist** thx for man, maybe I will use it next time

---

