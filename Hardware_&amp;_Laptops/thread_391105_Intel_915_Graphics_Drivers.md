---
title: "Intel 915 Graphics Drivers"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by Clay_Banger on 2007-03-22
i have googled and searched through the ubuntu forums trying to find a how-to install the i915 graphics drivers and have had no luck. the best i have done is get to [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) and download the latest i915 package. i tried to install it using "sudo sh install.sh" but it gets through 2 confirmation screens then says:
```
The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...[: 696: ==: unexpected operator
install.sh: 696: Syntax error: Bad fd number
```

What am i doing wrong?

---

### Post by taurus on 2007-03-22
There is 915resolution driver in the repos.  You need to enable both universe & multiverse in /etc/apt/sources.list first.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Clay_Banger on 2007-03-22
after doing that all i get when searching in adept manager for "915" all i get is the 915resoulution changer, that isnt what im after.
In System Settings>Monitor & Display>Hardware tab it says that the driver and card is i810, however when u configure it, it says that the detected graphics card is "Intel 915". I wish to change the i810 driver to i915, the correct one.

---

### Post by ctnd on 2007-04-02
> **Clay_Banger said:**
> after doing that all i get when searching in adept manager for "915" all i get is the 915resoulution changer, that isnt what im after.
In System Settings>Monitor & Display>Hardware tab it says that the driver and card is i810, however when u configure it, it says that the detected graphics card is "Intel 915". I wish to change the i810 driver to i915, the correct one.

I've had this problem for a long time. My card is i915. The i810 driver *works* with the card, but does not work *properly*, it is very slow and there are errors that appear on glxgears. I figured using the *i915* driver, which one would think would be the correct one, would fix it. But all I am told is that "i810 is the correct driver" and that it "should work properly". It's clear that nobody knows anything about this problem. However, every month or so, as I am doing now, I search the web looking for a solution. I thought I'd share my story with someone suffering the same problem as me, as nobody else listens. If I find a solution, I'll post it here. Wish me luck!

---

### Post by Clay_Banger on 2007-04-02
> **ctnd said:**
> I've had this problem for a long time. My card is i915. The i810 driver *works* with the card, but does not work *properly*, it is very slow and there are errors that appear on glxgears. I figured using the *i915* driver, which one would think would be the correct one, would fix it. But all I am told is that "i810 is the correct driver" and that it "should work properly". It's clear that nobody knows anything about this problem. However, every month or so, as I am doing now, I search the web looking for a solution. I thought I'd share my story with someone suffering the same problem as me, as nobody else listens. If I find a solution, I'll post it here. Wish me luck!

ok, thx for filling me in on the info that you already know. i have done a far bit of googling but have had no result. i will continue having a look around, when i can b bothered 2. i would greatly appreciate it if you did notify me if you did find anything. gool luck:)

---

### Post by ramjet_1953 on 2007-04-03
What Taurus told you is the correct thing to do.

The 915resolution package covers a whole range of intel chipsets.

I suggest that you not use 32 bit colour depth, but instead us 24 bit.
32 bit often causes problems and can crash your system.

I submitted this how-to some time ago and it works for most people.

[http://www.ubuntuforums.org/showthread.php?t=351647&highlight=resolution](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=resolution)

Regards,
Roger :cool:

---

### Post by Clay_Banger on 2007-04-03
i dont need to change the resolution, i have the resolution working fine, its just, for example, playing warzone 2100 on windows on my box works flawlessly, no problems. playing warzone 2100 on kubuntu on this box, it barely runs. this is also the case for nexuiz and tremulous. i believe that installing the correct driver will fix this issue.

---

### Post by jjordan on 2007-04-04
OK, here is a link to the latest i915 driver.
[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

Your problem actually sounds like you need to enable DRI

Here is a link to another thread about the i915
[http://www.linuxquestions.org/questions/showthread.php?t=311096](http://www.linuxquestions.org/questions/showthread.php?t=311096)

I have an i915 and have no problems with performance but I am not a gamer.  It is very difficult to compare graphics performance between games on Windows and Linux.  Linux is free software, it is built by dedicated individuals frequently without the assistance of the companies that built the hardware.  i915 is not generaly considered a gaming video card.  Look at the Nvidia card for gaming under Linux.  Some ATI cards are also well supported but tend to be more difficult to get stable results.

-j

---

### Post by jjordan on 2007-04-04
P.S. i915resolution is NOT the video driver, it is a program to patch the bios of the i915.

---

### Post by Clay_Banger on 2007-04-04
ok, i dont know what i did, but its all good now, everything works now, within games... i honesty dont know what changed it. i mainly just had a play around with the stuff in System Settings>Monitor and Display>Hardware, and it all works.

---

### Post by imspecial on 2007-04-11
just wondering but where can the System Settings menu be found? I have looked for it, but haven't come to anything close to it.

---

### Post by Clay_Banger on 2007-04-11
im using kubuntu which uses the kde desktop environment, which is different to just straight ubuntu, so i dont know where it can b found.

---

### Post by imspecial on 2007-04-11
ok thanks

---

### Post by Shnuffey on 2007-12-14
Damnit I got the same error.. any idea at all on what u might have done ? I read the hold post and damn dont tell me that the 810 driver works it works for 2d use and 3d beryl use ye, but for 3d accelerating stuff no way in hell I know the comp is strong enough for it I tried it with windows but I dont wanna use that cause honestly its a pain ... anyhow specs needed to know is .. Hp laptop no idea on the type.. it has 2.4 ghz intel prossesor 512 ram and a i915 graphics card at 64 mb's ...
any idea on the driver? or a way to use the driver discussed in the first post ? 

Compiling...[: 696: ==: unexpected operator
install.sh: 696: Syntax error: Bad fd number
root@Shnuffey:/home/snuffy/Desktop/i915-20060403-linux.i386# 
root@Shnuffey:/home/snuffy/Desktop/i915-20060403-linux.i386# 


pS I cleansed out the previous 810 drivers so I doubt thats the problem

---

### Post by ckth on 2007-12-27
> **ctnd said:**
> I've had this problem for a long time. My card is i915. The i810 driver *works* with the card, but does not work *properly*, it is very slow and there are errors that appear on glxgears. I figured using the *i915* driver, which one would think would be the correct one, would fix it. But all I am told is that "i810 is the correct driver" and that it "should work properly". It's clear that nobody knows anything about this problem. However, every month or so, as I am doing now, I search the web looking for a solution. I thought I'd share my story with someone suffering the same problem as me, as nobody else listens. If I find a solution, I'll post it here. Wish me luck!

I have the exact same problem. An Intel 915GAV chipset, with Ubuntu using the 810 Drivers.  Compiz is quite jerky, and normal actions such as scrolling or rendering stutter as well.

I hope the 915 drivers are added to the repositories soon.

---

### Post by rosegarden78 on 2008-01-19
...

---

### Post by rosegarden78 on 2008-01-19
My solution to the Gordian Knot is to slice it:

1)  Backup your files
2)  Clean install

I use your graphics card on a Dell Inspiron 1200 laptop with Gutsy and it works perfectly.  Well, I think it does anyway.  I've never used multiple monitors or screen rotation anyway.  With a standard laptop I hardly see a use for those options in my daily activity.  If you seriously cannot get it working with Linux/Ubuntu it might have burned out.

You may consider booting your Windows partition to test the functionality ...

---

### Post by rosegarden78 on 2008-01-19
A clean install of Gutsy or the latest distro usually does the trick.  If not try falling back to your previous (yuck) operating system and/or legacy software.

---

### Post by cyber_bushi on 2008-02-09
Hey guys, I have a i915, am happy with my resolution (using ixxxresolution) but I don't have any rendering, i.e.
```

hot33331@x20:~$ glxinfo|grep render
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2

```
glxgears gives me:
```

4388 frames in 5.1 seconds = 865.859 FPS

```

I am using Gutsy and lsmod says:
```

intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp

```
also...
```

hot33331@x20:~$ lspci |grep Intel
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

You'd make me happy if you could help me out here. I'd really want to play my games WITH direct rendering. If you need any more files or something else posted, please let me know...

cb

---

### Post by Sirhanz on 2008-03-08
Hi I have a similar problem here. I have a Intel D915GLVG mother board with the intel 915gl express chipset also with the intel graphics media accelerator 900. I have been poking around with my configuration for months now trying to find the perfect settings. CLAY_BANGER could you perhaps post your xorg.conf from that system you unknowingly fixed. Also everytime I run GLXGEARS I get a window with gears turning, not a FPS count, am i missing something?

Update: Hey so I think I got this thing figured the best I can get on this current setup. I have the Intel 82915G/GV/910GL motherboard with onboard 915GL express chipset video with intel graphics media accelerator 900. I did the 915resolution patch to set my display to 1024x768 , I found using 16 color depth gave me the best FPS with glxgears. I chose the 16 color depth in both xorg.conf and the 915resolution patch. Here are all my settings.

xorg.conf
```
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
	Load	"bitmap"
	Load	"dbe"
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
	Option		"XkbLayout"	"dvorak"
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
	Identifier	"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	262144
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 109B"
	Option		"DPMS"
	HorizSync	30-97
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
	Monitor		"PHILIPS 109B"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection
```

glxinfo|grep render
```
sirhanz@Messiah:~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 915G 20050225
```

So theres that rendering :)

lsmod
```
sirhanz@Messiah:~$ lsmod
Module                  Size  Used by
i915                   20608  1
drm                    73236  2 i915
rfcomm                 40216  0
l2cap                  26372  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ipv6                  266112  6
af_packet              22920  4
dm_mod                 59192  1
md_mod                 72532  0
lp                     11844  0
usb_storage            74304  0
tsdev                   8000  0
parport_pc             35780  1
floppy                 62148  0
pcspkr                  2180  0
parport                36296  3 ppdev,lp,parport_pc
e100                   40580  0
mii                     5888  1 e100
psmouse                36100  0
usblp                  13056  0
usbhid                 39904  0
rtc                    13492  0
ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  3 ath_pci,ath_rate_sample
ath_hal               148816  3 ath_pci,ath_rate_sample
serio_raw               7300  0
snd_hda_intel          18964  1
snd_hda_codec         157616  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
intel_agp              22940  1
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
agpgart                34888  3 drm,intel_agp
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
sg                     37920  0
evdev                   9856  1
ext3                  135944  2
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  6 usb_storage,usblp,usbhid,ehci_hcd,uhci_hcd
sd_mod                 19984  3
ata_piix               11012  4
libata                 78992  1 ata_piix
scsi_mod              139496  4 usb_storage,sg,sd_mod,libata
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  2
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

lspci |grep
```
sirhanz@Messiah:~$ lspci |grep Intel
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller
0000:00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:05:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

```

And finally glxgears -printfps
```
sirhanz@Messiah:~$ glxgears -printfps
5239 frames in 5.0 seconds = 1047.667 FPS
5519 frames in 5.0 seconds = 1103.799 FPS
5532 frames in 5.0 seconds = 1106.375 FPS
5527 frames in 5.0 seconds = 1105.272 FPS
5533 frames in 5.0 seconds = 1106.496 FPS
5535 frames in 5.0 seconds = 1106.959 FPS
5536 frames in 5.0 seconds = 1107.056 FPS
5529 frames in 5.0 seconds = 1105.705 FPS
5532 frames in 5.0 seconds = 1106.353 FPS
5529 frames in 5.0 seconds = 1105.609 FPS
5533 frames in 5.0 seconds = 1106.489 FPS
```

That glxgears was done with everything closed for the most part, no berowser, kopete, and definately ktorrent and amarok. I generally to close amarok before I play any game, it causes a huge drop in available memory and causes games to be jumpy. I find my best performance test is a little game called liquidwars. If anybody can milk this for a bit more performance please do and let us know how. :guitar:

---

### Post by ChronoEngineer on 2008-03-24
I too am having this problem. I was able to get the install.sh script to run but it failed. Here is the dri.log file.

make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/coleary/Desktop/i915-20060403-linux.i386/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
+ ln -s ../shared-core/mga_drm.h mga_drm.h
+ ln -s ../shared-core/mga_drv.h mga_drv.h
+ ln -s ../shared-core/mga_irq.c mga_irq.c
+ ln -s ../shared-core/mga_state.c mga_state.c
+ ln -s ../shared-core/mga_ucode.h mga_ucode.h
+ ln -s ../shared-core/mga_warp.c mga_warp.c
+ ln -s ../shared-core/r128_drv.h r128_drv.h
+ ln -s ../shared-core/r128_drm.h r128_drm.h
+ ln -s ../shared-core/r128_cce.c r128_cce.c
+ ln -s ../shared-core/r128_state.c r128_state.c
+ ln -s ../shared-core/r128_irq.c r128_irq.c
+ ln -s ../shared-core/radeon_drv.h radeon_drv.h
+ ln -s ../shared-core/radeon_drm.h radeon_drm.h
+ ln -s ../shared-core/radeon_cp.c radeon_cp.c
+ ln -s ../shared-core/radeon_irq.c radeon_irq.c
+ ln -s ../shared-core/radeon_mem.c radeon_mem.c
+ ln -s ../shared-core/radeon_state.c radeon_state.c
+ ln -s ../shared-core/r300_cmdbuf.c r300_cmdbuf.c
+ ln -s ../shared-core/r300_reg.h r300_reg.h
+ ln -s ../shared-core/sis_drv.h sis_drv.h
+ ln -s ../shared-core/sis_drm.h sis_drm.h
+ ln -s ../shared-core/sis_ds.c sis_ds.c
+ ln -s ../shared-core/sis_ds.h sis_ds.h
+ ln -s ../shared-core/sis_mm.c sis_mm.c
+ ln -s ../shared-core/tdfx_drv.h tdfx_drv.h
+ ln -s ../shared-core/via_drm.h via_drm.h
+ ln -s ../shared-core/via_drv.h via_drv.h
+ ln -s ../shared-core/via_mm.h via_mm.h
+ ln -s ../shared-core/via_ds.h via_ds.h
+ ln -s ../shared-core/via_3d_reg.h via_3d_reg.h
+ ln -s ../shared-core/via_drv.c via_drv.c
+ ln -s ../shared-core/via_ds.c via_ds.c
+ ln -s ../shared-core/via_irq.c via_irq.c
+ ln -s ../shared-core/via_map.c via_map.c
+ ln -s ../shared-core/via_mm.c via_mm.c
+ ln -s ../shared-core/via_dma.c via_dma.c
+ ln -s ../shared-core/via_verifier.c via_verifier.c
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
+ ln -s ../shared-core/nv_drv.h nv_drv.h
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.22-14-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/coleary/Desktop/i915-20060403-linux.i386/drm/linux-core/drm_auth.o
In file included from /home/coleary/Desktop/i915-20060403-linux.i386/drm/linux-core/drm_auth.c:36:
/home/coleary/Desktop/i915-20060403-linux.i386/drm/linux-core/drmP.h:44:26: error: linux/config.h: No such file or directory
make[3]: *** [/home/coleary/Desktop/i915-20060403-linux.i386/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/home/coleary/Desktop/i915-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/coleary/Desktop/i915-20060403-linux.i386/drm/linux-core'
make: *** [i915.o] Error 2

---

### Post by jesusfreak107 on 2008-03-24
I am not THAT much of a geek, I cannot understand that much technobabble, but I recently had to get a driver for an MSI Nvidia 915 128MB graphics card, and I saw a Linux section, for the drivers.  If you can put the cable in the integrated video slot, then try and find a Linux version of your driver, download it and install it.  If you do not have a screen compatible with your integrated graphice, old CRT monitors are easy to find, look in your garage, or ask any geek, if you can get them to come out of their little holes into which we have fled.  we probably have 10 CRT monitors in our house, several which are being used, several more of which are sitting in our garage.  They are hard to kill, and last a LONG time.

---

### Post by Arielo on 2008-04-28
after MANY MANY month of trying to solve the problem and make ubuntu use 915 driver and not the i810 im still in a dead end.

as it seems there is NO solution for this and thats extremly sad since i love using ubuntu ,,,i guess ill go back on xp for playing games,

hope in the future this will be fixed and maybe a deb package to help our lifes/,

please ubuntu fix this its truly anoying.

this happend on hardy and gusty i guess on previous versions as well.

---

### Post by unclben on 2008-05-03
> **Arielo said:**
> after MANY MANY month of trying to solve the problem and make ubuntu use 915 driver and not the i810 im still in a dead end.I am confused. I thought 'intel' was the current driver and 'i810' was deprecated. Have you tried the 'intel' driver? I have been using the 'intel' driver on both 965 and 845 chipsets (maybe 915 too, not sure) since Feisty (IIRC).

---

### Post by Arielo on 2008-05-22
i tried the "intel" driver but i got this feeling that the driver isant working properly ive checked my xorg and all else needed to do.

is there anyway to make intel driver appear in restricted drivers ?

---

