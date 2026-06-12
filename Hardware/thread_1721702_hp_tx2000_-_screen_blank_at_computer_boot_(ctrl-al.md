---
title: "hp tx2000 - screen blank at computer boot (ctrl-alt-f6 -&gt; ctrl-alt-f7)"
date: 2011-04-04
forum: Hardware
---

### Post by s3gfault on 2011-04-04
I'm having a difficult problem with my tx2000 laptop.  I'm running maverick amd64 and most everything is working, but when the computer boots for the first time the screen does not activate.  Pressing ctrl-alt-f6 and then ctrl-alt-f7 will bring the screen up, but it's difficult for my wife to remember this key sequence and it is becoming a source of frustration.  Has anyone solved this problem?  Here is some info on my hardware and modules:

```
$ sudo lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
$ sudo lsmod
Module                  Size  Used by
michael_mic             2188  4 
arc4                    1497  2 
parport_pc             30086  0 
dm_crypt               13381  0 
ppdev                   6804  0 
snd_hda_codec_si3054     4292  1 
snd_hda_codec_realtek   300173  1 
binfmt_misc             7984  1 
nvidia              10221046  45 
rfcomm                 40787  4 
sco                     9986  2 
bnep                   11985  2 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
l2cap                  42304  16 rfcomm,bnep
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     8732  0 
hp_wmi                  6467  0 
uvcvideo               62379  0 
joydev                 11395  0 
btusb                  12929  2 
wl                   1965231  0 
videodev               49359  1 uvcvideo
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
snd                    64181  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            15519  2 uvcvideo,videodev
edac_core              46822  0 
wacom                  32508  0 
psmouse                62080  0 
v4l2_compat_ioctl32    12614  1 videodev
soundcore               1240  1 snd
edac_mce_amd            9387  0 
serio_raw               4910  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
k8temp                  4128  0 
i2c_nforce2             6155  0 
lib80211                6175  2 lib80211_crypt_tkip,wl
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  1 usbhid
video                  22176  0 
output                  2527  1 video
pata_amd               12050  0 
sata_nv                23770  2 
forcedeth              55649  0 

```

---

### Post by Favux on 2011-04-04
Hi s3gfault,

According to this thread it's a bug in the 2.6.35 kernel:  [http://ubuntuforums.org/showthread.php?t=1654787](http://ubuntuforums.org/showthread.php?t=1654787)  The "fix" is in post #5 where you use a PPA to upgrade to a 2.6.37 kernel.  Although it's not clear that actually works for everyone.  No recent activity on the Launchpad bug they link to, so you might want to consider reviving that if you can't get it working.

Are you using the Xorg Nvidia driver or the proprietary Nvidia drivers.

---

### Post by s3gfault on 2011-04-05
> **Favux said:**
> Hi s3gfault,

According to this thread it's a bug in the 2.6.35 kernel:  [http://ubuntuforums.org/showthread.php?t=1654787](http://ubuntuforums.org/showthread.php?t=1654787)  The "fix" is in post #5 where you use a PPA to upgrade to a 2.6.37 kernel.  Although it's not clear that actually works for everyone.  No recent activity on the Launchpad bug they link to, so you might want to consider reviving that if you can't get it working.

Are you using the Xorg Nvidia driver or the proprietary Nvidia drivers.

Thanks Favux, i'm using the proprietary Nvidia drivers, I think my problem matches that one and I'll try the new kernel tonight.

---

