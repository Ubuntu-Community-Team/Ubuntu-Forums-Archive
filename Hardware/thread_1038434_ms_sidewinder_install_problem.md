---
title: "ms sidewinder install problem?"
date: 2009-01-12
forum: Hardware
---

### Post by Nesaskewatch on 2009-01-12
I will start by apologizing for any stupid questions I might ask as I am a wee rook with ubu 8.10.  I am learning however...

I am trying to get my ms sidewinder precision pro joystick to install/work on my system.  I have been through virtually everything I could find by searching and have had no success.  (Joystick totally non functional)  I am trying to use it in Flightgear, but I am thinking I may not even have it installed correctly.  It is plugged into the "gameport" not a USB.  It works on my ms box with flight sim 2004.  I believe the module is installed (I show a sidewinder listed) If I run jscalibrator it is not listed there and I get an error stating it may not be installed.

Any assistance/links would be greatly appreciated!

---

### Post by Nesaskewatch on 2009-01-14
I will try and provide some detail here.  Sorry for being a noob.  MS Sidewinder precision pro plugged into the yellow plug on the soundcard.  SiS onboard chipset.  Ubuntu 8.10 stand alone.  Is there a way to confirm if Ubu is detecting the joystick?  lsmod shows this:

xxxxx@the-desktop:~$ lsmod
Module                  Size  Used by
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
video                  25232  0 
output                 11008  1 video
wmi                    14504  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
evdev                  17696  6 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
serio_raw              13444  0 
psmouse                45200  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_dummy          10884  0 
nvidia               6909268  36 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
button                 14224  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                 10624  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_sis96x             12420  0 
sis_agp                15232  1 
soundcore              15328  1 snd
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
agpgart                42184  2 nvidia,sis_agp
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
i2c_core               31892  2 nvidia,i2c_sis96x
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
pata_sis               18436  2 
ata_generic            12932  0 
sis900                 27904  0 
ohci_hcd               32016  0 
ehci_hcd               43788  0 
libata                178208  3 pata_acpi,pata_sis,ata_generic
mii                    13440  1 sis900
usbcore               149360  3 ohci_hcd,ehci_hcd
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
xxxxx@the-desktop:~$

lspci:

xxxxx@the-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 A-LE (rev a1)
xxxxx@the-desktop:~$ 

Other things I have fooled around with:

xxxxx@the-desktop:~$ jsdemo
bash: jsdemo: command not found
xxxxx@the-desktop:~$ js demo
The program 'js' can be found in the following packages:
 * spidermonkey-bin
 * rhino
Try: sudo apt-get install <selected package>
bash: js: command not found
xxxxx@the-desktop:~$ sudo apt-get install joystick
[sudo] password for xxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
joystick is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xxxxx@the-desktop:~$ listdev
bash: listdev: command not found
xxxxx@the-desktop:~$ list devices
bash: list: command not found
xxxxx@the-desktop:~$ sudo apt-get install joydev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package joydev
xxxxx@the-desktop:~$ sudo apt-get install sidewinder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sidewinder
xxxxx@the-desktop:~$

Am I a complete idiot?  Or just partially?  I am at my wits end.  End of me tether.  Fit to be tied.  Fixin' to bust a nut.  Ready to swing for it.

Any help is greatly appreciated!

---

### Post by sstakes1 on 2009-05-04
I know its been months after the original post. But I see no gameport module loaded. Can you try
```

sudo modprobe gameport; dmesg
```

and see what it says.

---

