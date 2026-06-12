---
title: "mic dont work Conexant CX20561 (Hermosa) at ICH9 - Toshiba Satellite U405"
date: 2009-05-06
forum: Hardware
---

### Post by Lanceloth01 on 2009-05-06
I have a Toshiba Satellite U405-S4856.  I am using 9.04, the sound is OK but the mic (internal and front) don't work. Many weeks ago I tried with 8.10 with same results.

The output to following commands are:
#aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

#cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20561 (Hermosa)

# lspci -vv
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at f4800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

#lshw
 *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

# lspci -nv
00:1b.0 0403: 8086:293e (rev 03)
    Subsystem: 1179:ff50
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f4800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

I have followed the suggestions:   :(
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

And I had inserting the followings options at the end of /etc/modprobe.d/alsa-base.conf
TEST1: mic (internal & external) don't work, only sound
options snd-hda-intel model=laptop
TEST2:  mic (internal & external) don't work and don't sound
options snd-hda-intel probe_mask=8 model=laptop
TEST3: mic (internal & external) don't work, only sound
options snd-hda-intel model=3stack

So, what I can do to my mic (internal and front) works???

Please I need your help...:confused:

---

### Post by Lanceloth01 on 2009-05-08
Are there some answers please??

---

### Post by shelterit on 2009-06-19
No answers here, just a "me, too." I'm currently trying to recompile a new kernel with the latest ALSA drivers (hoping the HCA9 drivers have been tweaked or fixed?), hoping it might help, but no luck so far. 

I'm starting to think there's something the ALSA driver hasn't got supported or not access to, but the Windows drivers do, like a mute switch. I'm not sure, but I think I muted the Mic in Windows before I blew it away to install Ubuntu. Not sure I want to go through the pain of installing a full Windows install to un-mute, but I might just have to give that a try as I need that mic for work. Aargh.

**Update:** Ok, I've resigned trying to make bloody ALSA work, and gone over to the dark side with OSS v.4. And it fixed my problem, with a sparkling of crackling sounds. *sigh* [Linux sounds system; a thorn in its side]("http://shelter.nu/blog/2009/06/linux-sound-system-sucks.html").

---

### Post by Infestdead on 2009-07-23
I have the same chipset CX20561 Hermosa on Dell Vostro A860, and when I plug the headphones - they mute the speakers but there's no sound in the phones - and they Do work. I'm really frustrated... :(

---

### Post by Reboli_NL on 2010-01-12
Here's a Lenovo X200 tablet with no sound period... Yet I "see" its presence...
I get a Alsa mixer for the HDA mixer and an OSS mixer for the conexant in Xfce...

---

### Post by ptn on 2010-05-07
I have a Toshiba Satellite U405-S2856 with exactly the same hardware, the commands you listed output exactly the same thing. 

Nothing I've tried has helped. Wanna file a bug? :P


I've noticed that USB mics do work.

---

### Post by ptn on 2010-05-10
Lanceloth01, there's now a bug report for this: [https://bugs.launchpad.net/ubuntu/+bug/575598](https://bugs.launchpad.net/ubuntu/+bug/575598)

---

### Post by Vigh on 2010-09-14
I got it to work by adding some lines into alsa-base.conf. But unfortunately I can only have 1 sound-card at a time and I am using multiple soundcards, which is frustrating.

Try

sudo gedit /etc/modprobe.d/alsa-base.conf

add line at bottom

options snd-hda-intel model=laptop mri=1 index=0

if not try

options snd-hda-intel model=toshiba mri=1 index=0

by the way this conexant chip works on alsa-1.0.23

---

### Post by xand on 2010-09-15
i tried your solution on Alsa 1.0.21 and unfortunately it did not work for me. Do you mean i have to update Alsa in order to get this working ?

---

