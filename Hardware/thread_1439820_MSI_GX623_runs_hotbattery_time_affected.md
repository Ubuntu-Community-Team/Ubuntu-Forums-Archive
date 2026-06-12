---
title: "MSI GX623 runs hot/battery time affected"
date: 2010-03-26
forum: Hardware
---

### Post by cTn on 2010-03-26
Hi guys, so

1. i am dualbooting latest ubuntu (10.04 beta1 fully updated) via wubi
2. main operating system is win7 (everything runs completely fine)
3. battery time on windows = 2h 30min, linux = 1h 20min

to get to my problem

1. i tried 9.10,10.04 on both ubuntu version "everything" runs pretty solid except laptop fan runs much faster and laptop is noticeable hotter
2. CPU scaling works just fine
3. i tried AMD ATI drivers on 9.10 (i had video playback problems and i had some bad delay maximizing windows, etc) laptop was still running hot
4. i am running "default" ATI drivers on my 10.04 (video playback works perfectly, even compiz effects could be enabled (awesome) but still laptop runs very hot

laptop is using ATI Mobility Radeon HD 4670

could anyone share any ideas how i could solve this?

my best guess is that there is some power-saving problem with gpu drivers (gpu is probably running on 3D clocks in performance mode) and its not down-clocking properly to 2D mode, 

i am and advanced windows user but i have only "basic" knowledge of linux systems, so if anyone could share some light how to debug and fix this overheating problem ill be really glad (i want to use ubuntu as main OS on my laptop, but this battery problem and "warm" case of my laptop is preventing me from using it) :(

thx for any ideas

---

### Post by tgalati4 on 2010-03-26
If you run the open drivers, there's a dynamic clock setting that you can turn on.
You can set it in /etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Driver "ati"
	Option "DynamicClocks" "on"
	Option "mtrr" "on"
	Option "DesktopSetup" "Single"
	Option "ScreenOverlap" "0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "Stereo" "off"
	Option "StereoSyncEnable" "1"
	Option "FSAAEnable" "no"
	Option "FSAAScale" "1"
	Option "FSAADisableGamma" "no"
	Option "FSAACustomizeMSPos" "no"
	Option "UseFastTLS" "0"
	Option "BlockSignalsOnLock" "on"
	Option "XAANoOffscreenPixmaps"
	Option "AccelMethod" "XAA"
EndSection

--------------------

You can also adjust the GPU and video RAM clock speeds:

sudo apt-get install rovclock
man rovclock

If you have an intel processor, you can run powertop to recover a few more watts:

sudo apt-get install powertop
man powertop

---

### Post by cTn on 2010-03-26
i have installed powertop, i also typed sudo gedit /etc/X11/xorg.conf
in terminal, but only empty file popped out, does it mean something is wrong?

rovclock isn't working properly (i think)
sudo rovclock -i
Radeon overclock 0.6e by Hasw (hasw@hasw.net)

Found ATI card on 08:00, device id: 0x9488
I/O base address: 0xe000
Video BIOS shadow found @ 0xc0000
Invalid reference clock from BIOS: 0.0 MHz
Memory size: 0 kB
Memory channels: 1, CD,CH only: 0
tRcdRD:   3
tRcdWR:   1
tRP:      3
tRAS:     6
tRRD:     1
tR2W-CL:  1
tWR:      1
tW2R:     0
tW2Rsb:   0
tR2R:     1
tRFC:     13
tWL(0.5): 0
tCAS:     0
tCMD:     0
tSTR:     0
Floating point exception (core dumped)

---

### Post by cTn on 2010-03-27
bump :(

---

### Post by tgalati4 on 2010-03-27
rovclock may not work for your card. Karmic eliminated xorg.conf, so you have to create one from scratch.  Search the forums for the command to give you a default template.

---

### Post by cTn on 2010-03-27
i tried Xorg -configure with gdm disabled as root, but my laptop just froze :(

---

### Post by tgalati4 on 2010-03-27
Here's my rov: (ibm thinkpad t43p with ati firegl)

tgalati4@tpad-Gloria7 ~ $ sudo rovclock -i
[sudo] password for tgalati4: 
Radeon overclock 0.6e by Hasw (hasw@hasw.net)

Found ATI card on 01:00, device id: 0x3154
I/O base address: 0x2000
Video BIOS shadow found @ 0xc0000
Reference clock from BIOS: 27.0 MHz
Memory size: 131072 kB
Memory channels: 1, CD,CH only: 0
tRcdRD:   5
tRcdWR:   3
tRP:      5
tRAS:     10
tRRD:     3
tR2W-CL:  2
tWR:      5
tW2R:     2
tW2Rsb:   1
tR2R:     2
tRFC:     17
tWL(0.5): 2
tCAS:     4
tCMD:     0
tSTR:     1
XTAL: 27.0 MHz, RefDiv: 6

Core: 398.25 MHz, Mem: 249.75 MHz

I can declock down to 125 MHz for each and save ~5 watts (from 21 watts to 15 watts).

According to:

man xorg

       -config file
               Read the server configuration from file.  This option will work
               for any file when the server is run as root (i.e, with real-uid
               0),  or  for files relative to a directory in the config search
               path for all other users.

If you give the -config switch without a valid xorg.conf file, it probably will freeze.

Post the output of your xorg.conf.

Why is gdm disabled?  That can create problems with logging out and logging in, since many session attributes are controlled by gdm.

---

### Post by cTn on 2010-03-27
> **tgalati4 said:**
> Here's my rov: (ibm thinkpad t43p with ati firegl)

tgalati4@tpad-Gloria7 ~ $ sudo rovclock -i
[sudo] password for tgalati4: 
Radeon overclock 0.6e by Hasw (hasw@hasw.net)

Found ATI card on 01:00, device id: 0x3154
I/O base address: 0x2000
Video BIOS shadow found @ 0xc0000
Reference clock from BIOS: 27.0 MHz
Memory size: 131072 kB
Memory channels: 1, CD,CH only: 0
tRcdRD:   5
tRcdWR:   3
tRP:      5
tRAS:     10
tRRD:     3
tR2W-CL:  2
tWR:      5
tW2R:     2
tW2Rsb:   1
tR2R:     2
tRFC:     17
tWL(0.5): 2
tCAS:     4
tCMD:     0
tSTR:     1
XTAL: 27.0 MHz, RefDiv: 6

Core: 398.25 MHz, Mem: 249.75 MHz

I can declock down to 125 MHz for each and save ~5 watts (from 21 watts to 15 watts).

According to:

man xorg

       -config file
               Read the server configuration from file.  This option will work
               for any file when the server is run as root (i.e, with real-uid
               0),  or  for files relative to a directory in the config search
               path for all other users.

If you give the -config switch without a valid xorg.conf file, it probably will freeze.

Post the output of your xorg.conf.

Why is gdm disabled?  That can create problems with logging out and logging in, since many session attributes are controlled by gdm.

i said -configure not config :), if i am correct Xorg -configure should generate a new xorg.conf, however it always freeze, so all i have its an empty xorg.conf

---

### Post by tgalati4 on 2010-03-27
Yes, my mistake.  -configure should create a valid xorg.conf file.  But the man page also says that it doesn't work on some systems.

Boot to a rescue shell (from the grub menu).

cd /etc/X11
ls
(probably no xorg.conf file to be found)
xorg -configure
ls
(hopefully you will have an xorg.conf file)

---

### Post by cTn on 2010-03-28
i am going to reinstall my 9.10 ubuntu (because 10.04 is full of bugs atm) and we will see what can i come up with

---

