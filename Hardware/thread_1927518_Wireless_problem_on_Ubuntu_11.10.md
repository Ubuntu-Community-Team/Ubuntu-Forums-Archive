---
title: "Wireless problem on Ubuntu 11.10"
date: 2012-02-18
forum: Hardware
---

### Post by pasoleatis on 2012-02-18
Hello,


I have an Acer 4830tg laptop. I a having problems with the wireless connection. I have a 16 Mbps connection but I can barely get half of it, in addition  to this the connection drops very often which makes the streaming pretty annoying. I tried changing MDU from unlimited to 1492 and disable IPv6, but it did not solve the problem. I have Atheros  wireless card. Some pages suggested that the wrong module is loaded. i need some instructions about to unload the wrong module and make it use the proper one.

Edit.: I do not care so much about the speed. i am ok with 1Mbps, but I need the  connection to be constant so that I can work remotely. Is it possible to fix the problem by disabling the n mode?

---

### Post by wolfen69 on 2012-02-18
Please provide information of what hardware you are using. Post the output of:```
sudo lshw -C network
```

---

### Post by pasoleatis on 2012-02-18
> **wolfen69 said:**
> Please provide information of what hardware you are using. Post the output of:```
sudo lshw -C network
```

Hello,

Here it is:

```

~$ sudo lshw -C network
  *-network                                                                                                                            
       description: Ethernet interface                                                                                                 
       product: AR8151 v2.0 Gigabit Ethernet                                                                                           
       vendor: Atheros Communications                                                                                                  
       physical id: 0                                                                                                                  
       bus info: pci@0000:02:00.0                                                                                                      
       logical name: eth0                                                                                                              
       version: c0                                                                                                                     
       serial: b8:70:f4:7e:83:b4                                                                                                       
       capacity: 1Gbit/s                                                                                                               
       width: 64 bits                                                                                                                  
       clock: 33MHz                                                                                                                    
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation                                                                                                                                     
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair                                                                                                                 
       resources: irq:51 memory:d1b00000-d1b3ffff ioport:2000(size=128)                                                                
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: c0:f8:da:89:ad:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=xxx.xx.xx.xx latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d1a00000-d1a0ffff

```

I do not think that device is AR9287 bt some other version.

---

### Post by pasoleatis on 2012-02-18
Here is the output from lsmod:

```

Module                  Size  Used by
usb_storage            57901  0 
uas                    18027  0 
snd_seq_dummy          12798  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
vmnet                  55630  13 
vsock                  52478  0 
vmci                   86607  1 vsock
vmmon                  89457  0 
parport_pc             36962  0 
ppdev                  17113  0 
bbswitch               13355  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              12128183  0 [permanent]
snd_seq                61896  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
dm_multipath           27433  0 
ath9k                 127538  0 
mac80211              310872  1 ath9k
ath9k_common           13839  1 ath9k
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw              312866  2 ath9k,ath9k_common
psmouse                73882  0 
serio_raw              13166  0 
i915                  566711  2 
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
rts_pstor             445246  0 
drm_kms_helper         42558  1 i915
drm                   236330  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
mxm_wmi                12979  0 
sparse_keymap          13890  0 
wmi                    19256  1 mxm_wmi
video                  19412  1 i915
coretemp               13420  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  3 
libahci                26861  1 ahci
atl1c                  41643  0 
xhci_hcd               78641  0 

```

---

