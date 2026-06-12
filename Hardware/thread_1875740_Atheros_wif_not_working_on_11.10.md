---
title: "Atheros wif not working on 11.10"
date: 2011-11-05
forum: Hardware
---

### Post by Zerberus on 2011-11-05
Hey It wasnt working from the beginning after install. I had to use Dr. Kurians method [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

on Lucid and Maverick but never required it from then on. However currently it's not working whatsoever. I have the following information below





> zerberus@Zerb:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:a3:d3:ae  
          inet addr:10.33.10.48  Bcast:10.33.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fea3:d3ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:315317 (315.3 KB)  TX bytes:97012 (97.0 KB)
          Interrupt:44 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




zerberus@Zerb:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)





zerberus@Zerb:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
i915                  505108  4 
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
usb_storage            44173  2 
snd_rawmidi            25241  1 snd_seq_midi
uas                    17699  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41905  0 
snd_timer              28932  2 snd_pcm,snd_seq
hid                    77367  1 usbhid
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
binfmt_misc            17292  1 
drm                   192226  5 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wlan_scan_sta          21921  1 
ath_rate_sample        17279  1 
i2c_algo_bit           13199  1 i915
wmi                    18744  1 acer_wmi
video                  18908  1 i915
ath_pci               187697  0 
wlan                  221175  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               398451  3 ath_rate_sample,ath_pci
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 


---

### Post by Zerberus on 2011-11-07
bump

---

### Post by roman5x3 on 2011-11-10
Same problem here? Anyone have a clue?
Roman

---

### Post by IcarusR on 2011-11-10
Do you both have acers ? There was a bug with acer_wmi causing wifi to be turned off. This was fixed in recent kernels.
May be worth trying rmmod on acer_wmi & see if wifi then works. 
```
sudo rmmod acer_wmi
```
I don't know what the effects of not running acer_wmi on other hardware will be.
Reboot will reload acer_wmi & dependant modules if it doesn't work.

---

