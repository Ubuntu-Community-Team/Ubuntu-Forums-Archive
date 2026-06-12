---
title: "nvidia-180 drivers"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by rpalmer on 2009-04-09
I am  using a Biostar video card with the Geforce 8400GS chipset.  I've tried installing the drivers from Nvidia's website and through synaptic.  I don't get it, they installed fine on version 9.04 but I can't get them to load on 8.10.

A couple weird things:
1. I updated my sources list to include avenard's repository BUT when I perform a search in synaptic, I don't see the the drivers HOWEVER, when I scroll down the list i can see them. Something is wrong here.

2. When I do try to install the nvidia-180 drivers from synaptic, I check everything that says nvidia-180 so I know I am getting everything I need but I get an error message when I restart forcing me to use low resolution mode.

Any ideas?

---

### Post by norwoods on 2009-04-09
install nvidia-glx-180.
if you dont get 180 driver after a reboot, run System-->Administration-->Hardware Drivers where you should see the 180 driver. Deactivate any active driver,then Activate the 180 driver and reboot.

---

### Post by rpalmer on 2009-04-09
Here's what is installed:

nvidia-glx-180 (180.44)
nvidia-glx-180-dev (180.44)
nvidia-180-kernel-source (180.44)
nvidia-180-libvdpau-dev (180.44)
nvidia-180-libvdpau(180.44)
nvidia-180-kernel-source(180.44)

---

### Post by norwoods on 2009-04-09
can you run sudo nvidia-xconfig to modify your xorg.conf file?

---

### Post by rpalmer on 2009-04-09
Yes,  when I run that command I get the following message:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by norwoods on 2009-04-10
caun you run gksu nvidia-settings and see which driver it thinks is installed?

can you alter screen settings in nvidia-settings?

have you limited yourself with System-->Preferences-->Screen Resolution?

---

### Post by rpalmer on 2009-04-10
When I run gksu nvidia-settings - I get an error message that says "You do not appear to be using the nvidia X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart X server"

When I run sudo nvidia-xconfig I see the following.
[I]
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using
         screen "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add
         new CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add
         new CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf`
[/I]

---

### Post by inobe on 2009-04-10
be sure you have 180-modealiases installed in synaptic !

you will need to reboot and check hardware drivers to see if the driver is listed.

---

### Post by unutbu on 2009-04-10
I just reinstalled intrepid today, and the version 180 driver was not shown as an option in System>Admin>Hardware Drivers until I installed nvidia-180-modaliases and nvidia-common.

PS. Have any chili lately, inobe? :)

---

### Post by blue carrot on 2009-04-10
Hi Guys,
I'm having a problem with my system, that when I install the nvidia 180 driver (or the 173 or the 177 for that matter), then reboot, upon startup my monitor is blank with the message "out of range" on it (viewsonic monitor). 

So I have to restart and go into recovery mode and get it to repair X server. But then when I start up, I can see again, except its back to damn 800x600 resolution which is the highest I can get. 

If i run sudo nvidia-xconfig , I get the following message:

[I]Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'[/I]

---

### Post by unutbu on 2009-04-10
blue carrot, Open a terminal (Applications>Accessories>Terminal).
Please post the output of the following commands:

```
dpkg --get-selections | grep nvidia
cat /etc/X11/xorg.conf
ls -l /etc/X11
```

---

### Post by inobe on 2009-04-10
> **unutbu said:**
> I just reinstalled intrepid today, and the version 180 driver was not shown as an option in System>Admin>Hardware Drivers until I installed nvidia-180-modaliases and nvidia-common.

PS. Have any chili lately, inobe? :)

pretty good, in fact i had some today ;)

so you didn't need to select the kernel module ?

---

### Post by inobe on 2009-04-10
> **blue carrot said:**
> Hi Guys,
I'm having a problem with my system, that when I install the nvidia 180 driver (or the 173 or the 177 for that matter), then reboot, upon startup my monitor is blank with the message "out of range" on it (viewsonic monitor). 

So I have to restart and go into recovery mode and get it to repair X server. But then when I start up, I can see again, except its back to damn 800x600 resolution which is the highest I can get. 

If i run sudo nvidia-xconfig , I get the following message:

[I]Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'[/I]


[http://www.hotubuntunews.com/blog_3.shtml](http://www.hotubuntunews.com/blog_3.shtml)

---

### Post by unutbu on 2009-04-10
Sorry; I guess I was unclear. I installed nvidia-glx-180. This pulled in nvidia-180-kernel-source for me. To my befuddlement, this did not alert System>Admin>Hardware Driver that version 180 was available. 

After a while I tried installing nvidia-common and nvidia-180-modaliases, and then (maybe after a reboot?) System>Admin>Hardware Driver was aware of nvidia-180.

Hm... chili. However, the beef stew was excellent :)

---

### Post by norwoods on 2009-04-10
> **rpalmer said:**
> When I run gksu nvidia-settings - I get an error message that says "You do not appear to be using the nvidia X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart X server"

When I run sudo nvidia-xconfig I see the following.
[I]
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using
         screen "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add
         new CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add
         new CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf`
[/I]
the warnings are ok, it just did not like your old xorg.conf
if you reboot at this point, you should start with the new xorg.conf with the new nvidia driver. if you run gksu nvidia-settings it should see the new driver.

---

### Post by blue carrot on 2009-04-11
unutbu, here's the output of those three commands:

> bart@shipibo:~$ dpkg --get-selections | grep nvidia
nvidia-173-modaliases				install
nvidia-177-modaliases				install
nvidia-180-kernel-source			install
nvidia-180-modaliases				install
nvidia-71-modaliases				install
nvidia-96-modaliases				install
nvidia-common					install
nvidia-glx-173					deinstall
nvidia-glx-177					deinstall
nvidia-glx-180					install
nvidia-settings					install

> bart@shipibo:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Wed Nov 26 11:27:46 PST 2008

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

> bart@shipibo:~$ ls -l /etc/X11
total 72
drwxr-xr-x 2 root root 4096 2009-04-05 15:38 app-defaults
drwxr-xr-x 2 root root 4096 2008-10-30 12:10 cursors
-rw-r--r-- 1 root root   14 2008-10-30 12:07 default-display-manager
drwxr-xr-x 6 root root 4096 2008-10-30 12:02 fonts
lrwxrwxrwx 1 root root   13 2009-04-04 02:18 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root 4096 2008-10-30 12:03 xinit
drwxr-xr-x 2 root root 4096 2009-04-05 15:36 xkb
-rw-r--r-- 1 root root 1469 2009-04-11 13:05 xorg.conf
-rw-r--r-- 1 root root 1137 2009-04-05 15:01 xorg.conf.20090405150143
-rw-r--r-- 1 root root 1137 2009-04-06 21:48 xorg.conf.20090406214802
-rw-r--r-- 1 root root 1292 2009-04-10 19:53 xorg.conf.20090410195331
-rw-r--r-- 1 root root 1469 2009-04-11 12:59 xorg.conf.20090411125940
-rw-r--r-- 1 root root 1037 2009-04-11 13:05 xorg.conf.backup
drwxr-xr-x 2 root root 4096 2008-10-30 11:58 Xresources
-rwxr-xr-x 1 root root 3730 2008-10-24 02:40 Xsession
drwxr-xr-x 2 root root 4096 2009-04-05 15:38 Xsession.d
-rw-r--r-- 1 root root  265 2008-10-24 02:40 Xsession.options
-rw-r--r-- 1 root root   13 2007-07-24 21:59 XvMCConfig
-rw------- 1 root root  614 2008-10-30 11:58 Xwrapper.config

---

### Post by unutbu on 2009-04-11
blue carrot, what model Viewsonic monitor are you working with?
You are getting a "monitor out of range" error, and I see in your xorg.conf:
```

HorizSync 28.0 - 33.0
```
This seems low to me. For a ViewSonic VA1926w, the correct range would be 
```
    HorizSync       30.0 - 82.0
```
See
[http://www.viewsonic.com/products/desktop-monitors/lcd/value-series/va1926w.htm](http://www.viewsonic.com/products/desktop-monitors/lcd/value-series/va1926w.htm) where it says
```
Frequency  	Fh: 30~82kHz, Fv: 50~75Hz
```

Also, which version of Ubuntu are you using? (e.g Gutsy, Hardy or Intrepid). As Ubuntu progresses, the developers are moving away from using xorg.conf to configure X. I'm thinking you may be able to removing the HorizSync and VertRefresh lines completely, and let the monitor send its [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data") info to the X server on its own.

---

### Post by blue carrot on 2009-04-11
Unutbu, thanks for taking the time to help.

I'm using a viewsonic VE710b , it's a few years old. 17 inch non-widescreen. 

I'm running Intrepid 32 bit (8.10).

How do I get into the xorg.conf to remove the two lines? When I enter cat /etc/X11/xorg.conf it shows me the sections ("monitor" "device" etc). but I can't see the lines below them. Sorry I am quite a noob.  

I would be really grateful for any help leading to a solution for this problem. 



Cheers

---

### Post by unutbu on 2009-04-11
Unfortunately, I could not find specs for the VE710b on viewsonic's website, but according to [http://www.linuxquestions.org/questions/linux-hardware-18/why-does-monitor-go-out-of-sync-in-text-mode-but-work-ok-in-graphics-mode-586290/](http://www.linuxquestions.org/questions/linux-hardware-18/why-does-monitor-go-out-of-sync-in-text-mode-but-work-ok-in-graphics-mode-586290/) and [http://www.superwarehouse.com/ViewSonic_VE710B_17_LCD_Monitor/VE710B-4/ps/624771](http://www.superwarehouse.com/ViewSonic_VE710B_17_LCD_Monitor/VE710B-4/ps/624771), the horizontal frequency range of the monitor is 30--80 kHz, and the vertical refresh rate range is 50--85 Hz.

So how about try the following:

If you can login and get a graphical display (even a low resolution display), open a terminal and type

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-20090411   # make backup copy just in case
gksu gedit /etc/X11/xorg.conf
```

Change 

```
Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

```
to

```
Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Unknown"
[B]HorizSync 30.0 - 80.0
VertRefresh 50.0 - 85.0[/B]
Option "DPMS"
EndSection
```

Save and exit gedit. Log out. Press Ctrl-Alt-Backspace. This will restart the X server.
Do you get a nicer graphical display?

---

### Post by blue carrot on 2009-04-12
Hi unutbu. Theres a problem here now, now when I open gksu gedit /etc/X11/xorg.conf
all I see is:
> 
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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


The parts that I can edit are no longer visible. Gargh!

---

### Post by unutbu on 2009-04-12
blue carrot, have you tried inobe's advice:
[http://www.hotubuntunews.com/blog_3.shtml](http://www.hotubuntunews.com/blog_3.shtml)
? Copy down these numbers:
```

HorizSync 30.0 - 80.0
VertRefresh 50.0 - 85.0

```
so you can use them when asked.

---

### Post by rpalmer on 2009-04-12
> **inobe said:**
> be sure you have 180-modealiases installed in synaptic !

you will need to reboot and check hardware drivers to see if the driver is listed.

nvidia 180 is listed in hardware drivers and modaliases is already installed.  I had no problems installing the nvidia 180 drivers in 9.04... maybe 9.04 installs a newer or older version of the 180 driver that works with my card?

---

### Post by blue carrot on 2009-04-12
unutbu, yes I tried that, but nowhere does it give me the option to configure the monitor. It talks about keyboard stuff and then exits after that's done. i also tried running gksu gedit /etc/X11/xorg.conf from the boot menu but it did the same thing as it does if I run it in terminal, which is not show the actual lines that i need to edit (as in my previous post). it seems like the driver has taken away the ability to edit xorg.conf or something?

---

