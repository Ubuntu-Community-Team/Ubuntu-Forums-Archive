---
title: "Speedstep (freq. scale) does not work"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by mslms on 2006-08-18
Today I got the 686 kernel to ubuntu and then to my great horror my CPU had stopped throttling down.

Some info.

uname -a
```

Linux laptop 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

```

cat /proc/cpuinfo
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.73GHz
stepping        : 8
cpu MHz         : 1729.318
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2
bogomips        : 1598.80

```

lsmod
```

ipv6                  286976  20
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
ppdev                   9668  0
i915                   21664  1
drm                    78484  2 i915
speedstep_centrino      8752  1
cpufreq_userspace       6496  1
cpufreq_stats           6688  0
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
af_packet              24520  4
dm_mod                 63256  1
md_mod                 76052  0
freq_table              4928  2 speedstep_centrino,cpufreq_stats
ndiswrapper           189876  0
sbp2                   25060  0
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
pcmcia                 41948  0
8139cp                 24032  0
joydev                 10432  0
tsdev                   8032  0
ipw2200               113548  0
ieee80211              38952  1 ipw2200
ieee80211_crypt         6528  1 ieee80211
usbhid                 42752  0
sdhci                  16096  0
ieee80211_1_1_13       39880  0
ieee80211_1_1_13_crypt     7040  1 ieee80211_1_1_13
mmc_core               31816  1 sdhci
yenta_socket           30124  2
rsrc_nonstatic         14624  1 yenta_socket
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
8139too                29056  0
mii                     6176  2 8139cp,8139too
snd_intel8x0           35772  1
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
psmouse                40004  0
serio_raw               7748  0
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
intel_agp              24700  1
agpgart                36784  3 drm,intel_agp
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
sg                     40160  0
sr_mod                 17988  0
cdrom                  41408  1 sr_mod
evdev                  10176  2
ext3                  148104  1
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0
uhci_hcd               35408  0
usbcore               139076  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
sd_mod                 20448  3
generic                 5124  0
ata_piix               11364  4
ahci                   18020  0
libata                 83440  2 ata_piix,ahci
scsi_mod              145960  6 sbp2,sg,sr_mod,sd_mod,ahci,libata
thermal                13768  0
processor              26888  2 speedstep_centrino,thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```

cat /sys/devices/system/cpu/cpu0/cpufreq/x
```

affected_cpus: 0
cpuinfo_max_freq: 1733000
cpuinfo_min_freq: 800000
scaling_available_frequencies: 1733000 1333000 1067000 800000
scaling_available_governors: userspace powersave ondemand conservative performance
scaling_cur_freq: 800000
scaling_driver: centrion
scaling_governor: userspace
scaling_max_freq: 1733000
scaling_min_freq: 800000
scaling_setspeed: 800000

```

powernow -v
```

powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Settings:
powernowd:   verbosity:        1
powernowd:   mode:             1     (AGGRESSIVE)
powernowd:   step:           100 MHz (100000 kHz)
powernowd:   lowwater:        20 %
powernowd:   highwater:       80 %
powernowd:   poll interval: 1000 ms
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 800Mhz - 1733Mhz (4 steps)
powernowd:      step1 : 1733Mhz
powernowd:      step2 : 1333Mhz
powernowd:      step3 : 1067Mhz
powernowd:      step4 : 800Mhz

```

What's odd is that I just discovered that /proc/cpuinfo says that the cpu is at 1729.318 MHz and that scaling_cur_freq says that the cpu is at 800 MHz. Which one is right? And if /proc/cpuinfo now is right how do I make the scaling work again?


Thanks!

---

### Post by pasipasi on 2006-11-02
I have the same problem. Now I'm using the 386 kernel because the fan is blowing at max when I use the 686 one.

---

### Post by hardyn on 2006-11-02
this is the problem i have.... try this out...
[http://www.ubuntuforums.org/showthread.php?t=291361](http://www.ubuntuforums.org/showthread.php?t=291361)

if this switch solves your problem, its the same as mine, and that means the problem is still present, and has not been fixed as they say... ill reopen the bug @ launchpad if this solves your problem.

arlen

---

