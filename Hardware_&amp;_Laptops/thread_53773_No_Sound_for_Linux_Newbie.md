---
title: "No Sound for Linux Newbie"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by JohnTzu on 2005-08-02
Hello, 

I'm New to Linux, and really have no clue what I'm doing, I just installed the latest 
version of Kubuntu, and I have no sound whatsoever,here are my hardware specs,

Sound Driver 3.8.1a-980706 (ALSA compliant v1.06 emulation code)
Kernel: Linux Ubuntu 2.6.10-5-386#1 Tue apr 5 12:12:40 UTC 2005 1686
Config options O

Installed Drivers
Type10: Alsa emulation
Card Config: Via 8235 with ALC200/200 at 0xe800 IRQ22
Audio Device: Via 8235 (Duplex)
No Synth Devise enabled
no midi device enabled

 Sys . Timer  7
Mixer: RealTEK ALC 200/200 Rev 0


LSPCI results:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridg                                            e
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C                                            /8139C+ (rev 10)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                            oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                            oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                            oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82                                            3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8                                            237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200                                             SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Se                                            condary) (rev 01)
ubuntu@ubuntu:~$


lsmod results

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridg                                            e
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C                                            /8139C+ (rev 10)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                            oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                            oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                            oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82                                            3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8                                            237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200                                             SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Se                                            condary) (rev 01)
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
radeon                 69760  1
drm                    59412  2 radeon
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_powersave       1920  0
cpufreq_ondemand        6172  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
container               4608  0
button                  6800  0
battery                10244  0
ac                      4996  0
ipv6                  229504  6
snd_via82xx            25248  1
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
via_ircc               24340  0
irda                  168000  1 via_ircc
crc_ccitt               2176  1 irda
pci_hotplug            30512  0
via_agp                 9216  1
agpgart                31784  2 drm,via_agp
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
capability              5000  0
tsdev                   7488  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
lp                     10792  0
dm_snapshot            16540  1
dm_mod                 53116  4 dm_snapshot
loop                   14728  0
cloop                  13536  1
af_packet              20744  0
8139too                24320  0
8139cp                 19200  0
mii                     4736  2 8139too,8139cp
nls_cp437               5888  1
isofs                  33720  1
ide_cd                 38532  1
cdrom                  36508  1 ide_cd
ide_disk               18176  1
ide_generic             1664  0
pdc202xx_new            8576  0
aec62xx                 7296  0
alim15x3               11404  0
amd74xx                13340  0
atiixp                  6160  0
cmd64x                 11292  0
cs5520                  4992  0
cs5530                  5504  0
cy82c693                4868  0
generic                 4480  0
hpt34x                  5376  0
ns87415                 4680  0
opti621                 4612  0
pdc202xx_old           10624  0
piix                    9988  0
rz1000                  3072  0
sc1200                  7296  0
serverworks             8840  0
siimage                11520  0
sis5513                15112  0
slc90e66                5888  0
triflex                 4224  0
trm290                  4612  0
floppy                 54864  0
usb_storage            64064  0
scsi_mod              119936  1 usb_storage
parport_pc             34372  1
parport                33480  2 lp,parport_pc
fbcon                  34048  71
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vga16fb                12488  1
vgastate                8576  1 vga16fb
vesafb                  6948  0
cfbcopyarea             3968  2 vga16fb,vesafb
cfbimgblt               3072  2 vga16fb,vesafb
cfbfillrect             3584  2 vga16fb,vesafb
usbserial              28136  0
usbhid                 29376  0
usbkbd                  6784  0
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
via82cxxx              12956  1
ide_core              118988  28 ide_cd,ide_disk,ide_generic,pdc202xx_new,aec62xx,alim15x3,amd74xx,atiixp,cmd64x,cs5520,cs5530,cy82c693,generic,hpt34x,ns87415,opti621,pdc202xx_old,piix,rz1000,sc1200,serverworks,siimage,sis5513,slc90e66,triflex,trm290,usb_storage,via82cxxx
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  7 usb_storage,usbserial,usbhid,usbkbd,ehci_hcd,uhci_hcd
evdev                   9088  0
unix                   26164  264
ubuntu@ubuntu:~$

I really want to say goodbye to Microsoft for good, please help me to resolve this issue.

JohnTzu

---

### Post by Lord Illidan on 2005-08-02
Try using alsamixer because it could be that your volume has been muted..so as not to blast you with sound..

```
alsamixer
```

---

### Post by JohnTzu on 2005-08-02
Done, Still Nothing, is it worth mention that I had the same problem in Linspire, also unresolved?

Johntzu

---

### Post by heimo on 2005-08-02
I second Lord Illidan. Your lspci and lsmod look fine. Use alsamixer to turn up master and pcm channels, check that no channel is muted (toggle with m). After setting levels, run [i]sudo alsactl store

EDIT: posted before noticed your previous post
[/i]

---

### Post by Lord Illidan on 2005-08-02
Is your soundcard internal? Is it enabled from the BIOS?

---

### Post by JohnTzu on 2005-08-02
Ran sudo alsactl store, after messing with mixer again, still nothing...
Could it have something to do with the fact that I'm using the Live version?

JohnTzu

---

### Post by Lord Illidan on 2005-08-02
> Ran sudo alsactl store, after messing with mixer again, still nothing...
Could it have something to do with the fact that I'm using the Live version?

Did you install Kubuntu, or is it a live CD u are using?

---

### Post by JohnTzu on 2005-08-02
[QUOTE=Lord Illidan]Is your soundcard internal? Is it enabled from the BIOS?[/QUOTE]

The Sound card is an On board Via 8235


And sound worked in windows up until the crash that broke the camel's back.
So I assume it's still enabled in the Bios

JohnTzu

---

### Post by JohnTzu on 2005-08-02
Still using Live at the moment....



JohnTzu

---

### Post by Lord Illidan on 2005-08-02
Make sure it is enabled in the bios, that all the cables are connected, that the speakers are on, etc. This way we can be sure that it is a software problem, not a hardware problem. Better be sure, than just rely on an assumption.

---

### Post by JohnTzu on 2005-08-02
Enabled in BIOS, but reads as VIA 3058, AC97 Audio, which is different from what I had above in system info.

All cables are where they should be, and speakers are powered up.


JohnTzu

---

### Post by unghiu on 2005-08-02
Hi!

The same problem as above for me. no sound, whatsoever. ](*,)

---

### Post by Lord Illidan on 2005-08-02
Try disabling the sound system in the Control Center. This will eliminate the noises and beeps of KDE, but should allow you to hear music files, etc, on your music players, sounds in games, etc.

Or try

```
killall esd
```

before you play music...or play a game, or whatever..

---

### Post by JohnTzu on 2005-08-05
Hello again.... After not being able to resolve this sound issue(see above) I went out and bought a Creative, SBlive 24 bit sound card and installed it....powered up the machine, disabled onboard in BIOS, and upon GUI startup, recieved this error message.

error while initiating sound server
Device/dev/dsp can't be opened
no such file or directory
sound server will continue using null output device

lspci rendered this:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:00:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)


and alsamixer gave me this:

alsamixer: function snd_ctl_open failed for default: No such file or directory

killall esd rendered: 

ubuntu@ubuntu:~$ killall esd
esd: no process killed


I also now have a red X over the volume icon in my system tray that wasn't present before.


Sorry to keep bothering you all with this, but I NEED sound, it's a non negotiable, and I really don't want to go back to windows.


Thanks again

JohnTzu

---

### Post by JohnTzu on 2005-08-05
oh, and  lsmod gave me:

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
radeon                 69760  1
drm                    59412  2 radeon
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_powersave       1920  0
cpufreq_ondemand        6172  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
container               4608  0
button                  6800  0
battery                10244  0
ac                      4996  0
ipv6                  229504  6
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
via_ircc               24340  0
irda                  168000  1 via_ircc
crc_ccitt               2176  1 irda
pci_hotplug            30512  0
via_agp                 9216  1
agpgart                31784  2 drm,via_agp
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
capability              5000  0
tsdev                   7488  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
lp                     10792  0
dm_snapshot            16540  1
dm_mod                 53116  4 dm_snapshot
loop                   14728  0
cloop                  13536  1
af_packet              20744  0
8139too                24320  0
8139cp                 19200  0
mii                     4736  2 8139too,8139cp
nls_cp437               5888  1
isofs                  33720  1
ide_cd                 38532  1
cdrom                  36508  1 ide_cd
ide_disk               18176  1
ide_generic             1664  0
pdc202xx_new            8576  0
aec62xx                 7296  0
alim15x3               11404  0
amd74xx                13340  0
atiixp                  6160  0
cmd64x                 11292  0
cs5520                  4992  0
cs5530                  5504  0
cy82c693                4868  0
generic                 4480  0
hpt34x                  5376  0
ns87415                 4680  0
opti621                 4612  0
pdc202xx_old           10624  0
piix                    9988  0
rz1000                  3072  0
sc1200                  7296  0
serverworks             8840  0
siimage                11520  0
sis5513                15112  0
slc90e66                5888  0
triflex                 4224  0
trm290                  4612  0
floppy                 54864  0
usb_storage            64064  0
scsi_mod              119936  1 usb_storage
parport_pc             34372  1
parport                33480  2 lp,parport_pc
fbcon                  34048  71
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vga16fb                12488  1
vgastate                8576  1 vga16fb
vesafb                  6948  0
cfbcopyarea             3968  2 vga16fb,vesafb
cfbimgblt               3072  2 vga16fb,vesafb
cfbfillrect             3584  2 vga16fb,vesafb
usbserial              28136  0
usbhid                 29376  0
usbkbd                  6784  0
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
via82cxxx              12956  1
ide_core              118988  28 ide_cd,ide_disk,ide_generic,pdc202xx_new,aec62xx,alim15x3,amd74xx,atiixp,cmd64x,cs5520,cs5530,cy82c693,generic,hpt34x,ns87415,opti621,pdc202xx_old,piix,rz1000,sc1200,serverworks,siimage,sis5513,slc90e66,triflex,trm290,usb_storage,via82cxxx
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  7 usb_storage,usbserial,usbhid,usbkbd,ehci_hcd,uhci_hcd
evdev                   9088  0
unix                   26164  288
ubuntu@ubuntu:~$

---

### Post by JohnTzu on 2005-08-05
two more things..., when restarting sound system from control panel, I get this message, 

Error while initializing the sound driver:
device: default can't be opened for playback (No such file or directory)
The sound server will continue, using the null output device.


and when running: uaplay /usr/share/sonds/login.wav,
I get this...

ubuntu@ubuntu:~$ uaplay /usr/share/sonds/login.wav
ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_card_driver return                             ed error: No such file or directory
ALSA lib confmisc.c:387:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_concat returned er                             ror: No such file or directory
ALSA lib confmisc.c:945:(snd_func_refer) error evaluating name
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_refer returned err                             or: No such file or directory
ALSA lib conf.c:3932:(snd_config_expand) Evaluate error: No such file or directo                             ry
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:508: audio open error: No such file or directory
ubuntu@ubuntu:~$

---

### Post by garydevitt on 2005-08-16
Hey, having the same problem here, ive got an audigy soundblaster 2, its coming up under lspci and all volumes levels are up full whack yet im getting no sound....
Any help?

---

### Post by garydevitt on 2005-08-16
ahh its ok, just configured my player to use /dev/dsp1 instead!

---

### Post by argosreality on 2005-08-16
I'm having the same problem. I have an SB Live! 7.1 card which apparently is actually an Audigy based chipset rather than the Live! chipset (emku701 (live) vs. 702 (audigy)). I've done all the steps listed in the major audio FAQ's on here but I STILL get the same errors taht the parent posted here. My Device Manager shows my card, but apparently the rest of the system doesn't even see it. I tried adding the drivers as kernel modules but even that didnt work.

I've gotten Ubuntu configured otherwise exactly as I want it and its vastly better than my WinXP install. Sadly, sound is literally the only thing I need left. My onboard nForce 2 (realtek) chipset worked fine if only for 2.1 channels but I really want my Logitech z-5300 to work (5.1).

Any ideas?

If ya need more details just let me know

---

