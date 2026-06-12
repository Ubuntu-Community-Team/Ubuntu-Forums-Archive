---
title: "tuner stopped working after motherboard replace."
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by poorotis on 2008-01-17
Gutsy / 2.6.22-14-generic / i386 is installed.

I have 2 bttv cards installed, one of them has FM radio.
It was working great previously. I have now replaced "asus A8N5X" motherboard with "gigabyte GA-M56S-S3" and "Athlon 64 3000+" with "Athlon64 X2 6000+", did not touch any configs.
Now when I trying to access /dev/radio0, I am getting kernel oops:
----------------
[  278.660000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000034
[  278.660000]  printing eip:
[  278.660000] f8b13601
[  278.660000] *pde = 00000000
[  278.660000] Oops: 0000 [#1]
[  278.660000] SMP 
[  278.660000] Modules linked in: snd_rtctimer vmnet(P) vmblock(P) vmmon(P) af_packet binfmt_misc ipv6 rfcomm l2cap nfsd exportfs lockd sunrpc ppdev powernow_k8 cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table video container sbs button dock ac battery sbp2 lp usbhid hid usb_storage libusual hci_usb bluetooth snd_hda_intel nvidia(P) snd_pcm_oss snd_mixer_oss snd_pcm agpgart snd_seq_dummy snd_seq_oss bt878 snd_seq_midi snd_rawmidi sg snd_seq_midi_event snd_seq snd_timer snd_seq_device tuner shpchp sd_mod bttv parport_pc parport video_buf ir_common pcspkr xpad compat_ioctl32 psmouse serio_raw pci_hotplug snd soundcore i2c_algo_bit btcx_risc k8temp tveeprom videodev v4l2_common v4l1_compat snd_page_alloc i2c_nforce2 i2c_core evdev reiserfs ide_disk ide_cd cdrom amd74xx ide_core ohci1394 ieee1394 ahci ata_generic libata scsi_mod forcedeth ehci_hcd ohci_hcd usbcore thermal processor fan fuse apparmor commoncap
[  278.660000] CPU:    1
[  278.660000] EIP:    0060:[<f8b13601>]    Tainted: P       VLI
[  278.660000] EFLAGS: 00010246   (2.6.22-14-generic #1)
[  278.660000] EIP is at radio_open+0x31/0x100 [bttv]
[  278.660000] eax: 00000000   ebx: 00000040   ecx: 00000000   edx: 00000000
[  278.660000] esi: 00000002   edi: f70a0600   ebp: 00000000   esp: f7601ea8
[  278.660000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
[  278.660000] Process wmtune (pid: 6918, ti=f7600000 task=f70cf4c0 task.ti=f7600000)
[  278.660000] Stack: f7e71020 00000000 f899d260 f70a0600 dfeea3c0 f899cd68 000000ff c0182ce0 
[  278.660000]        00000051 f899ccd0 df89c420 00000000 dfeea3c0 c0183416 f70a0600 00000040 
[  278.660000]        f70a0600 dfeea3c0 f7601f30 c0183370 c017ebf8 c319b380 dfaa27f8 f70a0600 
[  278.660000] Call Trace:
[  278.660000]  [<f899cd68>] video_open+0x98/0x130 [videodev]
[  278.660000]  [<c0182ce0>] exact_match+0x0/0x10
[  278.660000]  [<f899ccd0>] video_open+0x0/0x130 [videodev]
[  278.660000]  [<c0183416>] chrdev_open+0xa6/0x190
[  278.660000]  [<c0183370>] chrdev_open+0x0/0x190
[  278.660000]  [<c017ebf8>] __dentry_open+0xb8/0x1c0
[  278.660000]  [<c017edb5>] nameidata_to_filp+0x35/0x40
[  278.660000]  [<c017ee10>] do_filp_open+0x50/0x60
[  278.660000]  [<c017ee6e>] do_sys_open+0x4e/0xf0
[  278.660000]  [<c017ef4c>] sys_open+0x1c/0x20
[  278.660000]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[  278.660000]  =======================
[  278.660000] Code: ec 08 8b 58 34 a1 00 4a b3 f8 81 e3 ff ff 0f 00 85 c0 0f 85 a6 00 00 00 8b 35 08 4a b3 f8 85 f6 74 30 a1 94 4e b3 f8 31 c9 31 d2 <39> 58 34 75 1b e9 b6 00 00 00 90 8d 74 26 00 8b 82 08 57 b3 f8 
[  278.660000] EIP: [<f8b13601>] radio_open+0x31/0x100 [bttv] SS:ESP 0068:f7601ea8
----------------

Here is the bttv init process from dmesg:
----------------
[   11.092000] bttv: driver version 0.9.17 loaded
[   11.092000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.092000] bttv: Bt8xx card found (0).
[   11.092000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   11.092000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 21
[   11.092000] bttv0: Bt878 (rev 17) at 0000:01:07.0, irq: 21, latency: 32, mmio: 0xf2100000
[   11.092000] bttv0: detected: Pinnacle PCTV [bswap] [card=39], PCI subsystem ID is bd11:1200
[   11.092000] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,insmod option]
[   11.092000] bttv0: gpio: en=00000000, out=00000000 in=00ff3fff [init]
[   11.092000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   11.092000] bttv0: miro: id=15 tuner=16 radio=no stereo=no
[   11.092000] bttv0: using tuner=16
[   11.092000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   11.092000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   11.096000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   11.096000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   11.176000] tuner 2-0060: All bytes are equal. It is not a TEA5767
[   11.176000] tuner 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   11.176000] tuner 2-0060: type set to 16 (Temic PAL_DK (4016 FY5))
[   11.176000] tuner 2-0060: type set to 16 (Temic PAL_DK (4016 FY5))
[   11.208000] bttv0: registered device video0
[   11.208000] bttv0: registered device vbi0
[   11.208000] bttv0: PLL: 28636363 => 35468950 .. ok
[   11.240000] bttv: Bt8xx card found (1).
[   11.240000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   11.240000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 22
[   11.240000] bttv1: Bt878 (rev 17) at 0000:01:09.0, irq: 22, latency: 32, mmio: 0xf2102000
[   11.240000] bttv1: using: Jetway TV/Capture JW-TV878-FBK, Kworld KW-TV878RF [card=78,insmod option]
[   11.240000] bttv1: gpio: en=00000000, out=00000000 in=003fffff [init]
[   11.244000] tuner 3-0060: All bytes are equal. It is not a TEA5767
[   11.244000] tuner 3-0060: chip found @ 0xc0 (bt878 #1 [sw])
[   11.248000] bttv1: using tuner=5
[   11.248000] tuner 3-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   11.248000] bttv1: i2c: checking for TDA9875 @ 0xb0... not found
[   11.248000] bttv1: i2c: checking for TDA7432 @ 0x8a... not found
[   11.248000] bttv1: i2c: checking for TDA9887 @ 0x86... not found
[   11.264000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.264000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   11.264000] bttv1: registered device video1
[   11.264000] bttv1: registered device vbi1
[   11.264000] bttv1: registered device radio0
[   11.264000] bttv1: PLL: 28636363 => 35468950 .. ok
[   11.296000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.352000] bt878: AUDIO driver version 0.0.0 loaded
[   11.352000] bt878: Bt878 AUDIO function found (0).
[   11.352000] ACPI: PCI Interrupt 0000:01:07.1[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 21
[   11.352000] bt878_probe: card id=[0x1200bd11], Unknown card.
[   11.352000] Exiting..
[   11.352000] ACPI: PCI interrupt for device 0000:01:07.1 disabled
[   11.352000] bt878: probe of 0000:01:07.1 failed with error -22
[   11.352000] bt878: Bt878 AUDIO function found (0).
[   11.352000] ACPI: PCI Interrupt 0000:01:09.1[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 22
[   11.352000] bt878_probe: card id=[0x0], Unknown card.
[   11.352000] Exiting..
[   11.352000] ACPI: PCI interrupt for device 0000:01:09.1 disabled
[   11.352000] bt878: probe of 0000:01:09.1 failed with error -22
----------------

here is some additional info:
------
 cat /etc/modprobe.d/tuner 
options bttv card=39,78
------

------
$ lsmod |egrep "bt"
snd_bt87x              16420  0 
snd_pcm                80388  3 snd_bt87x,snd_hda_intel,snd_pcm_oss
bt878                  11832  0 
bttv                  177012  2 bt878
video_buf              26244  1 bttv
ir_common              35460  1 bttv
compat_ioctl32          2304  1 bttv
snd                    54660  15 snd_bt87x,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            7428  1 bttv
btcx_risc               5896  1 bttv
tveeprom               16784  1 bttv
videodev               29312  11 bttv
v4l2_common            18432  3 tuner,bttv,videodev
v4l1_compat            15364  2 bttv,videodev
snd_page_alloc         11400  3 snd_bt87x,snd_hda_intel,snd_pcm
i2c_core               26112  6 nvidia,tuner,bttv,i2c_algo_bit,tveeprom,i2c_nforce2
------

------
$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 SATA controller: nVidia Corporation MCP65 AHCI Controller (rev a3)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

$ lspci -n
00:00.0 0500: 10de:0444 (rev a3)
00:01.0 0601: 10de:0441 (rev a3)
00:01.1 0c05: 10de:0446 (rev a1)
00:01.2 0500: 10de:0445 (rev a1)
00:02.0 0c03: 10de:0454 (rev a3)
00:02.1 0c03: 10de:0455 (rev a3)
00:06.0 0200: 10de:0450 (rev a3)
00:07.0 0403: 10de:044a (rev a1)
00:08.0 0604: 10de:0449 (rev a1)
00:09.0 0101: 10de:0448 (rev a1)
00:0a.0 0106: 10de:044d (rev a3)
00:0d.0 0604: 10de:0458 (rev a1)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:07.0 0400: 109e:036e (rev 11)
01:07.1 0480: 109e:0878 (rev 11)
01:09.0 0400: 109e:036e (rev 11)
01:09.1 0480: 109e:0878 (rev 11)
01:0e.0 0c00: 104c:8024
02:00.0 0300: 10de:0140 (rev a2)
------

Maybe someone know how to deal with this issue?

---

