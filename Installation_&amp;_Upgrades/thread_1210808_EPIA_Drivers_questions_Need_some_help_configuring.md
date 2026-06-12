---
title: "EPIA Drivers questions Need some help configuring"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by kilgorq on 2009-07-11
I have 3 EPIA 50000 board that I am trying to get up an running with UBUNTU. but I am having issues with the display and audio. here is the lsconfig. How do I load specific drivers for these. so that I can get the display away from the generic and enable audio. 

quenton@quenton-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 05)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP]
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)
quenton@quenton-desktop:~$

---

### Post by cariboo on 2009-07-11
All the driver should install automatically including sound. If you can replace the graphics adapter, I would do that, as the support from the manufacturer is slim to nonexistent. to check if the drivers for the sound card are loaded, open a terminal and type:

```
lsmod | grep snd
```

Could you paste the results in your next post?

---

### Post by kilgorq on 2009-07-11
The install had to be performed on a different system due to BIOS CD rom lock out. I could not get into the bios to boot from cd and the network install did not work when I set it up. so I ran the install on a different system the moved the the drive over to this one. so I need to manually load drivers and edit config files. The sound drivers look like they are correct so I may have another issue there. But the video is trying to load the NV drivers for a Trident chipset.

[FONT=monospace]snd_via82xx            32152  3 
gameport               19340  1 snd_via82xx
snd_ac97_codec        112292  1 snd_via82xx
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16904  2 snd_via82xx,snd_pcm
snd_mpu401_uart        15104  1 snd_via82xx
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  17 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
[/FONT]

---

