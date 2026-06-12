---
title: "wifi problem sony vaio vgn-nr140e"
date: 2009-12-07
forum: Hardware
---

### Post by leofishman on 2009-12-07
Hi,

I need some help with my notebook.
I have installed a fresh version of karmic, everything works fine but the wireless card.

The argentinian ubuntu user group had helped me setting the card up in a live event, but is working very bad.
I am using ath5k driver on a atheros card, lspci:
*"06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)"*

The led indicator is not working and the wifi works very very bad, a lot of noise, this is the iwconfig:
          *Link Quality=70/70  Signal level=-26 dBm  Noise level=-98 dBm*


leo@vaio:~$ lsmod
Module                  Size  Used by
aes_i586                8124  2 
aes_generic            27484  1 aes_i586
ath5k                 124260  0 
mac80211              181236  1 ath5k
led_class               4096  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
ecb                     2524  2 
joydev                 10272  0 
snd_hda_codec_realtek   203328  1 
pcmcia                 36808  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_rawmidi            22208  1 snd_seq_midi
tifm_7xx1               5372  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_core               7832  1 tifm_7xx1
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                56500  0 
serio_raw               5280  0 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
sony_laptop            31972  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
ieee1394               86596  1 ohci1394
sky2                   46560  0 
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video


When using the original windows that came with the computer, everything works fine.

Thanks,
Leo

---

### Post by Deadwhisper on 2010-05-04
I'm having the same problem. Can somebody help please? I'm new to Ubuntu and installing 10.04. When running Windows Vista it seems to run fine.

I can't seem to find a fix for this WiFi issue. I also tried plugging in a network cable and it won't connect that way either.

It says I have a Marvell Technology Group LTD. 88E8039 for Ethernet Adapter and Atheros Communications Inc AR5001 for Wireless (dont know if that helps)

Please help.

Thanks

---

### Post by Deadwhisper on 2010-05-04
Correction - My ethernet IS working fine when plugging in a network cable directly. It is only the Wireless card that is not working.

I can scan and find wireless networks around but cant connect to them. It acts like it's connecting but never connects and eventually just stops.

Please help.

---

