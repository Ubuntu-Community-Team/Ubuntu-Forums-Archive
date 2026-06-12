---
title: "Nvidia Module Not Found"
date: 2005-12-05
forum: General Help
---

### Post by linj on 2005-12-05
I've been attempting to get nvidia drivers to work on this computer for a while, to no luck. I just finished compiling a custom kernel with nvidia modules, as described [here]("http://www.ubuntuforums.org/showthread.php?t=85064"), but of course... the greater powers still smite me over ye forehead.

It appears that the nvidia module is found... I think. I followed some ambiguous instructions and got to: 
```
jeff@ubuntu:~$ sudo dpkg -S nvidia.ko
nvidia-kernel-2.6.12-custom: /lib/modules/2.6.12-custom/nvidia/nvidia.ko

```

So, I'm guessing it exists. That's good. But I can't modprobe it:
```
jeff@ubuntu:~$ sudo modprobe nvidia
FATAL: Module nvidia not found.
jeff@ubuntu:~$ sudo modprobe nvidia.ko
FATAL: Module nvidia.ko not found.

```

And I can't load up xorg (/var/log/Xorg.0.log):
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

I'm using VESA right now, since nv made my xorg use up... much more CPU cycles than I would've expected (/etc/X11/xorg.conf):
```
Section "Module"
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection
```

I'm not sure how to proceed now. Can a kind soul help me out? 

Much appreciated.

---

### Post by tseliot on 2005-12-05
1) Did you install the .deb package with the nvidia modules you got after you compiled your new kernel?
2) Please post the content of your /etc/modules 
  (do: "sudo gedit /etc/modules")
3) Set the option I put in red in the example and set your driver to "nvidia" (in your xorg.conf):
```
Section "Device"
Identifier"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
Driver"nvidia"
BusID"PCI:1:0:0"
[COLOR="Red"]Option "NvAGP" "3"[/COLOR]
```

Then log out and press CTRL+ALT+BACKSPACE (or reboot just to be sure)

Tell me how it goes

---

### Post by linj on 2005-12-05
It's the great one!

Yup, I installed all the packages. I'll try again, but I don't think I could've got the module there anyway... right?

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
nvidia
```

I added the nvidia myself, before making the custom kernel. I haven't removed it yet. Should I?

Edit: I have a PCI-E graphics card. Will that change anything?

Edit2: Did as you said. (Somewhat) new errors!
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "3"
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by tseliot on 2005-12-05
> **linj]It's the great one!

Yup, I installed all the packages. I'll try again, but I don't think I could've got the module there anyway... right?[/QUOTE]
If you followed my guide you should have the deb package.
Do this and post the output:
```
cd /usr/src
ls
```

[QUOTE=linj]```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
nvidia
```

I added the nvidia myself, before making the custom kernel. I haven't removed it yet. Should I?[/QUOTE]
You shouldn't have done that. I always recommend users to follow the instructions ONLY. I usually know what I'm doing  said:**
> Edit: I have a PCI-E graphics card. Will that change anything?
It's useful information.

---

### Post by mo_x on 2005-12-05
You don't need to compile a kernel just to use the nvidia drivers, just use a stock Ubuntu kernel and execute the following commands:
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```

---

### Post by tseliot on 2005-12-05
[QUOTE=mo_x]You don't need to compile a kernel just to use the nvidia drivers, just use a stock Ubuntu kernel and execute the following commands:
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```[/QUOTE]
Yes, of course. That of recompiling the kernel is only method 3 in my guide. You are referring to what I call mathod 1.

---

### Post by linj on 2005-12-05
```
jeff@ubuntu:/usr/src$ ls
kernel-headers-2.6.12-custom
kernel-headers-2.6.12-custom_10.00.Custom_i386.deb
kernel-image-2.6.12-custom_10.00.Custom_i386.deb
kernel-source-2.6.10.tar.bz2
kernel-source.2.6.12.tar.bz2
linux
linux-headers-2.6.12-10
linux-headers-2.6.12-10-k7-smp
linux-patches
linux-source-2.6.12
linux-source-2.6.12.tar.bz2
modules
nvidia-kernel-2.6.12-custom_1.0.7667-0ubuntu3+10.00.Custom_i386.deb
nvidia-kernel-source.tar.gz
```

Hm. Well, it says i386 but I compiled it with K8 support. 

Did the /etc/modules bit. 

Oh, I've tried that (apt-get install nvidia-glx), as well as the drivers that Nvidia hosts themself. Neither works; the module isn't found, for whatever reason. Actually, the drivers that come in the *.run format worked for only one reboot, after which, they somehow disappeared and none of the methods worked again. As in, the error was similar to what happens when you modprobe a non existent module.

---

### Post by linj on 2005-12-06
Well, for some reason, I can modprobe it now! The other day, when trying to make it work, I had coped /lib/modules/2.6.12-custom/nvidia/nvidia.ko to /lib/modules/2.6.12-custom/kernel/drivers/video/nvidia/nvidia.ko as well. I hadn't rebooted after that, and I got the above problem. This afternoon, after booting again, I found I *could* modprobe nvidia, for whatever demonic reason. And, it all works fine, except starting Xorg has a blinking text cursor type thing on the very top left for two seconds, but that doesn't bug me as much as nvidia not working. 

Thank you tseliot!

---

