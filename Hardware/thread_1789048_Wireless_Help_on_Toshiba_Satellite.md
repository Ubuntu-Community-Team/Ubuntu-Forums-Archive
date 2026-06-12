---
title: "Wireless Help on Toshiba Satellite"
date: 2011-06-23
forum: Hardware
---

### Post by jskinner1724 on 2011-06-23
Please forgive if I have mis-posted or failed to follow forum etiquette. I searched and found no other adequate place for such a post.

Please help! At my wits end (which didn't take long btw) trying to figure this one out. After the 2.6.32-32 kernel upgrade my wireless stopped working. No big deal, just boot to the older kernel version, right? Well, after going through the forums, I tried everything I could find to upgrade the drivers, etc. to no avail. Now I am left with a system that will not recognize my wireless card. Here are some of the results of scans I assume you will ask for;

jskinner1724@jskinner1724-laptop:~$ sudo -i
[sudo] password for jskinner1724: 
root@jskinner1724-laptop:~#**[COLOR=SeaGreen] lshw -C network[/COLOR]**
 _ *-network UNCLAIMED  _   
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:ff600000-ff603fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:5a:eb:87
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.55 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:c000(size=256) memory:d0104000-d0104fff(prefetchable) memory:d0100000-d0103fff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
(This is my virtual machine which I expect to be disabled)

root@jskinner1724-laptop:~# **[COLOR=SeaGreen]lspci -n[/COLOR]**
00:00.0 0600: 1022:9601
00:01.0 0604: 1179:9602
00:06.0 0604: 1022:9606
00:07.0 0604: 1022:9607
00:11.0 0106: 1002:4391
00:12.0 0c03: 1002:4397
00:12.2 0c03: 1002:4396
00:13.0 0c03: 1002:4397
00:13.2 0c03: 1002:4396
00:14.0 0c05: 1002:4385 (rev 41)
00:14.2 0403: 1002:4383 (rev 40)
00:14.3 0601: 1002:439d (rev 40)
00:14.4 0604: 1002:4384 (rev 40)
00:18.0 0600: 1022:1200
00:18.1 0600: 1022:1201
00:18.2 0600: 1022:1202
00:18.3 0600: 1022:1203
00:18.4 0600: 1022:1204
01:05.0 0300: 1002:9712
01:05.1 0403: 1002:970f
_02:00.0 0280: 10ec:8176 (rev 01)_
03:00.0 0200: 10ec:8136 (rev 05)

root@jskinner1724-laptop:~#**[COLOR=SeaGreen] lsmod[/COLOR]**
Module                  Size  Used by
binfmt_misc             7960  1 
vboxnetadp              5171  0 
vboxnetflt             14998  0 
vboxdrv              1792504  2 vboxnetadp,vboxnetflt
iptable_filter          1841  0 
ip_tables              18201  1 iptable_filter
x_tables               22361  1 ip_tables
ppdev                   6375  0 
parport_pc             29958  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   279008  1 
snd_seq_dummy           1782  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_seq_oss            31191  0 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
fglrx                2353486  32 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd_timer              23649  2 snd_pcm,snd_seq
joydev                 11104  0 
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
psmouse                64576  0 
ndiswrapper           244800  0 
serio_raw               4918  0 
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_seq_device,snd_timer
edac_core              45423  0 
i2c_piix4               9639  0 
shpchp                 33711  0 
edac_mce_amd            9278  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
raid10                 21450  0 
raid456                54784  0 
async_pq                3891  1 raid456
async_xor               3111  2 raid456,async_pq
xor                     4685  1 async_xor
async_memcpy            1537  1 raid456
async_raid6_recov       1816  1 raid456
usb_storage            50377  0 
raid6_pq               80147  2 async_pq,async_raid6_recov
async_tx                2545  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  22610  0 
usbhid                 41116  0 
hid                    83600  1 usbhid
raid0                   6778  0 
multipath               7181  0 
linear                  4158  0 
r8169                  39714  0 
mii                     5237  1 r8169
ahci                   38030  2

root@jskinner1724-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

Normally, my machine had seen my wireless as wlan0, but as you can tell from above, it seems to have gotten lost somehow after the upgrade. I tried the rtl8192ce-dkms for Lucid since I am running 10.04, followed the instructions precisely, rebooted and found myself no further than before I started. Any suggestions?

---

