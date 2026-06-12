---
title: "Touchpad not working"
date: 2010-11-26
forum: Hardware
---

### Post by Fr33_z3 on 2010-11-26
Hi guys,
I have just installed Ubuntu 10.10 Maverick Meerkat on my laptop. The  touchpad does not work at all. The pointer doesn't move and none of the  buttons work either.

My laptop is a Sony Vaio - VPCEB34EN which has 3 GB RAM, Intel i3 @ 2.40GHz, 512MB ATI Mobility Radeon 5270.
It came preloaded with Windows 7 64-bit Home Basic. I have used Wubi to  install Ubuntu onto my hard drive on a separate partition.

These are the outputs of **lspci**, **lsusb** and **lsmod**.  Please note that I have run them from inside the LiveCD, would that make  a difference? : 

**lspci** :

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8059 PCI-E Gigabit Ethernet Controller (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02) 
------------------------------------------------------------------------------------------------------------------------------
**lsusb** : 

Bus 002 Device 003: ID 12d1:1411 Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 0c45:6409 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
--------------------------------------------------------------------------------------------------------------------------------

**lsmod**:

Module                  Size  Used by
ppp_deflate             3726  0 
bsd_comp                4791  0 
ppp_async               6778  1 
crc_ccitt               1351  1 ppp_async
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
rfcomm                 33811  4 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
sco                     7998  2 
snd_rawmidi            17783  1 snd_seq_midi
bnep                    9542  2 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
l2cap                  37008  16 rfcomm,bnep
arc4                    1165  2 
snd_timer              19067  2 snd_pcm,snd_seq
ath9k                  88756  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common            5982  1 ath9k
ath9k_hw              292297  2 ath9k,ath9k_common
snd                    49006  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
soundcore                880  1 snd
uvcvideo               55847  0 
option                 13133  1 
btusb                  10969  2 
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
usb_wwan                9953  1 option
sony_laptop            29088  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
usbserial              33100  5 option,usb_wwan
videodev               43098  1 uvcvideo
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
v4l1_compat            13359  2 uvcvideo,videodev
squashfs               25209  1 
aufs                  152358  4446 
nls_cp437               4931  1 
isofs                  30022  1 
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  2 ppp_deflate,btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
radeon                825934  2 
usb_storage            40172  0 
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
ahci                   19013  0 
drm                   168054  4 radeon,ttm,drm_kms_helper
sky2                   45127  0 
intel_agp              26360  0 
libahci                21667  3 ahci
sdhci_pci               6339  0 
video                  18712  0 
sdhci                  15890  1 sdhci_pci
output                  1883  1 video
i2c_algo_bit            5168  1 radeon
agpgart                32011  3 ttm,drm,intel_agp
led_class               2633  2 ath9k,sdhci
-------------------------------------------------------------------------------------------------------------------------------


Also, I use a CDMA modem to connect to the internet. I tried installing  wvdial, but I got a message saying that the package could not be found. I  then tried installing it off the LiveCD while inside Ubuntu, but it  says that the libwvstreams package et al. could not be located on the  disc. 

I'm on the LiveCD now, and I managed to install it onto the memory  without any problems from the LiveCD and connect to the internet. 
Is it possible for me to install the packages from the LiveCD directly  onto my harddrive instead of using it temporarily inside the LiveCD?

Can anybody please help me with this?

EDIT : **_Guys, my wireless mouse works. The transmitter uses a USB port. I'd still like to have a functional touch pad._**

TIA,
Fr33_z3

---

### Post by IcarusR on 2010-11-26
> Is it possible for me to install the packages from the LiveCD directly onto my harddrive

Yes it is..

Launch Synaptic & go to Settings > Repositories, select the cd in the bottom of the window & reload repositories with cd in the drive.
Then you can search for the package you want to install.

When you get online you should install all available updates, this may help getting hardware to work properly.

This may help getting touchpad to work

[http://ubuntuforums.org/showpost.php?p=9315670&postcount=6]("http://ubuntuforums.org/showpost.php?p=9315670&postcount=6")

---

### Post by Fr33_z3 on 2010-11-26
Thanks, I'll try them out and revert.

---

