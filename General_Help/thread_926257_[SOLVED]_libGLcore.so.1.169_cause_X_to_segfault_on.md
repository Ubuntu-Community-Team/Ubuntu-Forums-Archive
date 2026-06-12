---
title: "[SOLVED] libGLcore.so.1.169 cause X to segfault on start"
date: 2008-09-21
forum: General Help
---

### Post by jfbilodeau on 2008-09-21
Call me a fool if you want, but in my desperate attempt to get SPORE working with Wine, I did the unthinkable, and install the latest drivers from the nvidia site.

The good news is that I got SPORE working 100%. Yay! The bad news is (as many of you expect I'm sure) is that when updates rolled in, it broke my nvidia driver. The system would only start in low-graphics mode.

I've tried to reinstalled the driver but that didn't fix the problem. The next thing I tried was to reinstall the Ubuntu driver. That didn't work either.

Everytime I start X, I get a segfault.

I fought with this for a while, until I manually deleted every files that are installed by the nvidia driver and re-apt-getted nvidia-glx-new and the related kernel files. X is still not happy. I went as far as doing apt-get remove ubuntu-desktop and apt-get install ubunto-desktop. At this point, I'm 90% sure I removed any nvidia 173.14.12 driver files.

I finally managed to get the X server up by *deleting* libGLcore.so.1.169.12. Miracle or miracles! X works! I tried re-installing libGLcore from the repositories, and it causes my server to crash again.

Anyone has an idea why libGLcore is now causing my X server to crash?

Some config info, if that can help:

```
jfbilodeau@golbez:~$ uname -r
2.6.24-21-generic
jfbilodeau@golbez:~$ cat /etc/X11/xorg.conf
Section "Module"
	Load		"glx"
	Load		"dri"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"	
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24

	Option		"NoLogo" "True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 0 0
	InputDevice	"Synaptics Touchpad"
EndSection
jfbilodeau@golbez:~$ lsmod
Module                  Size  Used by
af_packet              23812  4 
isofs                  36388  1 
udf                    88612  0 
snd_rtctimer            4640  1 
binfmt_misc            12808  1 
ipv6                  267780  23 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
rfkill_input            5760  0 
vboxdrv                61360  0 
ppdev                  10372  0 
powernow_k8            16704  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
container               5632  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
b43                   144548  0 
rfkill                  8596  3 rfkill_input,b43
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
uvcvideo               58116  0 
led_class               6020  1 b43
compat_ioctl32          2304  1 uvcvideo
input_polldev           5896  1 b43
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
sdhci                  19076  0 
snd_hda_intel         344856  2 
wl                   1073940  0 
mmc_core               51460  1 sdhci
ricoh_mmc               4352  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
ieee80211_crypt         7040  1 wl
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
serio_raw               7940  0 
snd_rawmidi            25760  1 snd_seq_midi
video                  19856  8 
output                  4736  1 video
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
evdev                  13056  8 
psmouse                40336  0 
snd_seq                54224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               7825536  20 
snd_timer              24836  3 snd_rtctimer,snd_pcm,snd_seq
wmi_acer                9644  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                14212  0 
button                  9232  0 
ac                      6916  0 
agpgart                34760  1 nvidia
shpchp                 34452  0 
snd                    56996  17 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                  6656  0 
i2c_core               24832  1 nvidia
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
pcspkr                  4224  0 
ext3                  136840  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sd_mod                 30720  5 
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
ahci                   28548  3 
pata_acpi               8320  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
ssb                    34308  1 b43
ata_generic             8324  0 
forcedeth              51980  0 
ohci1394               33584  0 
pata_amd               14212  1 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  4 ahci,pata_acpi,ata_generic,pata_amd
ohci_hcd               26640  0 
ehci_hcd               37900  0 
scsi_mod              151436  5 sbp2,sd_mod,sg,sr_mod,libata
usbcore               146412  5 uvcvideo,usbhid,ohci_hcd,ehci_hcd
thermal                16796  0 
processor              37384  4 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

Thanks in advance!

---

### Post by jfbilodeau on 2008-09-23
Fixed.

Duh.

Had I taken the time to do a locate on 173.14.12 (version of the NVIDIA driver I installed), I would have solved this ages ago.

Instead, I used strace glxgears, and manually tried to reinstall every lib that it was loading, thinking that I had a corrupt lib.

It turned out that /usr/lib/tls/libnvidia-tls.so.173.14.12 was the culprit.

sudo rm libnvidia-tls.so.173.14.12 

Problem solve!

:oops:

---

