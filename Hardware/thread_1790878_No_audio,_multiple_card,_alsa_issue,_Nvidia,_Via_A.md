---
title: "No audio, multiple card, alsa issue, Nvidia, Via Azalia"
date: 2011-06-25
forum: Hardware
---

### Post by luishasbon on 2011-06-25
[B]Hello Dear Community.

When I had UBUNTU 10.04 sound WORKED!

I have post several threads about this issue, I hope this would be the last one, My OS version is Ubuntu 11.04, my hardware is: Nvidia GTS 450 video Card EGS; and an integrated sound card reference: Via Azalia HDAC VT1708/A; After installing ubuntu I had no audio through my integrated sound card, I cant use my NVidia HDA card because I need for it an HDMI AUDIO, and I dont have any HDMI sound devices like dvd or TV. So I need to use my integrated default Via soundcard. I Updated the OS, nothing changed. After typing aplay -l it showed this:[/B]

-------------------------------------------------------
aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 7: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 8: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 9: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
------------------------------------------------------------
[B]
So Alsa does not recognize my integrated soundcard. So maybe its not recognized at all by the OS, but lspci -v shows this:[/B]

-------------------------------------------------------------

02:00.1 Audio device: nVidia Corporation GF106 High Definition Audio Controller (rev a1)
	Subsystem: Elitegroup Computer Systems Device 2023
	Physical Slot: 0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 25
	Region 0: Memory at ddffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	[B]Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel[/B]

80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7253
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at <ignored> (64-bit, non-prefetchable)
	Capabilities: <access denied>
	**Kernel modules: snd-hda-intel**

----------------------------------------------------------------
[B]THIS IS INFORMATION REGARDING THE lspci -v output; ""NOTICE THAT THE Via (80:01.0) Device doesnt use a driver but it has an asigned module "snd-hda-intel"""
I need to use the Via 80:01.0 device nor the 02:00.1 Audio device: nVidia Corporation GF106 High Definition Audio Controller;

Searching and "Googling": I found out that: Nvida HDA GF106 and Via Azalai HDAC uses the same sound module "snd-hda-intel"; going to modprobe.d/alsa-base-conf
throws this:[/B]

---------------------------------------------------

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklis$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use$
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

----------------------------------------------------------

[B]I tried to put in alsa-base this: options snd-hda-intel model=3stack; also 6stack; nothing changed still no audio.
I NEED TO USE MY INTEGRATED AZALIA VIA SOUND CARD THAT USES THE SAME MODULE SND-HDA-INTEL LIKE MY NVIDIA HDA CARD(THAT I DONT NEED).

SO now I went to /proc/asound/cards and it showed this:[/B]

-----------------------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xddffc000 irq 25
---------------------------------------------

**SO I DOES NOT RECOGNIZE ANY OTHER CARD BUT NVIDIA THouGH lspci -v shows both sound cards. Notice that this card uses IRQ 25 and Via Azalia uses IRQ 16 but it doesnt show the memory location.**

80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7253
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to **IRQ 17**
	Region 0: **Memory at <ignored> **(64-bit, non-prefetchable)
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

**So PLEASE COMMUNITY HOW DO I CONFIGURE ALSA TO USE MY INTEGRATED VIA AZALIA IRQ 17 VT1708/A WITH SND-HDA-INTEL MODULE AND STOP USING MY NVIDIA GF106 HDA sound card????**

I CASE YOU NEED TO LOOK AT THE ALSA-INFO.sh here it is:

[http://www.alsa-project.org/db/?f=69dcc205b7747599e92a3f9a49000793c247b2af](http://www.alsa-project.org/db/?f=69dcc205b7747599e92a3f9a49000793c247b2af)

FINALLY THANK YOU.

BTW, ARE YOU AN EXPERT CONFIGURING MULTIPLE CARDS IN ALSA???

---

### Post by lidex on 2011-06-26
Take a breath. OK, feel better now? I have been trying to fix every sound issue I've come across in the last couple years. Call via and ask them why they don't support linux. They write closed source drivers for MS. How many people do you need to have working for free with no idea of the outcome to meet the goal?

---

### Post by luishasbon on 2011-06-26
> **lidex said:**
> Take a breath. OK, feel better now? I have been trying to fix every sound issue I've come across in the last couple years. Call via and ask them why they don't support linux. They write closed source drivers for MS. How many people do you need to have working for free with no idea of the outcome to meet the goal?

Hey lidex thanks for the reply, I know writing open source drivers is uncommon, and I don't blame them or VIA, nor Ubuntu team hehe, I just want the sound back =); the deal, is that in ubuntu 10.04 with alsa 1.0.23 I had audio, trying with debian 6, and fedora 15, I noticed that after alsa 1.0.24 ubuntu and fedora have the same issue, thought debian doesn't, debian 6 comes with alsa 1.0.23. So this issue is not exclusive of ubuntu, is of every OS using alsa 1.0.24. 

I just want to fix it in order to listen some music and watch movies, Im a developer and I love writing code listening to music. I hope to get this fixed and make it public, but now I need some help regarding this issue, and how to configure alsa with multiple soundcards. Thank you for your interest and time.

---

### Post by lidex on 2011-06-29
First remove that model=3stack entry from alsa-base.conf. then have a look here: 
[http://ubuntuforums.org/showthread.php?t=1593095](http://ubuntuforums.org/showthread.php?t=1593095)

---

