---
title: "Nvidia 630m"
date: 2012-06-18
forum: Hardware
---

### Post by Pes88 on 2012-06-18
I have got a new laptop with Optimus technology! 

I didn't install bubble bee to use this technology but I would like to use the official Nvidia driver because I got some issues to use my system! It quite often freeze... 

Can I use the Nvidi Driver instead of intel one? 
Can I disable the Nvidia Driver and use just intel driver?

lspci -vvv 
```

01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 181b
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PleERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at a0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at b0000000 (64-bit, prefetchable) [size=32M]
        Region 5: I/O ports at 4000 [size=128]
        Expansion ROM at b2000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [78] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 <64us
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <4us
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x8, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -3.5dB
        Capabilities: [b4] Vendor Specific Information: Len=14 <?>
        Capabilities: [100 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Capabilities: [128 v1] Power Budgeting <?>
        Capabilities: [600 v1] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Kernel driver in use: nouveau
        Kernel modules: nouveau, nvidiafb

```

General Info : 

```

Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
Intel Corporation Ivy Bridge Graphics Controller (rev 09) NVIDIA Corporation Device 0de9 (rev a1)
ALSA Timer Device
ALSA Sequencer Device
HDA Intel PCH (STAC92xx Analog)
HDA Intel PCH(HDA Intel ALSA hardware specific Device)
HDA Intel PCH
HDA Intel PCH (HDMI 0)
Loopback device Interface
AR9285 Wireless Network Adapter (PCI-Express)
RTL8111/8168B PCI Express Gigabit Ethernet controller

```

Modules : 

```


Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
ath9k                 132390  0 
mac80211              506816  1 ath9k
psmouse                87692  0 
serio_raw              13211  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
joydev                 17693  0 
v4l2_compat_ioctl32    17128  1 videodev
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  3 ath9k,mac80211,ath
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
input_polldev          13896  1 lis3lv02d
lp                     17799  0 
parport                46562  2 ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
nouveau               774571  0 
ttm                    76949  1 nouveau
i915                  468764  4 
drm_kms_helper         46978  2 nouveau,i915
drm                   242038  7 nouveau,ttm,i915,drm_kms_helper
r8169                  62099  0 
i2c_algo_bit           13423  2 nouveau,i915
mxm_wmi                12979  1 nouveau
wmi                    19256  2 hp_wmi,mxm_wmi
video                  19596  2 nouveau,i915

```

---

