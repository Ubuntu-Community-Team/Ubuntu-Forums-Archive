---
title: "Asus A6T and Edgy"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by Phalle on 2006-10-30
Hello! 
I'm so happy coz i just installed Ubuntu on my laptop and it works! (This is the first time I use Linux) Alltho I have not found drivers and stuff for everything. Does anyone besides me got Edgy to work with A6T? How do I get the scroll on the touchpad to work? And allso the built in webcam?

Another thing is the resolution, how did you do to change it? I have installed the latest Nvidia drivers.

Thx.

/Ph :KS

---

### Post by alditch on 2006-11-03
Hi
I also have asus A6 laptop, but i haven´t figure anything out about the touchpad and webcam (i wish i did) but for the resolution you have to add more optional resolutions via configuration tool. try typing: sudo nvidia-xconfig into the terminal and configure your settings.
for more info i would recommend you this site: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
regards

---

### Post by Tyx on 2006-11-08
I just configured the touchpad on my ASUS A8F, and I'm positive it's the
same for yours.
Firstly, you must make sure that the Synaptics TouchPad driver for X.Org server is installed. Open a terminal and type:
```
sudo apt-get install xserver-xorg-input-synaptics
```
Now you just have to add the following lines to xorg.conf (sudo gedit /etc/X11/xorg.conf)
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

```
Put the above under the section about the mouse.
And then further down, where it says Section "ServerLayout",
again under the "Configured Mouse", add
```
        InputDevice     "Synaptics Touchpad"
```

Now close all windows, and press Ctrl-Alt-Backspace, to restart X, or
alternatively just reboot. All ready.

A very nice application to configure your touchpad, is gsynaptic:
```
sudo apt-get install gsynaptic
```
Then look under System-Preferences-Touchpad!!

I hope that helps! :)

P.S. It would be a different procedure if your touchpad was not a synaptics touchpad, but ASUS laptops have synaptics ones. You can check with: cat /proc/bus/input/devices

---

### Post by Tyx on 2006-11-08
As for the resolution, what graphics card does your A6T come with? I think some of them are not nvidia... But if they are, alditch's info is probably enough.

---

### Post by darkmaster on 2007-01-14
As for the touchpad, the answer you have received are good. It works for me too.

For the Nvidia driver and the resolution... do you have 3D working? If not, don't be scared. Latest nvidia drivers are buggy. To know if 3D work, run 
sudo glxgear
from a terminal and see if the gear move smooth. Otherwise, you can run a screensaver such as solar winds or euphoria. They must work well if you are 3D accelerated.

First of all, find and install envy
it's a script for the nvidia card automated instalaltion. Google for it, search envy nvidia script, download the debian package and install it (double clock on the .deb file, package manager will load up)
You can connect to the internet with the laptop, can you? For having wifi work, just follow the simple instructions here:

[https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6T?highlight=%28asus%29%7C%28a6t%29](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6T?highlight=%28asus%29%7C%28a6t%29)

If you cannot use ndiswrapper, go the main site, the instructions are clear and easy to follow.
For the ethernet card everything is even more simple. You just have to download and install the proprietary drivers.

[http://gentoo-wiki.com/HARDWARE_Asus_A6T#Ethernet](http://gentoo-wiki.com/HARDWARE_Asus_A6T#Ethernet)

It is for gentoo but works perfect for Ubuntu :) Just be sure to donload also the build-essential package or you won't be able to install the drivers.

Are you using the 64 bit version of Ubuntu? I use the 32 bit version. In either case, you have to find in synaptic the package:

linux-general

and download it. This file is needen for your Ubuntu to load both of your processors! Otherwise, only one of the CPU will be recognized. It is an SMP Linux version. After downloading and installing it, the touchpad will be autoconfigured but Xorg will be misconfigured. Don't worry, be happy. At this stage, boot Ubuntu in safe mode, only the console will be available. Run simply

envy

and choose the install Nvidia drivers option. At reboot, X will load properly and everything will be fine. Maybe still a buggy resolution.... open a terminal and run

sudo gedit /etc/X11/xorg.conf

and then edit this lines:
> 
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

See that I have a 1280x800 written there? You can add it before the others resolutions, no need to erase all the others like I did. If you try and use the nvidia configurator, for an unknown reason, it will not save to xorg.conf the resolution so, after a restart, you'll be stuck again in a damned 1024.... Aniway :)

Another problem another solution... external mouse detection! Asus A6t usually does not detect external mouses. Just run from a terminal:

sudo modprobe -r ohci_hcd
sudo modprobe ohci_hcd no_handshake=1

and External mouses will magically work!
Another tip. Try downloading network-manager. We need this tool since the ethernet detection is a little confusing and buggy in Ubuntu. And in Linux in general I guess :) after installing this, we have to make it work. Just run from a terminal:

sudo gedit /etc/network/interfaces

and delete a lot of things... well, make it look like this :)

> # Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

# iface eth1 inet dhcp
# wireless-essid 3Com

auto eth1

# iface eth0 inet dhcp

auto eth0

# iface eth1 inet dhcp

iface eth0 inet dhcp

The restart the PC and Network manager will load on the gnome panel. Click over it and, after plugging the ethernet cable, choose wthernet connection. It will load it up for you. Usually it autoloads the connection but with the Asus A6T hardware it does not work... this toll can guide you trought the wireless vonfiguration and autodection too! It should come bundle with Gnome I guess.
To know if you are running on both CPUs, just write this from a terminal:

sudo cat /proc/cpuinfo

You'll se 2 CPUs and not only one :) Be sure to boot from Linux-Kernel-General and not from i386 standard! If it is the second choice in your grub menù, you can change the boot order by editing this file:

sudo gedit '/boot/grub/menu.lst'

and simply cut paste the second option instead of the first. Invert the options !! :))

Well, that's all for now... If I solve any other issue, I'll be sure to tell you! Hope I've been usefull, bye bye!

The DarkMaster

---

### Post by Slade Winstone on 2007-02-12
For a possible fix to the usb mouse problems try:
[http://ubuntuforums.org/showthread.php?t=359482](http://ubuntuforums.org/showthread.php?t=359482)

---

