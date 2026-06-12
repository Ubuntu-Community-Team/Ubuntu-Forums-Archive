---
title: "inspiron 1521 installed drivers for wireless but cant access it"
date: 2012-05-29
forum: Hardware
---

### Post by kensauaga on 2012-05-29
Well i think that everything installed right but nothing see the card as installed. here is what i got.



03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01fc]
    Flags: bus master, fast devsel, latency 64, IRQ 21
    Memory at fe5fe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: wl, ssb


[IMG]https://lh3.googleusercontent.com/-VlPgyOxvr0U/T8WKeTdci1I/AAAAAAAAC0s/SsWUvdLE1ew/s576/Screenshot%2520from%25202012-05-29%252019%253A43%253A47.png[/IMG]




i cant select it as a net work device? 

[IMG]https://lh5.googleusercontent.com/-y_-1-o1RyHs/T8WM1VjarTI/AAAAAAAAC00/8OdS3jMji-0/s558/Screenshot%2520from%25202012-05-29%252019%253A53%253A53.png[/IMG]


Let me know if you need anymore info.
thank you for your help and time.

---

### Post by kensauaga on 2012-05-29
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by bohemian9485 on 2012-05-30
Can you print out the result of command ```
lsmod | grep cfg80211
```?

---

### Post by kensauaga on 2012-05-30
> **bohemian9485 said:**
> Can you print out the result of command ```
lsmod | grep cfg80211
```?


:(
That did not return anything? not even an error?


here is just lsmod

Module                  Size  Used by
joydev                 17693  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
r852                   18277  0 
snd_timer              29990  2 snd_pcm,snd_seq
sm_common              16865  1 r852
nand                   54955  2 r852,sm_common
psmouse                87692  0 
r592                   18144  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
nand_ids               12723  1 nand
mtd                    33087  2 sm_common,nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
memstick               16569  1 r592
k8temp                 13057  0 
nand_ecc               13230  1 nand
serio_raw              13211  0 
rfcomm                 47604  12 
bnep                   18281  2 
edac_core              53746  0 
snd                    78855  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32866  0 
edac_mce_amd           23709  0 
ppdev                  17113  0 
sp5100_tco             13791  0 
i2c_piix4              13301  0 
btusb                  18288  2 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47199  0 
b44                    36276  0 
bluetooth             180104  23 rfcomm,bnep,btusb
hid                    99559  1 usbhid
radeon                804372  3 
ssb                    52752  1 b44
mac_hid                13253  0 
wl                   2568210  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
video                  19596  0 
drm                   242038  5 radeon,ttm,drm_kms_helper
wmi                    19256  1 dell_wmi
i2c_algo_bit           13423  1 radeon
shpchp                 37277  0 
lib80211               14381  1 wl
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13204  0

---

### Post by bohemian9485 on 2012-05-31
Sorry for the delayed reply.  I did a little research on your Broadcom chipset, and from this [**Archlinux Wiki**]("https://wiki.archlinux.org/index.php/Broadcom_wireless"), you need to use b43/b43legacy drivers.
First you have to make sure the kernel is not loading the broadcom-wl (Broadcom STA driver) and ssb drivers. Check it using the command
```

lsmod | grep wl
lsmod | grep ssb

```If the above commands retun nothing, then you have to check if you have b43 module by typing the command ```
modprobe -l | grep b43
```If the above command returns
```

kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko

```then you can insert the driver by using the command ```
sudo modprobe b43
```
If the lsmod commands did not return anything, you have to install the driver ```
sudo apt-get install firmware-b43-installer
```
By the way, what is your version of Ubuntu? On my main partition I'm  running 12.04 with kernel 3.2.0-24, which uses brcmsmac driver for my  Broadcom BCM 4313 chipset.

---

