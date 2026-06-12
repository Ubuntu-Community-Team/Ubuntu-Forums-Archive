---
title: "HPG70-460 US atheros wifi card is not detected auto. from &quot;Additional drivers&quot;"
date: 2011-04-21
forum: Hardware
---

### Post by samMD on 2011-04-21
Looks like i installed ubuntu while i had my card off (there is a button to turn it on and off) so now it remains off. I posted the output of the two commands below 

this the info on my card: Network controller: Atheros Communications Inc. **AR928X Wireless Network** 


**sudo lsmod**

Module                  Size  Used by
udf                    79366  0 
crc_itu_t               1383  1 udf
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
joydev                  8767  0 
arc4                    1165  2 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_conexant    30003  1 
i915                  295435  5 
drm_kms_helper         30200  1 i915
snd_hda_intel          22235  2 
drm                   168060  5 i915,drm_kms_helper
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
ath9k                  88884  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ath9k_common            5982  1 ath9k
snd_timer              19067  2 snd_pcm,snd_seq
ath9k_hw              292329  2 ath9k,ath9k_common
ath                     8153  2 ath9k,ath9k_hw
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
mac80211              231959  2 ath9k,ath9k_common
videodev               43098  1 uvcvideo
hp_wmi                  5223  0 
v4l1_compat            13359  2 uvcvideo,videodev
cfg80211              144694  4 ath9k,ath9k_common,ath,mac80211
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26566  2 i915
led_class               2633  1 ath9k
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40204  0 
ahci                   19198  2 
libahci                21728  1 ahci
r8169                  36521  0 
mii                     4425  1 r8169

**sudo ifconfig -a :**

eth0      Link encap:Ethernet  HWaddr 00:1f:16:da:a5:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1744 (1.7 KB)  TX bytes:1744 (1.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:56:93:a2:5a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by samMD on 2011-06-07
found the solution here: [http://www.linuxforums.org/forum/ubuntu-linux/176409-ubuntu-additional-drivers-tool-not-finding-wifi-card.html](http://www.linuxforums.org/forum/ubuntu-linux/176409-ubuntu-additional-drivers-tool-not-finding-wifi-card.html)

---

