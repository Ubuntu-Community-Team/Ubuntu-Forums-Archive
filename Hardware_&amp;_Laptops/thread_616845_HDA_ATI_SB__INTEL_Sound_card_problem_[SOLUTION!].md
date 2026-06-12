---
title: "HDA ATI SB / INTEL Sound card problem [SOLUTION!]"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by Donny K. on 2007-11-18
Hi people,

It seems that many people are struggling with the HDA ATI or INTEL sound card/chip. Especially laptop users seem to have different problems. Hearing no sound from their speakers but only with their headphones. Or the other way around, no jack sensitivity or only hearing sound from their headphones and not trough the speakers. And, of course the worst kind, not having any sound at all.

Many forums are giving the 3stack of 6stack solution which (partially) works for some people. 
(Changing or adding the following sentence: **options snd-hda-intel model=3stack** ) into the **/etc/modprobe.d/alsa-base** file.

But the HDA soundcards seem to be complexer than that. There are a lot of different HDA cards with their own set of "rules" To tackle this problem, you have to find out what type of card is in your computer. you can check that by typing: **cat /proc/asound/card0/codec#* | grep Codec** (or if that fails : **aplay -l** )
The output will contain the exact type your your card or chip. For example: "Code:ALC861VD/660VD"

Now that you know this, you can look up that type in the list posted below:

 Model name Description
---------- -----------
ALC880
3stack 3-jack in back and a headphone out
3stack-digout 3-jack in back, a HP out and a SPDIF out
5stack 5-jack in back, 2-jack in front
5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
6stack 6-jack in back, 2-jack in front
6stack-digout 6-jack with a SPDIF out
w810 3-jack
z71v 3-jack (HP shared SPDIF)
asus 3-jack (ASUS Mobo)
asus-w1v ASUS W1V
asus-dig ASUS with SPDIF out
asus-dig2 ASUS with SPDIF out (using GPIO2)
uniwill 3-jack
fujitsu Fujitsu Laptops (Pi1536)
F1734 2-jack
lg LG laptop (m1 express dual)
lg-lw LG LW20/LW25 laptop
tcl TCL S700
clevo Clevo laptops (m520G, m665n)
test for testing/debugging purpose, almost all controls can be
adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y
auto auto-config reading BIOS (default)

ALC260
hp HP machines
hp-3013 HP machines (3013-variant)
fujitsu Fujitsu S7020
acer Acer TravelMate
will Will laptops (PB V7900)
replacer Replacer 672V
basic fixed pin assignment (old default model)
auto auto-config reading BIOS (default)

ALC262
fujitsu Fujitsu Laptop
hp-bpc HP xw4400/6400/8400/9400 laptops
hp-bpc-d7000 HP BPC D7000
benq Benq ED8
benq-t31 Benq T31
hippo Hippo (ATI) with jack detection, Sony UX-90s
hippo_1 Hippo (Benq) with jack detection
sony-assamd Sony ASSAMD
basic fixed pin assignment w/o SPDIF
auto auto-config reading BIOS (default)

ALC268
3stack 3-stack model
toshiba Toshiba A205
acer Acer laptops
auto auto-config reading BIOS (default)

ALC662
3stack-dig 3-stack (2-channel) with SPDIF
3stack-6ch 3-stack (6-channel)
3stack-6ch-dig 3-stack (6-channel) with SPDIF
6stack-dig 6-stack with SPDIF
lenovo-101e Lenovo laptop
auto auto-config reading BIOS (default)

ALC882/885
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
arima Arima W820Di1
targa Targa T8, MSI-1049 T8
asus-a7j ASUS A7J
asus-a7m ASUS A7M
macpro MacPro support
mbp3 Macbook Pro rev3
imac24 iMac 24'' with jack detection
w2jc ASUS W2JC
auto auto-config reading BIOS (default)

ALC883/888
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
3stack-6ch 3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
6stack-dig-demo 6-jack digital for Intel demo board
acer Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
acer-aspire Acer Aspire 9810
medion Medion Laptops
medion-md2 Medion MD2
targa-dig Targa/MSI
targa-2ch-dig Targs/MSI with 2-channel
laptop-eapd 3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
lenovo-101e Lenovo 101E
lenovo-nb0763 Lenovo NB0763
lenovo-ms7195-dig Lenovo MS7195
haier-w66 Haier W66
6stack-hp HP machines with 6stack (Nettle boards)
3stack-hp HP machines with 3stack (Lucknow, Samba boards)
auto auto-config reading BIOS (default)

ALC861/660
3stack 3-jack
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack with SPDIF I/O
3stack-660 3-jack (for ALC660)
uniwill-m31 Uniwill M31 laptop
toshiba Toshiba laptop support
asus Asus laptop support
asus-laptop ASUS F2/F3 laptops
auto auto-config reading BIOS (default)

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

CMI9880
minimal 3-jack in back
min_fp 3-jack in back, 2-jack in front
full 6-jack in back, 2-jack in front
full_dig 6-jack in back, 2-jack in front, SPDIF I/O
allout 5-jack in back, 2-jack in front, SPDIF out
auto auto-config reading BIOS (default)

AD1882
3stack 3-stack mode (default)
6stack 6-stack mode

AD1884
N/A

AD1981
basic 3-jack (default)
hp HP nx6320
thinkpad Lenovo Thinkpad T60/X60/Z60
toshiba Toshiba U205

AD1983
N/A

AD1984
basic default configuration
thinkpad Lenovo Thinkpad T61/X61

AD1986A
6stack 6-jack, separate surrounds (default)
3stack 3-stack, shared surrounds
laptop 2-channel only (FSC V2060, Samsung M50)
laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
ultra 2-channel with EAPD (Samsung Ultra tablet PC)

AD1988
6stack 6-jack
6stack-dig ditto with SPDIF
3stack 3-jack
3stack-dig ditto with SPDIF
laptop 3-jack with hp-jack automute
laptop-dig ditto with SPDIF
auto auto-config reading BIOS (default)

Conexant 5045
laptop Laptop config
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

Conexant 5047
laptop Basic Laptop config
laptop-hp Laptop config for some HP models (subdevice 30A5)
laptop-eapd Laptop config with EAPD support
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

STAC9200
ref Reference board
dell-d21 Dell (unknown)
dell-d22 Dell (unknown)
dell-d23 Dell (unknown)
dell-m21 Dell Inspiron 630m, Dell Inspiron 640m
dell-m22 Dell Latitude D620, Dell Latitude D820
dell-m23 Dell XPS M1710, Dell Precision M90
dell-m24 Dell Latitude 120L
dell-m25 Dell Inspiron E1505n
dell-m26 Dell Inspiron 1501
dell-m27 Dell Inspiron E1705/9400

STAC9205/9254
ref Reference board
dell-m42 Dell (unknown)
dell-m43 Dell Precision
dell-m44 Dell Inspiron

STAC9220/9221
ref Reference board
3stack D945 3stack
5stack D945 5stack + SPDIF
intel-mac-v1 Intel Mac Type 1
intel-mac-v2 Intel Mac Type 2
intel-mac-v3 Intel Mac Type 3
intel-mac-v4 Intel Mac Type 4
intel-mac-v5 Intel Mac Type 5
macmini Intel Mac Mini (equivalent with type 3)
macbook Intel Mac Book (eq. type 5)
macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
macbook-pro Intel Mac Book Pro 2nd generation (eq. type 3)
imac-intel Intel iMac (eq. type 2)
imac-intel-20 Intel iMac (newer version) (eq. type 3)
dell-d81 Dell (unknown)
dell-d82 Dell (unknown)
dell-m81 Dell (unknown)
dell-m82 Dell XPS M1210

STAC9202/9250/9251
ref Reference board, base config
m2-2 Some Gateway MX series laptops
m6 Some Gateway NX series laptops
pa6 Gateway NX860 series

STAC9227/9228/9229/927x
ref Reference board
3stack D965 3stack
5stack D965 5stack + SPDIF
dell-3stack Dell Dimension E520

STAC9872
vaio Setup for VAIO FE550G/SZ110
vaio-ar Setup for VAIO AR


As you can see, every type / chipset has several possibilities. Type the first word from the list in **/etc/modprobe.d/alsa-base** or (if that one does not exist) **/etc/modprobe.conf**  Just try them until you've found the right match.  ( you can edit these files with your favourite text editor, for example: **sudo gedit /etc/modprobe.d/alsa-base** or **sudo gedit /etc/modprobe.conf** )

For example: If **cat /proc/asound/card0/codec#* | grep Codec**  or  : **aplay -l ** return "Realtek ALC260" , Look under "ALC260" in the list and add the following line in your **/etc/modprobe.d/alsa-base** or (if that one does not exist or is empty) **/etc/modprobe.conf** 

options snd-hda-intel model=hp

Reboot and check if your sound if working. [COLOR="Red"]Do not forget to check your mixer to see if (new) channels are muted.[/COLOR] If that one doesn't work or partially works, try another one in the list eg: 
options snd-hda-intel model=base
options snd-hda-intel model=will
or
options snd-hda-intel model=acer

That's all there is to it! I hope this forum post will help you as good as the info, gathered on the internet by me, in combination with days/weeks/months of testing and searching by me. I would like to know this this post solved your problems. Please let me know by posting your result in this thread. Thank you for your time, good luck and enjoy your sound!

Donny K. (Linux Freak)

---

### Post by LarryEdwards on 2007-11-26
I have just installed 7.10 to a Vista Toshiba laptop.  In Vista the sound works fine.  In Ubuntu there is no sound.  The command   cat /proc/asound/card0/codec#* | grep Codec    returned
Codec:  Generic 11c1 Si3054
Codec:  Generic ffff ID ffff
Any ideas?

---

### Post by portotrix on 2007-11-27
I think the  Si3054 interfaces is a MODEM
My aplay -l in a Packard Bell easynote laptop returns:

Codec: Analog Devices AD1986A
Codec: Motorola Si3054

and this typing cat /proc/asound/card0/codec#* | grep Codec

card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by EugeneK on 2007-12-01
I've been looking for exactly this list. Thanks for the post.

---

### Post by Aristocrates on 2007-12-08
Unfortunately, this still doesn't solve my problem - I've changed the model several times and don't get even a trace of sound output, whether with headphones, nothing (laptop speakers), or external speakers. 

I've attached the output from running the "alsa-info.sh" script.

My computer is an Asus F7F dual boot with Windows Vista and sound works in Vista and in the Asus boot screen (it makes a sound), so the hardware isn't faulty.  I just don't understand where in the settings I've gone wrong!

Any help would be appreciated.

---

### Post by Aristocrates on 2007-12-08
Here's the output:

> !!################################
!!ALSA Information Script v 0.4.34
!!################################

!!Script ran on: Sat Dec  8 21:12:58 GMT 2007


!!Linux Distribution
!!------------------

Ubuntu 7.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 7.04"


!!Kernel Information
!!------------------

Kernel release:    2.6.20-16-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.14rc1
Library version:    
Utilities version:  1.0.13


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfeb3c000 irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 1043:1339


!!Modprobe options (Sound related)
!!--------------------------------

snd-bt87x: index=-2
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-hda-intel: model=6stack-dig=digout


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
enable : N
id : <NULL>
index : -1
model : 6stack-dig=digout
position_fix : 0
probe_mask : -1
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------

Codec: Realtek ALC660-VD
Address: 0
Vendor Id: 0x10ec0660
Subsystem Id: 0x10431339
Revision Id: 0x100001
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x34 0x34]
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x09, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x0a 0x0a] [0x0b 0x0b] [0x19 0x19] [0x00 0x00] [0x19 0x19] [0x1f 0x1f]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1c 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081003c: IN OUT HP EAPD Detect
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0810034: IN OUT EAPD Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0834: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0834: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x01 0x01]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x081734: IN OUT Detect
  Pin Default 0x01a1183f: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x24: IN
  Connection: 1
     0x0e
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x01 0x01] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x08173c: IN OUT HP Detect
  Pin Default 0x99a30130: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x24: IN
  Connection: 2
     0x0c* 0x0f
Node 0x1a [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0834: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 1
     0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x08173c: IN OUT HP Detect
  Pin Default 0x0121101f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0xc0: OUT HP
  Connection: 2
     0x0c* 0x0f
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x598301f0: [N/A] Line In at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x99430120: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x00 0x00] [0x00 0x00] [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x26 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: Motorola Si3054
Address: 1
Vendor Id: 0x10573055
Subsystem Id: 0x10431316
Revision Id: 0x100700


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116, 8 2007-12-08 21:06 /dev/snd/controlC0
crw-rw---- 1 root audio 116, 7 2007-12-08 21:06 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 6 2007-12-08 21:06 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 5 2007-12-08 21:06 /dev/snd/pcmC0D6c
crw-rw---- 1 root audio 116, 4 2007-12-08 21:06 /dev/snd/pcmC0D6p
crw-rw---- 1 root audio 116, 3 2007-12-08 21:06 /dev/snd/seq
crw-rw---- 1 root audio 116, 2 2007-12-08 21:06 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 52 [81%] [-12.00dB] [on]
  Front Right: Playback 52 [81%] [-12.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 11 [35%] [-18.00dB] [on]
  Front Right: Playback 11 [35%] [-18.00dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%]
  Front Right: 1 [33%]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 10 [32%] [-19.50dB] [on]
  Front Right: Playback 10 [32%] [-19.50dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 1 [33%]
  Front Right: 1 [33%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-13.50dB] [on]
  Front Right: Capture 0 [0%] [-13.50dB] [on]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Line'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]


!!All Loaded Modules
!!------------------

Module
i915
drm
binfmt_misc
rfcomm
l2cap
bluetooth
ppdev
cpufreq_userspace
cpufreq_stats
cpufreq_conservative
cpufreq_powersave
cpufreq_ondemand
freq_table
tc1100_wmi
dev_acpi
sony_acpi
pcc_acpi
container
dock
video
battery
asus_acpi
backlight
ac
sbs
i2c_ec
button
ipv6
nls_utf8
ntfs
nls_iso8859_1
nls_cp437
vfat
fat
michael_mic
arc4
ecb
blkcipher
ieee80211_crypt_tkip
sbp2
parport_pc
lp
parport
fuse
joydev
snd_hda_intel
snd_hda_codec
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
dvb_usb_dtt200u
dvb_usb
ipw3945
uvcvideo
snd_seq
dvb_core
videodev
v4l1_compat
dvb_pll
v4l2_common
snd_timer
snd_seq_device
i2c_core
ieee80211
ieee80211_crypt
snd
soundcore
serio_raw
sdhci
mmc_core
snd_page_alloc
pcspkr
af_packet
psmouse
shpchp
pci_hotplug
intel_agp
agpgart
iTCO_wdt
iTCO_vendor_support
tsdev
evdev
ext3
jbd
mbcache
usb_storage
sg
sr_mod
cdrom
sd_mod
generic
usbhid
hid
libusual
ata_piix
ehci_hcd
r8169
ohci1394
ieee1394
ata_generic
libata
scsi_mod
uhci_hcd
usbcore
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
vesafb
capability
commoncap

---

### Post by PROCYYON on 2008-01-10
im here

AD1986A
6stack 6-jack, separate surrounds (default)
3stack 3-stack, shared surrounds
laptop 2-channel only (FSC V2060, Samsung M50)
laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
ultra 2-channel with EAPD (Samsung Ultra tablet PC)

mine is lenovo. What i should type now?

---

### Post by vervelover on 2008-01-15
I'm with a Medion RIM 2150, Realtek Alc880, no solution seems to work, only very low sound from headphones out.. anyone can help?

---

### Post by memm on 2008-01-18
I have a Gateway T-1616 running 64-bit Gutsy,

cat /proc/asound/card0/codec#* | grep Codec

gave 

Codec: SigmaTel STAC9205
Codec: Generic 11c1 Si3054

for me. Then adding the line 

options snd-hda-intel model=dell-m42

to /etc/modprobe.d/alsa-base solved my headphones problem.

Thank you!

---

### Post by tokker73 on 2008-01-19
Hi, I have an Acer Travelmate 4720 laptop.

Your method worked perfectly and allows me to give Ubuntu a second chance (I wouldn't start using it unless something basic like my headphones work...). Thanks a lot for the clear and simple explanation which is not always the case on these forums...

Keep up the good work.

Tom

---

### Post by timsath on 2008-01-20
> root@tim-laptop:/home/tim# hwinfo --sound
19: PCI 07.0: 0403 Audio device                                 
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_10de_55c
  Unique ID: M71A.fmA23IIoz13
  SysFS ID: /devices/pci0000:00/0000:00:07.0
  SysFS BusID: 0000:00:07.0
  Hardware Class: sound
  Model: "Hewlett-Packard Company Audio device"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x055c 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30ea 
  Revision: 0xa1
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf6480000-0xf6483fff (rw,non-prefetchable)
  IRQ: 21 (312 events)
  Module Alias: "pci:v000010DEd0000055Csv0000103Csd000030EAbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

I posted a separate message in this forum about this same problem...does anyone know what I need to add to my conf files??

Thanks!

---

### Post by timsath on 2008-01-20
Does anyone know the flags for a Conexant 5051?

---

### Post by gutsy goober on 2008-01-20
Thank you.. this made the headphones on my sony fz laptop work perfectly.

---

### Post by d3ngar on 2008-01-21
I'm getting very confused here:

I have no sound at all and have been spending WAY too much time on this already. Now I'm trying the forums and IRC.

I read on the Alsa site that the ICH8 isn't supported and that there is NO driver for that card (see here: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)). 

However, there are about a million workarounds which I unfortunately all tried without result.
The only alternative that I still haven't tried is upgrading the Kernel to 2.6.23, which I really don't want to do.

Now here is my card:

lspci -v:
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1339
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at febf8000t (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

 cat /proc/asound/card0/codec#* | grep Codec
> 
Codec: Realtek ALC660-VD
Codec: Motorola Si3054

alsamixer tells me that it identified the card correctly and that it is in fact using it, I have the sound mixer icon in the task-bar and I don't get an error message,

It's highly confusing and would appreciate your help.

Some additional resources that I already checked:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

[http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem) This latest one actually led me to believe that the card group is simply not supported...

And yes, I'm running on a Asus F3Sr, Ubuntu 7.10 | Kernel 2.6.22.14.21 (rumor has it that upgrading the Kernel really helps - any comments to this?)

Thanks,

Chris

---

### Post by timsath on 2008-01-21
> **d3ngar said:**
> I'm getting very confused here:

I have no sound at all and have been spending WAY too much time on this already. Now I'm trying the forums and IRC.

I read on the Alsa site that the ICH8 isn't supported and that there is NO driver for that card (see here: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)). 

However, there are about a million workarounds which I unfortunately all tried without result.
The only alternative that I still haven't tried is upgrading the Kernel to 2.6.23, which I really don't want to do.

Now here is my card:

lspci -v:


 cat /proc/asound/card0/codec#* | grep Codec


alsamixer tells me that it identified the card correctly and that it is in fact using it, I have the sound mixer icon in the task-bar and I don't get an error message,

It's highly confusing and would appreciate your help.

Some additional resources that I already checked:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

[http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem) This latest one actually led me to believe that the card group is simply not supported...

And yes, I'm running on a Asus F3Sr, Ubuntu 7.10 | Kernel 2.6.22.14.21 (rumor has it that upgrading the Kernel really helps - any comments to this?)

Thanks,

Chris

Not to be insulting, but did you unmute your channels?  I'm sure you did...but sometimes...its the simple things we forget :)  Run alsamixer then press M to unmute the channels.

---

### Post by mchaggis on 2008-01-22
I followed a lot of the howtos etc and nothing worked for me:

Alienware M9750
Codec: Realtek ALC885
Codec: Generic 11c1 Si3054

(aplay -l says it's ALC882 though)

I downloaded the 4.07b linux drivers from Realtek's site ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false))

At first there was no change. Now at this point, I should mention that my flavour of problem with this driver/card is that I get sound out of the headphones and all output jacks, but nothing from the built in speakers.

I then checked the alsa-kernel/Documentation/ALSA-Configuration.txt file and decided this time to go through every ALC882/885 option have had some success:

No sound:
 * mbp3          Macbook Pro rev3
 * macpro        MacPro support

Headphones Only:
 * auto          auto-config reading BIOS (default)
 * imac24        iMac 24'' with jack detection

All Speakers Work
 * 3stack-dig    3-jack with SPDIF I/O
 * 6stack-dig    6-jack digital with SPDIF I/O
 * arima         Arima W820Di1
 * targa         Targa T8, MSI-1049 T8
 * asus-a7j      ASUS A7J - 
 * asus-a7m      ASUS A7M
 * w2jcASUS     W2JC

So I am now very happy as after 6months of having this laptop, I now have sound working.

My finaly issue with sound now, is that when I plug headphones in, the back speaker/subwoofer is muted, the headphones play no sound and the front continue to play sound, so if anyone can help out with the final problem it'll be much appreciated (although I have now written a script to switch back to auto when I want headphones)

Hope this helps others

---

### Post by d3ngar on 2008-01-22
> 
I then checked the alsa-kernel/Documentation/ALSA-Configuration.txt file and decided this time to go through every ALC882/885 option have had some success:


Sorry, what do you mean exactly by going through the ALC(blah) options?
I have been there and I know you should specify your model so you decide what exact variant of that card you are using, but where exactly is that MODEL???

I have been confused with this before and I used:
```
 options snd-intel8x0 XXXX 
``` in my etc/modprobe.d/alsa-base
But I'm not sure I used the correct variable for XXXX, can you tell me how you tried yours?

I will try to get the realtek stuff later and will post a reply.

Thanks,

Chris

---

### Post by mchaggis on 2008-01-22
> **d3ngar said:**
> 
I have been confused with this before and I used:
```
 options snd-intel8x0 XXXX 
``` in my etc/modprobe.d/alsa-base
But I'm not sure I used the correct variable for XXXX, can you tell me how you tried yours?


The line I have in my alsa-base file is:

```
options snd-hda-intel model=6stack-dig
```

I do have one more problem now in that the microphone now does not work, although I have solved the headphone issue. From the volume applet I went to switches and if I uncheck headphones the speakers turn off, but I can have headphones plugged in, not to the headphone jack, but the center jack so am making some progress :-S

---

### Post by d3ngar on 2008-01-22
OK, here we go again: I have removed all alsa stuff after getting the realtek drivers from their website. I compiled the packages as suggested in the install AND: no luck!

However, I can see that the update for alsa finally worked, coz alsamixer tells me it's running 1.0.15.

The other strange thing is the install readme file itself (here attached) it seems that it seems that also my card is listed in the beginning (it's the Realtek ALC660VD), it's not mentioned in the bloody section 4! What's that all about???

Well, what can I do? Any further ideas?

Thanks,

Chris

---

### Post by Master_Z on 2008-01-24
I have the Sigmatel STAC9200 in my Gateway MT3705. I tried all of those under STAC9200. None worked. Any other solution?

---

### Post by d3ngar on 2008-01-25
OK, I tried all relevant models for this Realtek card (it's a VLC660VD), none of them worked. I found that there is a bug logged, so I guess I need to wait for a fix...

here is the link to the bug, so you can check if it's still open:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174203](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/174203)

Best of luck and keep the people posted!

Tansk

---

### Post by th3t1nm4n on 2008-01-25
Hello, I have a SigmaTel 92HD71B Dual SPDF and haven't been able to get it to work. Any help?
I have a thread about it here:

[http://ubuntuforums.org/showthread.php?t=676550](http://ubuntuforums.org/showthread.php?t=676550)

---

### Post by pwn on 2008-01-28
```
wotanist@Renderman:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel CXD9872AKD
Codec: Conexant ID 2c06
Codec: Realtek ALC262
wotanist@Renderman:~$
```

```

wotanist@Renderman:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wotanist@Renderman:~$ 
```

I'm not sure which of the ones in the list to use since mine is a Sony Vaio AR590E. There is a headphone out, Mic, and Optical Out, and an Internal Mic

I get audio through the internal speakers. It doesn't detect a headphone plugged in. I tried the ones under ALC262 but they didn't work. How do I know if my sound card really is ALC262? Maybe it wasn't detected correctly? The optical out doesn't work either.

They didn't make any difference.

Following is my original alsa-base file. There was no "options snd-hda-intel ..." before this
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

---

### Post by redcrayon on 2008-01-30
Finally after hours and hours trying to get alsa to detect when headphones are plugged in :D :D :D
THANK YOU !

******For anyone using an MSI notebook having sound issues definately check out this post.
try adding targa-dig or targa-2ch-dig... worked for me.

---

### Post by mchaggis on 2008-02-07
Ok, now I'm confused! There was a linux-headers update on Tuesday, no no sound again. Well I say no sound, I have the annoying system beep and that's it.

If I try and run alsamixer I get:
```
alsamixer: function snd_ctl_open failed for default: No such device
```

Very frustrating, any suggestions?

---

### Post by mchaggis on 2008-02-07
it seems running the realteak installer again solved the prob.

Would be nice through for this to get resolved with out this happening

---

### Post by lomaxfalconer on 2008-02-09
i have a Realtek ALC882 on a ASUS A7M

after the last upgrade my sound is failing 50% of the time.

i have to restart a few times to get it to work, it used to have no problems.

it started to happen right after the  linux-headers update on Tuesday

any solutions?


i am a noob so i would need a very simple step by step

thanks

---

### Post by pwn on 2008-02-16
Still no luck with this

---

### Post by augied on 2008-02-16
No luck here.  Toshiba L35-S2174 with ALC861VD
Edit: Worked with 6stack-digout

---

### Post by black-flag on 2008-02-23
no luck for fujitsu AMILO pi1505 & Realtek ALC861 under ubuntu 7.10
> 
superuser@b-f:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Motorola Si3054
Codec: Realtek ALC861
superuser@b-f:~$

ok i tested all models of ALC861/660 and ALC861VD/660VD one after one with rebooting  but always my mic don't working 
> 
options snd-hda-intel model=3stack
options snd-hda-intel model=3stack-dig
options snd-hda-intel model=6stack-dig
options snd-hda-intel model=uniwill-m31
options snd-hda-intel model=lenovo
options snd-hda-intel model=dallas
options snd-hda-intel model=hp
options snd-hda-intel model=uniwill-m31
options snd-hda-intel model=asus
options snd-hda-intel model=asus-laptop
options snd-hda-intel model=auto
options snd-hda-intel model=3stack-660


---

### Post by Travelin_Light on 2008-02-23
Worked for a Lenovo 3000 n200

Codec: Realtek ALC861-VD
Codec: Generic 11c1 ID 1040

Added:
options snd-hda-intel model=lenovo

Thanks

---

### Post by mmbates on 2008-02-24
G'day,
I'm having problems with the ALC882/885.  I'm only getting sound out of the headphones, and not out of the digital jack.  It's a built in sound card on the Gigabyte GA-MA790FX-DQ6 motherboard.
```

~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC885
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I have been right through the list for the ALC882/885 and the best I can do is get sound from the headphones (presumably this is analog).  I have checked with Alsa Mixer in all cases and made sure that nothing is muted and all turned up loud enough to hear.

Are there any new or updated models for this codec that aren't listed?  Or any other suggestions/ideas?

Thanks,
Michael

---

### Post by black-flag on 2008-02-29
Greeting,
any solution for our problem (7.10/amilo PI1505/Realtek ALC861) ???
Kind Regards.

---

### Post by blastus on 2008-03-08
This thread was exactly what I was looking for :)

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
Codec: Generic 11c1 Si3054

I added "options snd-hda-intel model=6stack-dig" to /etc/modprobe.d/alsa-base. 

Now I can finally turn off my laptop's speakers when using headphones by unchecking the headphone switch. Headphone sense doesn't work and I haven't tried the microphone, but I don't really care. I just wanted some way to turn off the speakers when using headphones.

---

### Post by d_deniz on 2008-03-08
how did you edit this file i can edit but i can't save it.
when i try to reach it by "sudo gedit /etc/modeprobe.d/alsa-base" it opens an blank page and I wirte the necessary line("options .....") there but when I want to save it, it returns "file not found" error
or when i try to do it manually it doesn't let me to save the edited file and says "you dont have permission"
this is my computer of course I have the permission:) 
please help

---

### Post by blastus on 2008-03-08
> **d_deniz said:**
> how did you edit this file i can edit but i can't save it.
when i try to reach it by "sudo gedit /etc/modeprobe.d/alsa-base" it opens an blank page and I wirte the necessary line("options .....") there but when I want to save it, it returns "file not found" error
or when i try to do it manually it doesn't let me to save the edited file and says "you dont have permission"
this is my computer of course I have the permission:) 
please help

The OP said to edit /etc/modprobe.d/alsa-base or (if that one does not exist or is empty) then edit /etc/modprobe.conf. Since your alsa-base file doesn't exist, I would try editing /etc/modprobe.conf instead.

```
sudo gedit /etc/modprobe.conf
```

---

### Post by d_deniz on 2008-03-08
thank you
now I can edit but I cant solve my problem
when I edited "options snd-hda-intel model=3stack" it only solves sound problem, but stil I can't get sound when I use headphones,I have a HDA ATI SB card and other stuff is Realtek ALC861-VD
I followed the steps written under first message
     ALC861/660
    3stack 3-jack
    3stack-dig 3-jack with SPDIF I/O
    6stack-dig 6-jack with SPDIF I/O
    3stack-660 3-jack (for ALC660)/* up to this line. my laptop is none of below
    uniwill-m31 Uniwill M31 laptop 
    toshiba Toshiba laptop support
    asus Asus laptop support
    asus-laptop ASUS F2/F3 laptops
    auto auto-config reading BIOS (default)


and none of these lines solved headphone problem any suggestion?

---

### Post by nothingspecial on 2008-03-08
After 4 weeks I finally have sound. Those congas on start up never sounded so sweet!
I`d tried everything in this thread but to no avail:( I think the problem was I`d tried so many other things that something I`d done to my system prevented this method from working.
So I did a fresh install.
Then sudo apt-get install linux-backports-modules-generic
Then sudo gedit /etc/modprobe.d/alsa-base
Then options snd-hda-intel model=toshiba

And bingo - sound:):):)

I stress that I`d done all this before without success. The thing that clinched it was the fresh install.
Thankyou!

---

### Post by archwndas on 2008-03-10
Hi there,
I have an ACER Aspire 5633. The output of the command 
 cat /proc/asound/card0/codec#* | grep Codec

is 
Codec: Realtek ALC883
Codec: Conexant ID 2bfa


I added in the file /etc/modprobe.d/alsa-base
options snd-hda-intel model=acer

I get no sound though. Skype says: Call failed: Problem with Audio Playback.
I tried all:
options snd-hda-intel model=base
options snd-hda-intel model=will
options snd-hda-intel model=auto
options snd-hda-intel model=3stack
nothing.

Could somebody give me some advice? If not how can I fall back to the original Ubundu configuration (I have installed the latest alsa drivers). 

Thanks,
Archwn.

---

### Post by kmb`` on 2008-03-25
hey guys im on a hp dv6500 
for my codec i got this 

Codec: Realtek ID 268
Codec: Motorola Si3054

what do i look under?
i tryd options snd-hda-intel model=hp 

didnt work
any suggestions?

---

### Post by erginemr on 2008-03-25
> **kmb`` said:**
> hey guys im on a hp dv6500 
for my codec i got this 

Codec: Realtek ID 268
Codec: Motorola Si3054

what do i look under?
i tryd options snd-hda-intel model=hp 

didnt work
any suggestions?

I suggest you to follow **Temujin**'s following post:
[http://ubuntuforums.org/showpost.php?p=4450631&postcount=5](http://ubuntuforums.org/showpost.php?p=4450631&postcount=5)

to first try the second link and if it doesn't work, to **update your ALSA drivers to version 1.0.16** with the excellent, simple to use scripts that he has written.

Following his second link, under the category ALC268, I suggest you to try: "options snd-hda-intel model=**3stack**" and "options snd-hda-intel model=**auto**" first.

---

### Post by erginemr on 2008-03-25
Alternatively, although your card doesn't match, you may refer to:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

and try installing **linux-backports-modules-generic** after enabling backports as suggested before, which will update ALSA sound modules in your system.

---

### Post by kmb`` on 2008-03-25
thanks alot m8!!!!! i updated my drivers and now it works fine :)
thanks again guys!!

---

### Post by nguyendinhtu on 2008-03-28
Please help me! My laptop is Lenovo Y410. Its speaker has been working after I add "options snd-hda-intel model=fujitsu" in "/etc/modprobe.d/alsa-base" but headphone hasn't. I have tried to make it work in many ways but lost :(.
My **aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC262 Digital [ALC262 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

My **cat /proc/asound/card0/codec#* | grep Codec**
```
Codec: Realtek ALC262
Codec: Motorola Si3054

```

---

### Post by the_analyzer on 2008-03-28
> **Donny K. said:**
> Hi people,

It seems that many people are struggling with the HDA ATI or INTEL sound card/chip. Especially laptop users seem to have different problems. Hearing no sound from their speakers but only with their headphones. Or the other way around, no jack sensitivity or only hearing sound from their headphones and not trough the speakers. And, of course the worst kind, not having any sound at all.

Many forums are giving the 3stack of 6stack solution which (partially) works for some people. 
(Changing or adding the following sentence: **options snd-hda-intel model=3stack** ) into the **/etc/modprobe.d/alsa-base** file.

But the HDA soundcards seem to be complexer than that. There are a lot of different HDA cards with their own set of "rules" To tackle this problem, you have to find out what type of card is in your computer. you can check that by typing: **cat /proc/asound/card0/codec#* | grep Codec** (or if that fails : **aplay -l** )
The output will contain the exact ty

pe your your card or chip. For example: "Code:ALC861VD/660VD"

Now that you know this, you can look up that type in the list posted below:

 Model name Description
---------- -----------
ALC880
3stack 3-jack in back and a headphone out
3stack-digout 3-jack in back, a HP out and a SPDIF out
5stack 5-jack in back, 2-jack in front
5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
6stack 6-jack in back, 2-jack in front
6stack-digout 6-jack with a SPDIF out
w810 3-jack
z71v 3-jack (HP shared SPDIF)
asus 3-jack (ASUS Mobo)
asus-w1v ASUS W1V
asus-dig ASUS with SPDIF out
asus-dig2 ASUS with SPDIF out (using GPIO2)
uniwill 3-jack
fujitsu Fujitsu Laptops (Pi1536)
F1734 2-jack
lg LG laptop (m1 express dual)
lg-lw LG LW20/LW25 laptop
tcl TCL S700
clevo Clevo laptops (m520G, m665n)
test for testing/debugging purpose, almost all controls can be
adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y
auto auto-config reading BIOS (default)

ALC260
hp HP machines
hp-3013 HP machines (3013-variant)
fujitsu Fujitsu S7020
acer Acer TravelMate
will Will laptops (PB V7900)
replacer Replacer 672V
basic fixed pin assignment (old default model)
auto auto-config reading BIOS (default)

ALC262
fujitsu Fujitsu Laptop
hp-bpc HP xw4400/6400/8400/9400 laptops
hp-bpc-d7000 HP BPC D7000
benq Benq ED8
benq-t31 Benq T31
hippo Hippo (ATI) with jack detection, Sony UX-90s
hippo_1 Hippo (Benq) with jack detection
sony-assamd Sony ASSAMD
basic fixed pin assignment w/o SPDIF
auto auto-config reading BIOS (default)

ALC268
3stack 3-stack model
toshiba Toshiba A205
acer Acer laptops
auto auto-config reading BIOS (default)

ALC662
3stack-dig 3-stack (2-channel) with SPDIF
3stack-6ch 3-stack (6-channel)
3stack-6ch-dig 3-stack (6-channel) with SPDIF
6stack-dig 6-stack with SPDIF
lenovo-101e Lenovo laptop
auto auto-config reading BIOS (default)

ALC882/885
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
arima Arima W820Di1
targa Targa T8, MSI-1049 T8
asus-a7j ASUS A7J
asus-a7m ASUS A7M
macpro MacPro support
mbp3 Macbook Pro rev3
imac24 iMac 24'' with jack detection
w2jc ASUS W2JC
auto auto-config reading BIOS (default)

ALC883/888
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
3stack-6ch 3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
6stack-dig-demo 6-jack digital for Intel demo board
acer Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
acer-aspire Acer Aspire 9810
medion Medion Laptops
medion-md2 Medion MD2
targa-dig Targa/MSI
targa-2ch-dig Targs/MSI with 2-channel
laptop-eapd 3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
lenovo-101e Lenovo 101E
lenovo-nb0763 Lenovo NB0763
lenovo-ms7195-dig Lenovo MS7195
haier-w66 Haier W66
6stack-hp HP machines with 6stack (Nettle boards)
3stack-hp HP machines with 3stack (Lucknow, Samba boards)
auto auto-config reading BIOS (default)

ALC861/660
3stack 3-jack
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack with SPDIF I/O
3stack-660 3-jack (for ALC660)
uniwill-m31 Uniwill M31 laptop
toshiba Toshiba laptop support
asus Asus laptop support
asus-laptop ASUS F2/F3 laptops
auto auto-config reading BIOS (default)

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

CMI9880
minimal 3-jack in back
min_fp 3-jack in back, 2-jack in front
full 6-jack in back, 2-jack in front
full_dig 6-jack in back, 2-jack in front, SPDIF I/O
allout 5-jack in back, 2-jack in front, SPDIF out
auto auto-config reading BIOS (default)

AD1882
3stack 3-stack mode (default)
6stack 6-stack mode

AD1884
N/A

AD1981
basic 3-jack (default)
hp HP nx6320
thinkpad Lenovo Thinkpad T60/X60/Z60
toshiba Toshiba U205

AD1983
N/A

AD1984
basic default configuration
thinkpad Lenovo Thinkpad T61/X61

AD1986A
6stack 6-jack, separate surrounds (default)
3stack 3-stack, shared surrounds
laptop 2-channel only (FSC V2060, Samsung M50)
laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
ultra 2-channel with EAPD (Samsung Ultra tablet PC)

AD1988
6stack 6-jack
6stack-dig ditto with SPDIF
3stack 3-jack
3stack-dig ditto with SPDIF
laptop 3-jack with hp-jack automute
laptop-dig ditto with SPDIF
auto auto-config reading BIOS (default)

Conexant 5045
laptop Laptop config
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

Conexant 5047
laptop Basic Laptop config
laptop-hp Laptop config for some HP models (subdevice 30A5)
laptop-eapd Laptop config with EAPD support
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

STAC9200
ref Reference board
dell-d21 Dell (unknown)
dell-d22 Dell (unknown)
dell-d23 Dell (unknown)
dell-m21 Dell Inspiron 630m, Dell Inspiron 640m
dell-m22 Dell Latitude D620, Dell Latitude D820
dell-m23 Dell XPS M1710, Dell Precision M90
dell-m24 Dell Latitude 120L
dell-m25 Dell Inspiron E1505n
dell-m26 Dell Inspiron 1501
dell-m27 Dell Inspiron E1705/9400

STAC9205/9254
ref Reference board
dell-m42 Dell (unknown)
dell-m43 Dell Precision
dell-m44 Dell Inspiron

STAC9220/9221
ref Reference board
3stack D945 3stack
5stack D945 5stack + SPDIF
intel-mac-v1 Intel Mac Type 1
intel-mac-v2 Intel Mac Type 2
intel-mac-v3 Intel Mac Type 3
intel-mac-v4 Intel Mac Type 4
intel-mac-v5 Intel Mac Type 5
macmini Intel Mac Mini (equivalent with type 3)
macbook Intel Mac Book (eq. type 5)
macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
macbook-pro Intel Mac Book Pro 2nd generation (eq. type 3)
imac-intel Intel iMac (eq. type 2)
imac-intel-20 Intel iMac (newer version) (eq. type 3)
dell-d81 Dell (unknown)
dell-d82 Dell (unknown)
dell-m81 Dell (unknown)
dell-m82 Dell XPS M1210

STAC9202/9250/9251
ref Reference board, base config
m2-2 Some Gateway MX series laptops
m6 Some Gateway NX series laptops
pa6 Gateway NX860 series

STAC9227/9228/9229/927x
ref Reference board
3stack D965 3stack
5stack D965 5stack + SPDIF
dell-3stack Dell Dimension E520

STAC9872
vaio Setup for VAIO FE550G/SZ110
vaio-ar Setup for VAIO AR


As you can see, every type / chipset has several possibilities. Type the first word from the list in **/etc/modprobe.d/alsa-base** or (if that one does not exist) **/etc/modprobe.conf**  Just try them until you've found the right match.  ( you can edit these files with your favourite text editor, for example: **sudo gedit /etc/modprobe.d/alsa-base** or **sudo gedit /etc/modprobe.conf** )

For example: If **cat /proc/asound/card0/codec#* | grep Codec**  or  : **aplay -l ** return "Realtek ALC260" , Look under "ALC260" in the list and add the following line in your **/etc/modprobe.d/alsa-base** or (if that one does not exist or is empty) **/etc/modprobe.conf** 

options snd-hda-intel model=hp

Reboot and check if your sound if working. [COLOR="Red"]Do not forget to check your mixer to see if (new) channels are muted.[/COLOR] If that one doesn't work or partially works, try another one in the list eg: 
options snd-hda-intel model=base
options snd-hda-intel model=will
or
options snd-hda-intel model=acer

That's all there is to it! I hope this forum post will help you as good as the info, gathered on the internet by me, in combination with days/weeks/months of testing and searching by me. I would like to know this this post solved your problems. Please let me know by posting your result in this thread. Thank you for your time, good luck and enjoy your sound!

Donny K. (Linux Freak)


I have that (hearing from speakers but no from headphones) problem man, what should I do?
I did that but What I got is:

********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************

**** List of PLAYBACK Hardware Devices ****
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 0: OSS ID [High Definition Audio speaker]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 1: OSS ID [High Definition Audio headphone]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 2: OSS ID [High Definition Audio rec1]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 3: OSS ID [High Definition Audio rec2]
  Subdevices: 1/1
  Subdevice #0: OSS subname

---

### Post by awashington on 2008-03-30
using toshiba satellite laptop a135-s4467 used the list to find my codec but I still have no sound in my headphones sound comes out of speakers with no problem

Tri-Boot-Laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC861-VD
Codec: Generic 11c1 Si3054

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUTALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

](*,)

---

### Post by egillmaron on 2008-03-31
Thanks that worked great! I have Packard bell easynote and installed Ubuntu 7.10. Sound didn't work. This fixed it: 
options snd-hda-intel model=3stack

Cheers!

---

### Post by Scorpion1031 on 2008-04-01
Great work.  I have been looking for this list ever since I installed Gutsy. :guitar:

---

### Post by johanpdx on 2008-04-01
Can't believe it was this simple, but it was! (For Sony Vaio VGN SZ660.) Thanks.

johanpdx

---

### Post by Matthewslf on 2008-04-01
Just as a side note for the people saying that they still have no sound, in terminal, run alsamixer, and try muting switches like external amplifier and headphone jack sense. That's the most often problem. This, however, is only if it appears to recognize your sound card.

---

### Post by reefsrt4 on 2008-04-14
This worked great for me!  Thanks a ton.

---

### Post by monkeymind90 on 2008-04-14
My ID is Conexant 5051. I don't see it on any of the lists and I've tried all the obvious ones (hp, laptop, hp-laptop, test) without luck. Any ideas?

---

### Post by Yellow Pasque on 2008-04-16
Here are the scripts to upgrade to ALSA 1.0.16 for those using Gutsy (7.10)
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by ghonz on 2008-04-16
hey hey, I tried this and for the first time my mute button is now light blue, however I have no more sound and when I try to open volume control I get
"No volume control GStreamer plugins and/or devices found."

Any advice?

---

### Post by mholst on 2008-04-26
Thanx a bunch. Why have I first found this today... Darned the size of the Internet.

I have seriously been doing all kinds of weird installs, and the fact that one single line can do the trick. Well, that just makes me feel stupid. Never the less. Thank you very very much.

Just for the record:
To my laptop: Lenovo 3000 N100
/proc/asound/card0/codec#* | grep Codec: AD1986A
i added: options snd-hda-intel model=6stack
to file: /etc/modprobe.d/alsa-base
after: # Prevent abnormal drivers from grabbing index 0


Best regards
Morten

---

### Post by anne_maree on 2008-04-26
A big thanks from me too - adding ```
options snd-hda-intel model=lenovo
``` to  /etc/modprobe.d/alsa-base on an Asus M51SN-AP067G running Hardy works :KS

---

### Post by gavinjb on 2008-04-26
Just found this thread, 8.04 is driving me crazy as sound works fine on LiveCD but not on upgrade form 7.10 on HD.

Did notice an article I found on google for Gutsy which mentioned installing the linux-backports-modules, when I used synaptics to install this I had the wrong kernel version installed!

```

cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory

```

```

aplay -l
aplay: device_list:205: no soundcards found...

```

but if I run lspci | grep -i audio I get
```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

---

### Post by Kcrsh10 on 2008-04-26
I have a dell inspiron 1525. I have upgraded to hardy, from 7.10 and now ubuntu is failing to detecting any sound card.


~$ aplay -l
aplay: device_list:205: no soundcards found...

Any Ideas. I am new to ubuntu  and am unsure where to start.

**Just seen the post above, I have the above device. Thanks!

---

### Post by gavinjb on 2008-04-26
Kcrsh10 looks like we have the same problem, I did find the following article, but it didn't work for me.

[http://ubuntuforums.org/showthread.php?t=762349&highlight=dell+inspiron+1525](http://ubuntuforums.org/showthread.php?t=762349&highlight=dell+inspiron+1525)

---

### Post by Kcrsh10 on 2008-04-26
Cheers gavinjb, I Tried that but it didn't work for me either!

---

### Post by gavinjb on 2008-04-27
Kcrsh10 - I had a bit of success last night (or I got closer anyway), I went through the process from my last post again, and I realized that I forgot to rename the file mentioned, I then re-ran

$ sudo depmod -a
$ sudo update-initramfs -u

and after rebooting I then had my driver listed in System/Prefs/Sound, mind you I now get the following error when trying to play sound, but I have the feeling that I am getting closer

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument

```

Gavin,

Update: when I run  cat /proc/asound/card0/codec#* | grep Codec I now get Codec: Conexant ID 2c06, but this is not listed as far as I can see in the list so can anyone help.

---

### Post by rastari on 2008-04-27
i'm on an ispiron 1525 and can't get sound no matter how hard i try despite the fact that i could when I was running gutsy

---

### Post by Kcrsh10 on 2008-04-27
I got sound by installing the 386 kernel! Follow the link [http://ph.ubuntuforums.com/showthread.php?t=720043&page=5&](http://ph.ubuntuforums.com/showthread.php?t=720043&page=5&)

or run:

sudo apt-get install linux-386

Code was taken from thread, and not mine.

---

### Post by jonspencerbx on 2008-04-27
I got my realtek alc888 in my acer 5920g working by adding 
```
options snd-hda-intel model=auto
```

M.

---

### Post by jswhite on 2008-04-28
This thread just solved my own sound issues. I have an Inspiron 1420n, pre-installed with feisty, upgraded to gutsy and then hardy yesterday. The gutsy -> hardy upgrade borked my sound, and I had nothing at all.

Codec returned was STAC9228, but the Inspiron was not listed in the models. After trying a few, I found the "dell-3stack" model restored my sound completely. So, "Inspiron 1420n" should be added to that one along with the Dimension E520.

---

### Post by Imaculent on 2008-04-28
Hello, I got this one:

Model name Description
---------- -----------
**ALC880**
3stack 3-jack in back and a headphone out
3stack-digout 3-jack in back, a HP out and a SPDIF out
5stack 5-jack in back, 2-jack in front
5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
6stack 6-jack in back, 2-jack in front
6stack-digout 6-jack with a SPDIF out
w810 3-jack
z71v 3-jack (HP shared SPDIF)
asus 3-jack (ASUS Mobo)
asus-w1v ASUS W1V
asus-dig ASUS with SPDIF out
asus-dig2 ASUS with SPDIF out (using GPIO2)
uniwill 3-jack
fujitsu Fujitsu Laptops (Pi1536)
F1734 2-jack
lg LG laptop (m1 express dual)
lg-lw LG LW20/LW25 laptop
tcl TCL S700
clevo Clevo laptops (m520G, m665n)
test for testing/debugging purpose, almost all controls can be
adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y
auto auto-config reading BIOS (default)

...on a Fujitsu laptop. But I really dont understand what to do with it, im quite new with Ubuntu. I found:
/etc/modprobe.d/alsa-base
and know how to edit, but...
[B]What should I write?
And does it matter where in the file I write the line I should write?
[/B]
I looked on the examlpe with "Realtek ALC260" but where does "options snd-hda-intel model=hp" come from?

Thanks!

---

### Post by mchaggis on 2008-04-29
Hi,

Just thought I'd post a followup after upgrading to 8.04 Hardy Heron...

It came as no surprise when me laptop rebooted and was thrown yet again into silence. However, to my surprise and pleasure, the resolve was a simple one this time.

Just to remind, my laptop is as follows:

```

Alienware M9750
Codec: Realtek ALC885
Codec: Generic 11c1 Si3054

```

I kept a back up of the last /etc/modprobe.d/alsa-base file prior to upgrading and found that re-adding the following line (and rebooting) worked a treat.

```
options snd-hda-intel model=6stack-dig
```

Ok, I'm not 100% sure that a fresh install would have been this easy, but I'd like to think it was :guitar:

---

### Post by jswhite on 2008-04-30
> **Imaculent said:**
> ...on a Fujitsu laptop. But I really dont understand what to do with it, im quite new with Ubuntu. I found:
/etc/modprobe.d/alsa-base
and know how to edit, but...
[B]What should I write?
And does it matter where in the file I write the line I should write?
[/B]
I looked on the examlpe with "Realtek ALC260" but where does "options snd-hda-intel model=hp" come from?

Thanks!

Okay, as far as what you write...these steps should work:

1. You'll need to edit it as root, so open the terminal and type "gksudo gedit /etc/modprobe.d/alsa-base". If you don't edit the file as root, you won't be able to save your changes.

2. Scroll down to the bottom of the file and throw in a couple of spaces. I don't believe there's any reason why it **has** to go at the very bottom, but that's what I did. Plus, it makes it easier to find if you have to keep changing things.

3. At the end, type "options snd-hda-intel model=fujitsu". In case it's unclear from the list that was provided, the things that could potentially be the "model" would be the first word posted before a space, such as "3stack", "6stack-digout", etc. Given that you've already mentioned you're using a Fujitsu laptop, you should probably start with "model=fujitsu" since it's the most likely candidate and you probably don't want to repeat this for several hours.

4. Save.

5. Reboot, then see if you have sound. You should probably notice pretty quickly whether or not you get the startup sound when gnome loads, but just to be sure you might want to break out some music or something.

6. If that didn't work, do step 1 again, scroll down through the file, and replace "fujitsu" with another one of the listed "model"s for your card.

7. Save, reboot, test, and repeat that process until your sound works perfectly.

---

### Post by jhemi442 on 2008-05-01
> **d3ngar said:**
> I'm getting very confused here:

I have no sound at all and have been spending WAY too much time on this already. Now I'm trying the forums and IRC.

I read on the Alsa site that the ICH8 isn't supported and that there is NO driver for that card (see here: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)). 

However, there are about a million workarounds which I unfortunately all tried without result.
The only alternative that I still haven't tried is upgrading the Kernel to 2.6.23, which I really don't want to do.

Now here is my card:

lspci -v:


 cat /proc/asound/card0/codec#* | grep Codec


alsamixer tells me that it identified the card correctly and that it is in fact using it, I have the sound mixer icon in the task-bar and I don't get an error message,

It's highly confusing and would appreciate your help.

Some additional resources that I already checked:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

[http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem) This latest one actually led me to believe that the card group is simply not supported...

And yes, I'm running on a Asus F3Sr, Ubuntu 7.10 | Kernel 2.6.22.14.21 (rumor has it that upgrading the Kernel really helps - any comments to this?)

Thanks,

Chris

Hi, any progress with it? I have F3Sr too and sound isn't working as well. I have Ubuntu 8.04.

Thanks in advance.

---

### Post by haldyr on 2008-05-04
It's working on my Fujitsu-Siemens Amilo Pi1536.
I added this:
options snd-hda-intel model=3stack-dig

into:
/etc/modprobe.d/alsa-base

for changing volume for headphone/ext. speakers use "Surround 3D" a for internal speakers use "Front".

Thanks very much. I was trying to resolve this problem for a few months.

---

### Post by hugsrwarmy on 2008-05-06
Hi, I have a L35-S1054 Toshiba Satellite.

I tried your method, and it worked for this:

options snd-hda-intel model=3stack

But there's a slight problem.

The speaker works, but the headphones don't.
Before trying this, the headphones work, but the speakers didn't!
So it switched.

Is there another way to try to make both of these work? T^T

Here's my alsa-base file. (/etc/modprobe.d/alsa-base)

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-hda-intel model=3stack
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by Brightbelt on 2008-05-07
Many Thanks!! Worked like a charm for me on my 24" iMac. Mine was ALC885, model=imac24

Frank B.

---

### Post by Gotisch on 2008-05-08
WOW thanks a lot dude :) this really helped to fix everything! you dont actually have to restart the pc everytime though (if noone said that till now) you can just do "sudo alsa reload" and it will reload everything then a "sudo alsamixer" and unmute all new thinggies and try to play some sound :) works like a charm now thanks again

---

### Post by aurora_consurgens on 2008-05-10
This is my laptop:

theerapong@ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ID 268
Codec: Motorola Si3054

---

### Post by gamood on 2008-05-10
Hello every one here
I wanted to report a success with my iMAc 24 wich has already been reported
i'm running a prereleased vervion of Hardy Heron wich have been updated after the official release of hardy on april  2008
I didn't activate the backports deposite to get this to work this time.
I have great admiration for such skillfull guys that dedicate their time to the anonym communauty.
thanks a lot (from a blues addict)
:guitar:=D>=D>

---

### Post by jalanbuntu on 2008-05-11
Still got  no luck with my lenovo y410 :(
Laptop speakers works but not for the headphone....

---

### Post by dublued on 2008-05-11
this just may be the answer i'm looking for ... but a quick question or two before i try it...
i have an asus motherboard (M2NPV-VM) with onboard sound.  when i do cat /proc/asound/card0/codec#* | grep Codec, i get:
```
Codec:  Analong Devices AD1986A
```
when i do lspci | grep -i audio, i get:
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

my problem is that i only get sound out of the front two speakers.  i have 5.1 speakers and i get no sound out of the rest of the speakers.  when i do the speaker-test, it works perfectly fine.

so my question is... since this is obviously not an intel sound card, what would i add in the alsa-base file?

these are all of the options i see in that file:
```
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

i don't want to share the sound from the fronts to the rear, i can already get that to work... i want actual true surround... if that's even possible.

thanks for looking and i appreciate all the help

---

### Post by NeQaSh on 2008-05-13
thnx alot dear, Donny K.
i do this :
> sudo gedit /etc/modprobe.conf
 
this option work as crystal with me on my laptop [COLOR="DarkOrange"]SONY VGN-FZ35M [/COLOR]
> options snd-hda-intel model=[COLOR="Red"]vaio[/COLOR]


and save the new config to the modefied file.

then i reboot and login,i play a song and my headsetphone woking 100 % ,

 when i remove it, the sound came from my lap-speaker as normal

thnx again and again **[COLOR="Blue"]Donny K.[/COLOR]**

---

### Post by thorbjornw on 2008-05-14
Thanks for the very useful guide.  I have a brand-new VAIO VGN SZ750N notebook.  Sound was working from the speakers, but not the headphones.  

It turned out to be a Sigmatel STAC9872AK (conexant ID 2c06), and adding the line 

option snd-hda-intel model=vaio 

gave me sound in the headphones.  

The microphone is still not working, however, neither the built-in one with the motioneye camere (not working either), nor the microphone jack.  Doubleclicking the sound icon shows that the mircophone jack is actually ticked off.

Any clue?

---

### Post by dancer58 on 2008-05-18
I tried everything I found here but still no sound

I looked at the mother board and found a chip AD1988A
Then I booted WinXP and found DEV_1988 under sound
I have to assume I have AD1988 audio chip 

aplay -l always says no sound card

Here is the rest of what I know including my hardware:

linux 2.6.24-17
Ubuntu 8.04
mother board = Asus P5B
processor = Intel core 2 duo

--------------------------------------------------------------------------------------------

audio = Intel 82801H (on mother board)
   pci.product = '82801H (ICH8 Family) HD Audio Controller'

THIS IS FROM HWINFO:
31: PCI 1b.0: 0403 Audio device
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_284b
  Unique ID: u1Nb.kURRCMIOEo3
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "ASUSTeK HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x284b "HD Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81ec 
  Revision: 0x02
  Memory Range: 0xfebf8000-0xfebfbfff (rw,non-prefetchable)
  IRQ: 3 (no events)
  Module Alias: "pci:v00008086d0000284Bsv00001043sd000081ECbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is not active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

-------------------------------------------------------------

Alsa.sh does not find a sound card

   !!Loaded ALSA module

   !!Soundcards recognised by ALSA
   --- no soundcards ---

   !!PCI Soundcards installed in the system
   00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

--------------------------------------------------------------------------------------------

Agere V.92 winmodem
video = nVidia G72 (GEForse 7300 LE)
2 hard drives
keyboard & mouse are USB
USB bluetooth BCM2045A

I hope someone has an idea

Thanks
Harold

---

### Post by Ceadda on 2008-05-28
MSI M662 

cat /proc/asound/card0/codec#* | grep Codec

Produced...

Codec: Realtek ALC883
Codec: Generic 11c1 Si3054

After following this script...

[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24]("http://ubuntuforums.org/showpost.php?p=4298894&postcount=24")

I edited.../etc/modprobe.d/alsa-base...with this line...

options snd-hda-intel model=targa-dig

Rebooted, everything worked very nicely. thank you!!

---

### Post by jagnet on 2008-05-28
Has anyone managed to find a solution for the ALC889 (maybe known as the alc889a) ?

im using the acer aspire 8920g
Ive tried several but the only one that got close was the
options snd-hda-intel model=acer-aspire

though all i got was a vague noise on headphones, but not speakers.

---

### Post by Yellow Pasque on 2008-05-28
jagnet, have you upgraded to ALSA 1.0.16 or Ubuntu 8.04 Hardy? If you're using an older Ubuntu version, try these scripts: [http://ubuntuforums.org/showthread.php?p=4298894#post4298894](http://ubuntuforums.org/showthread.php?p=4298894#post4298894)

You can also try OSS4. Let me know if you want to go this route and I will guide you through installing the latest version from the repo.

---

### Post by Raistlin82 on 2008-05-29
Hi there, many thanks for this post!!  Still not got headphones sensed, but can turn off laptop volume b muting front speakers. 

Philips Freevents  

alc268

options snd-hda-intel model=auto

---

### Post by ionize on 2008-05-30
I buy local brand Laptop, 
when I use Gutsy G its no problem with the soundcard, but now I'm using hardy and same with other guys here thre is problem with the sound card 
but when I do (type) "lscpi -v" on terminal I found my soundcard are detected,  
-----------------------------------------------------------------------
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: CLEVO/KAPOK Computer Unknown device 5401
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at a0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
----------------------------------------------------------------------
I already add some script like on previous post but it isn't work.
may I know (based on what I found) what is my type of Soundcard? what series of Realtek? what the right script for that soundcard?

Thanx for your help

---

### Post by Raistlin82 on 2008-05-31
Just as a bit of an update, my laptop is now auto sensing headphones! Cant say as I'm sure why, it seems to have happened whilst installed mplayer in order to listen to BBC iplayer listen again programs, which worked so.. Bonus i guess :)

Edit - I take that back, it auto senses some fo the time and not at other times <shrugs>!

---

### Post by Gwaihirjp on 2008-06-01
> **jswhite said:**
> This thread just solved my own sound issues. I have an Inspiron 1420n, pre-installed with feisty, upgraded to gutsy and then hardy yesterday. The gutsy -> hardy upgrade borked my sound, and I had nothing at all.

Codec returned was STAC9228, but the Inspiron was not listed in the models. After trying a few, I found the "dell-3stack" model restored my sound completely. So, "Inspiron 1420n" should be added to that one along with the Dimension E520.
Mine is a bit like yours jswhite, I have an Inspiron 1420 (dual-booted with Vista) running Hardy, with that STAC9228 sound card. On my laptop the sound works only through the headphones but not the speakers... so I typed the following line at the end of /etc/modprobe.d/alsa-base:

options snd-hda-intel model=dell-3stack

But when I rebooted nothing had changed.. still no sound from speakers. I wonder if I'm doing something wrong? I would really appreciate some help on this. Thanks in advance!

EDIT: Ok I got it working, I'm sooo happy!!!!! The reason why it hadn't worked the first time was because for some reason, there were two lines before the "options snd-hda-intel model=dell-3stack" line which were like this: 

options snd-hda-intel model=ref
options snd-hda-intel model=auto

Not sure why those were there in the first place but I deleted the two lines leaving only the "dell-3stack" line and now it works. Thanks so much for this thread!!!

---

### Post by Audi.RS4 on 2008-06-03
I'd been searching for months for the solution to my problem and finally I found it. Thanks for your post.

My sound worked, I just had no input. So my line-in and microphone did not work. It was very upsetting.

As it turns out Ubuntu set the option to 3jack. So I just changed it to 6 jack and all is well.

> options snd-hda-intel model=6stack

I'm running a AMD X2 on a ASUS M2R32-MVP motherboard with the AD1988 codec.

Finally I don't have to reboot into XP to play my Xbox360 (which connects to the PC and LCD).

Thanks again.

---

### Post by jagnet on 2008-06-03
> **Temüjin said:**
> jagnet, have you upgraded to ALSA 1.0.16 or Ubuntu 8.04 Hardy? If you're using an older Ubuntu version, try these scripts: [http://ubuntuforums.org/showthread.php?p=4298894#post4298894](http://ubuntuforums.org/showthread.php?p=4298894#post4298894)

You can also try OSS4. Let me know if you want to go this route and I will guide you through installing the latest version from the repo.

Hey Temüjin.
 I already tried all of the above, have the latest Ubuntu 8.04 (kernel 2.6.24-17) and the latest ALSA. That wasnt working. 

 I just installed OSS 4. Not sure how to configure it so your help would be welcome. 
THanks :)

---

### Post by bluester on 2008-06-04
> **Raistlin82 said:**
> Hi there, many thanks for this post!!  Still not got headphones sensed, but can turn off laptop volume b muting front speakers. 

Philips Freevents  

alc268

options snd-hda-intel model=auto

I have a similar issue....
I have a Toshiba A205-S5825 laptop, Xubuntu 8.04, and default Xubuntu options - I did update the wireless drivers to madwifi.
It has the ALC268 sound chipset.
I tried 3stack, toshiba, and auto....
The issue:
My headphones work along with my laptop speakers.
I would like to use the headphones without the speakers on.
Is there a program or tool that I can use to turn off the laptop speakers while listening with my headphones?
Any help would be greatly appreciated....

Never mind, I solved the issue.
I must leave the headphones unplugged at boot-up.
If I plug them in after boot-up, the headphones work and laptop speakers are muted. :)

---

### Post by Raistlin82 on 2008-06-05
Hi all,  encountered a new problem, if I suspend my laptop when i "awaken" it sound does not work, any suggestions:confused:

---

### Post by DJAltair on 2008-06-06
I've managed to get my speakers and headphone output working on my Lenovo Y410. There is no jack detection and the microphones don't seem to be working, but those are minor issues compared to no headphone output at all.

I used:

options snd-hda-intel model=vaio

Which was a little surprising, to say the least. To think, after all this time, a more compatible model selection was available that wasn't even listed under the models for my card (ALC262).

Anywho, I hope that helps out some Y410 owners.

Update: Scratch that. It doesn't really work all the time, so it's not more compatible. It's actually kind of strange. In order to get the headphone output working, I have to set the model to benq first, do a "sudo alsa force-reload", then change the model to vaio and perform another "sudo alsa force-reload". Only then do I get any output from the headphone jack. Very curious indeed.

---

### Post by jagnet on 2008-06-08
For anyone with an ACER 8920G and/or have the Realtek alc889 (acl889)  I have found a working solution using OSS 4 :)


The second post by Temüjin in this link works (thanks Temüjin ) >

[http://ubuntuforums.org/showthread.php?t=780961&highlight=oss4](http://ubuntuforums.org/showthread.php?t=780961&highlight=oss4)

---

### Post by msegmx on 2008-06-10
I just want to thank :)

after installation of hardy heron there was no sound at all.

my output :
first output :
Codec: Realtek ALC660-VD
Codec: Motorola Si3054

second output : 
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


so i added this line as you suggested :

options snd-hda-intel model=hp

i use a Asus laptop with 82801H (ICH8 Family) but "hp" worked, i don't know why :)

btw, there's a program "Sysinfo", not installed by default in hardy heron.
it says under sound card - subsystem : ASUSTeK Comp. Inc. Unknown device 1783

but adding the line solved the sound problem.
thanks for your research :)

---

### Post by Yellow Pasque on 2008-06-10
> btw, there's a program "Sysinfo", not installed by default in hardy heron.
it says under sound card - subsystem : ASUSTeK Comp. Inc. Unknown device 1783
For aesthetics (because your sound works), try this command:
```
sudo update-pciids
```

---

### Post by hotweiss on 2008-06-11
I have an Asus notebook with the 883 chipset and after trying every option I still could not get my speakers to mute after pluging in my headphones. Any Asus users here with a solution?

---

### Post by portlandor on 2008-06-12
Hi,

I had HDA problems on my VAIO S460N/C.  I am using Hardy.
I installed the linux-backports-modules2.6.2 v. 2.6.24-19.17
I added the line "options snd-hda-intel model=vaio to /etc/modprobe.d/alsa-base

Still none of my sound inputs would work.  Turns out the problem was alsamixer and alsamixergui.  When I switched to gnome-alsamixer, I was finally able to turn on the inputs.  I also found that other mixers worked as well such as xmix, gamix, and qamix.

Rob.

---

### Post by msegmx on 2008-06-20
> **Temüjin said:**
> For aesthetics (because your sound works), try this command:
```
sudo update-pciids
```


thanks for the tip :)


i had to change my model name to *lenoveo* because with *hp* there is no sound when headphone is plugged in headphone. now with 

options snd-hda-intel model=lenovo

everything works fine like it should.

again for all the folks using an Asus M51Sn laptop and 
ALC861VD/660VD sound card / codec (whatever) :

*options snd-hda-intel model=lenovo*

works fine for me.

i hope this info helps someone because it s pretty frustrating sitting in front of a new laptop without any sound :)

---

### Post by jamesetch on 2008-06-23
Using Toshiba satellite L30-106 with aplay -l:

card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]

Started with no sound whatsoever, then tried:

options snd-hda-intel model=3stack

This got my built in speakers working, however, not the headphones. I tried to unmute the headphones in alsamixer, however, I could not raise the level on this channel - stuck at zero. Eventually I tried (rather speculative as mine is a Toshiba):

 options snd-hda-intel model=dallas

This worked, I now have in built speakers and headphones (had to unmute headphones though).

Great post, thanks.

---

### Post by Yellow Pasque on 2008-06-23
james, thanks for the feedback. I am trying to keep a current list here: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
I will add your model to the list.

---

### Post by bicchi on 2008-06-23
I would like to report what worked for me and perhaps what might help others. I have sound but it is really low even after increasing it through alsamixer.
My system: Dell XPS 410 with the a SigmaTel STAC9227
 
I was able to get the sound working using the "dell-bios" options as follows:
options snd-hda-intel model=dell-bios

As a matter of fact, the dell-bios options needs to be added to the list of: STAC9227 
If you download the Linux kernel you will see a file: ["Documentation/sound/alsa/ALSA-Configuration.txt"]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=Documentation/sound/alsa/ALSA-Configuration.txt;hb=HEAD") and dell-bios is an option for the Intel STAC9227

Thanks and hope this helps others,

---

### Post by Dipper60 on 2008-06-25
Hi. 
I have done what you told; added options snd-hda-intel model=toshiba to the text, and then the headphones work perfectly, but know the speakers don't work... What to do??

---

### Post by prabath_fun on 2008-06-30
Hi,
  I want to enable 5.1 surround while playing DVD's in Ubuntu 8.04.
  My Mother board Details are
D102GGC2.
Xpress200 chipset.
for "aplay -l" command
**** List of PLAYBACK Hardware Device *****
card 0: SB{HDA ATI SB], Device 0: ALC883 Analog [ALC883 Analog]
Subdevice: 1/1
Subdevice #0: Subdevice #0

I tried the option list available in your thread. No improvement.

I tried by changing volume levels for surround, LFE, PCM,Channels from 2ch to 6ch etc., in "alsamixer". Also, I installed "AlsaMixerGUI" and there also checked. Nothing muted. 

I am getting same sound in my rear speakers as in front speaker (only while changing 2 to 6 channel in alsamixer), not dolby surround.
 I have tried speaker test. Only for front right, sound is available. Nothing else.

Please help me to enable 5.1 in my motherboard.

---

### Post by prabath_fun on 2008-06-30
Please help me...........................:(:(:(:(:(:(:(:(

---

### Post by jalanbuntu on 2008-07-01
Does anyone got the solution to make lenovo y410 jack output to work?

---

### Post by Yellow Pasque on 2008-07-01
> **jalanbuntu said:**
> Does anyone got the solution to make lenovo y410 jack output to work?
See this thread: [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

---

### Post by nickdbliss on 2008-07-05
I have Hp nx6325
The command showed AD1981

Using toshiba worked instead of hp. Thanks problem solved.

---

### Post by nitindb on 2008-07-10
Hi, 
I have a Dell 1526 and I was able to get the inbuilt microphone on my laptop working only after adding the following to /etc/modprobe.d/alsa-base and rebooting:-

> options snd-hda-intel model=dell-3stack

The only problem is that I can't get an external mic to work using the front mic jack.  Any so0lutions for this?  

The following is what after entering the terminal command:- 
hwinfo --sound

> 14: PCI 105.2: 0403 Audio device                                
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1002_7919
  Unique ID: dP62.3eubOLksOn3
  Parent ID: vSkL.HjQnVRFuoa8
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:05.2
  SysFS BusID: 0000:01:05.2
  Hardware Class: sound
  Model: "ATI Audio device"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x7919 
  SubVendor: pci 0x1002 "ATI Technologies Inc"
  SubDevice: pci 0x7919 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe9ec000-0xfe9effff (rw,non-prefetchable)
  IRQ: 22 (17 events)
  Module Alias: "pci:v00001002d00007919sv00001002sd00007919bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #34 (PCI bridge)

22: PCI 14.2: 0403 Audio device
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4383
  Unique ID: 5Dex.LA+ehfgIyxB
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "Dell Audio device"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0230 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfebfc000-0xfebfffff (rw,non-prefetchable)
  IRQ: 16 (264280 events)
  Module Alias: "pci:v00001002d00004383sv00001028sd00000230bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by w00fer10 on 2008-07-12
Hey, i just want to say Thank You for all your reseach and being community-minded enough to post this thread. For the record, i drive a HP DV6626US laptop and had no separation of speaker / headphone volume under the intial Hardy install - your post helped me work around that (I used a Toshiba ID, i think). 

It's somewhat moot now, as i shortly thereafter went to UbuntuStudio Edition which, oddly enuf works fine EXCEPT, after it boots you have to insert / remove the headphone jack one time for it to start working.... 

Thanks again,

c

---

### Post by danex_ali on 2008-07-17
First of all i want to thanks Donny K. for his brilliant post and the many help that it gave me.
I have an Asus Z53S with:
cat /proc/asound/card0/codec#* | grep Codec 

Codec: Realtek ALC660-VD
Codec: Motorola Si3054

And my sound works great! :)

I just want to give a little advise to some people that have ALC660-VD codec.
The most common mistake is that we use the words of 'non VD' codecs, for example, in my case i have try to use the words of ALC660, when in fact i sould be trying the words of ALC660-VD that are compeletely diferent from the 'non VD' words.
for example, the common mistake is to use, these words:

ALC861/660
3stack 3-jack
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack with SPDIF I/O
3stack-660 3-jack (for ALC660)
uniwill-m31 Uniwill M31 laptop
toshiba Toshiba laptop support
asus Asus laptop support
asus-laptop ASUS F2/F3 laptops
auto auto-config reading BIOS (default)


insted of this ones:

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

Thats why most people with ALC660-VD have problems, because they dont see the 'lenovo' and the 'hp' words.
This mistake happened to me and to some of my friends, so im just alerting people for this mistake. for me the solution was only reading well the post :P :lolflag:
hope this helps someone ;)

---

### Post by vaidas on 2008-07-18
hey , i am new to linux and ubuntu

i've got realtek (ALC880) sound card.
when i installed ubuntu 8.04 i could hear the sound from the speakers but the headphones and micro did not work.
downloaded realtek realtek-linux-audiopack-5.04 and installed it manually
b. ./configure
c. make
d. make install
e. ./snddevices

and added to /etc/modules
snd-hda-intel
snd-atiixp
# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss
restarted the machine. now neither the speakers nor the headphones work :(
when i switch on the alsamixergui i can manage every part of it except the "head" part.
i tried adding lines to modprobe.d/alsa-lib
but it does not change anything.

please help!

---

### Post by Moufou69 on 2008-07-21
> **vaidas said:**
> hey , i am new to linux and ubuntu

i've got realtek (ALC880) sound card.
when i installed ubuntu 8.04 i could hear the sound from the speakers but the headphones and micro did not work.
downloaded realtek realtek-linux-audiopack-5.04 and installed it manually
b. ./configure
c. make
d. make install
e. ./snddevices

and added to /etc/modules
snd-hda-intel
snd-atiixp
# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss
restarted the machine. now neither the speakers nor the headphones work :(
when i switch on the alsamixergui i can manage every part of it except the "head" part.
i tried adding lines to modprobe.d/alsa-lib
but it does not change anything.

please help!
Hi Mine is :
ALC861VD Analog

what next bcoz there is nothing solved so far

---

### Post by ghoulsblade on 2008-07-22
thank you very much !   
i've got ASUS M51SN laptop with 
intel 82801H (ICH8 Family) , codec : ALC660-VD
and  
options snd-hda-intel enable=1 index=0 model=lenovo
worked for me =)

---

