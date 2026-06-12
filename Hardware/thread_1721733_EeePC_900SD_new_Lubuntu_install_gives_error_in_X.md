---
title: "EeePC 900SD new Lubuntu install gives error in X"
date: 2011-04-04
forum: Hardware
---

### Post by fabricator4 on 2011-04-04
This morning I tried Lubuntu Live CD and everything worked well, so I did a full install on the machine.  Now when I boot, instead of automatically logging in I get an error that X cannot work and it drops me back to the login screen.  I tried the "netbook" login but there's no Network and even Chrome will not run - programs seem to be missing or not working.

I'm currently booted off the Lubuntu LiveCD on this machine as it's the only one I have available.  I'll have to reboot to get the exact error message.

Searches don't seem to throw up any know problems with Lubuntu and the 900SD.


The results of lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)

```

and lsmod:

```

Module                  Size  Used by
ppp_deflate             3726  0
zlib_deflate           19266  1 ppp_deflate
bsd_comp                4791  0
ppp_async               6778  1
crc_ccitt               1351  1 ppp_async
parport_pc             26058  0
ppdev                   5556  0
lp                      7342  0
dm_crypt               11385  0
parport                31492  3 parport_pc,ppdev,lp
snd_hda_codec_realtek   217980  1
joydev                  8735  0
snd_hda_intel          22107  1
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0
option                 13133  2
usb_wwan                9953  1 option
snd                    49006  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_s$
videodev               43098  1 uvcvideo
usbserial              33100  7 option,usb_wwan
psmouse                59033  0
v4l1_compat            13359  2 uvcvideo,videodev
soundcore                880  1 snd
serio_raw               4022  0
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
eeepc_laptop           14193  0
sparse_keymap           3145  1 eeepc_laptop
led_class               2633  1 eeepc_laptop
squashfs               25209  1
aufs                  152358  1953
nls_iso8859_1           3261  1
nls_cp437               4931  1
vfat                    9201  1
fat                    48240  1 vfat
dm_raid45              81721  0
xor                    15136  1 dm_raid45
i915                  290938  2
drm_kms_helper         30200  1 i915
drm                   168054  3 i915,drm_kms_helper
intel_agp              26360  2 i915
usb_storage            40172  2
atl1e                  29331  0
agpgart                32011  2 drm,intel_agp
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video


``` 

I feel like my arms are cut, not having a working machine to investigate this with.  Does anyone know of any know problems with this machine and Lubuntu, or can spot anything that might be causing problems.  Obviously the LiveCD works, and the machine has been running Ubuntu 10.04 and 11.04 beta no problems.

Chris

---

### Post by fabricator4 on 2011-04-05
Problem solved, though I'm not too sure what was causing it.  A third re-install this time formatting the /home partition worked fine.

FWIW Lubuntu is a great choice for this little machine.  1.5 GB of drive space used, and Gkrellm reports less than 70 MB of memory being used with nothing running (130 MB with Chrome in memory).  I do need to find out how to tweak things before I'll be happy with this install however

Chris.

---

