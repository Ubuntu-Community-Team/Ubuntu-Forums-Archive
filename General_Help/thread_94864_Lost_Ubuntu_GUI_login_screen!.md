---
title: "Lost Ubuntu GUI login screen!"
date: 2005-11-25
forum: General Help
---

### Post by iNerdSure on 2005-11-25
Recent updates have resulted in the loss of Ubuntu (Breezy) GUI login screen!. On booting up, I get terminal text login screen. Can still type in username and password, and " startx ", and then back to usual apps in GUI.

But how do I get back or restore the Ubuntu GUI screen? :confused: 

Please help. Many thanks.

---

### Post by Haegin on 2005-11-25
When you login install BUM (boot-up manager) and make sure that GDM is installed and set to run on  startup. If you use kde you need kdm though gdm will still work. The same goes for all the other window managers - just install gdm and make sure it starts...

In bum use the services script and set start-up priority to 13 (at least thats what mine is) and set shut down priority to 1.

Hope this helps

---

### Post by iNerdSure on 2005-11-25
[QUOTE=Human Prototype]When you login install BUM (boot-up manager) and make sure that GDM is installed and set to run on  startup. If you use kde you need kdm though gdm will still work. The same goes for all the other window managers - just install gdm and make sure it starts...

In bum use the services script and set start-up priority to 13 (at least thats what mine is) and set shut down priority to 1.

Hope this helps[/QUOTE]
Many thanks for the quick help. But I'm a Linux newbie convert. I use Gnome and not KDE. How do I go about installing BUM and GDM? In simple newbie language, please. Thanks.

---

### Post by Randy Sparks on 2005-11-25
A few things might have happened here:

1) you've somehow lost the GDM program (this handles the startup of the GUI during boot)

or

2) you've somehow lost the link to make it run during boot

After you login, type 

sudo /etc/init.d/gdm start 

If you see the usual login screen then GDM is installed and you need to recreate the link so it runs at boot (see below). If you get an error along the lines of program/file not found then GDM is missing. In that case you can try

sudo apt-get install gdm

This depends on your apt repositories being setup correctly.

If GDM appears to be present, you can try recreating the link. If it ran then you should now have access to the desktop. Open Gnome Terminal (Applications - Accessories - Terminal). Type the following at the comand line prompt

sudo ln -s /etc/init.d/gdm /etc/rc2.d/S13gdm

Then reboot (sudo reboot). Everything should work OK now. 

Just one other thing - make sure that you're set to the correct run level. Open inittab (type sudo gedit /etc/inittab at the prompt) and ensure that the third and fourth lines read:

# The default runlevel.
id:2:initdefault:

---

### Post by jonny on 2005-11-25
Have you installed the restricted nvidia modules?  The last update didn't force these to the latest version for me and I had the same problem as you.

When your system first boots, press esc to get the Grub menu, and try booting a different kernel.  If that restores your gui, go to synaptic package manager and choose the nvidia package that matches your kernel.

---

### Post by iNerdSure on 2005-11-25
Many thanks, Randy Sparks.

Followed your steps and now I have got back the Ubuntu GUI login screen and the "logout, shut down, restart, hibernate" sceens back.

However, the screen resolution is now changed to 1024 x 768, instead of previously at 1280 x 800 laptop wide screen setting.

Tried changing from GUI System => Preferences => Screen Resolution , but there is only one default setting of 1024 x 768 available.

Rather puzzling. Anyway, it's working. Except, with visual distortion. Thanks again.

---

### Post by iNerdSure on 2005-11-25
Thanks, jonny. I don't think I installed nvidia modules. All I did was to follow the System Update Manager notifier, and the updates were done automatically.

---

### Post by teaker1s on 2005-11-25
hit esc on boot and you can run previous kernel that will boot with gui next install kernel restricted module that is right for you eg 386i /686/k7
reboot if you still have no gui you will need to repeat restart with old kernel as before and use synaptic to install nvidia-glx-legacy if you have nvidia card. as many older nvidia cards now appear to be supported under legacy still problems then boot latest kernel
if need be
sudo dpkg-reconfigure xserver-xorg 
NV is basic no thrills or open gl driver
nvidia is open gl
as for other brands you will have to select as required

---

### Post by iNerdSure on 2005-11-25
[QUOTE=teaker1s]hit esc on boot and you can run previous kernel that will boot with gui next install kernel restricted module that is right for you eg 386i /686/k7
reboot if you still have no gui you will need to repeat restart with old kernel as before and use synaptic to install nvidia-glx-legacy if you have nvidia card. as many older nvidia cards now appear to be supported under legacy still problems then boot latest kernel
if need be
sudo dpkg-reconfigure xserver-xorg 
NV is basic no thrills or open gl driver
nvidia is open gl
as for other brands you will have to select as required[/QUOTE]
Thanks, Teaker1s. The display card in my Acer 4061 laptop is Intel 915GM Integrated 3D Graphics with Media Graphics Accelerator 900. Can I follow the same steps you have described for NVidia?   :confused:

---

### Post by Randy Sparks on 2005-11-25
To fix your resolution problems, you can either edit the /etc/X11/xorg.config file or simply reconfigure Xorg by typing the following at the command prompt:

sudo dpkg-reconfigure xserver-xorg

You'll have to setup everything, from keyboard to display, but it'll only take a few minutes.

---

### Post by teaker1s on 2005-11-25
I'm guessing that you may be missing the linux restricted module-try that first when you boot old kernel while in old kernel sudo gedit /etc/X11/xorg.conf
look for section

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	131072
EndSection

you can see my driver this will give you a hint on your driver
sudo dpkg-reconfigure xserver-xorg is an easy way of safely editing xorg.conf
if your still having problems with driver I would search synaptic for eg nvidia or ati or what ever your xorg.conf driver is in case the driver has changed

---

### Post by iNerdSure on 2005-11-25
I check the contents of /etc/X11/xorg.conf file:

[PHP]Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection[/PHP]
It appears that 1280x800 resolution setting is already in place. However, the actual display has been forced down to 1024x768. Don't know what's causing this from happening. :confused: 

I think I'll bear with this distortion for the time being, until I figure out why restoring GDM is forcing the laptop LCD res from 1280x800 down to 1024x768.

---

### Post by iNerdSure on 2005-11-25
Teaker1s, I checked the  /etc/X11/xorg.conf and found the "Device" as:
[PHP]Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        128000
        Option          "UseFBDev"              "true"
EndSection[/PHP]
Do I need to do anything different from that of "NVidia"?   :confused:

---

### Post by teaker1s on 2005-11-25
the intel driver will be more suitable as you have intel graphics unless anyone knows of an alternative or newer driver 
have you in konsole run
'sudo dpkg-reconfigure xserver-xorg' as your xorg.conf file looks wrong in the way the resolution data is. plus I dont see 
HorizSync		VertRefresh	which you will need to set for your lcd to get correct display

when you run the above command -space selects an option, tab button moves you to ok enter=enter

see mine below

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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	131072
EndSection

[COLOR="Red"]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
[/COLOR]
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by iNerdSure on 2005-11-26
Teaker1s, I ran:
[PHP]sudo dpkg-reconfigure xserver-xorg[/PHP]
and it seems to "half" ok now. :confused: 

What's happening now is that when I first power-up and boot-up, I now get the Ubuntu GUI login screen. And the resolution is now defaulted to 1024x768. Well, at least I now have GUI login, instead of Terminal text login.

Now, here is the puzzle: When I logout by Ctrl+Alt+Backspace, and re-login via Terminal, and "startx", I am back to 1280x800 resolution!  :razz:  :confused:

I suppose I can "live with this oddity" for the time being, but it will be great if I can get the 1280x800 on the first login, instead of going through two logins to get it.

---

### Post by teaker1s on 2005-11-26
system-preferences-screen resolution
tick make default for ubuntu and when you log out of session you will have to save it
if you use gnome just tick the box 
if you use kde then you will have to change sessions settings in system settings to manual save session

glad you have a gui back coming from a windows past I'm lost without it too:KS

---

### Post by iNerdSure on 2005-11-27
[QUOTE=teaker1s]system-preferences-screen resolution
tick make default for ubuntu and when you log out of session you will have to save it
if you use gnome just tick the box 
if you use kde then you will have to change sessions settings in system settings to manual save session

glad you have a gui back coming from a windows past I'm lost without it too:KS[/QUOTE]
Thanks, Teaker1s. Yes, I have recovered the Ubuntu GUI login screen. I've also learn from the "readme" files in 855 resolution (which I downloaded via Synaptic Package Manager for) for Intel 915 GM chipset graphics, that the 1280x800 resolution doesn't "stick". I have to tweak it via rc.local or local.start.

Well, will get to it when I find some time. The priority is to get the first sound to beep, or the first tune to play. I've been sound-proofed in this silent mode, ever since I first installed Breezy from its launch date. :mad:  

Need to crack this (no)sound barrier soon, otherwise, I need to revert to M$WXp on dual boot. :rolleyes:

---

### Post by teaker1s on 2005-11-27
glad your gui sorted
in system-preferences sound can you see your sound card?
if so then you need to use the same audio sink on system and app eg.alsa mixer.
if it's not there then i'd look at device manager and find out the vendor id and product id so you can fine out make and model and start from there.


good luck

---

### Post by iNerdSure on 2005-11-28
[QUOTE=teaker1s]glad your gui sorted
in system-preferences sound can you see your sound card?
if so then you need to use the same audio sink on system and app eg.alsa mixer.
if it's not there then i'd look at device manager and find out the vendor id and product id so you can fine out make and model and start from there.


good luck[/QUOTE]
Tried that several times before. Didn't work. No luck! :(

---

### Post by teaker1s on 2005-11-28
look in device manager for unknown devices and check out the vendor id and model/product id should look something like screenshot and google them

---

