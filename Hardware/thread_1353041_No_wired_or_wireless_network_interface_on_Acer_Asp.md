---
title: "No wired or wireless network interface on Acer Aspire 8935G-874G100BN"
date: 2009-12-12
forum: Hardware
---

### Post by mondalaci on 2009-12-12
Hi guys,

That's the situation after installing Karmic (I've tried both the 32 and 64 bit versions):

```
root@ubuntu:/home/ubuntu# lshw -C network

  *-network UNCLAIMED
       description: Ethernet controller
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ba000000-ba00ffff
  *-network
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: driver=iwlagn latency=0
       resources: irq:17 memory:ba100000-ba101fff

root@ubuntu:/home/ubuntu# ifconfig -a

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 52:54:29:2f:59:6e
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@ubuntu:/home/ubuntu# lsmod

Module                  Size  Used by
nls_iso8859_1           3740  1 
vfat                   10716  1 
fat                    51452  1 vfat
usb_storage            52544  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
snd_hda_codec_atihdmi     3356  1 
bridge                 47952  0 
snd_hda_codec_realtek   203328  1 
stp                     2272  1 bridge
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
bnep                   12060  2 
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10272  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                109052  0 
sdhci_pci               7100  0 
acer_wmi               15936  0 
iwlcore               112508  1 iwlagn
uvcvideo               59080  0 
sdhci                  17472  1 sdhci_pci
psmouse                56180  0 
iptable_filter          3100  0 
videodev               36736  1 uvcvideo
dm_crypt               12928  0 
soundcore               7264  1 snd
serio_raw               5280  0 
v4l1_compat            14496  2 uvcvideo,videodev
led_class               4096  3 acer_wmi,iwlcore,sdhci
btusb                  11856  2 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
mac80211              181236  2 iwlagn,iwlcore
ip_tables              11692  1 iptable_filter
cfg80211               93052  3 iwlagn,iwlcore,mac80211
x_tables               16544  1 ip_tables
squashfs               22912  1 
aufs                  149420  1 
nls_cp437               5372  2 
isofs                  31620  1 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
tg3                   109600  0 
ieee1394               86596  1 ohci1394
radeon                636000  0 
ttm                    36212  1 radeon
i915                  221064  3 
drm                   159584  5 radeon,ttm,i915
i2c_algo_bit            5760  2 radeon,i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  3 ttm,drm,intel_agp

```

Please somebody help me!  Here I am with this kickass laptop and I don't have any networking.

Thanks in advance,
Laci

---

### Post by mondalaci on 2009-12-31
I had to install the most recent kernel (from a pendrive) to make networking work.  After booting up the new kernel networking worked as expected.

I plan to test every Ubuntu releases before the release from now on to spot such critical bugs because such bugs are unacceptable.

---

### Post by Graham C Williams on 2010-01-13
Hi Laci.
REF: Kernel upgrade - 9.10 - Acer 8935g 

Please can you give me some more detail about how you did this? What Kernel and how you actually did the swap?
Did changing the Kernel fix the problem with the sound system? Sorry I'm assuming you have had the same difficulties as I - after loading 9.10 onto the 8935g the Networking and the Sound system did not work correctly. I didn't think of loading a kernel upgrade from a pen drive. Ha, I loaded Fedora 12 instead. just got that system running reasonably but still the sound system is only using 2 of the 6 speakers (5.1). Come 10.04 I'll probably have another go with Ubuntu. 
Interesting, I also loaded 9.10 onto an Acer 8930g and that runs fine in all respects!.

Graham.

---

### Post by unknownofflineuser on 2010-02-10
I installed 9.10 x64 normally, no network.
Then I just got linux-image-2.6.31.19...deb (or something like that, *-19 is important) from another computer on usb disk and dpkg -i
Hint - check /var/cache/apt or something like that for .debs on another ubuntu system.

But I have no ATI graphics with HDMI :)

---

### Post by mondalaci on 2010-04-06
Sorry for the very late reply!  Seems that I haven't been subscribed.  I didn't do anything fancy, just installed the latest kernel package and rebooted.  Regarding the audio, I didn't have such problems.

> **Graham C Williams said:**
> Hi Laci.
REF: Kernel upgrade - 9.10 - Acer 8935g 

Please can you give me some more detail about how you did this? What Kernel and how you actually did the swap?
Did changing the Kernel fix the problem with the sound system? Sorry I'm assuming you have had the same difficulties as I - after loading 9.10 onto the 8935g the Networking and the Sound system did not work correctly. I didn't think of loading a kernel upgrade from a pen drive. Ha, I loaded Fedora 12 instead. just got that system running reasonably but still the sound system is only using 2 of the 6 speakers (5.1). Come 10.04 I'll probably have another go with Ubuntu. 
Interesting, I also loaded 9.10 onto an Acer 8930g and that runs fine in all respects!.

Graham.

---

