---
title: "T4220 and Hardy"
date: 2008-04-26
forum: Hardware
---

### Post by ranpha on 2008-04-26
New Ubuntu New problems

Only thing what doesn't work perfect is screen rotate.
When i rotate the screen is filled only half and only my mouse cursor works
Gnome also freeze and i need to restart GDM

Anyway else have this problem ? the chipset is x1300 , on the San Rosa platform

I saw this [http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_an_X61_Tablet](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_an_X61_Tablet) 
The X61 is almost the same as the Fujitsu T4220 but the display thingie doesn't work

Edit: Disbaling the 3d part solves the problem but if i was correct this was a bug in gutsy and should be fixed in Hardy ...anybody knows this ?

---

### Post by Alexis.fischer on 2008-04-29
In the documentation by DennisM4 about the T4220 and gusty :([https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)) it is mentionned that there are new problems with Hardy.
Actually i can't make the pen of my T4110 working with Hardy Heron whereas it was working with Gusty.

The Log reveal the following error related to the wacom driver version:

(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(EE) module ABI major version (0) doesn't match the server's version (2)
(II) UnloadModule: "wacom"
(II) Unloading /usr/lib/xorg/modules/input//wacom_drv.so
(EE) Failed to load module "wacom" (module requirement mismatch, 0)


Is there any solution for making the tablet pc and its pen working with Hardy Heron ?

---

### Post by ranpha on 2008-04-29
> **Alexis.fischer said:**
> In the documentation by DennisM4 about the T4220 and gusty :([https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)) it is mentionned that there are new problems with Hardy.
Actually i can't make the pen of my T4110 working with Hardy Heron whereas it was working with Gusty.

The Log reveal the following error related to the wacom driver version:

(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(EE) module ABI major version (0) doesn't match the server's version (2)
(II) UnloadModule: "wacom"
(II) Unloading /usr/lib/xorg/modules/input//wacom_drv.so
(EE) Failed to load module "wacom" (module requirement mismatch, 0)


Is there any solution for making the tablet pc and its pen working with Hardy Heron ?
 
well following that guide, which i mad
e , dennism is my wiki name, you only need to remove the # in xorg.onf and set it to /dev/ttys0 if im correct otherwise in sound as a bas install because it works  here

---

### Post by Alexis.fischer on 2008-04-30
Ranpha do you confirm the pen of your tablet works with hardy ?
I will check mine again, but i don't understand why the Xorg.O.log gives a mismatch version error and refuse to load the wacom driver.

Actually i succeeded to make the pen working on fujitsu siemens T4010 with gutsy. I was following one of your wiki and the linux wacom project where i downloaded the linuxwacom-0.7.8-3.tar.bz2. Now i have the linuxwacom-0.8.0 and it doesn't work. I checked the Xorg.conf which looks fine. 
Which version of the wacom driver do you have ?

doi

---

### Post by ranpha on 2008-05-01
got the default driver from hardy but did you followed the guide as for gutsy because they are the same. works like a charme.
and for rotation i switch of the effects and it works perfect

---

### Post by Alterac on 2008-05-04
Something I want to bring up:

After upgrading to Hardy from Gutsy, I experienced the problem with my tablet pen not working as well.

I used the Synaptic Package Manager and removed "wacom-tools" and "xserver-xorg-input-wacom". Then reinstalled both.

After I did the "ctrl-alt-backspace" thingy, it started to work again. Don't really know what happened but it works fine now.

---

### Post by schmolch on 2008-05-04
Im using a X60T which has the older GMA950 GPU so this might not apply but you can try it anyways.

I have to disable dri otherwise my rotated Display is very slow:

Section "Device"
	Identifier  "Videocard0"
	Driver      "intel"
	Option	    "DRI" "false"
EndSection

You might try the same with glx and composite:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "Module"
        Disable "glx"
EndSection


Good luck

---

### Post by ranpha on 2008-05-04
Well the rotation bug is stil present in the intel driver.
I just switch off the 3d theme and then it works fine.

No need to edit the xorg.conf just turn off 3d theme

---

### Post by Alexis.fischer on 2008-05-17
Ranpha coudl you tell me what is your kernel number and the number of the wacom packages you were using ? Did you got the wacom package from the linuxwacomporject.sourceforget.net ?

---

### Post by ranpha on 2008-05-18
just got the ubuntu packages of wacom. Didn't install anything else execpt setserial. But i even think that won't be nesserary.

can you post your xorg.conf otherwise?

---

### Post by Alexis.fischer on 2008-05-18
Hi,

I have dumped Ubuntu 8.04 and came back to 7.10. The wacom tablet works perfectly. (Nice with Xournal and Cellwriter)
I just follow line by line the instruction in :
[https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)

Before that i was downloading the linuxwacomproject packages from the correspondign website. Apparently the wacom package one get with synaptic match the kernel version whereas it bugs with Hardy and with the package from the linuxwacome(ABI class errore).

So now i try to go on with the rotation stuff.
and i got  the following error :

[I]root@alexis-tablet:/usr/local/bin# rotate tablet
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
root@alexis-tablet:/usr/local/bin# rotate laptop
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'
root@alexis-tablet:/usr/local/bin# cd
root@alexis-tablet:~# cd /usr/local/bin
root@alexis-tablet:/usr/local/bin# ls
rotate
root@alexis-tablet:/usr/local/bin# cd
root@alexis-tablet:~# synaptics
bash: synaptics : commande introuvabl[/I]e


Ranpha any idea why i'm getting this ? where does this instruction wacomeConfigOpenDevice  come from ?

---

### Post by ranpha on 2008-05-19
Well your screen rotates and also your pointer (mouse) rotates.

root@alexis-tablet:/usr/local/bin# rotate tablet
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Synaptics'

I also get that error message but everthing works fine. Dunno why this happens. You should ask the maker of the script. The link is provide in the Wiki entry. I didn't write anything just put the pieces together to get everthing working.

Strange thing stil is that Hardy won't work on your laptop. Because it uses the same wacom on Gutsy.

---

### Post by roy.nico on 2008-05-21
> **Alterac said:**
> Something I want to bring up:

After upgrading to Hardy from Gutsy, I experienced the problem with my tablet pen not working as well.

I used the Synaptic Package Manager and removed "wacom-tools" and "xserver-xorg-input-wacom". Then reinstalled both.

After I did the "ctrl-alt-backspace" thingy, it started to work again. Don't really know what happened but it works fine now.

Hello, 

i experienced exactly the same problem : my tablet pen used to work perfectly under Gutsy. Then after i upgraded today to hardy, it did not work at all. Following you, a uninstalled an reinstalled   "wacom-tools" and "xserver-xorg-input-wacom" and it works now. 

nico

---

### Post by ranpha on 2008-05-21
You know off course that the Xorg.conf has been reset to a default one. Thus clearing all the wacom entries. ...

Just checking

---

### Post by roy.nico on 2008-05-22
> **ranpha said:**
> You know off course that the Xorg.conf has been reset to a default one. Thus clearing all the wacom entries. ...

Just checking
Well, i checked it precisely BEFORE re-installing xorg, but i did not see any changes. Everything about the tablet, stylus, eraser was here, as i set it before. But maybe i missed something. I could check in the backup versions of xorg...

nico

---

### Post by ranpha on 2008-05-22
Can you post your Xorg.conf ? makes it easier for me to check

---

### Post by roy.nico on 2008-05-22
> **ranpha said:**
> Can you post your Xorg.conf ? makes it easier for me to check
my actual xorg.conf has 23 April 08 as date of modification (and I reinstalled wacom Yesterday)... So, it seems, it was even not modified...

```



Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/ttyS0" # "/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/ttyS0" # "/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/ttyS0" # "/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	Option          "DRI"           "false"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Écran générique"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by ranpha on 2008-05-23
It seems i got some extra entry in here ....mmmmm don't remeber why...try this

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option        "Mode"          "Absolute" #extra entry unknown
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

---

