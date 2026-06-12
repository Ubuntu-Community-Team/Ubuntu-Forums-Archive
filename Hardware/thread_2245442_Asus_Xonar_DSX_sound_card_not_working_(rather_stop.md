---
title: "Asus Xonar DSX sound card not working (rather stopped working)"
date: 2014-09-23
forum: Hardware
---

### Post by Neko_no_Nya on 2014-09-23
I just received an Asus Xonar DSX sound card in the mail today and am having some issues. I am running Ubuntu Gnome 14.04 64 bit and am installing the card into a Biostar TA970 motherboard.

I installed the card and booted into Ubuntu (I forgot to disable onboard which didn't work anyway). After booting, I immediately went to my sound controls and saw the card listed as CIMI8788 [Oxygen HD Audio] along with my onboard and HDMI sound. I selected the Xonar (or Oxygen I guess) and did a speaker test. The sound played perfectly through my right and left speakers. So I figured everything was good and launched Firefox to play some music in Play Music. All of a sudden I had no sound. I went back to my sound options and my Analog CIMI8788 [Oxygen HD Audio] was gone from the list. The digital output for the card was still listed as was the card under my input options.

I tried restarting and disabling the onboard but once I restarted the card is no longer listed. It only shows my digital output and line in options. The sound still appears to be working however, because if I select HDMI, I still get audio from my monitor speakers.

Also, now when I boot into Ubuntu it sounds like I hear a capacitor click twice. I don't think I heard that the first time I booted into Ubuntu.

The card works perfect in Windows 7 64 bit and I don't hear the capacitor click when booting into it either.

EDIT: Upon listening closely, I hear it click only one time when booting into Windows and two when booting into Ubuntu. Could it be the card is turning itself on and off in Ubuntu?

sudo aplay -l gives me:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DSX [Xonar DSX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DSX [Xonar DSX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v | grep -A7 -i "audio" gives me
```
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 2011
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fe080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

02:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03) (prog-if 00 [Normal decode])
--
03:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
    Subsystem: ASUSTeK Computer Inc. Device 8522
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at d000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: snd_virtuoso

06:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller (prog-if 30 [XHCI])
```

Any help would be greatly appreciated!

---

### Post by Neko_no_Nya on 2014-09-23
I just realized I forgot to mention I'm using Ubuntu Gnome, which I actually think may be relevant.

Ok, so I decided to do a little experiment. I decided to try a live cd and see what would happen. Mint 17 KDE and Ubuntu Unity 14.04 both work. The sound card is detectable and works just fine. The audio quality dosn't sound as good as in Windows, but it does work.

The live cd of Ubuntu Gnome gave me the same trouble it is giving me now. After bootup, the card was visible and selectable. Except this time, I didn't even get time to test the speakers out. I selected it and it disappeared after a couple seconds. Once again, I can select the digital output and it is visible for my input selections.

I am wondering if Gnome is actually causing the problem here?

---

