---
title: "No video res. except 600x480 in dell system."
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by Silversierra on 2005-08-23
Hello, Thanks in advance for any help.
First, I'm completely(really really completely) new to linux.  I know basically nothing about how to use it.  I have been trying Ubuntu, as people have said it's easy and a good distro.

My issue is that I can't get any video modes above 640x480.
I have a dell 2300 mobo, and a dell e551c monitor.
I think the monitors h refresh is 30-54, and the v refresh is 50-120.  Those may be wrong.
I want to get 800x600 or 1024x768 res., so I can see all of the dialog boxes, they're cut off, and I can't see/use the buttons at the bottom.

Here's part of my xorg.conf file.
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E551c"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL E551c"
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

I don't know where to start.
Also, if you tell me to "run" a command, tell me how to do that.  What do I run it from?  I'm really a noob in this area, so sorry.  I've searched around, and it seems I have to add my h refresh and v refresh rates, but I don't understand how to do it.  I 'm a bit confused, everythings so new.
Silversierra

---

### Post by s_p_a_r_k_y on 2005-08-24
can you post your Xorg.0.log file?
its located in /var/logs/ so we can take a look at any error messages.

Also try changing i810 to vesa to see if that has any effect

type these commands at a command prompt. Applications->System Tools->Terminal
```

suco cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

```

---

### Post by Gargamella on 2005-08-24
i have got an ibm xserver with the same video card and problem and it's 6 mounths old,please help me too.

thanks

---

### Post by new2hoary on 2005-08-24
Funny - I knew it would be a i810 before I opened your post.

I had the same problem with that card when I used Debian. The problem is you video ram is not being detected.

I had a similar prolem with SIS when switching to Hoary.

Read this thread and it should help you get it sorted;

[http://www.ubuntuforums.org/showthread.php?t=57430](http://www.ubuntuforums.org/showthread.php?t=57430)

---

### Post by Silversierra on 2005-08-24
Thanks for the replies.

Sparky:  In your command, do you mean sudo or suco in the first part?  I've never seen suco, but lots of sudo in linux, although I really wouldn't know, I'm so new to this.

I'm running ubuntu now(live) on my gaming pc(amd64, 6600gt), and it works great, at 1024x768 85hz.  It looks much better at high res.

I'll try to get the file for you to look at soon.

Before posting, I searched and found many with similar problems, and several ways to attempt to fix the problem, except the posts assume that the reader knows what the writer is talking about, which I don't.  I need something simple, or step by step, so I can figure out how to do it.

Thanks again.

---

### Post by s_p_a_r_k_y on 2005-08-24
sudo is what I meant, sorry for the typo. If you want to see if a command exists on your system, type this into the command line
which command

which sudo would return /usr/bin/sudo
which suco would return nothing meaning that there is no executable or script with that name in your path.

---

### Post by Silversierra on 2005-08-25
Ok, I had time to check the xorg.o.log file, but it's huge, and I don't think you'd want me to post it all, here are some of the parts I think are relevant(even the relevant( I think) is huge.
II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, 915GM
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 832 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 845G
(--) I810(0): Chipset: "845G"
(--) I810(0): Linear framebuffer at 0xE0000000
(--) I810(0): IO registers at addr 0xEC000000
(II) I810(0): 1 display pipe available.
(II) I810(0): detected 892 kB stolen memory.
(II) I810(0): I830CheckAvailableMemory: 448508 kB available
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(WW) I810(0): Extended BIOS function 0x5f11 not supported.
(II) I810(0): Before: SWF1 is 0x00000101
(II) I810(0): After: SWF1 is 0x00000108
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 8000 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 892 kByte
(==) I810(0): VideoRAM: 32768 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 2607
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: LFP (local flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: CRT2 (second CRT): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 32600 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: DEL  Model: d000  Serial#: 808800563
(II) I810(0): Year: 2002  Week: 36
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) I810(0): Sync:  Separate
(II) I810(0): Max H-Image Size [cm]: horiz.: 28  vert.: 21
(II) I810(0): Gamma: 3.00
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.619 redY: 0.347   greenX: 0.308 greenY: 0.591
(II) I810(0): blueX: 0.144 blueY: 0.059   whiteX: 0.283 whiteY: 0.297
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) I810(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 56.2 MHz   Image Size:  270 x 202 mm
(II) I810(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) I810(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) I810(0): Serial No: 6418029405Q3
(II) I810(0): Monitor name: DELL E551c
(II) I810(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 54 kHz, PixClock max 70 MHz
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 30-54
(II) I810(0): 	VertRefresh 50-120

Does that help?
I hope someone knows how to figure this out, I sure don't.

Oh, I tried the command you gave me, I don't know if/what it did though.  It asked for my password, but then I couldn't tell if anything happened.  What should it have done?
Thanks again.

---

### Post by s_p_a_r_k_y on 2005-08-25
try changing your default depth to 16 or 15 in the xorg.conf file

---

### Post by kevinat0r on 2005-08-25
I have the same problem, I'm on a Dimension 3000 though. It's really starting to annoy me, I worked with an experienced Debian user online for 4 hours today, still no luck. I've tested every solution I've read on this forum, still no luck. I find it hard to believe that there's no definite answer, since I'm sure that plenty of people use Ubuntu on a Dell machine.

Here's my Xorg file. I've tried multiple ways of changing the graphics controller and things, nothing has worked.


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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

			# local font server
	# if the local font server has problems, we can fall back on these
        # paths to defoma fonts
	FontPath     "unix/:7100"
	FontPath     "/usr/lib/X11/fonts/misc"
	FontPath     "/usr/lib/X11/fonts/cyrillic"
	FontPath     "/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/Type1"
	FontPath     "/usr/lib/X11/fonts/CID"
	FontPath     "/usr/lib/X11/fonts/100dpi"
	FontPath     "/usr/lib/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "keyboard"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "DELL E153FP"
	Option	    "DPMS"
HorizSync 28-49
VertRefresh 43-72
EndSection

Section "Device"
	Identifier  "Intel Corporation 82865G Integrated Graphics Device"
	Driver      "i810"
	BusID       "PCI:0:2:0"
VideoRam "4096"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Intel Corporation 82865G Integrated Graphics Device"
	Monitor    "DELL E153FP"
	DefaultDepth     16
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600"	
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by s_p_a_r_k_y on 2005-08-26
hi,

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82865G Integrated Graphics Device"
Monitor "DELL E153FP"
DefaultDepth 16
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection
EndSection

I'm not experienced with X but I have troubleshot my own config file many times. You have defaultDepth 16 defined but no Depth 16 sub section. You have a Depth24... Try adding one for 16.

---

### Post by th3p14gu3 on 2005-08-26
no idea how that happened, but,  it didn't change a thing.

---

### Post by Silversierra on 2005-08-26
[QUOTE=s_p_a_r_k_y]try changing your default depth to 16 or 15 in the xorg.conf file[/QUOTE]

How?  I tried to type in the xorg.conf, but apparantly it's read only.

---

### Post by new2hoary on 2005-08-26
[QUOTE=kevinat0r]
Section "Device"
	Identifier  "Intel Corporation 82865G Integrated Graphics Device"
	Driver      "i810"
	BusID       "PCI:0:2:0"
VideoRam "4096"
EndSection
[/QUOTE]

Is that 'VideoRam' setting of 4MB correct?

---

### Post by s_p_a_r_k_y on 2005-08-26
Silversierra,

sudo nano /etc/X11/xorg.conf

will ask you for your password but give you admin rights to edit that file

---

### Post by th3p14gu3 on 2005-08-26
I was helping kevinat0r, with ssh and aim, to fix his problem we used 855resolution ([http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb](http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb) ), followed the instructions in the readme, worked like a charm.

---

### Post by Peferling on 2005-08-26
Just to add for others, I had the same problem with MEPIS on a Dell C400 laptop that uses shared ram also (very common issue for Dells).  MEPIS installs XFree.  I manually replaced Xfree with Xorg and that solved my problem.  (BTW There were other issues (PCMCIA for one) that could only be fixed by switching to Kubuntu..)

---

### Post by forumguy on 2005-08-27
the problem is with the bios in some dell computers... the correct amount of video ram is not allocated to the xserver

this problem has been solved on many distros i've tried with the 8x5patch available at [http://www.chzsoft.com.ar/855patch.html](http://www.chzsoft.com.ar/855patch.html)  ; use the patch specific to your chipset as seen in sudo lspci


however, i have been unable to get this patch working under kubuntu... which is odd, since i have seen it work under suse and kubuntu uses a far more standard linux kernel and gnu layout

i run the patch using /path/to/845patch 16384 and the console prints that the video ram was successfully changed.... however, i still only get 640x480 resolution although my xorg.conf file does specify to use the 16 bit resolution and even gives the correct horizontal and vertical refresh rates for the monitor (same problem occurs without these settings)....


can anyone else get this patch running?

---

### Post by forumguy on 2005-08-27
repeat...

---

### Post by forumguy on 2005-08-27
repeat...

---

