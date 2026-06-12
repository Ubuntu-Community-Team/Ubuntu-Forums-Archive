---
title: "Sound issues since removing TV tuner card"
date: 2015-03-27
forum: Hardware
---

### Post by Chris_Davies on 2015-03-27
Hello

Apologies for this being my first post. I have searched, but can't find anything to help, and my head has started spinning. I cannot for the life of me see why this isn't working.

I have an ancient Dell Dimension 5150. It is old, but has been a great computer and still works quite well.


  It currently has Lubuntu 14.04 lts. Everything works fine apart from the sound.


  When I first installed it, it had a Happupauge WinTV tv tuner card.  This was always the default sound device, but when I disabled it in  Alsamixer I always managed to get the sound working through the onboard  sound.

  
I tried to get it to default to use the sound card, and couldn't. I  removed the TV tuner card from the computer entirely. Now I can't get  any sound card to work at all.

  
Output of lspci:

  
> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300]
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370 [Radeon X300 SE]
03:03.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation NM10/ICH7 Family LAN Controller (rev 01)
  lsmod | grep '^snd' | column -t
  > snd_hda_codec_idt   54762   1
snd_hda_intel       56531   4
snd_hda_codec       192906  2   snd_hda_codec_idt,snd_hda_intel
snd_hwdep           13602   1   snd_hda_codec
snd_pcm             102099  2   snd_hda_codec,snd_hda_intel
snd_page_alloc      18710   2   snd_pcm,snd_hda_intel
snd_seq_midi        13324   0
snd_seq_midi_event  14899   1   snd_seq_midi
snd_rawmidi         30144   1   snd_seq_midi
snd_seq             61560   2   snd_seq_midi_event,snd_seq_midi
snd_seq_device      14497   3   snd_seq,snd_rawmidi,snd_seq_midi
snd_timer           29482   2   snd_pcm,snd_seq
snd                 69322   18  snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
  ls -l /dev/snd/
  > total 0
drwxr-xr-x  2 root root       60 Mar 26 20:22 by-path
crw-rw----+ 1 root audio 116,  6 Mar 26 20:22 controlC0
crw-rw----+ 1 root audio 116,  5 Mar 26 20:22 hwC0D0
crw-rw----+ 1 root audio 116,  4 Mar 26 20:22 pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Mar 26 20:23 pcmC0D0p
crw-rw----+ 1 root audio 116,  2 Mar 26 20:22 pcmC0D2c
crw-rw----+ 1 root audio 116,  1 Mar 26 20:22 seq
crw-rw----+ 1 root audio 116, 33 Mar 26 20:22 timer
      


---

### Post by Yellow Pasque on 2015-03-27
Does Lubuntu use pulseaudio (I can never remember)?
If so, try clearing the pulseaudio configuration to reset it:
```
rm -r ~/.config/pulse
pulseaudio -k
pavucontrol
```

---

