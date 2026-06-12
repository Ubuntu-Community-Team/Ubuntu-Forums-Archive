---
title: "Visual effects wont work"
date: 2008-09-12
forum: General Help
---

### Post by rubecuber on 2008-09-12
HI, IM A NEWB when it comes to linux, and  just installed ubuntu 8.04 hardy heron. I can't get the visual effects to work since i click on a different setting (extra, or normal) the screen pauses then it says the desktop effects could not be enabled, please help

---

### Post by JECHO on 2008-09-12
> **rubecuber said:**
> HI, IM A NEWB when it comes to linux, and  just installed ubuntu 8.04 hardy heron. I can't get the visual effects to work since i click on a different setting (extra, or normal) the screen pauses then it says the desktop effects could not be enabled, please help

go to system > administration > hardware drivers and enable the restricted  video driver

---

### Post by Moe Fugger on 2008-09-13
I have the same problem!  I've enabled the restricted driver and it tells me to reboot.  When I do, it boots back up in low graphics mode (640x480).  I adjust monitor settings to give better resolution, set the video card options to detect a GeForce 7800GS...  and the cycle starts over again!  

I'm running the latest kernal, have all of the updates installed, a 256 MB 8xAGP GeForce 7800GS, 1.2 Ghz AMD, 512 MB Ram...  

I've installed Envy and it manages to detect and auto-install the latest driver for the card. After Envy installs the driver, the machine recognizes the card, gives me all kinds of options to fool with, (only thing I change is resolution to 1024x768) but still con't enable visual effects...

PLEASE HELP!

---

### Post by northern lights on 2008-09-13
Envy is not even required for a 7800GS.

Can you post the output of ```
sudo lshw -C network
``` What happens if you run ```
nvidia-xconfig
```

---

### Post by Redial2416 on 2008-09-14
I also am a NOOB.  I am having the same problem as described above, on a 64 bit system.  I have read all of the FAQ's, installed the latest driver listed on the Nvidia website (took forever to figure out how to kill Xserver so it would install) and I too am chasing my tail.  In system it says that there are no proprietary drivers installed.  All I can say is WTF????  Is there anyone out there that can help with this issue?  I am very impressed by Ubuntu and want to continue to use it, but the frustration level is reaching the boiling point for an issue that should be simple to correct.  Any real help would be GREATLY appreciated.

---

### Post by northern lights on 2008-09-14
@Redial: Please also supply the requested outputs.

---

### Post by Redial2416 on 2008-09-14
Here you go....*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:df:cd:f7
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half ip=192.168.1.110 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:8e:32:f6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by northern lights on 2008-09-14
Crap.

Only now did I realize my screw up.

Obviously, network device information is irrelevant, I meant to ask for ```
sudo lshw -C display
```

...


[EDIT]
Sorry mate.
[/EDIT]

---

### Post by Redial2416 on 2008-09-14
That makes more sense....*-display UNCLAIMED
       description: VGA compatible controller
       product: GeForce 8500 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0

---

### Post by northern lights on 2008-09-14
I don't know what you did with the latest driver you downloaded, but it appears not to be installed. The card is not assigned any driver anyhow.

For the 8500 GT, the nvidia driver from the Ubuntu repositories is sufficient though, anyway (compare: [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html")).

Run ```
sudo apt-get update && sudo apt-get install nvidia-glx nvidia-settings nvidia-xconfig
```

Then run 'nvidia-xconfig'. Now what?

---

### Post by Redial2416 on 2008-09-14
Here is what I get now for the driver info:*-display
       description: VGA compatible controller
       product: GeForce 8500 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

However, I still can not adjust the resolution or turn on display extras.  So, as you put it, now what??

I do appreciate you taking the time to help me.  I have come closer now to a working system than I have been able to so far.

---

### Post by northern lights on 2008-09-15
While you should be able to set the resolution under 'System > Preferences > Screen Resolution', running ```
nvidia-settings
``` also will allow this and provide further options.

If neither works, we'll have to dig deeper.

---

### Post by Redial2416 on 2008-09-15
Let me correct myself.  I can choose between two resolutions, 640x480 and 800x600.  This monitor and card are capable of much higher settings.  Also I can still not set the normal or extended features in the applet.

---

### Post by northern lights on 2008-09-16
This is odd, since the correct driver is now assigned, still try to reconfigure X by running```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Redial2416 on 2008-09-16
Hello again.  I entered the code as per your instructions.  I now have a screen resolution of 1280x1024.  I still can not enable visual effects.  I can live with this but would like to continue the troubleshooting process if you are inclined to keep working with me.  It is obvious that you have an excellent working knowledge of this system and its capabilities.  I will catch on to it eventually and only wish that I had started learning it earlier.  It seems that there is a great amount of information to absorb and not very many places to go to for reference (except for kind individuals such as yourself).  I have been working with computers for some time now.  Just as I thought that I had mastered DOS they came out with Windoes95.  Well, I know that I have bored you to death by now so I will end with a very sincere Thank You.

---

### Post by northern lights on 2008-09-16
It could be that the reconfiguring might have removed the driver again, as wicked as that may sound to you given the resolution increase.

Can you check with ```
sudo lshw -C display
```again and post the outputs of```
glxinfo | grep rendering
```and```
compiz --replace
```

As an aside, in my experience, the perceived learning curve of switching to a new OS is highly dependent on your past computing experience and your understanding of the hardware part of things. If you've been with PCs since DOS, the preconditions look good.

Some general advice might be to not give up easily and try to not get frustrated.

Good reads are, amongst others:
[http://psychocats.net/ubuntu/index.php]("http://psychocats.net/ubuntu/index.php")
[linuxcommand.org - learning the shell]("http://www.linuxcommand.org/learning_the_shell.php")

---

### Post by Redial2416 on 2008-09-17
*-display UNCLAIMED
       description: VGA compatible controller
       product: GeForce 8500 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

Obviously you are correct in your assumption that the driver is not installed.  I will attempt to do it again.

---

### Post by Redial2416 on 2008-09-17
When I ran the nvida-xconfig it returned the following:
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by Redial2416 on 2008-09-17
I have attempted to install the driver again.  It is still not loading per the output of lshw -C display.  One thing I have noticed is that when the system is booting I see a line that states, "wrong chipset detected. 915 resolution only works with Intel 800/900 chipset.  I think that this is playing into it.  My computer has an Intel G33/G31/P35 Express chipset.  Your thoughts?

---

### Post by northern lights on 2008-09-18
> **Redial2416 said:**
> [QUOTE=Redial2416;5809339]One thing I have noticed is that when the system is booting I see a line that states, "wrong chipset detected. 915 resolution only works with Intel 800/900 chipset.This is an intel graphics chipset.

> **Redial2416 said:**
> [QUOTE=Redial2416;5809339]My computer has an Intel G33/G31/P35 Express chipset.That is your motherboard chipset (North/South Bridge).

Even though your mainboard chips got nothing to do with the entire thing, it still is trifling why your system would mention an Intel GPU chipset when you don't even have one.

You could manually add the information 'nvidia-xconfig' complains about, but can't really picture why it does in the first place. The xorg.conf has gotten much less important in Hardy anyhow. Still, try the following:

Run```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```to backup the original file. Thereupon edit it```
gksu gedit /etc/X11/xorg.conf
```locate the following section and add the line in italics```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

```

Honestly though, I'm not too certain this will solve everything.

---

### Post by Redial2416 on 2008-09-18
I have followed your instructions.  Here is the xorg.conf /etc/X11 configuration file as it is currently:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:5:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"800x600@60"	"1024x768@60"	"800x600@56"	"1280x960@60"	"640x480@60"	"1280x1024@60"
	EndSubSection
EndSection


I am now running at 1280x1024, however when I run the Nvidia Xserver settings applet it still informs me that I am not running the Nvidia x driver, the change screen resolution option won't even open.  I now believe that I know how a dog feels when it is chasing its tail.  Well, I think I have had enough for one night.  I look forward to our next communication.

---

### Post by Redial2416 on 2008-09-21
Great news!  I now have a working graphics system.  Thanks to you I was sniffing up the right trail when I found this webpage (link below).  I followed the steps and was presented with a graphical program that installed the driver correctly and resolved that issue completely.  
  Now if anyone knows where I can find a linux driver for a Kodak ESP 3 printer..........
[https://answers.launchpad.net/ubuntu/+question/41152](https://answers.launchpad.net/ubuntu/+question/41152)

I have been playing for an hour or so now.  These effects are awesome and blow away the preloaded operating system my computer came with.  I must admit that I was getting close to giving up but thanks to your help and encouragement I am very glad that I didn't.  I am sure that with a little more time and effort I will continue to enjoy Hardy and all that goes with it.  Couldn't have done it without you.

---

### Post by markthys on 2008-09-28
Hi guys,

I had also the same problem concerning visual effects.
I've a GeForce4 MX 440. At the beginning the resolution was ok,
but after installation of nividia-xconfig and envyng,
the thing is even worse. I've now only a 600x800.


math@math-desktop:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV17 [GeForce4 MX 440]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5


If I type nvidia-settings, I see the message:


You do not appear to be using the NVIDIA X driver. 
Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008
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
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
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
    Driver         "vesa"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
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
EndSection


Can some put me on the right track? Thx!

---

### Post by Redial2416 on 2008-10-08
I ended up using Nvidia version 173.14.12 and have had mixed results.  If I boot .19 desktop the system hangs, in recover mode or not.  If I boot .19 server it turns into one of the most enjoyable visual experiences I have ever had with any pc.  You just have to keep searching for that right driver for your video card / motherboard combination.  This OS's hardware detection is much better than even two years ago but it needs a little polish to be a 100% replacement for the pay for license OS.

---

### Post by macman3130 on 2008-10-12
im running vmware fussion with a macbook and have ubuntu running as a virtual machine. i cant turn on my effects and have tried a few different things. got any suggestions???

---

