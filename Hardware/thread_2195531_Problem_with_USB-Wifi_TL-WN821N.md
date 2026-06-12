---
title: "Problem with USB-Wifi TL-WN821N"
date: 2013-12-24
forum: Hardware
---

### Post by drodezno on 2013-12-24
Problem with USB-Wifi TL-WN821N:

Hi Everyone I recently bought an USB-Wifi model "TL-WN821N" but I'm having problems using it.
When I used it for the first time, I just connected it and worked well; but when I was using my computer again It did not work, and never worked the other times I tried, Actually It does not work anymore.

What can I do? 

PLEASE HELP!

---

### Post by mikewhatever on 2013-12-25
Take a look at [post one here]("http://askubuntu.com/questions/238140/internet-timeouts-with-tp-link-tl-wn821n-v2-wireless-usb-stick"). You should provide the same outputs to, ...well, help us help you.

---

### Post by drodezno on 2014-01-12
> **mikewhatever said:**
> Take a look at [post one here]("http://askubuntu.com/questions/238140/internet-timeouts-with-tp-link-tl-wn821n-v2-wireless-usb-stick"). You should provide the same outputs to, ...well, help us help you.

Hello and first I want to apologise for answering late, but it is because I've been very busy.

well I will give the outputs now.

1. I think there might be something wrong with this output, it seems it has 2 drivers installed. And it seems this is the only output that shows the device we are talking about. 

diego@diego-Dell-System-Inspiron-N411Z:~$ lsusb
Bus 002 Device 005: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 802.11n [Atheros AR7010+AR9287]

2. I pasted this all because it seems I dont find the information that matches the first output result. 

Module                  Size  Used by
btrfs                 816158  0 
zlib_deflate           27110  1 btrfs
ufs                    75150  0 
qnx4                   13396  0 
hfsplus                89061  0 
hfs                    54780  0 
minix                  36386  0 
ntfs                  101633  0 
msdos                  17332  0 
jfs                   186588  0 
xfs                   888367  0 
libcrc32c              12615  2 btrfs,xfs
reiserfs              248298  0 
ext2                   73755  0 
pci_stub               12622  1 
vboxpci                23236  0 
vboxnetadp             25670  0 
vboxnetflt             27612  0 
vboxdrv               335187  3 vboxpci,vboxnetadp,vboxnetflt
vmnet                  55722  13 
vsock                  52889  0 
vmci                   87376  1 vsock
vmmon                  80249  0 
rfcomm                 47864  12 
bnep                   18258  2 
parport_pc             28284  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
uvcvideo               82214  0 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
coretemp               13596  0 
kvm_intel             137899  0 
kvm                   455932  1 kvm_intel
ath3k                  12968  0 
ghash_clmulni_intel    13259  0 
btusb                  22431  0 
bluetooth             247165  25 rfcomm,bnep,ath3k,btusb
snd_hda_codec_hdmi     37463  1 
snd_hda_codec_conexant    62464  1 
i915                  620571  3 
aesni_intel            55495  1 
ablk_helper            13597  1 aesni_intel
joydev                 17613  0 
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
snd_hda_intel          44339  3 
drm_kms_helper         49597  1 i915
arc4                   12573  2 
aes_x86_64             17255  1 aesni_intel
drm                   287564  4 i915,drm_kms_helper
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
ath9k                 151796  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              630977  1 ath9k
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
psmouse                97873  0 
ath9k_common           14053  1 ath9k
ath9k_hw              422432  2 ath9k,ath9k_common
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13564  1 i915
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
snd_timer              29989  2 snd_pcm,snd_seq
serio_raw              13215  0 
dell_wmi               12681  0 
dell_laptop            17425  0 
sparse_keymap          13890  1 dell_wmi
video                  19652  1 i915
cfg80211              525326  3 ath9k,mac80211,ath
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41820  0 
soundcore              12680  1 snd
mac_hid                13253  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
dcdbas                 14449  1 dell_laptop
wmi                    19256  1 dell_wmi
microcode              23017  0 
lpc_ich                17144  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            18256  0 
usb_storage            61749  1 ums_realtek
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105826  2 hid_generic,usbhid
atl1c                  41977  0 
ahci                   25879  2 
libahci                31606  1 ahci

3. The next output just show the wify of my notebook, but it does not show the USB-Wifi, wish I remember was "wlan1", the only time I used it.

diego@diego-Dell-System-Inspiron-N411Z:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"Familia R-CH"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:19:A6:3A   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:65   Missed beacon:0

4. In this one again it only show the ethernet and wify of the notebook, not the usb wify.

diego@diego-Dell-System-Inspiron-N411Z:~$ sudo lshw -C network
[sudo] password for diego: 
  *-network               
       descripción: Interfaz inalámbrica
       producto: AR9285 Wireless Network Adapter (PCI-Express)
       fabricante: Qualcomm Atheros
       id físico: 0
       información del bus: pci@0000:02:00.0
       nombre lógico: wlan0
       versión: 01
       serie: 7c:e9:d3:8a:8b:75
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=ath9k driverversion=3.8.0-34-generic firmware=N/A ip=192.168.1.108 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       recursos: irq:17 memoria:d0600000-d060ffff
  *-network
       descripción: Ethernet interface
       producto: AR8152 v2.0 Fast Ethernet
       fabricante: Qualcomm Atheros
       id físico: 0
       información del bus: pci@0000:04:00.0
       nombre lógico: eth0
       versión: c1
       serie: 84:8f:69:cc:65:13
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       recursos: irq:49 memoria:d0400000-d043ffff ioport:2000(size=128)

---

### Post by berthold-t on 2014-01-13
Had same problem with usb wifi card. solved by physically removing the inbuilt wifi card because could not stop system switching between WLAN0 and WLAN1...(lenovo ideapad s 10-2)

---

### Post by drodezno on 2014-01-15
> **berthold-t said:**
> Had same problem with usb wifi card. solved by physically removing the inbuilt wifi card because could not stop system switching between WLAN0 and WLAN1...(lenovo ideapad s 10-2)

Yes but my situation is very weird because in my pc the first and only time I could use the usb wify I could choose wlan0 or wlan1 OR EVEN use both of them.! :mad:

---

