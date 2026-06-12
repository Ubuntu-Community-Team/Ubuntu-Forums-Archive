---
title: "doesn't recognize internal sound card"
date: 2010-01-30
forum: Hardware
---

### Post by cskavai on 2010-01-30
Hi folks,
The gnome-volume-control program doesn't list my internal sound card, therefore there is no sound of it. It used to work when I installed Ubunu (ver 9.10), but after updated kernel to 2.6.31.17, sometimes it works, sometimes not. I have a Genius USB headset, it always works, when I plug it in, gnome-volume-control lists it as the only output device, but when I unplug, there is no output.
Can someone help me, please?

Here are some info:

lspci:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Uniwill Computer Corp Device 907c                                                  
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 32 bytes                                                                
        Interrupt: pin A routed to IRQ 16                                                                    
        Region 0: Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]                                   
        Capabilities: <access denied>                                                                        
        Kernel driver in use: HDA Intel                                                                      
        Kernel modules: snd-hda-intel                                                                        


lsmod:
Module                  Size  Used by
binfmt_misc            10220  1      
bridge                 56384  0      
stp                     3012  1 bridge
bnep                   15168  2       
vmnet                  49404  13      
ppdev                   8232  0       
parport_pc             37352  0       
vmblock                15240  1       
vsock                  46464  0       
vmci                   61704  1 vsock 
vmmon                  84620  0       
joydev                 13088  0       
snd_hda_codec_realtek   277860  1     
snd_hda_codec_si3054     5856  1      
arc4                    2144  2       
ecb                     3296  2       
iwl3945                90208  0       
iwlcore               133600  1 iwl3945
mac80211              210008  2 iwl3945,iwlcore
led_class               5256  2 iwl3945,iwlcore
snd_hda_intel          31880  3
snd_hda_codec          87584  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0
snd_seq_oss            33440  0
snd_seq_midi            8192  0
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
psmouse                57124  0
serio_raw               6596  0
btusb                  14260  2
iptable_filter          3872  0
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
cfg80211              109144  3 iwl3945,iwlcore,mac80211
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  17 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0
parport                40528  3 ppdev,parport_pc,lp
usbhid                 43968  0
ohci1394               33780  0
video                  23612  0
ieee1394              100896  1 ohci1394
radeon                684512  2
output                  3680  1 video
ttm                    43056  1 radeon
drm                   193856  4 radeon,ttm
i2c_algo_bit            7076  1 radeon
sky2                   55556  0
intel_agp              32816  0

---

### Post by toni77 on 2010-01-31
there is only one solution for this: in the Grub menu select Windows and it will always play your music. :p

---

### Post by cskavai on 2010-01-31
Just a piece of info: I installed kernel  2.6.31-14 again, and lo and behold: there is sound again. Just on the 2.6.31-17 (as well as 16) there is no sound.

---

### Post by cskavai on 2010-01-31
Just today I got an answer from another forum, I share with you if anyone gets interested. With kernel 2.6.31-17 I disabled the Software modem from System | Administration | Hardware Drivers menu, and the sound is working again (even without system reboot!).

Regards,
Csaba

---

