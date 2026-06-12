---
title: "Front speaker and microphone slots don't work with VIA VT1818S"
date: 2016-03-19
forum: Hardware
---

### Post by leozinho29_eu on 2016-03-19
Hello

Nor the frontal microphone nor the frontal speaker slots are working in my computer. I have installed Lubuntu 14.04.1 in a external HD, and since then I've used it in some computers, and in all of them all the sound slots worked fine. Unless in my computer :(. One thing I noted is that the only computer with a VIA codec was mine. 

What is happening is: the rear slots work fine, but the frontal ones don't. The motherboard is ASRock H55M-LE and the sound card is Intel HDA with VIA VT1818S. Currently the the state of the computer case is pretty... dramatic. The button to turn it on has fallen so there's a minuscule part which I press and it *may* turn on, and the most important: the frontal sound speaker has a bad connection (the sound is perfect in some positions, in different ones the sound is distorted and in another one there is no sound). However, when using the internal HD with Windows 7, both the speaker (under the previously cited conditions) and the microphone (this one always perfectly) work. 

Here is some information that may be useful:

```
usuario@HDTosh:~$ sudo aplay -l
**** Lista de Dispositivos PLAYBACK Hardware ****
Home directory not accessible: Permissão negada
placa 0: MID [HDA Intel MID], dispositivo 0: VT1818S Analog [VT1818S Analog]
  Dispositivo secundário: 0/1
  Dispositivo secundário #0: subdevice #0
placa 0: MID [HDA Intel MID], dispositivo 3: VT1818S Digital [VT1818S Digital]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 1: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Dispositivo secundário: 0/1
  Dispositivo secundário #0: subdevice #0
usuario@HDTosh:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: ASRock Incorporation Device 2718
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fbcf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
--
05:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
    Subsystem: Gigabyte Technology Co., Ltd Device aa68
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fbffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

```

I installed the alsa-utils-gui, used the HDAJackRetask and tried to override all the slots using the "Show unconnected pins" option with no success. I installed, uninstalled and reinstalled alsa, linux-sound-base, pulseaudio. And I installed the codecgraph to generate this:

[http://i.imgur.com/XNMwyF6.png](http://i.imgur.com/XNMwyF6.png)

The ASRock site has no Linux drivers for H55M-LE. While searching, I found little to no information about VIA VT1818S, but I've found about VIA VT1718S. My best hope is that they are not very different, so there would be a possibility the configuration of VT1718S could be usable in VT1818S:

[http://helllabs.org/codecgraph/out/asrock-h55m.svg](http://helllabs.org/codecgraph/out/asrock-h55m.svg)

Sadly, looks like the helllabs's site is outdated (4 years without updates). 

From what I have seen, the most probable cause is related to software, but I cannot discard the hardware issues (although I think it's not the responsible one).

I asked this in Lubuntu's IRC, but 10 minutes later a blackout happened, so I'm sorry if someone had answered there. I hope I have provided enough information about the issue. Thank you.

---

### Post by bcschmerker on 2016-03-20
I found at the VIA® Technologies Website that the [VT-1818S Vinyl HD DSP](http://www.viatech.com/en/silicon/legacy/audio/vt1818s/) (driver: snd-hda-intel) is a 4-out/2-in stereo codec theoretically capable of 7.1 audio.  The planar 10-pin header (sans Pin 8 as a key) should be wired for Intel® High Definition Audio™, which uses dedicated sense circuits to determine the presence of 3.5mm plugs in the front audio jacks; the sense switches are isolated from the front audio I/O circuitry.  Be advised that hdajackretask cannot compensate for a bad DSP, the reason I bypassed my Hot Rod gPC's noisy planar Realtek® ALC-889A (standard audio for a Gigabyte® GA-MA78GM-S2HP Rev. 2.0) in favor of a since-reinstalled Creative Laboratories® SB0350 PCI 2.2 audio card and SB0250 I/O drive (driver: snd-emu10k1).

Is a stock-replacement front jack and harness set available for your case?  The jacks thereon will be a clue to whether your system is HDA-compatible, or wired to the obsolete AC '97 standard, which returns audio to the motherboard when the jacks are empty.

---

### Post by Yellow Pasque on 2016-03-20
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by leozinho29_eu on 2016-03-20
About the replacement: I don't know, I will try to see if I can find  where I bought it, but if I have to buy a off-board card, will I be able  to use the front slots? It's due to the length of the cables.

About the AlsaInfo, here is the link provided: [http://www.alsa-project.org/db/?f=c58e90a17da41ac79a87f9dc59635e47a4b3a681](http://www.alsa-project.org/db/?f=c58e90a17da41ac79a87f9dc59635e47a4b3a681)

---

### Post by bcschmerker on 2016-03-21
After reading /db/?f=c58e90a17da41ac79a87f9dc59635e47a4b3a681 at ALSA-Project.org, we need to rule out diversion of audio to the display (via the Advanced Micro Devices® Radeon® HD GPU), as the High Definition Multimedia Interface is capable of transmitting multichannel audio to an offboard receiver or television unit.  What audio sink is primary in your Sound Settings?

---

### Post by Yellow Pasque on 2016-03-21
I was going to suggest the ALSA dkms PPA, but it appears to be having issues: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)

The next thing I would suggest is trying Ubuntu 16.04 on a LiveUSB, if it's not too much trouble. That would help rule out the possibility that it's a bug that has already been fixed upstream.

> While searching, I found little to no information about VIA VT1818S, but I've found about VIA VT1718S. My best hope is that they are not very different, so there would be a possibility the configuration of VT1718S could be usable in VT1818S:

It's actually grouped with the 1708S: [https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_via.c#L185](https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_via.c#L185)

---

### Post by leozinho29_eu on 2016-03-21
I'm sorry I took so much time to answer. Using alsamixer, the "default" device appears as VIA VT1818S (when I select nor 0 nor 1, just "- (padrão)"), and cat /proc/asound/cards command shown:

 ```
0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xfbcf8000 irq 42
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfbffc000 irq 44
```

I have never used the HDMI entrance of my AMD video card, not even in Windows. If there is another place to find configuration about this, where could I find it? Maybe there could be the answer.

About a newer system: I was unable to find a link to download 16.04 (it is still being tested, so no wonder it would be hard to reach for a average user), but I tested with Lubuntu 15.10, but the issue was not solved there.

---

### Post by leozinho29_eu on 2016-03-26
Hello

I was able to make both front slots to work. After some search at both VIA and ASRock sites FAQ and found that VIA codec had some issues identifying the front slots [http://www.asrock.com/support/faq.asp?c=Audio](http://www.asrock.com/support/faq.asp?c=Audio) , I reconfigured the BIOS: instead of automatically identify the slots, now it forces the front slots to be enabled. This means that, probably, my computer has the old standard front panel (AC'97).

After this, the green front slot was able to reproduce sounds, but it was unable to make the microphone work. Using alsamixer I noticed the microphone was appearing "[Desligado]", even if it was there. Thought alsamixer I was unable to activate it (lack of knowledge, i suppose), then I used the Gnome Alsa Mixer and made it work. 

Thank you for the replies, this issue is solved now.

---

