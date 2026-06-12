---
title: "Toshiba Qosmio X505 Microphone not being detected"
date: 2010-03-28
forum: Hardware
---

### Post by Kainous on 2010-03-28
Now Ubuntu 9.10 64 bit works near flawlessly on this laptop.

A Toshiba Qosmio X505-Q850 (I believe)

The microphone is not being detected. The wireless driver wasn't pre-installed but I found and compiled. The funny thing is that the webcam works without issues.

How do I find out my microphone and where would I get drivers for it?

This is the LAST remaining issue I have. And then I will be completely satisfied.

---

### Post by Kainous on 2010-04-02
No ideas/help at all?

---

### Post by Kainous on 2010-05-10
bump

---

### Post by BlackNinjaVirus on 2010-06-17
> **Kainous said:**
> bump

Set

Spike ! ! !

I have this issue also, which forces me to use Windows 7 Pro 64-bit, until this issue is resolved so I can Skype my girlfriend.

BNV

---

### Post by Warface on 2010-07-05
I have same problem here and for headphones too. When plugged, I can still hear music from the speakers. And I don't see any option to only choose headphone output in the sound preference.

Alsa need to update this quick I think.

---

### Post by lidex on 2010-07-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags (the # in toolbar)

---

### Post by Warface on 2010-07-07
uname -a 

```
Linux warface-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

dpkg -l | grep "alsa"

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
warface@warface-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                         0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                 1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 

```

head -n 1 /proc/asound/card*/codec#*

```
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5067

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID d

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID d

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID d

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID d

```


Hope this can help!

---

### Post by maluka on 2010-07-07
I've been living with this problem for the last 9 months! Still no workable solution.

---

### Post by lidex on 2010-07-07
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Warface on 2010-07-08
Nope alsamixer didn't fixed it. Still hearing from both speakers ans headphone.

---

### Post by arrhenius_ny on 2010-09-02
After 
My X505-Q890 Microphone now works!!!

What I did:

Go to [www.realtek.com](www.realtek.com) and get the latest HD Codec

Follow the ubuntu instructions in the readme.txt file (and installed it).

(if it doesn't install, you'll need to read the error messages and sudo apt-get XXX the relevant stuff)

Loaded up GNOME ALSA Mixer

Activate/Check Mic F, 
Deactivate/Uncheck Mic B

Voila!
My voice now plays back to me on sound recorder.

Unfortunately, the headphone jack doesn't work... probably would if I messed around enough with ALSA Mixer, but I can live with it this way. (Anyone got the headphone sorted out?)

---

### Post by HalfEmptyHero on 2010-09-12
I'm trying to do this, but I get an error during make. There weren't any errors in  ./configure --with-cards=hda-intel. This is what I keep on getting

```
make
make dep
make[1]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include'
make -C sound prepare
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/sound'
make prepare2
make[4]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/sound'
make[4]: Nothing to be done for `prepare2'.
make[4]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/sound'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/sound'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/oss'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/oss'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/seq'
make[4]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/seq/oss'
make[4]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/seq/oss'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/seq'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/i2c'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/i2c/l3'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/i2c/l3'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/i2c/other'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/i2c/other'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/i2c'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/opl3'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/opl3'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/opl4'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/opl4'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/vx'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers/vx'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/drivers'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/ad1848'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/ad1848'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/cs423x'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/cs423x'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/es1688'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/es1688'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/gus'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/gus'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/msnd'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/msnd'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/sb'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/sb'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/wavefront'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/wavefront'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/wss'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa/wss'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/isa'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/synth'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/synth/emux'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/synth/emux'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/synth'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ac97'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ac97'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ali5451'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ali5451'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/asihpi'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/asihpi'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/au88x0'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/au88x0'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/aw2'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/aw2'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ca0106'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ca0106'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/hda'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/hda'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ice1712'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ice1712'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/korg1212'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/korg1212'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/mixart'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/mixart'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/nm256'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/nm256'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/oxygen'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/oxygen'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/pdplus'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/pdplus'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/riptide'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/riptide'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/rme9652'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/rme9652'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/trident'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/trident'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/vx222'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/vx222'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ymfpci'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci/ymfpci'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pci'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/codecs'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/codecs'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/core'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/core'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/soundbus'
make[4]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa/soundbus'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/aoa'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/atmel'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/atmel'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/au1x'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/au1x'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/blackfin'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/blackfin'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/codecs'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/codecs'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/davinci'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/davinci'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/fsl'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/fsl'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/imx'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/imx'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/omap'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/omap'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/pxa'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/pxa'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/s6000'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/s6000'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/sh'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/sh'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/txx9'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc/txx9'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/soc'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/usb'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/usb/caiaq'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/usb/caiaq'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/usb/misc'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/usb/misc'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/usb/usx2y'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/usb/usx2y'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/usb'
make[2]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pcmcia'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pcmcia/vx'
make[3]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pcmcia/vx'
make[2]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/pcmcia'
make[1]: Leaving directory `/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23'
make -C /lib/modules/2.6.35-20-generic/build SUBDIRS=/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-20-generic'
  CC [M]  /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/memalloc.o
In file included from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/config.h:6,
                 from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/memalloc.c:1:
/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2100: note: this is the location of the previous definition
In file included from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/config.h:6,
                 from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/alsa-autoconf.h:4,
                 from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/memalloc.inc:1,
                 from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/memalloc.c:1:
/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2100: note: this is the location of the previous definition
  CC [M]  /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/pcm_native.o
In file included from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/config.h:6,
                 from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/adriver.h:25,
                 from /home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/pcm_native.c:2:
/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2100: note: this is the location of the previous definition
/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/home/brendan/Downloads/realtek-linux-audiopack-5.15/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-20-generic'
make: *** [compile] Error 2

```

Any ideas?

---

### Post by vdubhack on 2010-10-17
I have a x505 as well just a diff model than the OP and do not have a working mic though have working speakers, though there max volume is lower than when using it in windows, yes verified I have everything turned up. Have not had time to check audio on the HDMI out or the headphone jack. Cam works. I will post the results from what one of the posters requested, but I do not get what I need to install and how to configure it. Do I for the nVidia audio, intel, conextant or what? Kinda lost as to what approach to take, I am on Ubuntu 10.10 64bit, thanks for any help and or info on this one.

```

vdubhack@UAV-mioU:~$ uname -a
Linux UAV-mioU 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

``````

vdubhack@UAV-mioU:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

vdubhack@UAV-mioU:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
ii  alsa-utils                           1.0.23-2ubuntu3.2                                 Utilities for configuring and using ALSA
ii  bluez-alsa                           4.69-0ubuntu2                                     Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.30-2                                         GStreamer plugin for ALSA

``````

vdubhack@UAV-mioU:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20583 (Pebble HSF)

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GT240 HDMI

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GT240 HDMI

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GT240 HDMI

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GT240 HDMI

``````

vdubhack@UAV-mioU:~$ lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
vdubhack@UAV-mioU:~$ 

```

---

### Post by lidex on 2010-10-17
> **vdubhack said:**
> I have a x505 as well just a diff model than the OP and do not have a working mic though have working speakers, though there max volume is lower than when using it in windows, yes verified I have everything turned up. Have not had time to check audio on the HDMI out or the headphone jack. Cam works. I will post the results from what one of the posters requested, but I do not get what I need to install and how to configure it. Do I for the nVidia audio, intel, conextant or what? Kinda lost as to what approach to take, I am on Ubuntu 10.10 64bit, thanks for any help and or info on this one.


What have you tried to get mic input?
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by vdubhack on 2010-10-18
Did everything you mentioned just now and have just been trying to record my voice on the sound recorder. Still no luck and no luck with head phones.

---

### Post by lidex on 2010-10-19
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-vostro 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by aTEK on 2011-09-20
Sorry to dig up an old thread here, I am on ubuntu 11.04 64-bit. I downloaded the driver indicated by the OP and ran the auto install script. The install fails as follows:

>   CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd-hwdep.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd-hwdep.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd-page-alloc.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd-page-alloc.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd-pcm.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd-pcm.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd-timer.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd-timer.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/snd.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-analog.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-analog.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-atihdmi.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-atihdmi.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-ca0110.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-ca0110.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cirrus.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cirrus.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cmedia.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cmedia.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-conexant.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-conexant.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-hdmi.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-hdmi.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-idt.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-idt.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-intelhdmi.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-intelhdmi.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-nvhdmi.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-nvhdmi.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-realtek.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-realtek.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-si3054.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-si3054.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-via.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec-via.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-codec.ko
  CC      /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-intel.mod.o
  LD [M]  /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda/snd-hda-intel.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
utils/link-modules /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24

ALSA modules were successfully compiled.

if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.38-11-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.38-11-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.38-11-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.38-11-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/include'
make[1]: Nothing to be done for `modules_install'.
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/include'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore'
mkdir -p /lib/modules/2.6.38-11-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.38-11-generic/kernel/sound/acore
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/ioctl32'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/ioctl32'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/oss'
mkdir -p /lib/modules/2.6.38-11-generic/kernel/sound/acore/oss
cp snd-mixer-oss.ko snd-pcm-oss.ko /lib/modules/2.6.38-11-generic/kernel/sound/acore/oss
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/oss'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/seq'
mkdir -p /lib/modules/2.6.38-11-generic/kernel/sound/acore/seq
cp snd-seq-device.ko snd-seq-midi-event.ko snd-seq.ko /lib/modules/2.6.38-11-generic/kernel/sound/acore/seq
make[3]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/seq/oss'
mkdir -p /lib/modules/2.6.38-11-generic/kernel/sound/acore/seq/oss
cp snd-seq-oss.ko /lib/modules/2.6.38-11-generic/kernel/sound/acore/seq/oss
make[3]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/seq/oss'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore/seq'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/acore'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/i2c'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/i2c/l3'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/i2c/l3'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/i2c/other'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/i2c/other'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/i2c'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/mpu401'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/mpu401'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/opl3'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/opl3'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/opl4'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/opl4'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/pcsp'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/pcsp'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/vx'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers/vx'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/drivers'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/ad1816a'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/ad1816a'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/ad1848'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/ad1848'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/cs423x'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/cs423x'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/es1688'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/es1688'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/galaxy'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/galaxy'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/gus'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/gus'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/msnd'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/msnd'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/opti9xx'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/opti9xx'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/sb'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/sb'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/wavefront'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/wavefront'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/wss'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa/wss'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/isa'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/synth'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/synth/emux'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/synth/emux'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/synth'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ac97'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ac97'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ali5451'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ali5451'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/asihpi'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/asihpi'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/au88x0'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/au88x0'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/aw2'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/aw2'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ca0106'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ca0106'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/cs46xx'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/cs46xx'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/cs5535audio'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/cs5535audio'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ctxfi'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ctxfi'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/echoaudio'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/echoaudio'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/emu10k1'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/emu10k1'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda'
mkdir -p /lib/modules/2.6.38-11-generic/kernel/sound/pci/hda
cp snd-hda-codec-analog.ko snd-hda-codec-atihdmi.ko snd-hda-codec-ca0110.ko snd-hda-codec-cirrus.ko snd-hda-codec-cmedia.ko snd-hda-codec-conexant.ko snd-hda-codec-hdmi.ko snd-hda-codec-idt.ko snd-hda-codec-intelhdmi.ko snd-hda-codec-nvhdmi.ko snd-hda-codec-realtek.ko snd-hda-codec-si3054.ko snd-hda-codec-via.ko snd-hda-codec.ko snd-hda-intel.ko /lib/modules/2.6.38-11-generic/kernel/sound/pci/hda
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/hda'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ice1712'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ice1712'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/korg1212'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/korg1212'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/lx6464es'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/lx6464es'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/mixart'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/mixart'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/nm256'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/nm256'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/oxygen'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/oxygen'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/pcxhr'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/pcxhr'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/pdplus'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/pdplus'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/riptide'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/riptide'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/rme9652'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/rme9652'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/trident'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/trident'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/vx222'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/vx222'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ymfpci'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci/ymfpci'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pci'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/codecs'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/codecs'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/core'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/core'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/fabrics'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/fabrics'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/soundbus'
make[3]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/soundbus/i2sbus'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa/soundbus'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/aoa'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/atmel'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/atmel'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/au1x'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/au1x'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/blackfin'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/blackfin'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/codecs'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/codecs'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/davinci'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/davinci'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/ep93xx'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/ep93xx'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/fsl'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/fsl'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/imx'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/imx'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/jz4740'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/jz4740'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/kirkwood'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/kirkwood'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/mid-x86'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/mid-x86'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/nuc900'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/nuc900'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/omap'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/omap'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/pxa'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/pxa'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/s6000'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/s6000'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/samsung'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/samsung'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/sh'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/sh'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/tegra'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/tegra'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/txx9'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc/txx9'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/soc'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb/6fire'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb/6fire'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb/caiaq'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb/caiaq'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb/misc'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb/misc'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb/usx2y'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb/usx2y'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/usb'
make[1]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pcmcia'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pcmcia/pdaudiocf'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pcmcia/pdaudiocf'
make[2]: Entering directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pcmcia/vx'
make[2]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pcmcia/vx'
make[1]: Leaving directory `/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/pcmcia'
/sbin/depmod -a 2.6.38-11-generic 
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

Creating mixer?...done.
Creating sequencer...done.
Creating midi0?...done.
Creating dsp?...done.
Creating audio?...done.
Creating sndstat...done.
Creating music...done.
Creating dmmidi?...done.
Creating dmfm?...done.
Creating amixer?...done.
Creating adsp?...done.
Creating amidi?...done.
Creating admmidi?...done.
rm: cannot remove `/dev/snd': Is a directory
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.
Remove Folder.....
./install: 48: alsaconf: not found
root@jack-Qosmio-X505:/home/jack/Downloads/realtek/realtek-linux-audiopack-5.16# 


I rebooted my laptop, X505-Q898, and now my audio device is not recognised at all. I did have sound working without issues before this install. I have installed Gnome Alsa mixer but this does not show any information. When I attempt to select "sound card properties" in the gnome alsa mixer the app crashes and closes out. Can anyone help?

---

