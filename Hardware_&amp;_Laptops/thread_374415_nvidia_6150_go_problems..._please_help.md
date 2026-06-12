---
title: "nvidia 6150 go problems... please help"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by fusionisthefuture on 2007-03-02
im sure you guys are good and sick of these video cards, and i am too, but since i just bought this thing and i want it to work, im really hoping you guys can help me out.  ive been looking for like two days now and trying everything i can see about these cards, and i dont think ive found anything that works.  im also kinda a noob with linux, im used to windows, but i think im getting the hang of it.  first of all, i noticed you guys posted code boxes, and im not sure how to do that, but i dont think i need to just yet.  im not even sure which driver to use.  should i use the latest glx, or should i use the legacy driver, or should i use the nvidia linux display driver v 1.0-9746?  btw im using dapper, and ive tried to follow some howto's about installing nvidia drivers, but i always get lost when they tell me to edit xorg.conf because the part of that file in question looks like this :

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
ive seen one refrence to vesa, saying that it would work for certain video card, but it definitely doesnt work for mine, and the tutorials where they say im supposed to change nv to nvidia wont work cuz it doesnt say nv in the first place.  also all the other code copies ive seen atleast identify the video card.  

any help would be tremendously appreciated
thanks
-arne

---

### Post by taurus on 2007-03-02
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by fusionisthefuture on 2007-03-02
ok, so i setup all of those repositories, through the synaptic packet manager, and then it told me i had some new updates available, and one said something about amd and nvidia and i downloaded them, and im trying to follow the instructions on that website link that was given, but when i do sudo apt-get install linux-amd64, (amd64 which is the value returned by uname -r)  i get: 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-amd64
im pretty sure that im doing something minor wrong, because if i try the example provided, k7 or k8, i still get the same thing.  
thanks
-arne

---

### Post by fusionisthefuture on 2007-03-02
well i warned you i was noob, and now this confirms it, i was trying to install my wireless broadcom internet adapter, and i tried sudo apt-get install build-essentials, and of course that gave me the same problem return, can someone tell me what im doing wrong?
thanks
-arne

---

### Post by siralphred on 2007-03-02
i have nvidia 6150 go also and had some problems with it also, i am not sure what your problem is , mine was choppy firefox, after several days looking around i found this which solved all my video card problems plus you get beryl with it too ;) give it a try ...i am new to linux so thats all i can help you with for now [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation")

---

### Post by taurus on 2007-03-02
> **fusionisthefuture said:**
> well i warned you i was noob, and now this confirms it, i was trying to install my wireless broadcom internet adapter, and i tried sudo apt-get install build-essentials, and of course that gave me the same problem return, can someone tell me what im doing wrong?
thanks
-arne

Is your wireless network working at all?  If it doesn't, then you can't install anything over the net.  However, build-essential (without **_s_** at the end) package is on the install CD so insert it into a drive, open a terminal, and do

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by fusionisthefuture on 2007-03-02
first off, i dont know if that link will help me because i dont have edgy, i have dapper, will beryl work with dapper?  

second, im using wired internet right now, so i dont need to have my wireless card configed, that comes next though.  and i solved the problem i was having with sudo apt-get install linux-amd64, and that was that it had to read linux-amd64-generic.  silly howto.

well i did follow the howto further after i figured that out, and i get to the part where i run dpkg-reconfigure -phigh xserver-xorg and it brings up the blue screen within the terminal that says xserver configuration.  it asks me what driver to choose, and ive tried nvidia, nv, and vesa, and only nvidia and vesa allow me to choose a resolution, and if i do and choose 1200x800 which is the native for this monitor.  all 3 settings will, when i restart gdm only let me cmd line, and i have to restore my xorg.conf file.  im still not even sure if im supposed to install the legacy drivers or the new legacy drivers or the latest drivers, ive found sources saying both.  
thanks
-arne

---

### Post by fusionisthefuture on 2007-03-02
from what ive read, it seems that edgy supports this driver better than dapper, obviously edgy is newer, is there alot about it thats improved?  how would it be recommened for someone a little newer to linux?
-arne

---

### Post by deathshadow on 2007-03-03
You know, I am AMAZED at the hoops people jump through to implement video - sure, some things like dual head (or more) take some HD editing, but for flat video drivers they are in the repositories - the problem being the documentation for doing it DOESN'T seem to be 'step by step', relies on a knowledge of the command line the user might not even HAVE, or in general is two to three YEARS out of date. Simple stuff like enabling the 'extra' repositories where they expect people to manually edit the conf file - when it's TWO CHECKBOXES.

I mean, it's an nvidia 6 series - this SHOULD be simple.

First, you need to install the package, to do this turn multiverse on (and while in there, let's hit universe)

Start Synaptic
Settings > Repositories
Under the 'internet' section make sure 
'Community maintained Open Source Software (universe)'
and 
'Software restricted by copyright or license issues (multiverse)'
are checked. Close the settings window, hit reload, do a 'mark all upgrades', find and select the 'nvidia-glx' package. (search is good for this). Select it, let it do all the dependant packages, and hit apply to install it.

once that's done, close synaptic, and reboot JUST to make sure. 

Once the machine starts up again, instead of logging in, hit ctrl-alt-F1 to switch to a text session, login, and run
sudo nvidia-xconfig

once done with that (on most systems it won't even ask any questions if the monitor is P&P) hit ctrl-alt-F7 to switch back to the login manager, then hit CTRL-BACKSPACE to shutdown X. GDM will restart X and reload automatically. 

That SHOULD be it. Works fine on my 6150LE laptop, and on my 7600GT equipped desktop.

---

### Post by fusionisthefuture on 2007-03-03
well i upgraded to edgy last night to try and get beryl installed, and im not sure if im following this tutorial right:  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Creating_the_script](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Creating_the_script)

im at the part where it says configure xorg to use new nvidia driver, and i do submethod one, and that works, but when i try to go on to submethod 2 (am i supposed to use both methods???)  and i run 
grep "Composite extension" /var/log/Xorg.0.log
i dont get the return they say im supposed to get, it doesnt return anything, just brings up another prompt.
also if i skip submethod 2 and go to installing beryl repository, and i run this command
sudo echo -e "\n## Beryl repository\ndeb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main" >> /etc/apt/sources.list
i get an error that says: bash: /etc/apt/sources.list: permission denied, but it never asks me to give it a password for sudo?
thanks
-arne

---

### Post by fusionisthefuture on 2007-03-03
well im pretty sure im only supposed to do one of the submethods, and i choose to do the first one, cuz its the recommended one.  if i do that, and this has happened every time, when i run nvidia-xconfig in any way and try to restart the gdm, it will never work.  before it used to let me choose which driver to use and such, but now it doesnt, but i know its using nvidia.  every time it tries to restart itself it will fail and give me a big blue screen asking if i want to try and troubleshoot the issue, and then it will send me back to tty.  i have to restore my xorg.conf file if i want my gui back.  and the second submethod doesnt seem to work because after i run the first entry it doesnt give back the value they say its supposed to.  i can barely surf the net, every window i try to scroll through is so freaking choppy.  please help me.  
-arne

---

### Post by deathshadow on 2007-03-03
Hmm. If it's throwing you to the troubleshooting screen... the most common cause of that is a failure to find the hardware device (which we can rule out if nvidia-xconfig throws no errors)... the second most common is not being able to find a display mode compatable with the monitor section...

Pull the following files and post them up here, we should be able to diagnose this.

Your working 'baseline' /etc/X11/xorg.conf (we might need this for monitor info)

The /etc/X11/xorg.conf that nvidia-xconfig makes. 

after it bombs with the blue screen, make a copy of /var/log/Xorg.0.log and post that up here too.

With those three files, one of us here should be able to come up with a diagnosis and possible fix.

---

### Post by fusionisthefuture on 2007-03-03
this is going to be a long one
i was reading on the nvidia forums that instability can sometimes be rectified with adding to the kernel line in /boot/grub/menu.lst so i added a couple things, one was pci=nommconf  and i forget the other, anyways, when i went to reboot, it gave me a weird screen that looked like a config screen for a video card, but had no functionality.  anyways heres what it looked like after i changed it the first time

title		Ubuntu, kernel 2.6.15-28-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=UUID=3558fba7-1379-4f2e-987c-1f327de5aad5 ro quiet splash **pci=nommconf**
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
savedefault
boot

the bold being what i added the first time, that made it not work.  then i removed that, and now it looks like 

title		Ubuntu, kernel 2.6.15-28-amd64-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=UUID=3558fba7-1379-4f2e-987c-1f327de5aad5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
savedefault
boot

and if i try to boot to this kernel, it will do the same thing, stop at that weird colored screen.  stupidly i didnt backup that file before i ****** with it, thought it would be easy to just delete what i had added.  

anyways, heres my xorg.conf

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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

this monitor should be a 1200x800, 32 bit color 60 hz, atleast thats what vista runs it at.  it seems to me that all the other examples of this file that ive seen from other peoples computers show nvidia graphics card, or even more specific than that as the device, and usually something different for the driver, not vesa.  im not sure what you mean by the xorg.conf file that nvidia-xconfig makes, isnt that it?  
-arne

---

### Post by fusionisthefuture on 2007-03-03
i guess this is what you meant by the xorg.conf that nvidia-xconfig makes

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Fri Dec 15 10:40:27 PST 2006

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

-arne

---

### Post by fusionisthefuture on 2007-03-04
well heres the xorg.0.log file. i tried to jsut copy paste it in here, but i guess its too big, so its attached. 
thanks alot for the time, i hope you can help
-arne

---

### Post by serag on 2007-03-04
i have the same video card and was only able to get the nvidia drivers to work by adding this to grub acpi=off noapic
After booting up with that added, i then installed the nvidia drivers via the envy script and it worked fine.

---

### Post by deathshadow on 2007-03-04
>> *Identifier "Generic Video Card"*

from xconfig that CAN'T be good. Means your installed nv driver doesn't recognize the card by it's id number. The lack of a bus id also means something is REALLY screwy since nvidia-xconfig should plug that number in as well. 

When I'm back on a machine that actually has software installed that can open a .odf (I'm on a work machine runnning winblows right now) I'll see what I can figure out on the logfile, but I have the suspicion somewhere along the way your drivers went screwy... meaning that your best bet might be a wipe, clean install... a lot of times following the wrong instructions for video driver installs can fubar the whole house of cards that is X.

---

### Post by deathshadow on 2007-03-04
ok, the actual failure messages appears to be:

(EE) Failed to load module "wfb" (module does not exist, 0)

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!

Both of those are indicitive of something NOT being done right with the driver install. Out of curiousity, what technique did you try for putting in the drivers? Did you try to apt-get or via Synaptic, or did you use some other technique like the .deb download, or a hodge-podge of the two? There's a LOT of 'out of date' information on doing this, and most of it doesn't work with the past few releases of Ubuntu (in my experience at least).

Methinks a wipe, fresh install and putting the drivers in as I described above is your best bet - though it's POSSIBLE HP might have ****ed with things on that chipset.

---

### Post by fusionisthefuture on 2007-03-04
yeah, i think youre right about it being installed screwy, cuz ive tried every damn method under the sun, ive tried apt-get, ive tried synaptic package, and ive tried envy, not nessecarily in that order, and ive tried like 3 different drivers.  its probably all confused, a clean install sounds good right now.  so how do i go about uninstalling ubuntu?  or repairing?  im going to download the edgy alt cd tomorrow, and then later this week i should be able to install it.  is there such thing as a repair method for ubuntu where i could just make it go through and replace al the files that it thinks are corrupt and remove all the files it doesnt need, or should i just use a livecd and a gparted to erase it and start completely over?  
thanks
-arne

---

### Post by fusionisthefuture on 2007-03-05
well i finally got the driver installed, turned out i had it right all along, i just need to actually reboot the computer after in ran nvidia-xconfig, not just restart the gdm.  now i just need to get it to run in 1200x800 resolution, which is why i wanted to do this in the first place.  can someone help me do this?  i was looking at the other post on the forum about 1200x800 resolution, and i followed the link to the ubuntu howto and followed a link there to a modeline generator, but they didnt have 1200x800 as an option in the drop down list.  i followed the other link on the other post to a howto for an hp computer, and i just put in all the stuff he had into my xorg.conf, but that just made it not work at all when i rebooted.  
thanks
-arne

---

### Post by fusionisthefuture on 2007-03-06
well for anyone with my hardware, and this problem, it turns out that after you install the driver, and it lets you reboot and gives you a gui, all you need to do to get the correct resolution is use the nvidia configuration panel in the applications menu.  once you do that itll allow you to set the screen to the resolution you want, and then it has an option to save your settings to the xorg.conf file, and when i tried to do that, it didnt work for some reason, it wouldnt actually insert the new script into the file, so i had to manually copy and paste it, but i had to kinda choose what i wanted, cuz if i copied the whole thing, it took away the syanaptics touchpad input device driver, so i couldnt use the virtual scrolling anymore.  after you do that, itll allow you to change resolution without using the nvidia config program, you can do it right from the screen resolution config that comes with ubuntu.

---

