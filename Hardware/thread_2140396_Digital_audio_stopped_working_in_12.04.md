---
title: "Digital audio stopped working in 12.04"
date: 2013-04-29
forum: Hardware
---

### Post by mteppo on 2013-04-29
I have automatical updates on my livingroom ubuntu-box so cannot know exactly when this happened...

Now the sound is going just click-click-click roughly with 0.5second interval.
If I mute the sound the clicking stops. 
No other audio (speaker tests, audio files, video soundtracs) are being played

HW:
- Asus P5-D motherboard with integrated audio
- Nvidia 9600GT display adapter - connection cable for audio passthrough
- DVI-HDMI adapter
- Philips television on the other end of HDMI cable

And this was working at least 3 weeks or so ago.


So the kernel version
```

$ uname -a
Linux olohuone 3.2.0-40-generic #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

Nvidia drivers (although should this really matter as the HDMI sound is just passing through?):
```

$ dpkg -l | grep nvidia
ii  nvidia-173                             173.14.35-0ubuntu0.2                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                          1:0.2.44.2                               Find obsolete NVIDIA drivers
ii  nvidia-current                         304.88-0ubuntu0.0.2                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        304.88-0ubuntu0.0.2                      Tool of configuring the NVIDIA graphics driver

```
Using nvidia-current (checked with the nvidia-settings, which shows 304.88 now)

All devices in PCI - interface
```

$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G94 [GeForce 9600 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```



On Sound Settings I have still Digital Output selected (tried to play with the settings - thumping stops whenever I use other devices, starts again whenever I use this digital output)

Kernel modules 
```
$ lsmod
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
nfsd                  281980  13 
nfs                   436914  0 
lockd                  90326  2 nfsd,nfs
fscache                61529  1 nfs
auth_rpcgss            53380  2 nfsd,nfs
nfs_acl                12883  2 nfsd,nfs
sunrpc                255224  19 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
vesafb                 13844  1 
snd_hda_codec_analog    97987  1 
nvidia              11308613  40 
ppdev                  17113  0 
snd_hda_intel          33719  1 
snd_hda_codec         127706  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
psmouse                97485  0 
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32866  1 
asus_atk0110           18078  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
snd                    79041  11 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
hwmon_vid              12827  0 
coretemp               13554  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
r8169                  62154  0 
hid_logitech_dj        18730  0 
usbhid                 47238  1 hid_logitech_dj
hid                    99636  2 hid_logitech_dj,usbhid

```


I have checked dmesg (I could not see anything related - here is short piece on the initialization of the audio)
```

[   10.256971] w83627ehf: Found W83627DHG chip at 0x290
[   10.256999] ACPI: resource w83627ehf [io  0x0295-0x0296] conflicts with ACPI region HWRE [io 0x290-0x299]
[   10.257003] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.289550] parport_pc 00:0a: reported by Plug and Play ACPI
[   10.289666] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   10.291184] type=1400 audit(1367254665.793:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=460 comm="apparmor_pars
er"
[   10.291548] type=1400 audit(1367254665.793:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.acti
on" pid=460 comm="apparmor_parser"
[   10.291756] type=1400 audit(1367254665.793:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" p
id=460 comm="apparmor_parser"
[   10.294427] type=1400 audit(1367254665.797:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=493 comm="apparmor_pars
er"
[   10.346603] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.346649] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   10.346673] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   10.390453] lp0: using parport0 (interrupt-driven).
[   10.398697] nvidia: module license 'NVIDIA' taints kernel.
[   10.398701] Disabling lock debugging due to kernel taint
[   10.426020] ppdev: user-space parallel port driver
[   10.627456] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.627464] nvidia 0000:01:00.0: setting latency timer to 64

```

I'm bit at loss here how to continue on this - any pointers on investigating if this is a kernel, sound (pulseaudio?) or nvidia related issue is very welcome.
Also if I can provide anything more please do ask and I will try...
Also possible that our TV went somehow broken. Still I can get sound over HDMI from XBOX, so would think that is not the case...

---

