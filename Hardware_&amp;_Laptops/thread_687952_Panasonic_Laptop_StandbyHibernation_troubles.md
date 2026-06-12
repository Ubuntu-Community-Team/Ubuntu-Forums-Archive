---
title: "Panasonic Laptop Standby/Hibernation troubles"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by Homoludens1000 on 2008-02-04
Dear all:

I'm having troubles getting my laptop (a Panasonic "Let's Note" laptop, I think outside of Japan that's known as a "Toughbook") running again after putting it into Standby and/or Hibernation mode.

After standby, the laptop starts up fine, but the screen remains black.
As for hibernation, the system doesn't even enter hibernation mode; the screen does go dark, but there is a blinking terminal cursor left in the upper left corner, and the system becomes completely unresponsive.

Is there any way to fix this? :confused:

I'm running KUBUNTU Gutsy Gibbon. I asked for help already on the Kubuntu/KDE forums, but didn't get any responses -- perhaps few people are using a Panasonic laptop?
Perhaps someone could tell me at least what kind of processes are responsible for standby/hibernation, so that I have a point to start from.
(I suspect the problem has something to do with KDE; I tried the standby mode with a UBUNTU Gutsy live CD, and everything worked fine. Naturally, I wasn't able to test hibernation.

---

### Post by Homoludens1000 on 2008-02-07
... please, anyone??

---

### Post by HugoRune on 2008-02-07
I have a panasonic let's note t5. 

I had troubles with hibernation and standby too, but I have no idea how to solve it, so I gave up using them. I never found a conclusive answer on what was requiered to get standby to work, it was very annoying.
Someone else with an older model had no problems at all.

I just updated to ubuntu 7.10 (from 6.10 I think), and standby and hibernation **seem** to work.

You could try that, or maybe someone with a clue has another idea

---

### Post by Homoludens1000 on 2008-02-14
I installed OpenSuse10.3 the other day to see whether it agrees more with my laptop (I would prefer using (K)Ubuntu, but I need to get standby/hibernation running -- it's a bit inconvenient on a laptop not to be able to use it ... )

Unfortunately, standby/hibernation didn't work on OpenSuse either, but at least I got an error log.
Could someone take a look at it and, if possible, tell me what to do?

Thanks!

homo ludens

*** Error Log Standby Mode ***
```

Thu Feb 14 11:57:23 UTC 2008: running suspend hooks.
===== Thu Feb 14 11:57:24 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Thu Feb 14 11:57:25 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/01logging =====
suspend initiated: Thu Feb 14 11:57:25 UTC 2008

Module                  Size  Used by
ext3                  131848  0 
jbd                    68148  1 ext3
mbcache                12292  1 ext3
ip6t_LOG               10496  7 
nf_conntrack_ipv6      22848  4 
xt_pkttype              5888  3 
ipt_LOG                 9984  8 
xt_limit                6656  15 
rfcomm                 43928  0 
l2cap                  30336  9 rfcomm
bluetooth              57172  4 rfcomm,l2cap
snd_pcm_oss            50432  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq                54452  0 
snd_seq_device         12172  1 snd_seq
microcode              15372  0 
edd                    12996  0 
ip6t_REJECT             9216  3 
xt_tcpudp               7168  4 
ipt_REJECT              8448  3 
xt_state                6528  8 
iptable_mangle          6784  0 
iptable_nat            11140  0 
nf_nat                 21912  1 iptable_nat
iptable_filter          6912  1 
ip6table_mangle         6656  0 
nf_conntrack_ipv4      14856  6 iptable_nat
nf_conntrack           61684  5 nf_conntrack_ipv6,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               9752  4 nf_conntrack_ipv6,nf_nat,nf_conntrack_ipv4,nf_conntrack
ip_tables              16324  3 iptable_mangle,iptable_nat,iptable_filter
ip6table_filter         6784  1 
ip6_tables             17476  3 ip6t_LOG,ip6table_mangle,ip6table_filter
x_tables               18308  11 ip6t_LOG,xt_pkttype,ipt_LOG,xt_limit,ip6t_REJECT,xt_tcpudp,ipt_REJECT,xt_state,iptable_nat,ip_tables,ip6_tables
ipv6                  268152  15 nf_conntrack_ipv6,ip6t_REJECT,ip6table_mangle
cpufreq_conservative    11272  0 
cpufreq_userspace       8704  0 
cpufreq_powersave       5888  0 
acpi_cpufreq           13192  0 
speedstep_lib           9220  0 
apparmor               40736  0 
pcmcia                 41076  0 
usbhid                 41300  0 
hid                    29184  1 usbhid
ff_memless              9352  1 usbhid
ipw2200               141896  0 
iTCO_wdt               14372  0 
rtc_cmos               12064  0 
rtc_core               23048  1 rtc_cmos
rtc_lib                 7040  1 rtc_core
yenta_socket           28684  1 
rsrc_nonstatic         15872  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              35400  1 ipw2200
ieee80211_crypt         9728  1 ieee80211
firmware_class         13568  3 microcode,pcmcia,ipw2200
intel_agp              27156  1 
thermal                19848  1 
iTCO_vendor_support     7812  1 iTCO_wdt
agpgart                35764  2 intel_agp
uhci_hcd               27024  0 
processor              40744  2 acpi_cpufreq,thermal
shpchp                 35092  0 
pci_hotplug            33216  1 shpchp
i2c_i801               12560  0 
i2c_core               27520  1 i2c_i801
battery                14724  0 
joydev                 13632  0 
snd_intel8x0           36636  0 
button                 12432  0 
ac                      9604  0 
snd_intel8x0m          21132  0 
snd_ac97_codec         97060  2 snd_intel8x0,snd_intel8x0m
ac97_bus                6272  1 snd_ac97_codec
snd_pcm                82564  4 snd_pcm_oss,snd_intel8x0,snd_intel8x0m,snd_ac97_codec
snd_timer              26756  2 snd_seq,snd_pcm
snd                    58164  9 snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_intel8x0,snd_intel8x0m,snd_ac97_codec,snd_pcm,snd_timer
soundcore              11460  1 snd
snd_page_alloc         13960  3 snd_intel8x0,snd_intel8x0m,snd_pcm
serio_raw              10756  0 
aufs                  206088  1 
squashfs               48772  1 
loop                   21636  2 
nls_utf8                6144  1 
st                     40092  0 
ide_disk               20480  0 
BusLogic               68316  0 
ide_cd                 40324  0 
usb_storage            80780  0 
ide_core              122948  3 ide_disk,ide_cd,usb_storage
8139cp                 26112  0 
sr_mod                 19492  1 
cdrom                  37020  2 ide_cd,sr_mod
sd_mod                 31104  0 
8139too                29184  0 
mii                     9344  2 8139cp,8139too
ehci_hcd               34956  0 
usbcore               123372  5 usbhid,uhci_hcd,usb_storage,ehci_hcd
sg                     37036  0 
ata_generic            11524  0 
ata_piix               21380  1 
libata                136776  2 ata_generic,ata_piix
scsi_mod              140376  7 st,BusLogic,usb_storage,sr_mod,sd_mod,sg,libata

             total       used       free     shared    buffers     cached
Mem:        766728     564896     201832          0      82224     362024
-/+ buffers/cache:     120648     646080
Swap:            0          0          0

===== Thu Feb 14 11:57:25 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Thu Feb 14 11:57:25 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/06autofs =====
===== Thu Feb 14 11:57:25 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Thu Feb 14 11:57:25 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/24dock =====
Thu Feb 14 11:57:26 UTC 2008: running misc hooks for event undock.
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/30s2disk-check =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/45pcmcia =====
ejecting PCMCIA cards...
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/55battery =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/80acpi-fan =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/80videobios =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/99Zgrub =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/99info =====
Thu Feb 14 11:57:26 UTC 2008: done running suspend hooks.
+ /usr/sbin/s2ram
Machine is unknown.
This machine can be identified by:
    sys_vendor   = #&%$a Electric Industrial Co.,Ltd."
    sys_product  = "CF-Y2FW7AXR"
    sys_version  = "004"
    bios_version = "V4.00L11"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.
+ RET=127
+ set +x
Thu Feb 14 11:57:26 UTC 2008: running resume hooks.
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/99info =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/99Zgrub =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/80videobios =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/80acpi-fan =====
===== Thu Feb 14 11:57:26 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/55battery =====
method return sender=:1.0 -> dest=:1.58
   boolean true
===== Thu Feb 14 11:57:27 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Thu Feb 14 11:57:27 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/45pcmcia =====
inserting PCMCIA cards...
===== Thu Feb 14 11:57:27 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/30s2disk-check =====
===== Thu Feb 14 11:57:27 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/24dock =====
Thu Feb 14 11:57:27 UTC 2008: running misc hooks for event dock.
===== Thu Feb 14 11:57:27 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Thu Feb 14 11:57:27 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/06autofs =====
===== Thu Feb 14 11:57:27 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Thu Feb 14 11:57:27 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/01logging =====
===== Thu Feb 14 11:57:27 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Thu Feb 14 11:57:27 UTC 2008: done running resume hooks.

```

*** Error Log Hibernation Mode ***
```

Thu Feb 14 11:59:08 UTC 2008: running hibernate hooks.
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/01logging =====
hibernate initiated: Thu Feb 14 11:59:08 UTC 2008

Module                  Size  Used by
ext3                  131848  0 
jbd                    68148  1 ext3
mbcache                12292  1 ext3
ip6t_LOG               10496  7 
nf_conntrack_ipv6      22848  4 
xt_pkttype              5888  3 
ipt_LOG                 9984  8 
xt_limit                6656  15 
rfcomm                 43928  0 
l2cap                  30336  9 rfcomm
bluetooth              57172  4 rfcomm,l2cap
snd_pcm_oss            50432  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq                54452  0 
snd_seq_device         12172  1 snd_seq
microcode              15372  0 
edd                    12996  0 
ip6t_REJECT             9216  3 
xt_tcpudp               7168  4 
ipt_REJECT              8448  3 
xt_state                6528  8 
iptable_mangle          6784  0 
iptable_nat            11140  0 
nf_nat                 21912  1 iptable_nat
iptable_filter          6912  1 
ip6table_mangle         6656  0 
nf_conntrack_ipv4      14856  6 iptable_nat
nf_conntrack           61684  5 nf_conntrack_ipv6,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               9752  4 nf_conntrack_ipv6,nf_nat,nf_conntrack_ipv4,nf_conntrack
ip_tables              16324  3 iptable_mangle,iptable_nat,iptable_filter
ip6table_filter         6784  1 
ip6_tables             17476  3 ip6t_LOG,ip6table_mangle,ip6table_filter
x_tables               18308  11 ip6t_LOG,xt_pkttype,ipt_LOG,xt_limit,ip6t_REJECT,xt_tcpudp,ipt_REJECT,xt_state,iptable_nat,ip_tables,ip6_tables
ipv6                  268152  15 nf_conntrack_ipv6,ip6t_REJECT,ip6table_mangle
cpufreq_conservative    11272  0 
cpufreq_userspace       8704  0 
cpufreq_powersave       5888  0 
acpi_cpufreq           13192  0 
speedstep_lib           9220  0 
apparmor               40736  0 
pcmcia                 41076  0 
usbhid                 41300  0 
hid                    29184  1 usbhid
ff_memless              9352  1 usbhid
ipw2200               141896  0 
iTCO_wdt               14372  0 
rtc_cmos               12064  0 
rtc_core               23048  1 rtc_cmos
rtc_lib                 7040  1 rtc_core
yenta_socket           28684  1 
rsrc_nonstatic         15872  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              35400  1 ipw2200
ieee80211_crypt         9728  1 ieee80211
firmware_class         13568  3 microcode,pcmcia,ipw2200
intel_agp              27156  1 
thermal                19848  1 
iTCO_vendor_support     7812  1 iTCO_wdt
agpgart                35764  2 intel_agp
uhci_hcd               27024  0 
processor              40744  2 acpi_cpufreq,thermal
shpchp                 35092  0 
pci_hotplug            33216  1 shpchp
i2c_i801               12560  0 
i2c_core               27520  1 i2c_i801
battery                14724  0 
joydev                 13632  0 
snd_intel8x0           36636  0 
button                 12432  0 
ac                      9604  0 
snd_intel8x0m          21132  0 
snd_ac97_codec         97060  2 snd_intel8x0,snd_intel8x0m
ac97_bus                6272  1 snd_ac97_codec
snd_pcm                82564  4 snd_pcm_oss,snd_intel8x0,snd_intel8x0m,snd_ac97_codec
snd_timer              26756  2 snd_seq,snd_pcm
snd                    58164  9 snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_intel8x0,snd_intel8x0m,snd_ac97_codec,snd_pcm,snd_timer
soundcore              11460  1 snd
snd_page_alloc         13960  3 snd_intel8x0,snd_intel8x0m,snd_pcm
serio_raw              10756  0 
aufs                  206088  1 
squashfs               48772  1 
loop                   21636  2 
nls_utf8                6144  1 
st                     40092  0 
ide_disk               20480  0 
BusLogic               68316  0 
ide_cd                 40324  0 
usb_storage            80780  0 
ide_core              122948  3 ide_disk,ide_cd,usb_storage
8139cp                 26112  0 
sr_mod                 19492  1 
cdrom                  37020  2 ide_cd,sr_mod
sd_mod                 31104  0 
8139too                29184  0 
mii                     9344  2 8139cp,8139too
ehci_hcd               34956  0 
usbcore               123372  5 usbhid,uhci_hcd,usb_storage,ehci_hcd
sg                     37036  0 
ata_generic            11524  0 
ata_piix               21380  1 
libata                136776  2 ata_generic,ata_piix
scsi_mod              140376  7 st,BusLogic,usb_storage,sr_mod,sd_mod,sg,libata

             total       used       free     shared    buffers     cached
Mem:        766728     571708     195020          0      82944     364500
-/+ buffers/cache:     124264     642464
Swap:            0          0          0

===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/06autofs =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/24dock =====
Thu Feb 14 11:59:08 UTC 2008: running misc hooks for event undock.
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/30s2disk-check =====
INFO: checking for suspend-to-disk prerequisites...
ERROR: no resume parameter on kernel commandline, can not suspend
WARNING: /var/run/pm-utils.inhibit will be created to prevent suspending!
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/45pcmcia =====
ejecting PCMCIA cards...
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/55battery =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/80acpi-fan =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/80videobios =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Thu Feb 14 11:59:08 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/99Zgrub =====
INFO: running prepare-grub
/usr/lib/pm-utils/sleep.d/99Zgrub: line 14: /boot/grub/menu.lst: No such file or directory
WARNING: no kernelfile matching the running kernel found
running kernel: '2.6.22.5-31-default', probably booting kernel: '2.6.22.5-31-default'
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/99info =====
Thu Feb 14 11:59:10 UTC 2008: done running hibernate hooks.
Thu Feb 14 11:59:10 UTC 2008: running thaw hooks.
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/99info =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/99Zgrub =====
INFO: running grub-once-restore
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/80videobios =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/80acpi-fan =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/55battery =====
method return sender=:1.0 -> dest=:1.92
   boolean true
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/45pcmcia =====
inserting PCMCIA cards...
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/30s2disk-check =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/24dock =====
Thu Feb 14 11:59:10 UTC 2008: running misc hooks for event dock.
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/06autofs =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/01logging =====
===== Thu Feb 14 11:59:10 UTC 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Thu Feb 14 11:59:10 UTC 2008: done running thaw hooks.

```

---

