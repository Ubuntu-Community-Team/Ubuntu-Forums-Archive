---
title: "installing the appropriate drivers (HP)"
date: 2017-05-14
forum: Hardware
---

### Post by rolfUser on 2017-05-14
While restoring my desktop environment to its original state, it was discovered that  NVidia-304 had been previously installed on my PC. 
[https://ubuntuforums.org/showthread.php?t=2360548&page=2](https://ubuntuforums.org/showthread.php?t=2360548&page=2)

My Ubuntu 16.04 LTS desktop is back to its old self again, but the purpose of this thread would be to explore hardware specs and draw conclusions as to a good graphics driver for my HP PC. I'm not that sure why this is important, but this is how we learn, by asking questions.

---

### Post by Bashing-om on 2017-05-14
rolfUser; Hey again .

Lot's of ways we can ask the system questions to obtain a desired report .
Graphics:
> 
conclusions as to a good graphics driver for my HP PC. 

Though the kernel is very good at integrating the correct driver by default, sometimes we just want to know, and other times the kernel does need a little help .

We start with finding out the hardware :
```

inxi -G
lspci -nnk | grep -iA3 vga

```

From this we draw some conclusions as to the driver that "should" be installed; then we look at what is installed.

Remember,
[INDENT][INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-14
> **Bashing-om said:**
> rolfUser; Hey again .

Lot's of ways we can ask the system questions to obtain a desired report .
Graphics:

Though the kernel is very good at integrating the correct driver by default, sometimes we just want to know, and other times the kernel does need a little help .

We start with finding out the hardware :
```

inxi -G
lspci -nnk | grep -iA3 vga

```

From this we draw some conclusions as to the driver that "should" be installed; then we look at what is installed.

Remember,[INDENT][INDENT][INDENT]it is all a process of learning
[/INDENT]
[/INDENT]
[/INDENT]


input:
```
 inxi -G
```
output:
```
The program 'inxi' is currently not installed. You can install it by typing:
sudo apt install inxi
```

input:
```
 lspci -nnk | grep -iA3 vga
```
output:
```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330] [1002:9832]    Subsystem: Hewlett-Packard Company Kabini [Radeon HD 8330] [103c:2b18]
    Kernel driver in use: radeon
    Kernel modules: radeon
```

---

### Post by Yellow Pasque on 2017-05-14
The correct driver is already in use. What exactly is the issue?

---

### Post by Bashing-om on 2017-05-14
rolfUser; Welp;

Yeah the correct driver is in use .
Quick way to know.
```

man radeon

```
You see in the list - Kabini.

What other modules ( nvidia ???) are installed :
```

lsmod

```

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-15
input:
```
lsmod
```
output:
```
Module                  Size  Used bynls_utf8               16384  1
udf                    94208  1
crc_itu_t              16384  1 udf
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
binfmt_misc            20480  1
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
input_leds             16384  0
snd_usb_audio         176128  2
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_usbmidi_lib        36864  1 snd_usb_audio
snd_hda_intel          40960  7
amd_freq_sensitivity    16384  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
kvm_amd                65536  0
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
kvm                   544768  1 kvm_amd
snd_pcm               106496  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
irqbypass              16384  1 kvm
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
lrw                    16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
snd_timer              32768  2 snd_pcm,snd_seq
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd                    81920  30 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
edac_mce_amd           24576  0
k10temp                16384  0
edac_core              53248  0
fam15h_power           16384  0
shpchp                 36864  0
i2c_piix4              24576  0
mac_hid                16384  0
wmi                    20480  1 hp_wmi
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 24576  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack          106496  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
x_tables               36864  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
hid_generic            16384  0
radeon               1515520  57
i2c_algo_bit           16384  1 radeon
ums_realtek            20480  0
uas                    24576  0
ttm                    94208  1 radeon
usb_storage            69632  2 uas,ums_realtek
drm_kms_helper        155648  1 radeon
usbhid                 49152  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
hid                   118784  2 hid_generic,usbhid
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  4
drm                   364544  12 ttm,drm_kms_helper,radeon
libahci                32768  1 ahci
r8169                  81920  0
mii                    16384  1 r8169
fjes                   28672  0
video                  40960  0

```

---

### Post by Bashing-om on 2017-05-15
rolfUser; Hey .

Looks clean to me . 

Do you have any issues to report ? 

Questions ?

[INDENT][INDENT]help is what we do 
[/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-16
[[IMG]https://ubuntuforums.org/customavatars/avatar1111508_1.gif[/IMG]]("https://ubuntuforums.org/member.php?u=1111508")[COLOR=#000000][Bashing-om]("https://ubuntuforums.org/member.php?u=1111508")
[/COLOR]



There is actually one thing I think you can help me with. Part of the reason I installed NVidia was because I thought that if I did this, I can thus have additional aspect ratios available under Settings>Appearance.
Well I tried that and got no where. Then I entered these commands on the terminal:
```

sudo cvt 1280 720 60
sudo xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
sudo xrandr --addmode VGA-0 1280x720_60.00

```
The result of all this the (1024x768) 4:3 screen outputted on my HDTV converted to utilize the whole screen -- the entire screen is taken up -- 1280x720 16:9 aspect ratio.
The problem is that this new screen resolution goes away after I restart Ubuntu. There was a video tutorial ([https://youtu.be/LiP-YqtZoNQ](https://youtu.be/LiP-YqtZoNQ)) on how to keep the resolution. I followed instructions, but did not get the intended result. The screen just goes back to 4:3.

[https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions)
In spite of the resources, there's not much progress. 
How can I keep the resolution?

---

### Post by Bashing-om on 2017-05-16
rolfUserl Well,

Again, we are drifting too far from the subject of the present thread.
Open a new thread for this alternate issue.

In this new thread we explore how to set the resolution and which of the options to use to make it "persistent" .
The easier to implement is making up the ~/.xprofile file . Better way though, if ya running GDM as the desktop .

[INDENT][INDENT]threads like dead men
[INDENT][INDENT][INDENT]just one to the box
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-17
[h=2]Keeping an Undetected Desktop Reolution[/h]https://ubuntuforums.org/showthread.php?t=2361521&p=13646116#post13646116

---

### Post by rolfUser on 2017-05-18
Maybe just one more item. My screen has a bad habit of flickering, meaning the video, not the audio, will go black as if the screen was turned off for a a few seconds and turns itself back on. It will do this often. 
The light on the monitor indicating whether the TV is on or off stays blue (meaning it is on) while all this happens. The flickering only takes place during VGA output -- never through TV or HDMI output.
The screen will turn off for a few seconds then a second time 5 seconds or 20 seconds later. Sometimes not for another 30 minutes and it turns off and back on again.

Is this a graphics driver issue? Is it a VGA cable issue? Is it normal? What do I make of it?

---

### Post by Bashing-om on 2017-05-18
rolfUser; Hummmm ...

> 
Is this a graphics driver issue? Is it a VGA cable issue? Is it normal? What do I make of it?

Not normal at all . as to what to make if it .. Beats me. never have encountered such before . Might be good to spare the monitor cable off ( check that both ends are clean and secure) .
Then again, a TV is not a  good substitute for a computer monitor .

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

