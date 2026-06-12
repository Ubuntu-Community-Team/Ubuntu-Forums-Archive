---
title: "Compaq 6715s wifi problem"
date: 2012-09-19
forum: Hardware
---

### Post by LINJEinc on 2012-09-19
Hi everyone!

did an install of latest ubuntu 12.04 LTS on my Compaq 6715s laptop, and having a big problem, installed with cable connected.
so i had internet, but when i disconect the cable, my wifi card
refuses to work.

Pretty new to linux on laptop, so i realy don't know where to start.

Broadcom BCM5906M ( rev 02) is the name of the integrated wifi card.

Anyone have any idea of how to solve this?

---

### Post by einonm on 2012-09-19
Hi there,

1) What happens when you click on the network icon (two opposing arrows or a quadrant of lines) in the top right of the desktop? Look for the line 'Wireless Networks' and the lines underneath.

2) open a terminal and type 'ifconfig', and post the output, along with the output of the 'lsmod' command.

---

### Post by chriz on 2013-07-07
Myself I'm loosing connection from time to time and then have to reboot or switch the adapter off and back on. But that does not always help immediately

Here is the list:
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:83:29:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:dc:af:7f  
          inet addr:192.168.0.206  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fedc:af7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9936 errors:0 dropped:0 overruns:0 frame:13246
          TX packets:9153 errors:86 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9117379 (9.1 MB)  TX bytes:1501667 (1.5 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:477049 (477.0 KB)  TX bytes:477049 (477.0 KB)

christian@6715s-2:~$ lsmod
Module                  Size  Used by
michael_mic            12613  4 
arc4                   12530  2 
joydev                 17694  0 
snd_hda_codec_analog    97900  1 
hp_wmi                 18093  0 
sparse_keymap          13891  1 hp_wmi
snd_hda_intel          34063  2 
snd_hda_codec         135141  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 49390  0 
kvm_amd                56136  0 
kvm                   422160  1 kvm_amd
parport_pc             32867  0 
ppdev                  17114  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 47562  12 
bnep                   18240  2 
snd                    83674  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           32181  0 
pcmcia_rsrc            18431  1 yenta_socket
psmouse               102506  0 
pcmcia_core            22615  3 pcmcia,yenta_socket,pcmcia_rsrc
edac_core              53053  0 
edac_mce_amd           23548  0 
k8temp                 13065  0 
serio_raw              13216  0 
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
sp5100_tco             13792  0 
i2c_piix4              13302  0 
btusb                  22432  0 
bluetooth             211812  24 rfcomm,bnep,btusb
video                  19653  0 
lib80211_crypt_tkip    17391  0 
wl                   3074942  0 
radeon                917823  3 
wmi                    19257  1 hp_wmi
mac_hid                13254  0 
ttm                    88495  1 radeon
cfg80211              208382  1 wl
lib80211               14382  2 lib80211_crypt_tkip,wl
drm_kms_helper         49259  1 radeon
drm                   290595  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13565  1 radeon
shpchp                 37278  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
pata_atiixp            13205  0 
ahci                   25869  2 
libahci                27338  1 ahci
tg3                   156646  0

---

