---
title: "brand new ACER with Atheros AR9285 wireless adptr not working on 11.04"
date: 2011-08-12
forum: Hardware
---

### Post by mcalautt on 2011-08-12
sorry if this has been posted before but I could not find any related topics.


Has this problem been fixed for the AR9285  ?
 I just bought a brand new Acer Aspire AS5733Z-4445 Intel Pentium   P6100(2.00GHz) 15.6" 3GB Memory 320GB HDD Intel HD Graphics Notebook
 installed the latest ubuntu 11.04.
 Nothing shows up in a wireless scan and if I enter my access point info in manually it doesnt work.
also odd, sometimes iwlist scan returns info for wlan0 and sometimes it doesnt.
 here is some info from my laptop.




  lshw -C Network
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:b8:7f:39
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k  driverversion=2.6.38-10-generic firmware=N/A latency=0 link=yes  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d240ffff


 nm-tool
  - Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        68:A3:C4:B8:7F:39
   Capabilities:
   Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
   Wireless Access Points
    carcass:         Infra, 00:18:01:EF:6A:BA, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2


  lsmod
Module                  Size  Used by
cryptd                 20510  0
aes_x86_64             17208  0
aes_generic            38279  1 aes_x86_64
joydev                 17606  0
parport_pc             36959  0
ppdev                  17113  0
snd_hda_codec_realtek   336771  1
arc4                   12529  2
snd_hda_intel          33211  2
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
ath9k                 116068  0
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17565  1
i915                  514975  3
snd_timer              29602  2 snd_pcm,snd_seq
mac80211              296672  1 ath9k
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0
sparse_keymap          13898  0
snd                    67382  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,   snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,sn  d_seq_device
ath9k_common           14069  1 ath9k
ath9k_hw              329532  2 ath9k,ath9k_common
ath                    23779  2 ath9k,ath9k_hw
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
psmouse                73535  0
soundcore              12680  1 snd
intel_ips              18097  0
serio_raw              13166  0
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              181865  3 ath9k,mac80211,ath
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0
uas                    17996  0
ahci                   25951  2
libahci                26642  1 ahci
tg3                   141750  0


 Aspire-5733Z:~# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by wnelson on 2011-08-13
Try sudo modprobe -r acer_wmi. if that works add it to /etc/modules

---

### Post by mcalautt on 2011-08-15
thanks !
I tried that.. didnt get anything when I ran -r.  
still nothing... it wont pick up a signal at all.. from any wireless router.

---

### Post by mcalautt on 2011-08-19
amazing update.
I have been seeing a bunch of people claiming they can connect but the connection is very unstable.
I was wondering why I cant connect at all.?

so i brought it into work and gave it to a friend. He got it to work.. I said how ?
he did the same things I did.. checked rfkill list and blacklisted acer-wmi.  ( i saw posts about that
but ignored it since I dont have acer-wmi in a lsmod)
but i didnt care . he got it to work !!!

I brought it home... amazing. no connection...
and then it hit me... sun of a beeatch !!! I went down stairs and got closer to the router.
it connected instantly..
but now I have the problem that others are having.. extremely poor speed and unstable connection..

---

### Post by mcalautt on 2011-08-20
this worked for me .. seems ok so far.

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf

---

### Post by mcalautt on 2011-08-24
now im mad..

its extremely unstable and I can see the router from where I am.. !!!!
take 2 steps foward and it will connect..
the range is miserable !!
so as far as im concerned its not usable and the problem still exists.

---

