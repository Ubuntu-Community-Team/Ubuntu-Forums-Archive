---
title: "No sound"
date: 2019-08-03
forum: Hardware
---

### Post by kewldallas on 2019-08-03
[FONT=Lucida Grande][COLOR=#333333]I'm very new to Linux but trying to learn...

I installed an EFI bootable SSD of Ubuntu using MacBook Pro. No Sound.[/COLOR][/FONT]

[FONT=Lucida Grande][COLOR=#333333]I had originally tried working with Linux-Mint (LM) 19.1 and had the same issue.

So I know it has to do with compatibility of using the MacBook Pro.

I have installed both LM and Ubuntu as a VM using VirtualBox (on Win10) and sound works fine on both...

I have posted this issue under a LM Forum, with no success, so I thought I would try here 

[/COLOR][/FONT]sudo apt install inxi
```
inxi -FxzSystem:    Host: kewldallas-Ubuntu Kernel: 5.0.0-23-generic x86_64
           bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: Apple product: MacBookPro14 3 v: 1.0 serial: N/A
           Mobo: Apple model: Mac-551B86E5744E2388 v: MacBookPro14 3 serial: N/A
           UEFI: Apple v: 194.0.0.0.0 date: 04/11/2019
Battery    BAT0: charge: 66.0 Wh 97.0% condition: 68.1/76.7 Wh (89%)
           model: SMP bq20z451 status: Full
           hidpp__0: charge: N/A condition: NA/NA Wh
           model: Logitech MK700 status: Discharging
           hidpp__1: charge: 80% condition: NA/NA Wh
           model: Logitech M705 status: N/A
CPU:       Quad core Intel Core i7-7820HQ (-MT-MCP-) 
           arch: Skylake rev.9 cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 23232
           clock speeds: max: 3900 MHz 1: 912 MHz 2: 933 MHz 3: 938 MHz
           4: 992 MHz 5: 980 MHz 6: 932 MHz 7: 1000 MHz 8: 910 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Baffin [Radeon RX 460/560D / Pro 450/455/460/555/560]
           bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.4 ) driver: amdgpu
           Resolution: 2880x1800@60.00hz, 3840x2160@30.00hz, 3840x2160@30.00hz
           OpenGL: renderer: AMD Radeon RX Graphics (POLARIS11, DRM 3.27.0, 5.0.0-23-generic, LLVM 8.0.0)
           version: 4.5 Mesa 19.0.2 Direct Render: Yes
Audio:     Card-1 Intel 100 Series/C230 Series Family HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1f.3
           Card-2 Advanced Micro Devices [AMD/ATI] Device aae0
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k5.0.0-23-generic
Network:   Card: Broadcom and subsidiaries BCM43602 802.11ac Wireless LAN SoC
           driver: brcmfmac bus-ID: 03:00.0
           IF: wlp3s0 state: down mac: <filter>
Drives:    HDD Total Size: 1500.7GB (0.5% used)
           ID-1: /dev/nvme0n1 model: APPLE_SSD_SM1024L size: 1000.6GB
           ID-2: USB /dev/sda model: Portable_SSD_T5 size: 500.1GB temp: 0C
Partition: ID-1: / size: 457G used: 7.6G (2%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 64.0C mobo: N/A gpu: 57.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 306 Uptime: 37 min Memory: 2031.1/15935.2MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.201) inxi: 2.3.56 


```

aplay -l
```
aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Generic Analog [Generic Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

dmesg | grep snd
```
dmesg | grep snd[    5.510210] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[    5.510261] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[    5.510261] snd_hda_intel 0000:01:00.1: Force to non-snoop mode
[    5.531210] snd_hda_codec_generic hdaudioC0D0: autoconfig for Generic: line_outs=2 (0x24/0x25/0x0/0x0/0x0) type:speaker
[    5.531212] snd_hda_codec_generic hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.531213] snd_hda_codec_generic hdaudioC0D0:    hp_outs=1 (0x2c/0x0/0x0/0x0/0x0)
[    5.531214] snd_hda_codec_generic hdaudioC0D0:    mono: mono_out=0x0
[    5.531215] snd_hda_codec_generic hdaudioC0D0:    inputs:
[    5.531216] snd_hda_codec_generic hdaudioC0D0:      Internal Mic=0x44
[    5.531217] snd_hda_codec_generic hdaudioC0D0:      Mic=0x3c



```

---

### Post by gdesilva on 2019-08-06
Have you tried alsamixer ? You need to run this in a terminal. Select the sound card using F6 and  make sure the outputs are not muted - if muted there will be 'm' in the appropriate column. Pressing 'm' on the keyboard will toggle mute/unmute and make sure the sound levels are high enough.

---

