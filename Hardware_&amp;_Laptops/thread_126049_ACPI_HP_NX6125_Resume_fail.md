---
title: "ACPI HP NX6125 Resume fail"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by Mansor on 2006-02-05
Hi, everyone can help me out with this.
I've installed ubuntu breezy on a HP NX6125 with a Sempron 2800, everything was out of the box with some parameters at boot installation.

My problem is that I can't resume from suspend to memory.
When I pressed on button it freezes and no image from the LCD is displayed.

This is my info:

Linux lxlaptop 2.6.12-10-k7 #1 Mon Jan 16 19:20:45 UTC 2006 i686 GNU/Linux

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:05.0 PCI bridge: ATI Technologies Inc: Unknown device 5a37
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
0000:02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
0000:02:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:02:04.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:04.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:02:04.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:02:04.4 0805: Texas Instruments: Unknown device 8034

Module                  Size  Used by
ipv6                  252544  6
binfmt_misc            11592  1
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
powernow_k8            12424  0
cpufreq_userspace       4380  1
cpufreq_stats           5316  0
freq_table              4484  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
pcmcia                 26632  2
fglrx                 255780  7
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
i2c_core               21328  1 i2c_acpi_ec
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
af_packet              22088  4
rtc                    12408  0
pcspkr                  3460  0
ohci1394               34804  0
yenta_socket           25356  1
rsrc_nonstatic         13504  1 yenta_socket
pcmcia_core            49668  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_atiixp             20384  3
snd_ac97_codec         84028  1 snd_atiixp
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  12 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_atiixp,snd_pcm
pci_hotplug            27636  0
ati_agp                 9100  0
agpgart                34888  2 fglrx,ati_agp
nls_cp437               5760  1
ntfs                  109104  1
dm_mod                 58044  1
joydev                 10048  0
tsdev                   7872  0
evdev                   9728  1
ndiswrapper           132296  0
sr_mod                 17252  0
sbp2                   23176  0
scsi_mod              135944  2 sr_mod,sbp2
ieee1394              101752  2 ohci1394,sbp2
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
ext3                  137352  2
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  2 powernow_k8,thermal
fan                     4548  0
usbhid                 35552  0
tg3                    97220  0
ehci_hcd               34312  0
ohci_hcd               20740  0
usbcore               118396  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
ide_cd                 41732  0
cdrom                  39904  2 sr_mod,ide_cd
ide_disk               18560  5
ide_generic             1472  0
atiixp                  6096  1
ide_core              139028  4 ide_cd,ide_disk,ide_generic,atiixp
unix                   27248  816
capability              4808  0
commoncap               6912  1 capability
vesafb                  8088  1
vgastate                9792  0
softcursor              2496  1 vesafb
cfbimgblt               3008  1 vesafb
cfbfillrect             3968  1 vesafb
cfbcopyarea             4672  1 vesafb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon

# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
#ACPI_SLEEP_MODE=mem //Original
ACPI_SLEEP_MODE=standby

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
RADEON_LIGHT=true
# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
#HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
#RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

---

### Post by Ransu on 2006-02-12
I've also just recently bought NX6125 (with Turon ML-32) and trying to install linux on it. I'm very much a beginner and having fought two days with Debian, I'm ready to change to Ubuntu. Your post worried me though since if the suspend thing doesn't work properly, it's bad for battery life on the road. Have you tried looking among the unsupported packages - a real debian package specifically for AMD PowerNow! and for notebook power management packages? Maybe Ubuntu doesn't yet include them and you have to get them from debian unstable packages... ?

Not that I'd know where even to start to find and install them - we need a reply from on of those 'linux experts'...

[edit] ...and while I'm here, might as well ask a few questions, although the new-post/reply ration on this forum is terrible.

a no nothing newbie like me might have the impression of Ubuntu that, although it's all easy and inclusive, there must be some down side to this (you know, the 'no-free lunch' law of nature). Is it for example possible to use debian packages directly in Ubuntu (using, I assume a different package management than the one supported by Ubuntu). Can I use something like aptitude on Ubuntu? Let's say the I want to figure out how to install Broadcom drivers (which are still very much in beta) for my wireless card and then have it run kismet all that stuff on it - sure it's all 'linux' software - but if the packages offered are rpms, or even worse, source, what chance is there of Ubuntu basic install combined with newbie user in getting them to work? These are just examples that came to my mind as I'm trying to get a 'feel' of what this thing is about. At least with Debian I know all things are 'possible' albeit 'impossible' for the avarage newbie...

---

### Post by chele on 2006-02-12
> Is it for example possible to use debian packages directly in Ubuntu?Yes.

Ubuntu is simply a version of debian gnu/linux. All one needs is to add the 'Universe' list of packages via Synaptic > Settings > Repositories.

---

### Post by chele on 2006-02-12
I have not had much luck convincing this HP nw8000 to wake from sleep either. I am not sure if it is a kernel bug or a video bug or what.

If you enter your machine in the [GNU/Linux device driver check page]("http://kmuto.jp/debian/hcl/") does it show up fully supported, or not?

---

### Post by Mansor on 2006-02-13
Maybe it's only configuration, I edit the /etc/default/acpi-support file and I see many options.
I don't know which modules select to unload from kernel and which ones don't.
I entered the info in the link you gave me and there's a few works=yes.

If you can see I post my laptop hardware info and many devices says unknown device.

I don't know if I upgrade the kernel I can solve the problem, but I've got the latest image kernel from Ubuntu.

Any ideas?

---

### Post by chele on 2006-02-13
>  I entered the info in the link you gave me and there's a few works=yes.Hi Mansor

Did you save the info on that site? There is report button down below the results.

Heh Ransu, does resume from sleep work on standard Debian gnu/linux?

---

### Post by mjg59 on 2006-02-14
The nx6125 should suspend/resume fine in Dapper. It won't work in Breezy.

---

### Post by ojoi on 2006-02-18
hello everybody.
i too have purchased HP Nx6125 with a ml30 1.6 amd and rest of the config is to be same i guess.
i use to run ubuntu on my ibm laptop before i upgraded to this nx6125.
now i am stuck with the same problem, no display and have been hearing lot of compatibility problems with ubuntu on this laptop.
i hope ubuntu team makes a specific release for this laptop has they have done it with various other Hp laptops.
please please please you ubuntu guru's give me a release of ubuntu on HP Nx6125.
thanks
oj

---

### Post by Mansor on 2006-02-19
The Hardware result from Debian GNU/Linux device driver check

PCI ID	Works?	Vendor	Device	Driver	Comment
10025950	-	ATI Technologies Inc	RS480 Host Bridge	 	 
10025a3f	-	ATI Technologies Inc	no information	 	 
10025a36	-	ATI Technologies Inc	no information	 	 
10025a37	-	ATI Technologies Inc	no information	 	 
10024374	-	ATI Technologies Inc	IXP SB400 USB Host Controller	 	 
10024375	-	ATI Technologies Inc	IXP SB400 USB Host Controller	 	 
10024373	-	ATI Technologies Inc	IXP SB400 USB2 Host Controller	 	 
10024372	-	ATI Technologies Inc	IXP SB400 SMBus Controller	 	 
10024376	Yes	ATI Technologies Inc	Standard Dual Channel PCI IDE Controller ATI	atiixp	 
10024377	-	ATI Technologies Inc	IXP SB400 PCI-ISA Bridge	 	 
10024371	-	ATI Technologies Inc	IXP SB400 PCI-PCI Bridge	 	 
10024370	Yes	ATI Technologies Inc	IXP SB400 AC97 Audio Controller97 Audio Controller	snd-atiixp	 
10024378	Yes	ATI Technologies Inc	ATI SB400 - AC97 Modem Controller97 Modem Controller	snd-atiixp-modem	 
10221100	-	Advanced Micro Devices [AMD]	K8 [Athlon64/Opteron] HyperTransport Technology Configuration	 	 
10221101	-	Advanced Micro Devices [AMD]	K8 [Athlon64/Opteron] Address Map	 	 
10221102	-	Advanced Micro Devices [AMD]	K8 [Athlon64/Opteron] DRAM Controller	 	 
10221103	-	Advanced Micro Devices [AMD]	K8 [Athlon64/Opteron] Miscellaneous Control	 	 
10025955	Yes	ATI Technologies Inc	RS480 0x5955 [ATI Radeon XPRESS 200M 5955 (PCIE)]	ati	 
14e4169c	Yes	Broadcom Corporation	NetXtreme BCM5788 Gigabit Ethernet	tg3	 
14e44318	Yes	Broadcom Corporation	BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller	ndiswrapper	 
104c8031	Yes	Texas Instruments	PCIxx21/x515 Cardbus Controller	yenta_socket	 
104c8032	-	Texas Instruments	OHCI Compliant IEEE 1394 Host Controller	 	 
104c8033	-	Texas Instruments	PCIxx21 Integrated FlashMedia Controller	 	 
104c8034	-	Texas Instruments	PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

---

