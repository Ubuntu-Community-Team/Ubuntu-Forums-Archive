---
title: "Wireless adapter works but speed is capped to 5mbps"
date: 2016-02-25
forum: Hardware
---

### Post by gorkygd67 on 2016-02-25
Hello everyone.

The title pretty much explains the issue. I have a usb Wifi adapter to connect my desktop to my home network. While all the computers (including smartphones) have a download speed up to 20mbps, the desktop is restricted to 5mbps. I placed the stick on different computers and the drill is the same; the speed increases over 5mbps and then drops at 5 and is fixed there.

Posting relevant output below:

[COLOR=#111111][FONT=Ubuntu]My wireless adapter[/FONT][/COLOR]
Bus 006 Device 017: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]lsmod:


[/FONT]
Module                  Size  Used by
ctr                    16384  0 
ccm                    20480  0 
arc4                   16384  0 
rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              708608  3 rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt              16384  1 rt2800lib
btrfs                 937984  0 
xor                    24576  1 btrfs
raid6_pq               98304  1 btrfs
ufs                    77824  0 
qnx4                   16384  0 
hfsplus               106496  0 
hfs                    57344  0 
minix                  36864  0 
ntfs                   98304  0 
msdos                  20480  0 
jfs                   188416  0 
xfs                   917504  0 
libcrc32c              16384  1 xfs
nls_iso8859_1          16384  0 
uas                    24576  0 
usb_storage            69632  1 uas
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               417792  3 vboxnetadp,vboxnetflt,vboxpci
cfg80211              524288  2 mac80211,rt2x00lib
snd_hda_codec_hdmi     53248  4 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
r8712u                184320  0 
kvm_amd                61440  0 
kvm                   479232  1 kvm_amd
snd_rawmidi            32768  1 snd_seq_midi
crct10dif_pclmul       16384  0 
snd_hda_codec_realtek    81920  1 
crc32_pclmul           16384  0 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_intel          36864  6 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
aesni_intel           172032  0 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
bnep                   20480  2 
rfcomm                 69632  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0 
k10temp                16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
bluetooth             491520  10 bnep,rfcomm
snd                    86016  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_piix4              24576  0 
nouveau              1368064  4 
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
ttm                    94208  1 nouveau
drm_kms_helper        126976  1 nouveau
drm                   344064  7 ttm,drm_kms_helper,nouveau
soundcore              16384  2 snd,snd_hda_codec
i2c_algo_bit           16384  1 nouveau
shpchp                 40960  0 
binfmt_misc            20480  1 
8250_fintek            16384  0 
video                  20480  1 nouveau
mac_hid                16384  0 
parport_pc             32768  1 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
pata_acpi              16384  0 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
pata_atiixp            16384  0 
r8169                  81920  0 
mii                    16384  1 r8169
ahci                   36864  3 
libahci                32768  1 ahci



[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR]
sudo lsusb -v -d 0bda:8172 | grep bcdUSB

  bcdUSB               2.00
  bcdUSB               2.00

dmsg output


[438815.257964] usb 6-1: new high-speed USB device number 18 using ehci-pci
[438815.392953] usb 6-1: New USB device found, idVendor=0bda, idProduct=8172
[438815.392960] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[438815.392964] usb 6-1: Product: RTL8191S WLAN Adapter 
[438815.392967] usb 6-1: Manufacturer: Manufacturer Realtek 
[438815.392970] usb 6-1: SerialNumber: 00e04c000001
[438815.393591] r8712u: Staging version
[438815.393621] r8712u: register rtl8712_netdev_ops to netdev_ops
[438815.393627] usb 6-1: r8712u: USB_SPEED_HIGH with 4 endpoints
[438815.395195] usb 6-1: r8712u: Boot from EFUSE: Autoload OK
[438815.809255] usb 6-1: r8712u: CustomerID = 0x000a
[438815.809261] usb 6-1: r8712u: MAC Address from efuse = e8:4e:06:1e:3e:2e
[438815.809265] usb 6-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[438816.546318] r8712u 6-1:1.0 wlan0: 1 RCR=0x153f00e
[438816.547037] r8712u 6-1:1.0 wlan0: 2 RCR=0x553f00e


uname -r
3.19.0-43-generic


iwlist wlan0 bitrate
wlan0     4 available bit-rates :
      1 Mb/s
      2 Mb/s
      5.5 Mb/s
      11 Mb/s
          Current Bit Rate:150 Mb/s



lshw for the wlan

id: 
network
description:    Wireless interface
physical id:    
1
bus info:   
usb@6:1
logical name:   
wlan0
serial: e8:4e:06:1e:3e:2e
capabilities:   ethernet physical wireless
configuration:  
broadcast   =   yes
driver  =   r8712u
ip  =   192.168.1.103
multicast   =   yes
wireless    =   IEEE 802.11bgn

---

### Post by weatherman2 on 2016-02-25
My experience with these little USB WiFI adapters is that they don't match the performance of other adapters, especially adapters that have bigger antennas.  That's one reason why I have switched my desktops that can't easily be wired to my network to using a wireless ethernet bridge to get better wireless connections.  Find any wireless router that supports TomatoUSB firmware (mainly Broadcom-based routers, many old Linksys/Cisco routers) and you can install that and easily turn it into a wireless ethernet bridge.  DD-WRT firmware can do it too, but I find Tomato easier to setup.  (DD-WRT is supported on more routers.)  Some routers have factory firmware that also allows you to make a wireless ethernet bridge.

I have a handful of little USB wireless adapters in a box - handy for one-time uses here and there but not used daily anymore.

---

### Post by kurt18947 on 2016-02-26
This is my experience only, YMMV.

I have 2 nano sized USB wifi adapters. One contains an Ralink/MediaTek RT-5370, The other is a Edimax EW-7811UN containing a Ralink RTL-8188CUS chipset. The RT-5370 works out of the box but the signal is pretty weak and throughputs are fairly slow. I've never tried to build a patched driver for this device.  I find the Edimax EW-7811UN performs very well for its size if I install this patched driver:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I believe there is a more recent build-it-yourself driver but I haven't tried it. The last time I used the Edimax (or other RTL-8192CU based wifi adapters) they worked out of the box but not especially well. I haven't tried the native driver recently so they may have improved, I don't know.  I agree that the larger adapters tend to work better but the little Edimax does pretty well while being quite unobtrusive - assuming you're happy with N150 speeds.

---

