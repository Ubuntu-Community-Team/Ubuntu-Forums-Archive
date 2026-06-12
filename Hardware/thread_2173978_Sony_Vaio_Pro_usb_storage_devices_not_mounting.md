---
title: "Sony Vaio Pro: usb storage devices not mounting"
date: 2013-09-12
forum: Hardware
---

### Post by sander.lindeman on 2013-09-12
Since a few weeks I'm running Xubuntu 3.10 on the Sony Vaio Pro. After a few kernel compilations (haswell processor needed some care) it's now running a 3.11-rc7. 

uname -a:
```
Linux fleptep 3.11.0-rc7-custom3 #4 SMP Thu Sep 5 14:21:13 CEST 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I'm facing one last problem. The two usb 3 ports are working fine: wireless mouse works, usb-ethernet works. But when I insert a usb memory stick or dvd-player they are only recognized, but I'm unable to mount them.

Here are a few outputs:
lsusb
```

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:5727 Realtek Semiconductor Corp. 
Bus 002 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 006: ID 0424:4063 Standard Microsystems Corp. 
Bus 002 Device 005: ID 0424:2640 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 0df6:0056 Sitecom Europe B.V. LN-031 10/100/1000 Ethernet Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lspci
```

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

```

So when I plug in a usb memorystick this is what dmesg tells me:
```

[ 2852.680004] usb 2-2.1.3: new full-speed USB device number 7 using xhci_hcd
[ 2852.700155] usb 2-2.1.3: New USB device found, idVendor=046d, idProduct=c52b
[ 2852.700160] usb 2-2.1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2852.700163] usb 2-2.1.3: Product: USB Receiver
[ 2852.700165] usb 2-2.1.3: Manufacturer: Logitech
[ 2852.710722] hidraw: raw HID events driver (C) Jiri Kosina
[ 2852.722011] usbcore: registered new interface driver usbhid
[ 2852.722013] usbhid: USB HID core driver
[ 2852.728041] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-2.1.3/input2
[ 2852.732097] input: Logitech Unifying Device. Wireless PID:101b as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2.1/2-2.1.3/2-2.1.3:1.2/0003:046D:C52B.0003/input/input13
[ 2852.732581] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101b] on usb-0000:00:14.0-2.1.3:1
[B][ 3646.921423] usb 2-2.1.2: new high-speed USB device number 8 using xhci_hcd
[ 3646.986961] usb 2-2.1.2: New USB device found, idVendor=058f, idProduct=6387
[ 3646.986965] usb 2-2.1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3646.986968] usb 2-2.1.2: Product: Mass Storage
[ 3646.986970] usb 2-2.1.2: Manufacturer: Generic
[ 3646.986971] usb 2-2.1.2: SerialNumber: 16D4D231[/B]

```

Also lsusb shows it:
```

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:5727 Realtek Semiconductor Corp. 
Bus 002 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
**Bus 002 Device 008: ID 058f:6387 Alcor Micro Corp. Flash Drive**
Bus 002 Device 006: ID 0424:4063 Standard Microsystems Corp. 
Bus 002 Device 005: ID 0424:2640 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 0df6:0056 Sitecom Europe B.V. LN-031 10/100/1000 Ethernet Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Apparently, the xhci_hcd module is built in. I've tried to reload the xhci modules, but that didn't work. lsmod gives me this:
```

Module                  Size  Used by
hid_logitech_dj        18581  0 
usbhid                 52972  0 
hid                   100905  3 usbhid,hid_logitech_dj
md4                    12595  0 
snd_hda_codec_hdmi     41284  1 
snd_hda_codec_realtek    51465  1 
joydev                 17377  0 
arc4                   12608  2 
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
crc32_pclmul           13113  0 
parport_pc             36797  0 
ghash_clmulni_intel    13259  0 
snd_hwdep              13602  1 snd_hda_codec
ppdev                  17635  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aesni_intel            55585  2 
aes_x86_64             17131  1 aesni_intel
glue_helper            13990  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
pn544_mei              12787  0 
mei_phy                13881  1 pn544_mei
pn544                  17949  1 pn544_mei
hci                    44425  2 pn544,mei_phy
nfc                    94614  2 hci,pn544
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
bnep                   19564  2 
rfcomm                 68919  0 
bluetooth             367736  10 bnep,rfcomm
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
asix                   38914  0 
usbnet                 39410  1 asix
mii                    13934  2 asix,usbnet
uvcvideo               80834  0 
iwlmvm                165399  0 
videobuf2_vmalloc      13216  1 uvcvideo
snd_timer              29378  2 snd_pcm,snd_seq
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_core         40469  1 uvcvideo
videodev              133343  2 uvcvideo,videobuf2_core
mac80211              592570  1 iwlmvm
microcode              23518  0 
i915                  655185  5 
iwlwifi               150707  1 iwlmvm
psmouse                97626  0 
i2c_algo_bit           13413  1 i915
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13413  0 
drm_kms_helper         52651  1 i915
cfg80211              479711  3 iwlwifi,mac80211,iwlmvm
drm                   292559  4 i915,drm_kms_helper
mei_me                 18542  0 
mei                    77692  3 pn544_mei,mei_phy,mei_me
soundcore              12680  1 snd
lpc_ich                21080  0 
mac_hid                13205  0 
sony_laptop            54045  0 
binfmt_misc            17431  1 
intel_smartconnect     12690  0 
video                  19267  1 i915
lp                     17759  0 
parport                42264  3 lp,ppdev,parport_pc
nls_utf8               12557  2 
cifs                  435594  3 
fscache                58475  1 cifs
ahci                   25819  2 
libahci                31898  1 ahci

```

When I check lsblk it does not show up:
```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 238,5G  0 disk 
&#9500;&#9472;sda1   8:1    0 230,6G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   7,9G  0 part [SWAP]

```

I've tried a few memorysticks and dvd-players, with no luck so far. 

Most posts I could found about similar issues had to do with xhci-related errors, which is not apparent in this case.
Any suggestions on this?

Cheers!

---

### Post by sander.lindeman on 2013-09-14
Little update:

A new kernel compile did the trick.... 
I had been compiling the previous kernels using 'make localmodconfig'. 
This time I used 'make menuconfig' and kept it more or less default and my problem is solved.

One little issue remains (overlooked it before I guess): the cardreader is not working yet.... I'll be working on that now =)

Cheerio

---

