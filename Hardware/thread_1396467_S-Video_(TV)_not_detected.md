---
title: "S-Video (TV) not detected"
date: 2010-02-02
forum: Hardware
---

### Post by lacomax on 2010-02-02
:?:
Hi,
I have a Fujitsu-Siemens AMILO Pro V2020
Pentium M 725 / 1.6 GHz - Centrino 
RAM 768 MB 
Extreme Graphics 2 
15.1"TFT 1024 x 768 ( XGA )

and xubuntu 9.10 detects the following
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

I try then to connect my TV (PAL)on the S-Video port, but the only display availabe is the on-board TFT.
How can I use/activate my S-Video output?

Tx

---

### Post by IcarusR on 2010-02-02
With TV connected to S-video out & switched on go to

System > Preferences > Screen Resolution > Detect Displays

It should find TV

---

### Post by lacomax on 2010-02-02
I've already tried it, but with the TV on and the SVideo connected, it does not find any other Display than the TFT from the notebook.
Any other idea?

---

### Post by zwaardmeester on 2010-02-02
Try to boot Ubuntu with the TV switched on and the cable in. Does this help?

---

### Post by lacomax on 2010-02-02
no, it does not help. :(
It still does not recognise the Output. 
Someone plz help! otherwise I'll have to use Windows (also installed on the laptop, and it works)

---

### Post by zwaardmeester on 2010-02-02
You might need to edit the following configuration file: 
/etc/X11/xorg.conf 
This guy contains display information etc. which the Intel driver uses in turn. First make a backup for when things to ill:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
then edit the file to your needs by issueing:
```
gksudo gedit /etc/X11/xorg.conf
```
Take a look at the following tread to learn how to add a TV display: [http://ubuntuforums.org/showthread.php?t=9106&page=4]("http://ubuntuforums.org/showthread.php?t=9106&page=4"), especially post #35 i think. 

After you changed the file, save it and close Gedit. Log out and back in to apply the changes. 

To restore the backup:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

When there is no more display _at all_, you can always access a console by pressing the combination Ctrl-Alt-F1. The combination Ctrl-Alt-F7 brings you back to the "graphical world".

---

### Post by lacomax on 2010-02-02
[B]I've just tried it, but it still does not work.
When I execute xrandr I get the following: [/B]

a1@LAPTOPUBUNTU:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +   85.0*    75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS disconnected (normal left inverted right x axis y axis)
a1@LAPTOPUBUNTU:~$ 
[B]
And my Xorg.0.log has following Warnings:[/B]
a1@LAPTOPUBUNTU:~$ cat /var/log/Xorg.0.log|grep WW
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
(WW) intel(0): Allocation error, framebuffer compression disabled
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
(WW) intel(0): Chosen PLL clock of 66.5 Mhz more than 2% away from desired 65.0 Mhz
(WW) intel(0):   Hardware claims pipe A is on while software believes it is off
(WW) intel(0): Option "monitor-TV" is not used
(WW) intel(0): Option "monitor-LVCD" is not used
(WW) intel(0): Chosen PLL clock of 66.5 Mhz more than 2% away from desired 65.0 Mhz
a1@LAPTOPUBUNTU:~$ 

**I still need some help.....**

---

### Post by IcarusR on 2010-02-02
Did you put a 'TV' line in your xorg.conf ??
Reading the xorg log it would appear you have not defined TV in xorg.conf
You do not need TDMS 'man intel' says

> TMDS-1
       First DVI SDVO output

   TMDS-2
       Second DVI SDVO output

       SDVO and DVO TV outputs are not supported by the driver at this time.


So TMDS will not work.
Post your xorg.conf.

---

### Post by lacomax on 2010-02-02
**There you have that is the 'original' xorg.conf, the one suggested on  **
 [[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=9106&page=4[/COLOR]]("http://ubuntuforums.org/showthread.php?t=9106&page=4"), post #35 **didn't work**,  **I hope it helps**
 
Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" RightOf "Screen0"
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
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
 
Section "Module"
Load "dbe"
Load "dri"
Load "dri2"
Load "extmod"
Load "record"
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
 
Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection
 
Section "Monitor"
Identifier "Monitor1"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection
 
Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
### [arg]: arg optional
#Option "NoAccel" # [<bool>]
#Option "SWcursor" # [<bool>]
#Option "ColorKey" # <i>
#Option "CacheLines" # <i>
#Option "Dac6Bit" # [<bool>]
#Option "DRI" # [<bool>]
#Option "NoDDC" # [<bool>]
#Option "ShowCache" # [<bool>]
#Option "XvMCSurfaces" # <i>
#Option "PageFlip" # [<bool>]
Identifier "Card0"
Driver "intel"
VendorName "Intel Corporation"
BoardName "82852/855GM Integrated Graphics Device"
BusID "PCI:0:2:0"
EndSection
 
Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
### [arg]: arg optional
#Option "NoAccel" # [<bool>]
#Option "SWcursor" # [<bool>]
#Option "ColorKey" # <i>
#Option "CacheLines" # <i>
#Option "Dac6Bit" # [<bool>]
#Option "DRI" # [<bool>]
#Option "NoDDC" # [<bool>]
#Option "ShowCache" # [<bool>]
#Option "XvMCSurfaces" # <i>
#Option "PageFlip" # [<bool>]
Identifier "Card1"
Driver "intel"
VendorName "Intel Corporation"
BoardName "82852/855GM Integrated Graphics Device"
BusID "PCI:0:2:1"
EndSection
 
Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection
 
Section "Screen"
Identifier "Screen1"
Device "Card1"
Monitor "Monitor1"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

---

### Post by lacomax on 2010-02-03
Any Ideas? :?

---

### Post by IcarusR on 2010-02-03
Did you try adding this to your origional xorg.conf ? ...
> Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "monitor-VGA"  "VGA"
        Option          "monitor-TV"   "TV"
        Option          "monitor-LVCD" "LVCD"
EndSection

Section "Monitor"
        Identifier      "VGA"
        Option "Ignore" "true"
EndSection

Section "Monitor"
        Identifier      "LVCD"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "TV"
        Option  "Ignore" "false"
        Option "TV_FORMAT" "PAL"

EndSection

---

### Post by lacomax on 2010-02-04
Yep! but didn't help. My TV isn't detected.

---

### Post by lacomax on 2010-02-04
On the man page from intel "man intel" I found the following
> SDVO and DVO TV outputs are not supported by the driver at this time.
is that true?

---

### Post by lacomax on 2010-02-10
Ok, I've learned that SDVO has nothing to do with S-Video. 
So, does anyone have an Idea?

---

### Post by distilledwater on 2011-05-05
It looks like they have removed s-video support completely.

I have tried on both ubuntu 11.04 and kubuntu 11.04 and both fail to recognise the s-video output. However last week on kubuntu 10.10 i had my laptop connected fine to my TV through s-video.

Also the xorg.conf file has been moved and no longer exists in /etc/x11

If anyone has any updates on how to get s-video working it would be great.

I have tried forcing it to recognise the output like on this page: 
[https://wiki.ubuntu.com/X/Config/SVideo](https://wiki.ubuntu.com/X/Config/SVideo)

But to no avail. I just get this error readout:


ubuntu@ubuntu:~$ xrandr --output S-video --set load_detection 1
warning: output S-video not found; ignoring
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  26
  Current serial number in output stream:  26

---

### Post by takyoji on 2011-06-22
Your issue may be related to: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/763688](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/763688)
I'm also affected by this friggen regression, and nobody seems to have done anything about it for months yet.

---

