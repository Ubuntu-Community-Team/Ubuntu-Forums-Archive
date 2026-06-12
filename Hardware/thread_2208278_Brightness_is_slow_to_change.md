---
title: "Brightness is slow to change"
date: 2014-02-27
forum: Hardware
---

### Post by brian8765 on 2014-02-27
Hi,
Dell Latitude E5430
Ubuntu 13.10
Intel 3rd generation Graphics card

The brightness level is slow to react. This is when I change it via fn buttin and in the brightness settings. It takes about a second to update and is like it freezes for a second, however the cpu does not seem to go very high

Thanks

---

### Post by Toz on 2014-02-27
Lets have a closer look at some of the settings. Open a terminal window, type in the following commands, and post back the results within **[noparse]```
 
```[/noparse]** tags:

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```

3. Information about your known backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

4. A listing of your loaded kernel modules:
```
lsmod
```

5. Your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by brian8765 on 2014-03-01
Hi Thanks for the quick reply.
cat /proc/cmdline:
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic root=UUID=5e4fb84e-d8e6-46e7-aa6f-06bed9dfc9ee ro quiet splash vt.handoff=7
```

lspci -k | grep -iA2 VGA:
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Dell Device 053c
    Kernel driver in use: i915
```

for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done

```
 /sys/class/backlight/acpi_video0

6
100
6

 /sys/class/backlight/intel_backlight
123
976
123

```

lsmod:
```
 Module                  Size  Used by
rfcomm                 53664  12 
bnep                   18959  2 
binfmt_misc            13140  1 
snd_hda_codec_hdmi     40373  1 
snd_hda_codec_idt      44605  1 
joydev                 17097  0 
ip6t_REJECT            12826  1 
xt_hl                  12465  6 
ip6t_rt                13259  3 
nf_conntrack_ipv6      18414  7 
nf_defrag_ipv6         26070  1 nf_conntrack_ipv6
ipt_REJECT             12485  1 
xt_LOG                 17446  10 
xt_limit               12541  13 
xt_tcpudp              12756  22 
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  7 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  14 
arc4                   12536  2 
ip6table_filter        12711  1 
iwldvm                219872  0 
ip6_tables             17819  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
mac80211              517444  1 iwldvm
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
nf_nat                 25588  1 nf_nat_ftp
nf_conntrack_ftp       14056  1 nf_nat_ftp
nf_conntrack           82913  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
x86_pkg_temp_thermal    13810  0 
x_tables               22067  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
intel_powerclamp       14239  0 
coretemp               13195  0 
kvm_intel             128218  0 
kvm                   368949  1 kvm_intel
crc32_pclmul           12967  0 
aesni_intel            18156  1 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
ppdev                  17391  0 
dell_laptop            17161  0 
dcdbas                 14383  1 dell_laptop
btusb                  23443  0 
snd_hda_intel          42658  3 
snd_hda_codec         164003  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
microcode              18894  0 
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
psmouse                90642  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
serio_raw              13189  0 
snd_seq_midi_event     14475  1 snd_seq_midi
wmi                    18590  1 dell_wmi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
parport_pc             31981  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
bluetooth             323656  22 bnep,btusb,rfcomm
i915                  594442  3 
snd_timer              24447  2 snd_pcm,snd_seq
iwlwifi               147801  1 iwldvm
video                  18777  1 i915
drm_kms_helper         46867  1 i915
mac_hid                13037  0 
cfg80211              401762  3 iwlwifi,mac80211,iwldvm
drm                   242400  4 i915,drm_kms_helper
snd                    60790  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                16864  0 
mei_me                 13933  0 
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
mei                    66411  1 mei_me
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
tg3                   152066  0 
ahci                   25579  2 
sdhci_pci              18481  0 
ptp                    18156  1 tg3
libahci                26619  1 ahci
sdhci                  37644  1 sdhci_pci
pps_core               18546  1 ptp


```

/var/log/Xorg.0.log:
[http://paste.ubuntu.com/7019222/](http://paste.ubuntu.com/7019222/)

---

### Post by Toz on 2014-03-01
Your system is providing 2 backlight interfaces (acpi_video0 and intel_backlight) which may be causing this issue. With root privileges, create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...this will force your system to use the intel_backlight interface for backlight management. You'll need to log out and back in again for it take effect. See if that helps.

If not, we can try forcing it at the kernel level.

---

### Post by brian8765 on 2014-03-02
Hi,
That solved the issue of slow response,many thanks. However this is only the case when I change it with the slider in settings. With the fn key it is still slightly slow to respond and cannot go outside the range of 10-30%. In not sure if this is relevant but when I change with the fn key there is a flash before the change.
Thanks

---

### Post by Toz on 2014-03-02
Can you follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions at the [Kernel Boot Parameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") and boot with the **acpi_backlight=vendor** kernel parameter. When you boot with it, post back the same results as requested from post #2 and try both the slider and function keys to change the brightness and see if it makes a difference.

---

### Post by brian8765 on 2014-03-02
That did the trick, thank you. I have added that line to the boot parameters permanently.

cat /proc/cmdline:
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic root=UUID=5e4fb84e-d8e6-46e7-aa6f-06bed9dfc9ee ro quiet splash acpi_backlight=vendor vt.handoff=7


```

lspci -k | grep -iA2 VGA:
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Dell Device 053c
    Kernel driver in use: i915


```

for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat  $interface/{brightness,max_brightness,actual_brightness}; done
```

 /sys/class/backlight/dell_backlight
1
15
1

 /sys/class/backlight/intel_backlight
123
976
123


```

lsmod:
```

Module                  Size  Used by
rfcomm                 53664  12 
bnep                   18959  2 
binfmt_misc            13140  1 
joydev                 17097  0 
x86_pkg_temp_thermal    13810  0 
intel_powerclamp       14239  0 
coretemp               13195  0 
snd_hda_codec_hdmi     40373  1 
kvm_intel             128218  0 
kvm                   368949  1 kvm_intel
crc32_pclmul           12967  0 
aesni_intel            18156  2 
aes_i586               16995  1 aesni_intel
snd_hda_codec_idt      44605  1 
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
ppdev                  17391  0 
arc4                   12536  2 
ip6t_REJECT            12826  1 
xt_hl                  12465  6 
iwldvm                219872  0 
ip6t_rt                13259  3 
nf_conntrack_ipv6      18414  7 
mac80211              517444  1 iwldvm
nf_defrag_ipv6         26070  1 nf_conntrack_ipv6
ipt_REJECT             12485  1 
xt_LOG                 17446  10 
xt_limit               12541  13 
xt_tcpudp              12756  22 
xt_addrtype            12563  4 
nf_conntrack_ipv4      14492  7 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  14 
ip6table_filter        12711  1 
ip6_tables             17819  1 ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12645  0 
nf_nat                 25588  1 nf_nat_ftp
nf_conntrack_ftp       14056  1 nf_nat_ftp
nf_conntrack           82913  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12706  1 
ip_tables              17987  1 iptable_filter
x_tables               22067  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
dell_laptop            17161  0 
dcdbas                 14383  1 dell_laptop
snd_hda_intel          42658  3 
snd_hda_codec         164003  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
btusb                  23443  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
microcode              18894  0 
psmouse                90642  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13189  0 
snd_timer              24447  2 snd_pcm,snd_seq
iwlwifi               147801  1 iwldvm
lpc_ich                16864  0 
snd                    60790  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  594442  3 
bluetooth             323656  22 bnep,btusb,rfcomm
cfg80211              401762  3 iwlwifi,mac80211,iwldvm
soundcore              12600  1 snd
mei_me                 13933  0 
drm_kms_helper         46867  1 i915
mei                    66411  1 mei_me
drm                   242400  4 i915,drm_kms_helper
wmi                    18590  1 dell_wmi
i2c_algo_bit           13197  1 i915
parport_pc             31981  0 
video                  18777  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
tg3                   152066  0 
ahci                   25579  2 
ptp                    18156  1 tg3
sdhci_pci              18481  0 
libahci                26619  1 ahci
sdhci                  37644  1 sdhci_pci
pps_core               18546  1 ptp


```

---

### Post by brian8765 on 2014-03-02
/var/log/Xorg.0.log
[http://paste.ubuntu.com/7024434/](http://paste.ubuntu.com/7024434/)

---

