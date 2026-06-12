---
title: "Won't shutdown (instead reboots)"
date: 2010-07-05
forum: Hardware
---

### Post by solid000 on 2010-07-05
OK I have had this problem ever since 10.04 was released.  I have posted to alot of forums but mostly I have just been patiently waiting for a patch.  Ever since I upgraded to kubuntu 10.04 from kubuntu 9.x, my laptop will not shutdown.  I have tried "sudo shutdown -h now" and I have tried all the shutdown icons on the various menus.  In all cases, instead of shutting down, the system reboots (I even get to see the bios splash screen).  I am posting because it has been a few months and I am getting desperate as I shutdown every night because it is summer storm season where I live.

here is all the debugging info:
```

root@asus:~# uname -a
Linux asus 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
root@asus:~# lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
root@asus:~# lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_via      33207  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25677  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_via,snd_hda_intel
snd_pcm_oss            41394  0 
snd_hwdep               6924  1 snd_hda_codec
arc4                    1473  2 
snd_mixer_oss          16299  1 snd_pcm_oss
radeon                740390  2 
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
ath9k                 328989  0 
snd_seq_oss            31219  0 
ttm                    60847  1 radeon
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         30742  1 radeon
mac80211              238448  1 ath9k
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath                     9723  1 ath9k
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              148546  3 ath9k,mac80211,ath
snd                    71106  15 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_hwdep,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   199204  4 radeon,ttm,drm_kms_helper
video                  20623  0 
soundcore               8052  1 snd
output                  2503  1 video
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
asus_laptop            20584  0 
edac_core              45423  0 
uvcvideo               62467  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
led_class               3764  2 ath9k,asus_laptop
edac_mce_amd            9278  0 
i2c_piix4               9639  0 
i2c_algo_bit            6024  1 radeon
psmouse                64576  0 
v4l2_compat_ioctl32    12020  1 videodev
serio_raw               4918  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41084  0 
hid                    83440  1 usbhid
atl1e                  33233  0 
ahci                   37838  2 
root@asus:~# 


```

for sake of completeness, I have also tried several fixes each of which I backed out but here is the list:

I tried adding this line to the /etc/default/grub: GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force splash" and running update-grub

Also tried adding apm power_off=1 to /etc/modules and that does not help either.  Any help would be greatly appreciated.

---

### Post by IcarusR on 2010-07-05
Check the log files to see if there is any clue there.

Could also try removing the kernel boot parameter "quiet" in order to see what is happening when shutting down. May give a clue.

---

### Post by stumped on 2010-07-07
I have the exact same problem.
See here...  [http://ubuntuforums.org/showthread.php?t=1477489](http://ubuntuforums.org/showthread.php?t=1477489)

Still no answer.

---

