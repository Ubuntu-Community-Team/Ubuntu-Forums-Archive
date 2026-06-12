---
title: "Radeon IGP 320M/340M"
date: 2005-01-16
forum: Hardware &amp; Laptops
---

### Post by Nebula10111 on 2005-01-16
Allrighty I'm sure there are people out there with these mobile video cards. I have an IGP 320M and my roomate has a 340M. We're both running Ubuntu on our laptops. Now Ubuntu recognizes our cards no problem and they're working. HOWEVER we have   NO 3D support whatsoever. Does anyone have any idea how we can get 3D accel. running. I've been searching but with no luck. Any ideas???

---

### Post by merinda on 2005-01-17
No luck buddy.....

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards)

I have same problem with you.....

---

### Post by Slalomsk8er on 2005-03-11
I have same problem as you have (compaq nx9010 ATI IPG 340M).
[http://www.freax.eu.org/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop](http://www.freax.eu.org/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop)
There is a new driver out, maybe with this one it will work ;-)

---

### Post by wittygame on 2005-03-11
I have 3D out of the box on hp nx9005 AMD athlonm with the IGP 320M. 
I have hoary on it.

I do not know how to set X on ubuntu yet, it just worked without me touching a thing! quite impressive I say.


The problem with 3D enabled (meaning dri and agp modules are loaded) is that u can no longer recover from suspend! bugger!

---

### Post by Slalomsk8er on 2005-03-12
Can you post your xorg.conf?

What are  ```
glxgears
glxinfo | grep 's3tc\|direct'
dmesg | grep agp
dmesg | grep radeon
lsmod
``` showing?

> I have 3D out of the box on hp nx9005 AMD athlonm with the IGP 320M.
I have hoary on it.

If my mem is not playing tricks on me, it was working on my nx9010 but now DRI = no :sad:

---

### Post by Slalomsk8er on 2005-03-12
As 3D is a big point for me (blender) I desided to try XGI's drivers even if it will cost me £129 (if it works).
[http://www.xig.com/Pages/Summit/Demos/LX-PlatinumLinux.html](http://www.xig.com/Pages/Summit/Demos/LX-PlatinumLinux.html)

I think I have now all I need to start the installation (kernel source, kernel config, Summit_LX-Platinum-2.2-20-LINUX.tar)

---

### Post by Slalomsk8er on 2005-03-14
I gave up I could not compile the base for the driver :( 
I installed the needed tool and the kernel source but no go (man I never saw that much errors in a Gentoo compilation).

---

### Post by linasgricius on 2005-04-24
[QUOTE=Slalomsk8er]Can you post your xorg.conf?

What are  ```
glxgears
glxinfo | grep 's3tc\|direct'
dmesg | grep agp
dmesg | grep radeon
lsmod
``` showing?



If my mem is not playing tricks on me, it was working on my nx9010 but now DRI = no :sad:[/QUOTE]

Hello everyone! Sorry for my English but I would like to share my results with IGP 340M.  \\:D/ 

My computer: HP pavilion ze5630us.

After so many times without luck no I have normal IGP 340M video support!

OK, here is my results:

lg@ze5630us:~$ glxgears
2252 frames in 5.0 seconds = 450.400 FPS
2732 frames in 5.0 seconds = 546.400 FPS
2764 frames in 5.0 seconds = 552.800 FPS
2641 frames in 5.0 seconds = 528.200 FPS
2777 frames in 5.0 seconds = 555.400 FPS
2749 frames in 5.0 seconds = 549.800 FPS
2765 frames in 5.0 seconds = 553.000 FPS
2782 frames in 5.0 seconds = 556.400 FPS


The best results : 2966 frames in 5.0 seconds = 593.200 FPS

lg@ze5630us:~$ glxinfo | grep 's3tc\|direct'
direct rendering: Yes


lg@ze5630us:~$ dmesg | grep agp
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected Ati IGP345M chipset
agpgart: Maximum main memory to use for agp memory: 149M
agpgart: AGP aperture is 64M @ 0xd4000000
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode


lg@ze5630us:~$ dmesg | grep radeon
radeonfb: Retreived PLL infos from BIOS
radeonfb: Reference=14.32 MHz (RefDiv=31) Memory=183.00 Mhz, System=133.00 MHz
radeonfb: PLL min 12000 max 35000
radeonfb: Monitor 1 type LCD found
radeonfb: Monitor 2 type no found
radeonfb: panel ID string: Samsung LTN150P1-L02
radeonfb: detected LVDS panel size from BIOS: 1400x1050
radeondb: BIOS provided dividers will be used
radeonfb: Dynamic Clock Power Management enabled
radeonfb: Dynamic Clock Power Management enabled
radeonfb (0000:01:05.0): ATI Radeon C7
[drm] Initialized radeon 1.14.0 20050125 on minor 0: ATI Technologies Inc Radeon IGP 340M


lg@ze5630us:~$ lsmod
Module                  Size  Used by
nls_cp437               5600  1
isofs                  36280  1
udf                    89060  0
proc_intf               3908  0
cpufreq_userspace       4348  1
cpufreq_ondemand        6140  0
cpufreq_powersave       1632  0
pcmcia                 22244  2
video                  15972  0
sony_acpi               5928  0
pcc_acpi               11008  0
button                  6480  0
battery                 9988  0
container               4320  0
ac                      4676  0
ipv6                  257888  16
af_packet              21992  2
usbhid                 31936  0
natsemi                27200  0
i2c_ali1535             6980  0
i2c_ali15x3             7492  0
ehci_hcd               32708  0
uhci_hcd               32816  0
yenta_socket           21344  0
pcmcia_core            57984  2 pcmcia,yenta_socket
snd_ali5451            23684  2
snd_ac97_codec         74144  1 snd_ali5451
snd_pcm_oss            52132  1
snd_mixer_oss          19680  2 snd_pcm_oss
snd_pcm                94696  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  6 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  3 snd
snd_page_alloc          9732  1 snd_pcm
shpchp                 99172  0
pci_hotplug            33488  1 shpchp
pcspkr                  3496  0
rtc                    12472  0
md                     47440  0
dm_mod                 59420  1
capability              4648  0
commoncap               7712  1 capability
radeon                 77056  1
drm                    65172  2 radeon
radeonfb               71812  1
i2c_algo_bit            9800  1 radeonfb
i2c_core               22320  4 i2c_ali1535,i2c_ali15x3,radeonfb,i2c_algo_bit
ati_agp                 8364  1
agpgart                33608  2 drm,ati_agp
evdev                   9344  1
joydev                  9664  0
tsdev                   7520  0
ndiswrapper           120980  0
usbcore               119000  5 usbhid,ehci_hcd,uhci_hcd,ndiswrapper
p4_clockmod             4776  0
speedstep_lib           3940  1 p4_clockmod
freq_table              4004  1 p4_clockmod
psmouse                21320  0
mousedev               11288  1
parport_pc             37252  1
lp                     11144  0
parport                36744  2 parport_pc,lp
ide_cd                 41700  1
cdrom                  40220  1 ide_cd
ext3                  137256  2
jbd                    60536  1 ext3
mbcache                 8356  1 ext3
ide_generic             1312  0
ide_disk               20416  4
alim15x3               12300  1
ide_core              129356  4 ide_cd,ide_generic,ide_disk,alim15x3
unix                   28276  858
thermal                13320  0
processor              22452  1 thermal
fan                     4388  0
fbcon                  37504  71
font                    8192  1 fbcon
bitblit                 5472  1 fbcon
vesafb                  6724  0
cfbcopyarea             3808  2 radeonfb,vesafb
cfbimgblt               2912  2 radeonfb,vesafb
cfbfillrect             3488  2 radeonfb,vesafb


And here is my xorg.conf:

...

Section "Module"
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
# mano
	Load	"GLcore"
	Load	"synaptics"

EndSection

...

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"radeon"
	# Nauji nustatymai
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "True"
	Option		"EnablePageFlip" "True"
	BusID		"PCI:1:5:0"
	Option		"DPMS"
	Videoram	65536
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection






And /etc/modules :

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
#speedstep-ich
p4_clockmod
ndiswrapper
agpgart
ati_agp
radeonfb
radeon



Just yesterday my glxgears results was very puor - only about 300FPS and today I have about ~550FPS  \\:D/  I like it!

I case you have better solution, please share it with others!

---

### Post by enderson on 2005-11-26
I installed Ubuntu 5.10 today, and I have 3D working out of the box.

I have "Direct Rendering: Yes" as glxinfo output, so I think it's 3D support. Ok ?

Tell me if I'm wrong. :)

Now I need to make tvout work, it's a IGP 320M, Compaq nx9005 notebook.

---

### Post by JeremyPrivett on 2005-12-29
linasgricius,

Is there anything more you could tell me about what you did to get this working? My xorg.conf file looks identical to yours but I still cannot get it to work.

glxinfo | grep 's3tc\|direct'
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

???

---

### Post by linasgricius on 2006-01-07
My xorg.conf:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Driver		"radeon"
	BusID		"PCI:1:5:0"
	VideoRam	131072
	Option		"UseFBDev"		"true"
	Option		"AGPMode"		"4"
	Option		"AGPFastWrite"		"True"
	Option		"EnablePageFlip"	"True"
EndSection


/etc/modules:

ide-cd
ide-disk
ide-generic

lp
mousedev
psmouse

agpgart
ati_agp
radeonfb
radeon





lg@ze5630us:~$ glxgears -printfps
2695 frames in 5.0 seconds = 538.940 FPS
2696 frames in 5.0 seconds = 539.087 FPS


I'm using Ubuntu Dapper. It's very dificult to enable direct rendering as I don't know exactly on what depends but these results are my best result for my notebook...

Contact me by PM as I'm not monitoring this forum

---

### Post by mrmailer on 2006-02-01
I have 320m, and I get 467fps.  Am I doing everything OK?  I am using usefbdev.

---

### Post by kuzmaionitch on 2007-11-04
Well, I have full 3D support with Gutsy on my Radeon IGP card,
but if anyone could point me in the right direction for video-out i would appreciate it.

---

### Post by Corgana on 2007-11-11
Anyone get dual-screens working with this card?

---

### Post by raindog on 2007-11-12
I have an external monitor hooked up in clone mode, but I can't get the refresh rate to change and it's killing my eyes.  As far as a stretched desktop or multiple desktops I haven't messed around with that.

I have a post regarding my issues with an external monitor and the R200 Radeon 320M|340M [here]("http://ubuntuforums.org/showthread.php?t=609070").

Sorry I can't be of more help at this time.

---

### Post by Noiano on 2008-04-27
Hello everybody,
I have radeon IGP 320M on compaq evo n1015v and I cannot have a projector working on GDM. It only works on the console. When I try to switch to tty7 (the gdm one) the projector gets no signal. Xrandr says the projector is connected but it gets no signal. Any ideas?

---

