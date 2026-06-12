---
title: "Problem with 3D nvidia"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by corza on 2005-06-07
Hi I have an XpertVision Nvidia 6200 256mb video card and I have had troubles running 3D with it. I have followed the guides on wiki to installing the drivers and I'll just supply you with some information so that you could help me further..

Xorg.conf
> Section "Module"
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
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Okay from here you may see that I have changed it back to nv this is because my screen becomes EXTREMELY Blury + EXTREMELY Faded there is barely any colour in it at all!

> cat /var/log/Xorg.0.log | grep NVIDIA
(**) |   |-->Device "NVIDIA Corporation NV40? [Unknown nVidia Card]"
(II) Module glx: vendor="NVIDIA Corporation"
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)


> glxgears
Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.


> ldd /usr/lib/libGL.so                 libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0xb7829000)
        libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0xb7827000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7805000)
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0xb77f8000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0xb7733000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7730000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7603000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x80000000)


Thats all the information that i can think of right now if you have an idea of what this problem could be please post me a reply I'm desperate.

Thanks

---

### Post by nocturn on 2005-06-07
It seems not to recognize your card.
Maybe it is not supported in this version of the driver (you can check the Nvidia site).

It you want, you can try the new driver, but that requires compiling it...

---

### Post by corza on 2005-06-07
Yes.. well I tried that once before but that lead me to reinstalling my whole Operating System again.. So that was not a good idea :P

---

### Post by gcranston on 2005-06-08
under Modules comment out 

Load "dri" 



Also, the new driver does not require compiling.  You just download the binary and run it from console.  The whole process takes about 4 minutes.

Good luck

---

### Post by corza on 2005-06-30
[QUOTE=gcranston]under Modules comment out 

Load "dri" 



Also, the new driver does not require compiling.  You just download the binary and run it from console.  The whole process takes about 4 minutes.

Good luck[/QUOTE]
 Hi, sorry have been away for a bit on vacation. Um I'm not sure what you mean by downloading the binary and running it from console. What I did is download (i think it was the drivers) via apt-get. and I did comment out dri, it didnt change anything.

---

### Post by codejunkie on 2005-06-30
i think he's talking about the driver from [www.nvidia.com](www.nvidia.com) you don't have to complie it the installer does it for you as long as you have the kernel-headers for your kernel and build-essential packages installed.

---

### Post by corza on 2005-06-30
I downloaded the driver, began installing and it came up this message...

"No precompiled kernel interface was found to match your kernel"

I have looked at other websites and it says that it installs anyway but mine just ends.

---

### Post by corza on 2005-06-30
[QUOTE=corza]I downloaded the driver, began installing and it came up this message...

"No precompiled kernel interface was found to match your kernel"

I have looked at other websites and it says that it installs anyway but mine just ends.[/QUOTE]
 Here is the installer log file

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Jun 30 22:01:46 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by codejunkie on 2005-07-01
[QUOTE=corza]I downloaded the driver, began installing and it came up this message...

"No precompiled kernel interface was found to match your kernel"

I have looked at other websites and it says that it installs anyway but mine just ends.[/QUOTE]
here's the steps to install the the nvidia driver from scratch from a guide i wrote hope this helps.

find what kernel is listed when you type ```
uname -a
``` at the terminal for example mine displays ```
Linux ubuntu [COLOR=Red]2.6.10-5-k7[/COLOR] #1 Fri Jun 24 18:51:20 UTC 2005 i686 GNU/Linux
``` what l've listed in red is what to look at so  on mine i need the kernel headers for the k7 kernel. the easiest way to install these is using synaptic click on search and type headers it will list all the header packages avaliable so i install the package linux-headers-k7 these are the ones for my kernel. if you have a different kernel for example 2.6.10-5-386 you will need the package linux-headers-386 etc. you also need the build-essential package installed this provides the basic compilers and stuff used to build the kernel modules. if you can't get X running to use synaptic you can also install the kernel headers and build essential package like this. 
```
sudo apt-get update
sudo apt-get install linux-headers-386 
sudo apt-get install build-essential
```
for this example im using the 2.6.10-5-386 kernel because it's what ubuntu installs by default and the NVIDIA-Linux-x86-1.0-7667-pkg1.run nvidia driver from [www.nvidia.com](www.nvidia.com).

now to install the driver if your already in an x session exit it by hitting
```
ctrl+alt+F1
```
now at the terminal login and type:
```
sudo -s
```
enter you password 
```
telinit 3
```
if your using ubuntu
```
killall gdm
```
if your using kubuntu
```
killall kdm
```
cd to where the nvidia package is installed in this example i've placed it in /home/username/
```
cd /home/username
```
now run the installer with
```
sh NVIDIA-Linux-x86-1.0-7667-pkg1.run
```
after the installer has finished completely you need to edit your /etc/X11/xorg.conf
file and tell it to use the nvidia driver with.
```
nano /etc/X11/xorg.conf
```
example: find the line that looks like this
```

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        [COLOR=Red]Driver[/COLOR]          [COLOR=Blue]"vesa"[/COLOR]
        BusID           "PCI:1:0:0"
EndSection

```
and replace whatever is listed under the [COLOR=Red]Driver[/COLOR] section with [COLOR=Blue]"nvidia"[/COLOR] save the /etc/X11/xorg.conf file and reboot.

---

### Post by corza on 2005-07-01
Thanks a lot dude I didnt have those headers i think that was the problem works good now thank you for everything !! =)

---

