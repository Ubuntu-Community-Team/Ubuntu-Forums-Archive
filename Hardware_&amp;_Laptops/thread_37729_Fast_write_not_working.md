---
title: "Fast write not working"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by strikeforce on 2005-05-28
Hey all first post so be kind :)

I am a few year old FC user since FC1 so I'm not new to linux but I am new to kubuntu or ubuntu.

For some reason I can't get Side band working on my nvidia card or fast write.  Here are the relevant settings that I have in place and for some reason its still not working which has got me stumped.  I've searched in a lot of places and for some reason I can't seem to get it working.

```

marc@ubuntu:~$ sudo cat /proc/driver/nvidia/agp/status
Password:
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

```

```

marc@ubuntu:~$ sudo cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000217:0x00000104

```

```

marc@ubuntu:~$ sudo cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000217:0x1f000104

```

X11 section for the driver itself.
```

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800 GT]"
        Driver          "nvidia"
        #BusID          "PCI:1:0:0"
        Option          "NoLogo"                        "1"
        Option          "NvAGP"                         "1"
        VideoRam        131072
        Option          "RenderAccel"                   "1"
        Option          "AllowGLXWithComposite"         "1"
        Option          "EnablePageFlip"                "1"
        Option          "AGPMode"                       "4"
        Option          "AGPFastWrite"                  "1"
        Option          "EnableDepthMoves"              "1"

EndSection

```

I've run update-modules or sudo update-modules several times with the following two files written up as they are.

```

marc@ubuntu:~$ sudo cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia_agp
nvidia
options nvidia NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1
#
marc@ubuntu:~$ sudo cat /etc/modutils/nvidia-kernel-nkc
alias char-major-195 nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRate=4

```

For some reason none of it is working. I don't think its the bios because I haven't altered the bios and I've only just taken FC3 off and put kubuntu on.

I'm really starting to 
 ](*,) 

I'm hoping someone else has come across it and found a solution to this cause I'm stumped.

---

### Post by thrift on 2005-05-28
try to load the nvidia module like this during boot up:
modprobe nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

That should do it.  If you don't know how you would go about doing that. edit /etc/modprobe.d/nvidia-kernel-nkc and put this inside of it:

alias char-major-195 nvidia 
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

Good luck, hope that works.

---

### Post by strikeforce on 2005-05-28
[QUOTE=thrift]try to load the nvidia module like this during boot up:
modprobe nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

That should do it.  If you don't know how you would go about doing that. edit /etc/modprobe.d/nvidia-kernel-nkc and put this inside of it:

alias char-major-195 nvidia 
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

Good luck, hope that works.[/QUOTE]

Unfortunately I couldn't load up kde after that the screen went blank.

I tried put the script in my rc2.d/ and just adding the following code.

```

modprobe nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

```

It still didn't cause fastwrite to turn on :(

---

### Post by thrift on 2005-05-29
it most likely didn't turn fastwrite on because the nvidia module was already loaded.  What you need to do to start testing this is to hit 

ctrl+alt+f1 after x has started
then log in as your user
then sudu bash
<enter your password>

/etc/init.d/gdm stop
rmmod nvidia (if that doesn't work try modprobe -r nvidia
modprobe nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

if you get a failure on the modprobe then your AGP or card or the drivers that you are using with them don't support one of the options.

if you had no errors:
startx

check it out and see if it worked.  If it did you just need to figure out how to make that occur on boot.  My hackish way to do it was simply to edit /etc/init.d/gdm, right after the comment i rmmod the AGP modules loaded and the nvidia module if it was loaded, and then modprobe the nvidia module with the options we talked about

I've attached my /etc/init.d/gdm and my /proc/driver/nvidia/agp/status

You may need to setup you gdm a little differently, possibly removing the nvidia module as well and using the appropraite agp module to be removed.

I've also attached my /etc/X11/xorg.conf

This config works 100% on a gigabyte AMD 64 board running 32bit Ubuntu with an nVidia geforce FX 5700 Ultra.

In truth, I notice almost no advantage with fast writes enabled or disabled.  On the other hand, using the nvclock linux utility I can overclock my card and get some big performance gains.

Good luck.

---

### Post by begintmeta on 2005-10-09
It has been a long time since the last post in this thread. I have installed Breezy recently, and can('t) get fastwrites switched on.

I use a Intel D875PBZ and NVIDIA GeForce 6600.

By default the intel_agp driver is loaded, so i turned that off by adding agpgart and intel_agp to the blacklist. This works fine, they are not loaded on boot.

Then i noticed SBA is on and FW are off, so I lokked around and modified "nvidia-kernel-nkc"

it is now
```

alias char-major-195 nvidia
options nvidia NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1

```

after a reboot, still only SBA, no FW

so I decided to manually load the module "nvidia" with said options. This has worked, FW and SBA are switched on.

How can I get Ubuntu to enable fast-writes on boot by default?

Output cat /proc/driver/nvidia/agp/*
```

Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0xff000e1b:0x1f004312
Host Bridge:     Intel Corporation 82875P/E7210 Memory Controller Hub
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f004a1b:0x00000b12
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled

```

The line "Fast Writes:     Enabled" is different (Disabled) when I do not manually reaload the driver, of course. So, can I add the options to some file or script? Adding a line to nvidia-kernel-nkc apparently does not work. Of course I can always make or modify a script myself, but I guess Ubuntu has some standard way of accomplishing this.

---

### Post by begintmeta on 2005-10-10
Well, I just wrote my own script to load the module on startup, but I cannot believe Ubuntu does not work right out of the box in this regard, I would expect a lot of people would have similar problems, but this is apparently not the case...

---

### Post by ramba on 2005-10-23
[QUOTE=begintmeta]Well, I just wrote my own script to load the module on startup, but I cannot believe Ubuntu does not work right out of the box in this regard, I would expect a lot of people would have similar problems, but this is apparently not the case...[/QUOTE]

Actually I'm having the same problems...with same graphics card :J

---

### Post by 23meg on 2005-10-23
Is fastwrite supported on PCI Express cards/chips as well, or is it an AGP-only feature? Is there something else that is PCI-E specific that can result in a performance gain? Right now I'm getting quite bad 2d performance in Gnome with my Geforce Go6200 which uses PCI-E. Here's the content of my /proc/nvidia/driver/cards/0 :

```
Model: 		 GeForce Go 6600 TE/6200 TE
IRQ:   		 16
Video BIOS: 	 05.43.02.49.e2
Card Type: 	 PCI-E

```

---

### Post by Rizado on 2006-03-02
To make it autoload add "nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1" to /etc/modules

---

### Post by Hibountu on 2007-07-15
I got it to work using this line

options** nvidia_new** NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

---

### Post by Anubis on 2007-11-12
edit  /etc/modutils/nvidia-kernel-nkc

alias char-major-195 nvidia
options **nvidia** NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

Change the bold "nvidia" to "**nvidia_new**"

Fixed it for me.

---

