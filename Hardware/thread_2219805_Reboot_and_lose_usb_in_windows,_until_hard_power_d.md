---
title: "Reboot and lose usb in windows, until hard power down."
date: 2014-04-25
forum: Hardware
---

### Post by WTF_Shelley on 2014-04-25
So 14.04 64bit  is really stable for me and i installed from the release cd. If i reboot from unity into windows7 then my Keyboard and mouse both usb switch off during boot process and the only way to get them back is to switch the power off and wait a bit then boot into windows.

Any help would be wonderful
 
lspci
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT [Radeon HD 7870 GHz Edition]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)

```
lsusb
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 003: ID 1532:0015 Razer USA, Ltd 
Bus 003 Device 002: ID 046a:0011 Cherry GmbH G83 (RS 6000) Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
lsmod
```
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   19624  2 
rfcomm                 69160  8 
btusb                  32412  0 
bluetooth             395423  22 bnep,btusb,rfcomm
snd_hda_codec_hdmi     46207  1 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
snd_hda_codec_realtek    61438  1 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_seq_midi           13324  0 
ablk_helper            13597  1 aesni_intel
snd_hda_intel          52355  5 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_rawmidi            30144  1 snd_seq_midi
psmouse               102222  0 
serio_raw              13462  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
lpc_ich                21080  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82274  1 mei_me
fglrx                8085343  214 
amd_iommu_v2           19054  1 fglrx
soundcore              12680  1 snd
video                  19476  0 
parport_pc             32701  0 
mac_hid                13205  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
btrfs                 835954  1 
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
xor                    21411  1 btrfs
raid6_pq               97812  1 btrfs
libcrc32c              12644  1 btrfs
ahci                   25819  3 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169

```

---

### Post by chesaro on 2014-04-25
I'm not sure if this would work with your problem, but i have a slightly similar situation, when i reboot directly from windows to ubuntu, the wheel mouse goes crazy, the only way to keep this annoyance to the minimum was to shutdown the pc and then turn it on again, or remove and connect again the mouse usb port, it might not be a solution, but i'm not very sure why there's hardware that has this problems (i also had a similar problem when rebooting from windows to linux with the touch screen of a dell laptop)

---

