---
title: "Geforce GTX 560 TI"
date: 2011-02-03
forum: Hardware
---

### Post by Alp82 on 2011-02-03
I have a new computer with a Geforce GTX 560 TI graphics card. Currently, there is no appropriate driver and as a matter of fact i cannot use dualscreen or compiz fusion.

Does anyone know how i can fix this?

---

### Post by cascade9 on 2011-02-03
Wait for nvidia to get the drivers out, thats about all you can do.

---

### Post by Alp82 on 2011-02-03
Any idea how long this could take?

---

### Post by cascade9 on 2011-02-03
Could be a few days up to a few months. I'd guess a week or two, but thats just guessing.

---

### Post by lukaszr on 2011-02-03
There normally isn't a specific time frame. They work on it as it needs to be. 

I think ATI took over half a year to get supported drivers for their HD6000 series.

---

### Post by cascade9 on 2011-02-03
> **lukaszr said:**
> I think ATI took over half a year to get supported drivers for their HD6000 series.

Not quite. 6850/6870 released on 22-10-2010, the offical drivers were out on 26-01-2011. 

The 5XXX drivers work with the 6XXX cards as well, so I think that AMD decided that any early adopters with linux could just hack a bit and get the drivers going.

---

### Post by tlareywi on 2011-02-03
I just installed a GTX 560 TI and have it working on 10.10 with acceleration and compiz. Just go to nvidia's website and query for linux drivers for the gtx570 including beta drivers. Download and install the 270.xx driver that comes up. It doesn't outright say it will work with the 560 but I gave it a shot and it seems to work fine.
 
I haven't tried things like games but at least you can get your desktop back ;-)

---

### Post by cascade9 on 2011-02-03
Using  abeta drvier, with no offical support for that card? 

I wouldnt . Much higher chance of something going badly wrong, and it could go so wrong as to cause permanent damage. Thats not very likely, but it could happen.

---

### Post by Anthon berg on 2011-02-10
Anecdotal evidence - I'm a CUDA developer, and I've used beta drivers on many occasions - Never has anything gone wrong.

Especially since the GTX 560 isn't exactly a new architecture; In most respects it's a scaled-down 570, and driver support for the 570 is stable.

---

### Post by Alp82 on 2011-02-10
Could you give me some hints how to install the driver? What's the best way? I have Ubuntu 10.10 with Gnome.

---

### Post by Alp82 on 2011-02-14
I managed to install the appropriate driver by adding the following source to my apt list: ppa:ubuntu-x-swat/x-updates

(German) Source: [http://wiki.ubuntuusers.de/Grafikkarten/Nvidia/nvidia#Installation-aus-PPA](http://wiki.ubuntuusers.de/Grafikkarten/Nvidia/nvidia#Installation-aus-PPA)

---

### Post by defsam on 2011-02-17
Can you shed some lights on how you did it? i need the driver for me to use compiz and get 1080p resolution for my GTX 560 Ti.

---

### Post by defsam on 2011-02-18
bumpness

---

### Post by Alp82 on 2011-02-18
> **defsam said:**
> Can you shed some lights on how you did it? i need the driver for me to use compiz and get 1080p resolution for my GTX 560 Ti.

1 .If you have nvidia-current installed, deinstall it completly.

2. As root open Synaptic. Go the Settings -> Package sources -> Other Software. Hit the Add Button and copy "ppa:ubuntu-x-swat/x-updates" in the text input field.

3. Now reload the sources and reinstall nvidia-current, which is now loaded from the new source and is the most current version. You should also install nvidia-settings.

4. Optional: Make a backup of your /etc/X11/xorg.conf and run "nvidia-xconfig" in a terminal to create your nvidia X config file.

Please give me feedback if it works, writing all that from my memory.

---

### Post by defsam on 2011-02-18
> **Alp82 said:**
> 1 .If you have nvidia-current installed, deinstall it completly.

2. As root open Synaptic. Go the Settings -> Package sources -> Other Software. Hit the Add Button and copy "ppa:ubuntu-x-swat/x-updates" in the text input field.

3. Now reload the sources and reinstall nvidia-current, which is now loaded from the new source and is the most current version. You should also install nvidia-settings.

4. Optional: Make a backup of your /etc/X11/xorg.conf and run "nvidia-xconfig" in a terminal to create your nvidia X config file.

Please give me feedback if it works, writing all that from my memory.

ok i understand. ill try and see if i can make a back up of the config then run xconfig. thanks!

---

### Post by defsam on 2011-02-18
here is what i got after i did your steps (1 to 3) i clicked on system > preferences > Monitors
it says :
"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" 

i clicked yes

then a pop up appears saying:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

should i just run nvidia-xconfig? i tried backing up my /etc/x11/xorg.conf but the terminal says: "cp: cannot stat `/etc/X11/xorg.conf-backup': No such file or directory"


what should i do?

---

### Post by Alp82 on 2011-02-18
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo nvidia-xconfig

```

Then restart X.

---

### Post by defsam on 2011-02-18
says this after i typed what u suggested:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

how? ctrl+alt+backspace?

---

### Post by defsam on 2011-02-18
bumping for more help

---

### Post by defsam on 2011-02-18
> **Alp82 said:**
> ```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo nvidia-xconfig

```

Then restart X.
ok thank you! never mind my last psots i got it to work after getting  stuck ontty1 and restarting my computer made it work! tahnks a bunch!

---

### Post by Alp82 on 2011-02-18
No problem, glad i could help

---

### Post by Tanker1 on 2011-05-26
> **Alp82 said:**
> 1 .If you have nvidia-current installed, deinstall it completly.

2. As root open Synaptic. Go the Settings -> Package sources -> Other Software. Hit the Add Button and copy "ppa:ubuntu-x-swat/x-updates" in the text input field.

3. Now reload the sources and reinstall nvidia-current, which is now loaded from the new source and is the most current version. You should also install nvidia-settings.

4. Optional: Make a backup of your /etc/X11/xorg.conf and run "nvidia-xconfig" in a terminal to create your nvidia X config file.

Please give me feedback if it works, writing all that from my memory.

Hi Alp82,

i followed your steps above to install the nvidia driver. But i cannot start x. Here is the log:```
   693.199] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   693.200] X Protocol Version 11, Revision 0
[   693.200] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[   693.200] Current Operating System: Linux deadpool 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64
[   693.202] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=abc4a214-0237-43f4-abfa-6b36699950a9 ro quiet splash
[   693.202] Build Date: 09 January 2011  12:14:27PM
[   693.202] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[   693.203] Current version of pixman: 0.18.4
[   693.203] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   693.203] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   693.205] (==) Log file: "/var/log/Xorg.0.log", Time: Wed May 25 18:50:29 2011
[   693.205] (==) Using config file: "/etc/X11/xorg.conf"
[   693.205] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   693.206] (==) ServerLayout "Default Layout"
[   693.206] (**) |-->Screen "Default Screen" (0)
[   693.206] (**) |   |-->Monitor "Configured Monitor"
[   693.206] (**) |   |-->Device "Configured Video Device"
[   693.206] (**) |-->Input Device "Keyboard0"
[   693.206] (**) |-->Input Device "Mouse0"
[   693.206] (==) Automatically adding devices
[   693.206] (==) Automatically enabling devices
[   693.206] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   693.206] 	Entry deleted from font path.
[   693.206] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   693.206] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   693.206] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   693.206] (WW) Disabling Keyboard0
[   693.206] (WW) Disabling Mouse0
[   693.206] (II) Loader magic: 0x7d17a0
[   693.206] (II) Module ABI versions:
[   693.206] 	X.Org ANSI C Emulation: 0.4
[   693.206] 	X.Org Video Driver: 8.0
[   693.206] 	X.Org XInput driver : 11.0
[   693.206] 	X.Org Server Extension : 4.0
[   693.207] (--) PCI:*(0:1:0:0) 10de:1200:3842:1561 rev 161, Mem @ 0xf8000000/33554432, 0xe8000000/134217728, 0xf0000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   693.207] (II) Open ACPI successful (/var/run/acpid.socket)
[   693.207] (II) LoadModule: "extmod"
[   693.207] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   693.208] (II) Module extmod: vendor="X.Org Foundation"
[   693.208] 	compiled for 1.9.0, module version = 1.0.0
[   693.208] 	Module class: X.Org Server Extension
[   693.208] 	ABI class: X.Org Server Extension, version 4.0
[   693.208] (II) Loading extension MIT-SCREEN-SAVER
[   693.208] (II) Loading extension XFree86-VidModeExtension
[   693.208] (II) Loading extension XFree86-DGA
[   693.208] (II) Loading extension DPMS
[   693.208] (II) Loading extension XVideo
[   693.208] (II) Loading extension XVideo-MotionCompensation
[   693.208] (II) Loading extension X-Resource
[   693.208] (II) LoadModule: "dbe"
[   693.208] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   693.208] (II) Module dbe: vendor="X.Org Foundation"
[   693.208] 	compiled for 1.9.0, module version = 1.0.0
[   693.208] 	Module class: X.Org Server Extension
[   693.208] 	ABI class: X.Org Server Extension, version 4.0
[   693.208] (II) Loading extension DOUBLE-BUFFER
[   693.208] (II) LoadModule: "glx"
[   693.208] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   693.214] (II) Module glx: vendor="NVIDIA Corporation"
[   693.214] 	compiled for 4.0.2, module version = 1.0.0
[   693.214] 	Module class: X.Org Server Extension
[   693.214] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[   693.214] (II) Loading extension GLX
[   693.214] (II) LoadModule: "record"
[   693.214] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   693.214] (II) Module record: vendor="X.Org Foundation"
[   693.214] 	compiled for 1.9.0, module version = 1.13.0
[   693.214] 	Module class: X.Org Server Extension
[   693.214] 	ABI class: X.Org Server Extension, version 4.0
[   693.214] (II) Loading extension RECORD
[   693.214] (II) LoadModule: "dri"
[   693.214] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   693.214] (II) Module dri: vendor="X.Org Foundation"
[   693.214] 	compiled for 1.9.0, module version = 1.0.0
[   693.214] 	ABI class: X.Org Server Extension, version 4.0
[   693.214] (II) Loading extension XFree86-DRI
[   693.214] (II) LoadModule: "dri2"
[   693.214] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   693.214] (II) Module dri2: vendor="X.Org Foundation"
[   693.214] 	compiled for 1.9.0, module version = 1.2.0
[   693.214] 	ABI class: X.Org Server Extension, version 4.0
[   693.214] (II) Loading extension DRI2
[   693.214] (II) LoadModule: "nvidia"
[   693.214] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   693.220] (II) Module nvidia: vendor="NVIDIA Corporation"
[   693.221] 	compiled for 4.0.2, module version = 1.0.0
[   693.221] 	Module class: X.Org Video Driver
[   693.227] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[   693.227] (EE) NVIDIA:     system's kernel log for additional error messages.
[   693.227] (II) UnloadModule: "nvidia"
[   693.227] (II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   693.227] (EE) Failed to load module "nvidia" (module-specific error, 0)
[   693.228] (EE) No drivers available.
[   693.228] 
Fatal server error:
[   693.228] no screens found
[   693.228] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   693.229] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   693.229]
```

if you need more infos i can also generate the nvidia-bug-report.sh 
Thanks for ypur help

Best regards,
Tanker

---

### Post by Alp82 on 2011-05-26
From where did you install nvidia-current? Which version has it?

---

### Post by Tanker1 on 2011-05-26
I installed it via Synaptic.
Version is 270.41.06-0ubuntu1-xup-maverick

---

### Post by Alp82 on 2011-05-26
Same as mine. I have no idea, sorry.

---

### Post by Tanker1 on 2011-05-26
I have repeated the whole process now my system is killed completely when i enter startx.
When I entered: sudo nvidia-xconfig its said:
```
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout; using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout; using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

---

### Post by Tanker1 on 2011-05-27
Meanwhile i've updated to natty. After the update all nvidia driver are working...no idea why.:confused:

---

### Post by TweFoju on 2011-10-04
isn't the driver released already by Nvidia?

i am planning to buy this GPU, and i saw that the driver is already out

i dont know why hasn;t it worked for you guys? should i hold off my purchase of this GPU?

---

### Post by yugohugo on 2011-10-23
First, sorry for bad english =)

My question is:

Does games works with this GPU and how is the performance?

Best regards,
yugohugo

---

