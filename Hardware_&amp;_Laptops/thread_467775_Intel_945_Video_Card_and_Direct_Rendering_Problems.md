---
title: "Intel 945 Video Card and Direct Rendering Problems"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by Espionage724 on 2007-06-08
I have Kubuntu 7.04 Feisty Fawn and Intel 945 Video Card. First I did a clean install of Feisty and then I installed Beryl. 5mins later I uninstalled Beryl and installed Compiz. I had a probelm in Compiz so I restarted the computer. After the reboot, when I loaded Compiz the screen wouldn't come up (desktop, windows, nothing). I have the 915resolution and the xserver-xorg-video-intel packages. When i used the "glxinfo" command and it said my direct rendering was disabled. Any help?

---

### Post by Espionage724 on 2007-06-08
Fixed! I reconfigured my xserver and selected the i810 driver. VESA (or something) was selected for some reason

---

### Post by iblicf on 2007-10-21
hi , i have exactly the same poroblem .... intel 945G ... it should be gma950 accelerator

i have just installed the gutsy ...few days before , imagin apparently that "glxinfo|grep render" says YES ...:) , but now :
> 
iblicf@ubuntu:/tmp/dta$ glxinfo |grep render
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2

here is my xorg.conf

> Section "Device"
        Identifier      "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

glxgears  works fine  ...and compiz have transparent  effect ..seems  3D accelerate  worked ..
does this 'in reason ' or  'beyond reason'??

as you say ...should i change the "Driver=i810" ? 

any ideas  welcome :)

---

### Post by iblicf on 2007-10-23
strange ... maybe compiz coause this  ... dont's know "LIBGL_ALWAYS_INDIRECT" what's mean , i have installed gentoo yesterday , and use <Driver "i810"> , got the direct render ,but have not install compiz yet  

i try to change  <Driver "i810"> within ubuntu , no use ..

> iblicf@ubuntu:/etc/X11$ glxinfo|grep rend
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2

have somebody use this vedio card ? ( 945G )

---

### Post by katakaio on 2007-11-23
I'm also using the 945G video card, but I don't have any answers - I also have the "LIBGL_ALWAYS_INDIRECT set" problem which disables direct rendering. I'm getting choppy video because of it. I briefly looked at the code in /usr/bin/compiz to see where INDIRECT was being set, but I'm not skilled at the inner workings of Compiz. Could someone with more Compiz knowledge take a look at this file? I have a feeling that our problem may lie in there . . .

---

### Post by beercz on 2007-11-28
Thanks to JohnPhys in [this thread]("http://ubuntuforums.org/showthread.php?p=3853819") (Post #5).
 
I removed xserver-xgl and it enabled me to get direct rendering enabled.
 
Hope it helps.

---

### Post by katakaio on 2007-12-26
Good idea beercz . . . I had been suggested the same thing earlier, but I was still unable to get direct rendering up after removing xserver-xgl. I think I'm going to get into /usr/bin/compiz and see if I can work more good than bad . . .

---

### Post by Beholder87 on 2008-01-30
Hi i am having same problems here!
i tried to find an answer here: [http://ubuntuforums.org/showthread.php?t=675299&page=3](http://ubuntuforums.org/showthread.php?t=675299&page=3)
but i couldn't receive a answer.....

when i installed my gutsy, the video was horrible so they told me there to reconfigure the xorg using this command: ```
sudo dpkg-reconfigure xserver-xorg 
```
then this command changed the driver from vesa to intel because my graphics card is a Intel 945G integrated graphics.

after that (the first reconfig), the video as a little better, but still it isn't good enough, it's slow.....
when i run this command: glxinfo | grep -i direct, it says the same as you guys:
```
monster@monster:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
monster@monster:~$
```

do you know what is my problem or can you help me to solve this problem?
here is my /etc/X11/xorg.conf file:
```
Section "Files"
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
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"	
EndSection

Section "Monitor"
	Identifier	"DELL P780"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"DELL P780"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
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

you can check my posts from the link above. that solved a half of my problem... (desktop effects are working after the xorg reconfig...)

thanks
=)

---

### Post by Beholder87 on 2008-01-30
today i tried to reconfigure again the xorg and the terminal shows an error after reconfiguring: 
```
monster@monster:~$ sudo dpkg-reconfigure xserver-xorg
WARNING: Failed to open config file /etc/modprobe.d/blacklist-oss: No such file or directory
WARNING: Failed to open config file /etc/modprobe.d/blacklist-oss: No such file or directory
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080130130112
WARNING: Failed to open config file /etc/modprobe.d/blacklist-oss: No such file or directory
monster@monster:~$ 

```
what does this warnings have any mean?

here is my new xorg:
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

Section "Files"
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
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	VideoRam	262144
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"DELL P780"
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	48-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"DELL P780"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
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

somebody could help me please to get Hardware Acceleration?  thanks

**PROBLEM SOLVED!!! HERE IS THE LINK: [http://ubuntuforums.org/showthread.php?p=4246432#post4246432](http://ubuntuforums.org/showthread.php?p=4246432#post4246432)**

---

### Post by katakaio on 2008-04-22
Well, unfortunately Beholder87's fix didn't work for me. I even upgraded to Hardy (which doesn't include the xserver-xgl drivers, if I remember right - I didn't have them installed) to no avail. I still get the same old message:

katakaio@columbia:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

I would really like my direct rendering enabled so I can enjoy Compiz, but I couldn't find anything in /usr/bin/compiz that seemed obviously wrong. Is there a way to manually force direct rendering, i.e. force LIBGL_ALWAYS_INDIRECT to be unset?

---

