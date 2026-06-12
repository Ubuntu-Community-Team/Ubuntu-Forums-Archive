---
title: "Bumblebee drivers not working (in kernal 3.8+ ???)"
date: 2013-06-07
forum: Hardware
---

### Post by Reduced_Oxygen on 2013-06-07
Ok so the other day I noticed this:

[IMG]http://i.imgur.com/bBfUWxF.png[/IMG]

for me this is a bit odd as I also have a Nvidia 620m so I decided to look for a way to check if my graphics card is working properly. 

I came up with this:

```
gilligan@ThinkPad-T430u:~$ optirun nvidia-settings -c :8[15699.452334] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[15699.452355] [ERROR]Could not connect to bumblebee daemon - is it running?



```

I am now quite discouraged as after 3 - 4 hours of searching all I've found is alot of people with the same problem and no solution. What's even more concerning is every time I find a bug post it is closed by mods saying that the issue was caused by user error but they don't elaborate on this.

I also discovered that even though it's not being used my GPU is on.

Further information you might need:

```
gilligan@ThinkPad-T430u:~$ uname -r3.8.0-20-generic
gilligan@ThinkPad-T430u:~$ sudo bumblebeed -vv
[sudo] password for gilligan: 
[16044.896436] [DEBUG]Found card: 01:00.0 (discrete)
[16044.896461] [DEBUG]Found card: 00:02.0 (integrated)
[16044.896471] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[16044.896675] [INFO]Configured driver: nvidia
[16044.896692] [DEBUG]Skipping auto-detection, using configured driver 'nvidia'
[16044.896763] [DEBUG]Process /sbin/modprobe started, PID 11839.
[16044.896818] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[16044.898019] [DEBUG]SIGCHILD received, but wait failed with No child processes
[16044.898557] [INFO]Loading driver bbswitch (module bbswitch)
[16044.898755] [DEBUG]Process modprobe started, PID 11840.
FATAL: Module bbswitch not found.
[16044.900622] [DEBUG]Process with PID 11840 returned code 1
[16044.900775] [ERROR]Module bbswitch could not be loaded (timeout?)
[16044.900780] [DEBUG]bbswitch is not available, perhaps you need to insmod it?
[16044.900783] [INFO]Skipping switcheroo PM method because it is not explicitly selected in the configuration.
[16044.900786] [WARN]No switching method available. The dedicated card will always be on.
[16044.900789] [DEBUG]Active configuration:
[16044.900793] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[16044.900797] [DEBUG] X display: :8
[16044.900800] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-current:/usr/lib32/nvidia-current
[16044.900803] [DEBUG] Socket path: /var/run/bumblebee.socket
[16044.900805] [DEBUG] pidfile: /var/run/bumblebeed.pid
[16044.900811] [DEBUG] xorg.conf file: /etc/bumblebee/xorg.conf.nvidia
[16044.900815] [DEBUG] xorg.conf.d dir: /etc/bumblebee/xorg.conf.d
[16044.900818] [DEBUG] ModulePath: /usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
[16044.900820] [DEBUG] GID name: bumblebee
[16044.900823] [DEBUG] Power method: auto
[16044.900825] [DEBUG] Stop X on exit: 1
[16044.900828] [DEBUG] Driver: nvidia
[16044.900831] [DEBUG] Driver module: nvidia
[16044.900833] [DEBUG] Card shutdown state: 1
[16044.900900] [DEBUG]Process /sbin/modprobe started, PID 11841.
[16044.900925] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[16044.901879] [DEBUG]SIGCHILD received, but wait failed with No child processes
[16044.901892] [ERROR]Module 'nvidia' is not found.



```


thanks in advance to anyone who helps

---

### Post by Yellow Pasque on 2013-06-07
Nvm, sorry.

---

### Post by Reduced_Oxygen on 2013-06-07
> **Temüjin said:**
> Nvm, sorry.

huh? what?

---

### Post by Reduced_Oxygen on 2013-06-07
So I hear the new nvidia driver supports nvidia optimus without the need for bumblebee. can anyone support this claim? Does anyone have a guide to installing these drivers?

---

### Post by Yellow Pasque on 2013-06-07
[http://phoronix.com/forums/showthread.php?79655-NVIDIA-Has-Major-New-Linux-Driver-Optimus-RandR-1-4](http://phoronix.com/forums/showthread.php?79655-NVIDIA-Has-Major-New-Linux-Driver-Optimus-RandR-1-4)

---

### Post by Reduced_Oxygen on 2013-06-07
Yea that's where I saw it

---

### Post by axept on 2013-06-07
How did you install Bumblebee? I've got the same graphic card and working great with bumblebee.. But I'm on 12.10..

How is you bumblebee.conf look like? Have you tried to change it?

[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

BTW, it's normal to show the Intel Graphic in system-settings. The Nvidia card will only be used when you run a application or games with "optirun" or "primusrun"..

---

### Post by Reduced_Oxygen on 2013-06-07
I have installed it probably every way possible with similar results each time.

thank you for the link, I'll follow along with that as it presents a few things I have yet to try and let you know how I go.

Is it possible to have bumblebee use the dedicated graphics by default?

EDIT: I'd like to note for anyone using the webupd8.org tutorial [COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install bumblebee-config-gtk has been replaced with [/FONT][/COLOR][COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install bumblebee-config-gui[/FONT][/COLOR]

---

### Post by axept on 2013-06-07
I've not tested to use it by default. Cant see why I need to.. So I don't know.

---

### Post by Reduced_Oxygen on 2013-06-07
here is my bumblebee.conf file

```
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=nvidia
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d


## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false




# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods


## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-319
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-319:/usr/lib32/nvidia-319
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-319/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia


## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau



```

---

### Post by Reduced_Oxygen on 2013-06-07
hmmm the [COLOR=#000000][FONT=UbuntuBeta Mono]bumblebee-config-gui Doesnt seem to work no biggy though I can do it manually[/FONT][/COLOR]

---

### Post by Reduced_Oxygen on 2013-06-07
Well doesn't look like the webupd8.org tut helped, everything appears the same

---

### Post by axept on 2013-06-07
Strange.. Well, I don't know. For me on 12.10 the Nvidia card works. I use nvidia-current drivers.. Suppose it doesn't matter.
The Bumblebee Config GUI works also.

---

### Post by Reduced_Oxygen on 2013-06-08
which kernal are you using? (uname -r)

---

### Post by axept on 2013-06-08
> **Reduced_Oxygen said:**
> which kernal are you using? (uname -r)

I'm on 3.5.0-32-generic

---

### Post by Reduced_Oxygen on 2013-06-09
yea, that's why it works for you. I might have to downgrade

---

### Post by axept on 2013-06-09
> **Reduced_Oxygen said:**
> yea, that's why it works for you. I might have to downgrade

Yeah, maybe :P

---

### Post by Yellow Pasque on 2013-06-09
> **Reduced_Oxygen said:**
> So I hear the new nvidia driver supports nvidia optimus without the need for bumblebee. can anyone support this claim? Does anyone have a guide to installing these drivers?

Using the nvidia card for everything is still experimental right now, and it will decrease battery life. You need a 3.9.x kernel and an nvidia 319.xx driver. There's a rough guide here, but I personally wouldn't recommend most users toy with their systems that way unless they're comfortable with console recovery: [http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)

---

### Post by Reduced_Oxygen on 2013-06-10
I have recovered via console many a time, I think I'll give it a try

---

### Post by axept on 2013-06-13
How did it go? Figured out?

---

### Post by Reduced_Oxygen on 2013-06-30
unfortunately no, I still have not found a solution

---

### Post by markackerman8@gmail.com on 2014-02-04
I have been trying to get proprietary graphics working with my brand new HP Envy 17 m7-j078 notebook.  I had been trying for 2 1/2 years with my previous HP Laptop with no success and TRIED EVERYTHING - Over and Over.  It had ATI Muxless Hybrid Graphics with its' Intel I7.  I thought this one with its Optimus NVIDIA GeForce GT 740M dedicated card would solve the problem because of all the blogs saying Bumblebee works like a charm.  It has now been 2 weeks and over 20 attempts and 5--10 re-installs of Ubuntu Linux Mint, and still no luck.
   Perhaps someone can help me troubleshoot this and stop spinning my wheels and get me out of this rabbit hole, while even learning something, so I can help all the others I have convinced to get into Linux.  Thanks in advance, thanks a lot.

  Here are some details that may be useful (in no specific order)
• HP Envy Touchsmart m7-j078ca notebook
• Intel® Core™ i7-4700MQ
• NVIDIA GeForce GT 740M (2 GB DDR3 dedicated)
• Linux Mint 16 Petra
• Bumblebee 3.2.1
• ack@Aarawn ~ $ lspci -vnn | grep '\''[030[02]\]'
			00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor 				
					Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
			01:00.0 3D controller [0302]: NVIDIA Corporation GK208M [GeForce GT 740M] [10de:1292] (rev a1)
&#8728; Note that here it doesn't say 01:00 is a "VGA" Controller but a "3D Controller"
• ack@Aarawn ~ $ sudo modprobe nvidia
				[sudo] password for ack: 
				FATAL: Module nvidia not found.
• installed
&#8728; bumblebee-nvidia    primus
&#8728; nvidia-304   nvidia-current (304)   nvidia-prime  nvidia settings  nvidia settings-304
• Xorg.conf with any mention of Nvidia results in TTY1 X crash and only deleting sometimes returns mdm to functioning order
• $ optirun firefox
&#8728; [ 1228.929955] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver
&#8728; [ 1228.929986] [ERROR]Aborting because fallback start is disabled.
• ack@Aarawn ~ $ sudo gedit /etc/bumblebee/xorg.conf.nvidia
	Section "ServerLayout"
    		Identifier  "Layout0"
    		Option      "AutoAddDevices" "false"
    		Option      "AutoAddGPU" "false"
	EndSection

	Section "Device"
    		Identifier  "DiscreteNvidia"
    		Driver      "nvidia"
   		VendorName  "NVIDIA Corporation"
    		Option "ProbeAllGpus" "false"
    		Option "NoLogo" "true"
    		Option "UseEDID" "false"
    		Option "UseDisplayDevice" "none"
	EndSection

• ack@Aarawn ~ $ bumblebeed
&#8728; [ 3052.038351] [ERROR]Module 'nvidia' is not found.
• ack@Aarawn ~ $dmesg
	[ 2288.712311] NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:1292)
	[ 2288.712311] NVRM: installed in this system is not supported by the 304.116
	[ 2288.712311] NVRM: NVIDIA Linux driver release.  Please see 'Appendix
	[ 2288.712311] NVRM: A - Supported NVIDIA GPU Products' in this release's
	[ 2288.712311] NVRM: README, available on the Linux driver download page
	[ 2288.712311] NVRM: at [www.nvidia.com](www.nvidia.com).
	[ 2288.712320] nvidia: probe of 0000:01:00.0 failed with error -1
	[ 2288.712331] NVRM: The NVIDIA probe routine failed for 1 device(s).
	[ 2288.712332] NVRM: None of the NVIDIA graphics adapters were initialized!
- 

I am going to try a number of other things, but am getting exhausted and would really appreciate a fresh perspective on this issue.
Thanks again.

Mark
[email]markackerman8@gmail.com[/email]

---

