---
title: "N2N  Karmic 9.10 AMD64 Nvidia InDaComputa"
date: 2010-02-01
forum: Hardware
---

### Post by UbuAli on 2010-02-01
[COLOR=DarkRed]**N2N**[/COLOR] = **N**ewbie **2 N**ewbie so now you know.

This Thread contains useful or unuseful information depending on your knowledge to work basically with Nvidia Drivers.
All i discovered sofar. 

Sections to read are:

default
Xorg
Nvidia Ubuntu Install | Uninstall
Nvidia Errors
Nvidia Pakages v190 Stable, 195 Beta Driver
Nvidia Driver before 96.xx AMD64
Example xorg.conf's
xorg.conf.Xorg-generated
xorg.conf.nvidia
xorg.conf.failsafe
Ubuali xorg.conf
Offtopic
UbuAli other Beans

**so lets start**


------------------------------------------------------------------------------------------------------
**default**
------------------------------------------------------------------------------------------------------
Used Ubuntu : kernel 2.6.31-17 karmic amd64
Used Ubuntu : kernel 2.6.31-14 karmic amd64

You need for typing work sometimes the Terminal which could be located here

[COLOR=SeaGreen]Anwendungen -> Zubhör -> Terminal[/COLOR]
[COLOR=SeaGreen]Application -> Accessories -> Terminal[/COLOR]

You could make a shortcut to your desktop by right click and select the proper command to make a shortcut to your desktop.


If you are lazy in typing sudo command command command

[COLOR=DarkOrchid]type[/COLOR]
[COLOR=DarkRed]sudo -s[/COLOR]
password

therefore you are root user and don't need to sudo every action.

Sometimes the text is using sudo and sometimes not. So it could be required to sudo commands to get them to work properly if you didn't used sudo -s.
Better you do sudo -s

------------------------------------------------------------------------------------------------------
**Xorg**
------------------------------------------------------------------------------------------------------
First of all : Xorg is a Server :)

Xorg Default Driver seems to be : fbdev, or vesa.
You could also run the Server with your Nvidia Board by doing a xorg.conf file and set the Driver to "nv" (built-in)
nv = is free developed Nvidia Driver which is included by Xorg as default. It supports 2D but not 3D functionality.
nvidia = propi... Driver which are available by Hardware-Driver control panel supports 2D and 3D functionality.





Let's create a Xorg "xorg.conf" file
------------------------------------------------------------------------------------------------------
1. to know : xorg.conf will not be created default by ubuntu or Xorg.
2. to know : xorg.conf will be used by nvidia drivers.
3. to know : Path /etc/X11/xorg.conf


[COLOR=DarkOrchid]type [/COLOR]

[COLOR=DarkRed]Xorg -configure[/COLOR]


This will fail. We need to stop Xorg and therefore we have to close the desktop too.
By doing the following. 

Press-Key-Combi : Ctrl + Alt + F1

now you have a fullscreen console shell opened on F1.

if you want to switch back to your desktop try F6,F7,F8 Key-Combi
Press-Key-Combi : Ctrl + Alt + F6 ...



Stopping the Xorg Server and the Gnome Desktop
---------------------------------------------

[COLOR=DarkOrchid]type [/COLOR]

[COLOR=DarkRed]sudo service gdm stop[/COLOR]

Starting is the same just replace [COLOR=DarkRed]stop[/COLOR] with [COLOR=DarkRed]start[/COLOR]



create the Xorg "xorg.conf" file
---------------------------------------------

[COLOR=DarkOrchid]type [/COLOR]

[COLOR=DarkRed]Xorg -configure[/COLOR]


Now Xorg generated a "xorg.conf.new" file. You have to take a look where it is located. It is mentioned somewhere in the output text so read it.
Assumed xorg.conf.new is generated at /root/xorg.conf.new we will do a




Move xorg.conf.new to /etc/X11/xorg.conf
---------------------------------------------

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]mv /root/xorg.conf.new /etc/X11/xorg.conf[/COLOR]


if you dont want to move the file you could also copy the file by doing

[COLOR=DarkOrchid]type[/COLOR] 

[COLOR=DarkRed]cp /root/xorg.conf.new /etc/X11/xorg.conf[/COLOR]


But dont forget to Remove the xorg.conf.new file at /root/ by doing

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]rm /root/xorg.conf.new[/COLOR]


Here i try to restart the computer with the generated xorg.conf file.
Upps it didn't worked. So right now im using a generic session to fix the problem.


The fix is:

Let's delete the generated xorg.conf from Xorg.
------------------------------------------------------------------------------------------------------

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]rm /etc/X11/xorg.conf[/COLOR]


If your are interesed of what a generated xorg.conf could look like take a look at "xorg.conf.Xorg-generated"
While the xorg.conf is deleted. The System should now start as usually.




Check your Xorg log
---------------------------------------------
In case you have troubles with Xorg. You can take a look at the log file at /var/log/

The file or files are called : Xorg.0.log , Xorg.1.log .... or also Xorg.0.log.old ....


[COLOR=DarkOrchid]type[/COLOR] either (at desktop)
[COLOR=Red]
[COLOR=DarkRed]gedit /var/log/Xorg.0.log[/COLOR] [/COLOR]

or (at console)

[COLOR=DarkRed]nano /var/log/Xorg.0.log [/COLOR]





------------------------------------------------------------------------------------------------------
**Nvidia Ubuntu Install | Uninstall**
------------------------------------------------------------------------------------------------------
Since i'm using a fresh install for testing Nvidia Drivers. I discovered to use packages installation is a way better than to install them manually.

Install by Package
---------------------------------------------
First install the package just to the 2.6.31-17 kernel (latest) via Hardware- Driver Control Panel.

Uninstall by Package
---------------------------------------------
If it fails to start 2.6.31-17. 
Start the 2.6.31-14 kernel open the Hardware-Driver Panel and you can uninstall the driver. Which seems to make clean uninstall.
This just works for the as stable marked packages up to v190. I tried it with Beta 195 package Nvidia Driver which will be also starting the driver on kernel 2.6.31-14.

 Display Kernel Menu will be done by pressing the whole time shif-key if you see "Grub loading."


Install by Manually
---------------------------------------------
1. Download Nvidia Drivers from nvidia.
2. not required rename NVidia-verylongdescription.run -> nvidia.run by doing

Open Terminal

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]rn Nvidia-verylongdescription.run nvidia.run[/COLOR]

or rename by download link as.

Start Your Computa 2.6.31-17 kernel best in Recovery Mode -> Root Shell Access (last of menu)

You could also try NV + Tab Key or NV*.run

3. Install the driver

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]cd "path/to/your/saved/driver/"nvidia.run[/COLOR]

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]sh nvidia.run[/COLOR]

4. Follow instruction till finished.

5. Restart and see what happens.


Uninstall by Manually
---------------------------------------------

Here are two choices you could choose.
1. seems to be a bit messy (after some installs / uninstalls paketmanager was somehow unable to finish uninstalls)
2. seems to be a bit to perfectly in cleaning


1. copied + pasted from somewhere 
-2 sudo doesn't work for karmic
-4 sudo i didn't used

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings[/COLOR]
sudo rm /etc/init.d/nvidia-*
[COLOR=DarkRed]sudo update-rc.d nvidia-kernel remove[/COLOR]
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`


2. copied + pasted from somewhere 
Attention just say "y" to remove the driver while next time you will be asked to remove something related to Linux-Header files :just say "n".
Okay after doing this one. Hardware- Driver Panel is completly empty. So if you have an internet connection available you can install the drivers via Software-Center now and to activate them you could use Hardware-Driver Panel.

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]sudo apt-get --purge remove nvidia*; sudo apt-get --purge autoremove[/COLOR]


------------------------------------------------------------------------------------------------------
**Nvidia Errors**
------------------------------------------------------------------------------------------------------

Check your Xorg log
---------------------------------------------
In case you have troubles with Xorg/ Nvidia drivers. You can take a look at the log file at /var/log/

The file or files are called : Xorg.0.log , Xorg.1.log .... or also Xorg.0.log.old ....


[COLOR=DarkOrchid]type [/COLOR]either (at desktop)
[COLOR=DarkRed]
gedit /var/log/Xorg.0.log 
[/COLOR] 

or (at console) 

[COLOR=DarkRed]nano /var/log/Xorg.0.log [/COLOR]


Error Nvidia Kernel could not be loaded
---------------------------------------------

If your Xorg.0.log is telling that the Nvidia Kernel could not be loaded try to load it as default by doing

[COLOR=DarkOrchid]type[/COLOR] 

[COLOR=DarkRed]nano /etc/modules[/COLOR]

at the end of file

[COLOR=DarkOrchid]
type[/COLOR]

[COLOR=DarkRed]nvidia[/COLOR]

save + close restart and see what happens



Error (WW) NVIDIA(0): WAIT (0, 7, 0x8000,
---------------------------------------------
Hui this is really bad. It could be Hardware Site or Software Site. If its Hardware it could be mostly anything: the Powersupply, the Ram,the CPU, the Mainboard, the Nvidia card. The only Solution is than to replace the faulty component by a new one.
If its Software Site try some as # marked Solutions i found and added to the xorg.conf.nvidia



Error Nvidia Manually create a xorg.conf
---------------------------------------------

I didn't have to but in case do it by

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]sudo nvidia-xconfig[/COLOR]

If the command fails rename your /etc/X11/xorg.conf to something else or replace the content with the xorg.conf.nvidia file.


Error System -> System Administration -> Nvidia X Server Settings won't save to configure file
---------------------------------------------
Open Terminal

(gnome)
[COLOR=DarkOrchid]
type[/COLOR]

[COLOR=DarkRed]gksudo nvidia-settings[/COLOR]

------------------------------------------------------------------------------------------------------
**Nvidia Pakages v190 Stable, 195 Beta Driver**
------------------------------------------------------------------------------------------------------

Go here follow the instructions 

[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html)


------------------------------------------------------------------------------------------------------
**Nvidia Driver before 96.xx** **AMD64**
------------------------------------------------------------------------------------------------------

Go here 

[http://www.nvidia.com/object/linux_amd64_display_archive.html](http://www.nvidia.com/object/linux_amd64_display_archive.html)

------------------------------------------------------------------------------------------------------
**Example xorg.conf's**
------------------------------------------------------------------------------------------------------


xorg.conf.Xorg-generated
---------------------------------------------
[COLOR=Blue]Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "glx"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card0"
    Driver      "fbdev"
    VendorName  "nVidia Corporation"
    BoardName   "NV43 [GeForce 6600 GT]"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection[/COLOR]




xorg.conf.nvidia |the as # marked are not default and could be used to solve problems.
---------------------------------------------
[COLOR=Blue]Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    #Option "NvAGP"      "1"     default seems 0  ,  i saw also 3 ?
    #Option "DPMS"          "True"  default seems False
    #Option "UseEvents" "false"    default true
    #VideoRam 524288
    #Option "RandRRotation" "on"
    #Option "RenderAccel" "true"
    #
    # Required for XGL
    #
    #Option "AddARGBGLXVisuals" "true"
    # Insert Clocks lines here if appropriate

EndSection

[/COLOR]

**Need More Options to view take a look up here**

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/part-03.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/part-03.html)
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-d.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-d.html)
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/appendix-f.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/appendix-f.html)


xorg.conf.failsafe | this one works on my to recover to the desktop in case the nvidia didn't work 
it will be created sometimes at /etc/X11/xorg.conf.failsafe
---------------------------------------------
[COLOR=Blue]Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/COLOR]

UbuAli - xorg.conf
---------------------------------------------
[COLOR=Blue]Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
Option         "Xinerama" "0"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    #Option         "TwinViewXineramaInfoOrder" "CRT-0"
Option    "AddARGBGLXVisuals"    "False"
    Option         "metamodes" "1280x1024_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Module"
#Load "extmod"
#Load "dri"
#Load "record"
#Load "dbe"
#Load "dri2"
Load "glx"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

#Section "Monitor"
#Identifier "Monitor0"
#VendorName "Monitor Vendor"
#ModelName "Monitor Model"
#EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L1950S"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "Xinerama" "0"
    Option         "DPMS"
EndSection


Section "Device"
#Identifier "Default Device"
Identifier "Card0"
Driver "nvidia"
Option "NoLogo" "True"
BusID "PCI:1:0:0"
#Option "NvAGP" "0"
#Option "DPMS" "True"
#Option "UseEvents" "False"
Option "RenderAccel" "1"
Option "NvAGP" "1"
EndSection

#Section "Screen"
#Identifier "Screen0"
#Device "Card0"
#Monitor "Monitor0"
#SubSection "Display"
#Viewport 0 0
#Depth 1
#EndSubSection
#SubSection "Display"
#Viewport 0 0
#Depth 4
#EndSubSection
#SubSection "Display"
#Viewport 0 0
#Depth 8
#EndSubSection
#SubSection "Display"
#Viewport 0 0
#Depth 15
#EndSubSection
#SubSection "Display"
#Viewport 0 0
#Depth 16
#EndSubSection
#SubSection "Display"
#Viewport 0 0
#Depth 24
#EndSubSection
#EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection
[/COLOR]
------------------------------------------------------------------------------------------------------
**Offtopic**
------------------------------------------------------------------------------------------------------
Well its a personal reminder

Cpu Test Utility :: Prime95
Nvidia Bios Utility :: Nibitor |*RISKY*|
Memory Mainboard :: Memtest86+ Ubuntu LiveCD
Memory Nvidia :: VMT :: VideoMemoryTest , Desktop + Iso clean Environment *prefer* //vmt.zip
Bootable CD :: Nero Trail Version | Ahead\Nero\DosBootimage.Ima

Tools to edit Bootable CDs
.CAB Files :: Filzip  //fz306.exe
NTFS Read/Write :: NTFS4DOS  //ntfsinst.exe  |ntfs4dos.exe
.IMA Editor :: WinImage 8.5 //winima85.exe   |delete inject files .ima .iso

Ultimate Boot CD
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Other Tools
NTune 5.0.5
DxDiag
EverestHome
[http://www.xbitlabs.com/articles/video/display/nv18-nv28.html](http://www.xbitlabs.com/articles/video/display/nv18-nv28.html) (AGP x8 Hardware to x4 [Turn Card : from right count (**inner**/**outer**) contact 3 and 11 (both **outer**): tape] AGP 3.0 -> AGP 2.0)
------------------------------------------------------------------------------------------------------
**UbuAli other Beans**
------------------------------------------------------------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1393882](http://ubuntuforums.org/showthread.php?t=1393882) DMX6Fire 24/96
[http://ubuntuforums.org/showthread.php?t=1403260](http://ubuntuforums.org/showthread.php?t=1403260) Games

---

