---
title: "nb505 wireless problems"
date: 2012-02-07
forum: Hardware
---

### Post by qmynd on 2012-02-07
So I have been having alot of trouble with my wireless card.  At first I had ubuntu and nothing was wrong.  Since I have a netbook the most reasont version of ubuntu was too slow for me so I tried a different flavors the second most reasont is OpenSuse and wireless works fine in OpenSuse.  A bunch of differnt drivers didn't work in i think version 10 but it did in the very most reasont version of OpenSuse both KDE and Gnome. Again OpenSuse is too slow so I partitioned half my harddrive with Ubuntu netbook remix but now I have this horrible wireless problem again.  I will explain practily everything I have done and not not done to try to resolve this problem.  

Fix Attempt #1:
   Other forums sugget i get the wireless drivers from realtek and isntall either the linux drivers or use nswrapper for the other ones.  I tried both of these on the old version of OpenSuse with out success. I would try tem again on the netbook remix but I dout they will work because they didn't work in the old version of open suse.

Fix Attempt #2:

The first thing i tried to do to fix the problem with the netbook remix was these commands:
sudo add-apt-repository ppa:lexical/hwe-wireless 
sudo apt-get update 
sudo apt-get install rtl8192ce-dkms
sudo apt-get update
sudo apt-get upgrade

I found this in another forum and these 5 commands did work and I had wireless in the netbook version and everything was good again.  Then I had 8 or 10 updates which i updated my kernal got updated to something like 32-38  im not sure of the exact number and if matters I can get it.  After this update the wireless problem was back.  network tools wouldn't acknoledge I had a wireless device but I could go back to the old kernal version and it would work but I didn't have the secuirty updates from the new kernal.

Next I tried to unistall the driver with sudo apt-get remove rtl8192ce-dkms and then isntall it again. This didn't work.

Fix Attempt #3

I fallowed the fix here:
[http://www.techdrivein.com/2011/06/fixwifi-driver-breaks-after-update-in.html](http://www.techdrivein.com/2011/06/fixwifi-driver-breaks-after-update-in.html)
This didn't really help it just made ubuntu recognize my wireless card and driver but now it keeps saying the device is disabled.

you can check this by the commands bellow.

Fix Attempt #4

At this point I was trying to enable the wireless card and was told I needed something in synaptic s package manager.  I can't remember what its called but it had to do with firmware and possibly something to do with enabling the hot keys for the nb505 toshiba netbook.  This didn't do anything.

This is where I am now .  Below are a list of commands Ive seen people ask for when trouble shooting networking.  It would be nice to understand what all of them do but that is at the very bottom at my priority list.  The main thing I want to know is how do i get my wireless working.

Thanks in advance

 sudo lshw -C network

[sudo] password for shane: 
  *-network DISABLED      
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:42:9a:5e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.32-38-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: b8:70:f4:be:c3:be
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:3000(size=256) memory:f050c000-f050cfff(prefetchable) memory:f0508000-f050bfff(prefetchable)

 nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        D0:DF:9A:42:9A:5E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B8:70:F4:BE:C3:BE

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


 lspci -nn | grep 0280
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)

 lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 064e:a216 Suyin Corp. 
Bus 001 Device 003: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
shane@shane-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8933  2 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
joydev                  8740  0 
snd_hda_codec_realtek   203440  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
r8192ce_pci           443493  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8192ce             108470  0 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtlwifi                68470  1 rtl8192ce
mac80211              245329  2 rtl8192ce,rtlwifi
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              150158  2 rtlwifi,mac80211
compat                  7267  2 mac80211,cfg80211
uvcvideo               57438  0 
led_class               2864  1 compat
soundcore               6620  1 snd
psmouse                63677  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
pcmcia_core            32964  1 compat
compat_firmware_class     6200  1 rtl8192ce
lp                      7028  0 
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  289715  4 
drm_kms_helper         29329  1 i915
usb_storage            40033  2 
intel_agp              24375  2 i915
drm                   163747  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
ahci                   32680  2 
output                  1871  1 video
r8169                  34140  0 
mii                     4381  1 r8169
agpgart                31724  2 intel_agp,drm

---

