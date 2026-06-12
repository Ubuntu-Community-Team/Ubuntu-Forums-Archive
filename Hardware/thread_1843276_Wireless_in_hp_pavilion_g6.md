---
title: "Wireless in hp pavilion g6"
date: 2011-09-13
forum: Hardware
---

### Post by space.cyrus on 2011-09-13
wireless is not working in my hp pavilion g6 laptop.I have ubuntu 10.10.(It works fine in windows 7 though)

**lspci** gives the following output

[I]04:00.0 Network controller: Intel Corporation Device 008b (rev 34)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
[/I]
**lshw -C network** output is as follows


[I]*-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c2500000-c2501fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 2c:27:d7:d0:ba:e5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=10.1.39.44 latency=0 multicast=yes
       resources: irq:46 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
[/I]

---

### Post by josephmills on 2011-09-13
Hi there could we also see a ```
rfkill list all 
``` and a ```
lsmod
```
thanks

---

### Post by space.cyrus on 2011-09-13
**rfkill list all**

[I]2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no[/I]

**lsmod**

[I]Module                  Size  Used by
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
btusb                  11001  2 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
binfmt_misc             6599  1 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54951  1 
i915                  295819  3 
drm_kms_helper         30136  1 i915
ipt_REJECT              2004  2 
ipt_LOG                 4490  5 
drm                   168092  3 i915,drm_kms_helper
xt_limit                1394  7 
xt_tcpudp               1927  10 
ipt_addrtype            1611  4 
xt_state                1014  7 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
ip6table_filter         1275  1 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
ip6_tables             11796  1 ip6table_filter
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
snd_seq_midi            4588  0 
nf_nat_ftp              1398  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
snd_rawmidi            17783  1 snd_seq_midi
nf_conntrack_ipv4      10783  9 nf_nat
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
snd_seq_midi_event      6047  1 snd_seq_midi
nf_conntrack_ftp        5361  1 nf_nat_ftp
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          1302  1 
ip_tables              10492  1 iptable_filter
snd                    49102  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
uvcvideo               55911  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
intel_agp              26566  2 i915
output                  1883  1 video
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19326  2 
libahci                21728  1 ahci
r8169                  36553  0 
mii                     4425  1 r8169[/I]

---

### Post by josephmills on 2011-09-13
ok two more and I think that you are goos to go 

```
lspci -nn
```

and 

```
cat /etc/modprobe.d/blacklist.conf

``` 
thanks

---

### Post by space.cyrus on 2011-09-13
**lspci -nn**

[I]00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:01.1 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0105] (rev 09)
00:01.2 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0109] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:6760]
04:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
06:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01[/I])

**cat /etc/modprobe.d/blacklist.conf**

[I]# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac[/I]

---

### Post by josephmills on 2011-09-13
ok lets try this 
```
sudo modprobe iwlagn
```

still nothing lets see a 

```
 dmesg | grep iwl 
```

---

### Post by space.cyrus on 2011-09-13
**sudo modprobe iwlagn**

*{no output}*

**dmesg | grep iwl**



[I][ 7514.010387] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 7514.010390] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[/I]

---

### Post by josephmills on 2011-09-13
ok lets see  a ```
sudo iwlist scan 
```

---

### Post by space.cyrus on 2011-09-13
**sudo iwlist scan**


[I]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.[/I]

---

