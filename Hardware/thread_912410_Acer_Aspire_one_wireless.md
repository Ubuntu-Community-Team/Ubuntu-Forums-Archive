---
title: "Acer Aspire one wireless"
date: 2008-09-06
forum: Hardware
---

### Post by wtfrara on 2008-09-06
Hi, I just installed ubuntu 8.04.1 on my acer aspire one successfully according to the instructions at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) , but my wireless stopped working. After I finished most of the items on the page, (omitting the netbook remix stuff) my wireless was working. After a reboot, it no longer works. The network manager will attempt to connect but while waiting for a network key, it fails. 

Output of iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:3389  Rx invalid crypt:0  Rx invalid frag:0

```

Output of ifconfig:
```

ath0      Link encap:Ethernet  HWaddr 00:1f:e2:b8:d0:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:8a:6a:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:385568297 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60000 (58.5 KB)  TX bytes:60000 (58.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-E2-B8-D0-F5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3635 errors:0 dropped:0 overruns:0 frame:199
          TX packets:461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:419020 (409.1 KB)  TX bytes:21206 (20.7 KB)
          Interrupt:18 

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Output of lsmod:
```

Module                  Size  Used by
af_packet              23812  0 
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
wlan_scan_sta          16000  1 
ath_rate_sample        16128  1 
ath_pci               249016  0 
wlan                  236272  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               305376  3 ath_rate_sample,ath_pci
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
mmc_block              14980  2 
usbhid                 31872  0 
hid                    38784  1 usbhid

uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
evdev                  13056  7 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
video                  19856  0 
output                  4736  1 video
acer_acpi              18112  0 
led_class               6020  1 acer_acpi
wmi_acer                9644  1 acer_acpi
serio_raw               7940  0 
sdhci                  19076  0 
mmc_core               51460  2 mmc_block,sdhci
snd_seq_dummy           4868  0 
psmouse                40336  0 
battery                14212  0 
button                  9232  0 
ac                      6916  0 
snd_seq_oss            35584  0 
pcspkr                  4224  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
intel_agp              25492  1 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
agpgart                34760  3 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ext2                   73352  1 
mbcache                 9600  1 ext2
sg                     36880  0 
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_piix               19588  2 
ata_generic             8324  0 
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  3 sg,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 usbhid,uvcvideo,ehci_hcd,uhci_hcd
r8169                  32900  0 
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

Any help would be amazing! (I haven't been able to find the same problem on the forum, but if anyone else can point me to one, that would be just as good)

---

### Post by wtfrara on 2008-09-06
sigh... really easy and obvious solution. Already kicking myself... instead of using automatic connection or whatever, use aes-ccmp

---

### Post by donec on 2008-09-09
> **wtfrara said:**
> sigh... really easy and obvious solution. Already kicking myself... instead of using automatic connection or whatever, use aes-ccmpWhat is aes-ccmp?

---

### Post by somesnapper on 2008-09-09
I have the same problem..

---

### Post by lualiza on 2008-09-18
Hi:
I have the same problem with wireless.
could you explain us where you changed aes-ccmp?
thanks

---

