---
title: "Cannot Hibernate in Karmic"
date: 2010-03-22
forum: Hardware
---

### Post by snyderxc on 2010-03-22
Hi all! I'm new to the Ubuntu community and I'm loving it right now!

That said, I am having difficulty with hibernating my system. If I click the "Hibernate" button (from the "Shutdown" panel applet), it will not hibernate.  It appears as if it will, but instead, the mouse shuts off (laser mouse, light goes out), the keyboard stays on (Num-Lock lit) and the screen stays on (Black, but lit with an underscore ( _ ) flashing in the upper left hand corner). I have installed "USWSUSP," "Hibernate," and "pm-utils" in Synaptic Packet manager.

I should mention that I am using the Wusb54GSC Wireless card also, although I have tried turning off networking before suspend with the same results.

I have attached my log file:

```
Initial commandline parameters: 
Sat Mar  6 20:11:07 EST 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_cp437               5372  0 
cifs                  254908  0 
cbc                     3516  623 
aes_i586                8124  624 
aes_generic            27484  1 aes_i586
binfmt_misc             8356  1 
dm_crypt               12928  0 
arc4                    1660  0 
ecb                     2524  1 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
rndis_wlan             21476  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
cfg80211               93052  1 rndis_wlan
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1100816      54052          0      56276     644468
-/+ buffers/cache:     400072     754796
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Sat Mar  6 20:11:11 EST 2010: performing hibernate
Sat Mar  6 20:11:18 EST 2010: Awake.
Sat Mar  6 20:11:18 EST 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Sat Mar  6 20:11:23 EST 2010: Finished.
Initial commandline parameters: 
Mon Mar  8 23:11:46 EST 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
cbc                     3516  565 
aes_i586                8124  566 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
binfmt_misc             8356  1 
ipt_REJECT              2812  0 
ipt_LOG                 5344  0 
xt_limit                2176  0 
dm_crypt               12928  0 
xt_tcpudp               2780  0 
xt_state                1820  0 
ipt_addrtype            2204  0 
ip6table_filter         3164  1 
ip6_tables             13004  1 ip6table_filter
nf_nat_irc              2012  0 
nf_conntrack_irc        4992  1 nf_nat_irc
nf_nat_ftp              2652  0 
nf_nat                 18096  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      13352  2 nf_nat
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
nf_conntrack_ftp        6880  1 nf_nat_ftp
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
nf_conntrack           67484  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  1 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  1 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868     981248     173620          0      49272     443088
-/+ buffers/cache:     488888     665980
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Mar  8 23:11:52 EST 2010: performing hibernate
Mon Mar  8 23:12:11 EST 2010: Awake.
Mon Mar  8 23:12:13 EST 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Mon Mar  8 23:12:28 EST 2010: Finished.
Initial commandline parameters: 
Wed Mar 10 23:35:38 EST 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
cbc                     3516  1227 
aes_i586                8124  1228 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
ppdev                   6688  0 
k8temp                  4188  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1096328      58540          0      44112     438272
-/+ buffers/cache:     613944     540924
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Wed Mar 10 23:35:41 EST 2010: performing hibernate
Wed Mar 10 23:35:57 EST 2010: Awake.
Wed Mar 10 23:35:57 EST 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Wed Mar 10 23:36:10 EST 2010: Finished.
Initial commandline parameters: 
Thu Mar 11 23:37:17 EST 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
cbc                     3516  379 
aes_i586                8124  380 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  7 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
ppdev                   6688  0 
k8temp                  4188  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  23 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  98 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  2 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1115612      39256          0      18672     210444
-/+ buffers/cache:     886496     268372
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Thu Mar 11 23:37:26 EST 2010: performing hibernate
Thu Mar 11 23:37:43 EST 2010: Awake.
Thu Mar 11 23:37:44 EST 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Thu Mar 11 23:38:02 EST 2010: Finished.
Initial commandline parameters: 
Fri Mar 12 07:59:45 EST 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
cbc                     3516  118 
aes_i586                8124  119 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  7 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
ppdev                   6688  0 
k8temp                  4188  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  23 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  98 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  1 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1131748      23120          0       8740      62984
-/+ buffers/cache:    1060024      94844
Swap:            0          0          0
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Fri Mar 12 07:59:55 EST 2010: performing hibernate
Fri Mar 12 08:00:09 EST 2010: Awake.
Fri Mar 12 08:00:10 EST 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Fri Mar 12 08:00:24 EST 2010: Finished.
Initial commandline parameters: 
Sat Mar 13 23:47:32 EST 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
cbc                     3516  1495 
aes_i586                8124  1496 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1083160      71708          0      35408     640136
-/+ buffers/cache:     407616     747252
Swap:      1048568       2188    1046380
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Sat Mar 13 23:47:35 EST 2010: performing hibernate
Sat Mar 13 23:48:02 EST 2010: Awake.
Sat Mar 13 23:48:02 EST 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Sat Mar 13 23:48:09 EST 2010: Finished.
Initial commandline parameters: 
Mon Mar 15 16:32:10 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
cbc                     3516  165 
aes_i586                8124  166 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1119376      35492          0      18564     730744
-/+ buffers/cache:     370068     784800
Swap:      1048568      24996    1023572
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Mar 15 16:32:14 EDT 2010: performing hibernate
Mon Mar 15 16:32:37 EDT 2010: Awake.
Mon Mar 15 16:32:38 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: sInitial commandline parameters: 
Mon Mar 15 23:31:09 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  0 
vfat                   10716  0 
fat                    51452  1 vfat
cbc                     3516  339 
aes_i586                8124  340 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
snd                    59204  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868     820516     334352          0      32048     470264
-/+ buffers/cache:     318204     836664
Swap:      1048568          0    1048568
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Mar 15 23:31:12 EDT 2010: performing hibernate
Mon Mar 15 23:31:35 EDT 2010: Awake.
Mon Mar 15 23:31:35 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Mon Mar 15 23:31:39 EDT 2010: Finished.
Initial commandline parameters: 
Tue Mar 16 07:10:10 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
cbc                     3516  213 
aes_i586                8124  214 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
dm_crypt               12928  0 
binfmt_misc             8356  1 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
iptable_filter          3100  0 
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
parport_pc             31940  1 
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  2 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1102948      51920          0     158068     491596
-/+ buffers/cache:     453284     701584
Swap:      1048568        228    1048340
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Tue Mar 16 07:10:14 EDT 2010: performing hibernate
Tue Mar 16 07:10:43 EDT 2010: Awake.
Tue Mar 16 07:10:44 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Tue Mar 16 07:10:52 EDT 2010: Finished.
Initial commandline parameters: 
Wed Mar 17 07:06:54 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
cbc                     3516  844 
aes_i586                8124  845 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
iptable_filter          3100  0 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
rndis_host              7356  1 rndis_wlan
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52768  1 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1091456      63412          0      59420     528064
-/+ buffers/cache:     503972     650896
Swap:      1048568          0    1048568
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Wed Mar 17 07:06:58 EDT 2010: performing hibernate
Wed Mar 17 07:07:40 EDT 2010: Awake.
Wed Mar 17 07:07:40 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Wed Mar 17 07:07:52 EDT 2010: Finished.
Initial commandline parameters: 
Fri Mar 19 06:51:49 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  0 
vfat                   10716  0 
fat                    51452  1 vfat
cbc                     3516  368 
aes_i586                8124  369 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
ip_tables              11692  1 iptable_filter
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
x_tables               16544  1 ip_tables
i2c_nforce2             6784  0 
rndis_host              7356  1 rndis_wlan
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
nvidia               9586440  36 
cdc_ether               5308  1 rndis_host
agpgart                34988  1 nvidia
k8temp                  4188  0 
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
ppdev                   6688  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868     864928     289940          0      75932     375320
-/+ buffers/cache:     413676     741192
Swap:      1048568          0    1048568
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Fri Mar 19 06:51:54 EDT 2010: performing hibernate
Fri Mar 19 06:52:22 EDT 2010: Awake.
Fri Mar 19 06:52:22 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Fri Mar 19 06:52:29 EDT 2010: Finished.
Initial commandline parameters: 
Sat Mar 20 15:11:48 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
cbc                     3516  566 
aes_i586                8124  567 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
dm_crypt               12928  0 
binfmt_misc             8356  1 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
iptable_filter          3100  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868     828456     326412          0      79148     303060
-/+ buffers/cache:     446248     708620
Swap:      1048568      38144    1010424
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Sat Mar 20 15:11:52 EDT 2010: performing hibernate
Sat Mar 20 15:12:15 EDT 2010: Awake.
Sat Mar 20 15:12:15 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Sat Mar 20 15:12:22 EDT 2010: Finished.
Initial commandline parameters: 
Sat Mar 20 18:39:27 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  1 
ufs                    75524  0 
qnx4                    8576  0 
hfsplus                73632  0 
hfs                    43296  0 
minix                  27588  0 
ntfs                   98272  0 
vfat                   10716  1 
msdos                   7836  0 
fat                    51452  2 vfat,msdos
jfs                   177380  0 
xfs                   512096  0 
exportfs                4412  1 xfs
reiserfs              229288  0 
cbc                     3516  345 
aes_i586                8124  346 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  1 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_intel8x0           30168  4 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
snd                    59204  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  1 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1135796      19072          0      40748     468136
-/+ buffers/cache:     626912     527956
Swap:      1048568      21960    1026608
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Sat Mar 20 18:39:33 EDT 2010: performing hibernate
Sat Mar 20 18:40:11 EDT 2010: Awake.
Sat Mar 20 18:40:12 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Sat Mar 20 18:40:31 EDT 2010: Finished.
Initial commandline parameters: 
Sat Mar 20 18:43:27 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
k8temp                  4188  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
ppdev                   6688  0 
i2c_nforce2             6784  0 
parport_pc             31940  1 
nvidia               9586440  26 
agpgart                34988  1 nvidia
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868     374756     780112          0     112524     166056
-/+ buffers/cache:      96176    1058692
Swap:      1048568          0    1048568
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Sat Mar 20 18:43:29 EDT 2010: performing hibernate
Sat Mar 20 18:43:43 EDT 2010: Awake.
Sat Mar 20 18:43:43 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Sat Mar 20 18:43:45 EDT 2010: Finished.
Initial commandline parameters: 
Sat Mar 20 18:44:52 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
k8temp                  4188  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
ppdev                   6688  0 
i2c_nforce2             6784  0 
parport_pc             31940  1 
nvidia               9586440  26 
agpgart                34988  1 nvidia
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868     376820     778048          0     112556     167448
-/+ buffers/cache:      96816    1058052
Swap:      1048568          0    1048568
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Sat Mar 20 18:44:53 EDT 2010: performing hibernate
Sat Mar 20 18:45:08 EDT 2010: Awake.
Sat Mar 20 18:45:08 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Sat Mar 20 18:45:09 EDT 2010: Finished.
Initial commandline parameters: 
Mon Mar 22 00:10:55 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  0 
vfat                   10716  0 
fat                    51452  1 vfat
cbc                     3516  346 
aes_i586                8124  347 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  4 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
snd_timer              22276  2 snd_pcm,snd_seq
ip_tables              11692  1 iptable_filter
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               9586440  36 
snd                    59204  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               16544  1 ip_tables
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
i2c_nforce2             6784  0 
agpgart                34988  1 nvidia
k8temp                  4188  0 
rndis_host              7356  1 rndis_wlan
ppdev                   6688  0 
cdc_ether               5308  1 rndis_host
parport_pc             31940  1 
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  0 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1115916      38952          0      25424     258296
-/+ buffers/cache:     832196     322672
Swap:      1048568      89164     959404
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Mar 22 00:11:01 EDT 2010: performing hibernate
Mon Mar 22 00:11:31 EDT 2010: Awake.
Mon Mar 22 00:11:32 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Mon Mar 22 00:12:08 EDT 2010: Finished.
Initial commandline parameters: 
Mon Mar 22 08:16:42 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
cbc                     3516  137 
aes_i586                8124  138 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  3 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1123608      31260          0     124060     254504
-/+ buffers/cache:     745044     409824
Swap:      1048568      30332    1018236
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Mar 22 08:16:47 EDT 2010: performing hibernate
Mon Mar 22 08:17:08 EDT 2010: Awake.
Mon Mar 22 08:17:08 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Mon Mar 22 08:17:13 EDT 2010: Finished.
Initial commandline parameters: 
Mon Mar 22 19:22:01 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  1 
vfat                   10716  1 
fat                    51452  1 vfat
cbc                     3516  388 
aes_i586                8124  389 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  1 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  4 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
i2c_nforce2             6784  0 
nvidia               9586440  40 
agpgart                34988  1 nvidia
snd                    59204  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  1 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1067500      87368          0      17516     341352
-/+ buffers/cache:     708632     446236
Swap:      1048568     130528     918040
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Mar 22 19:22:06 EDT 2010: performing hibernate
Mon Mar 22 19:22:27 EDT 2010: Awake.
Mon Mar 22 19:22:27 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Mon Mar 22 19:22:31 EDT 2010: Finished.
Initial commandline parameters: 
Mon Mar 22 20:01:31 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3740  1 
vfat                   10716  1 
fat                    51452  1 vfat
cbc                     3516  301 
aes_i586                8124  302 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  1 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
i2c_nforce2             6784  0 
nvidia               9586440  40 
agpgart                34988  1 nvidia
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  2 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1129916      24952          0      42008     347116
-/+ buffers/cache:     740792     414076
Swap:      1048568     151892     896676
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Mar 22 20:01:40 EDT 2010: performing hibernate
Mon Mar 22 20:02:19 EDT 2010: Awake.
Mon Mar 22 20:02:22 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Mon Mar 22 20:02:47 EDT 2010: Finished.
Initial commandline parameters: 
Mon Mar 22 20:20:02 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
cbc                     3516  509 
aes_i586                8124  510 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
dm_crypt               12928  0 
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
nvidia               9586440  36 
agpgart                34988  1 nvidia
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  1 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868     920164     234704          0      46856     544716
-/+ buffers/cache:     328592     826276
Swap:      1048568          0    1048568
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Mar 22 20:20:06 EDT 2010: performing hibernate
Mon Mar 22 20:20:27 EDT 2010: Awake.
Mon Mar 22 20:20:27 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Mon Mar 22 20:20:32 EDT 2010: Finished.
Initial commandline parameters: 
Mon Mar 22 20:38:48 EDT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux Ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
cbc                     3516  1142 
aes_i586                8124  1143 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
nls_cp437               5372  0 
nls_utf8                1568  1 
cifs                  254908  2 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
rndis_wlan             21476  0 
cfg80211               93052  1 rndis_wlan
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ppdev                   6688  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
rndis_host              7356  1 rndis_wlan
cdc_ether               5308  1 rndis_host
usbnet                 17188  3 rndis_wlan,rndis_host,cdc_ether
mii                     5212  1 usbnet
k8temp                  4188  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
parport_pc             31940  1 
nvidia               9586440  36 
agpgart                34988  1 nvidia
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52768  1 
usbhid                 38208  0 
forcedeth              54152  0 
             total       used       free     shared    buffers     cached
Mem:       1154868    1051280     103588          0      95244     584636
-/+ buffers/cache:     371400     783468
Swap:      1048568          0    1048568
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Mar 22 20:38:51 EDT 2010: performing hibernate
Mon Mar 22 20:39:20 EDT 2010: Awake.
Mon Mar 22 20:39:20 EDT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Mon Mar 22 20:39:28 EDT 2010: Finished.

```

Thanks in advance,
SnyderXC

---

### Post by snyderxc on 2010-03-24
Can anyone give me help with this? I really like Ubuntu otherwise!

---

### Post by bcbc on 2010-03-24
> **snyderxc said:**
> Can anyone give me help with this? I really like Ubuntu otherwise!

Your swap has to be as big as your RAM. Run 'free' from terminal. From your output it looks like you don't have any swap - if that's the case it's not going to work.

Your swap will be in the /etc/fstab file. If you change it, the UUID will have to be updated here. It also has to be in /etc/initramfs-tools/conf.d/resume - this needs to match the uuid on the swap. If you have to change this file, then you must run:
```
$ sudo update-initramfs -u
```

---

### Post by snyderxc on 2010-03-24
Thanks for the reply! I ran free and my out put was:
```
             total       used       free     shared    buffers     cached
Mem:       1154868     692336     462532          0      58308     339444
-/+ buffers/cache:     294584     860284
Swap:      1048568          0    1048568

```

I have 1.15 Gigs RAM, so it would appear that I only have 1 Gig swap.  I have added an additional 2 Gigs, so I hope all goes well.  Will update soon!

Thanks again,
SnyderXC

---

### Post by snyderxc on 2010-03-24
Ok, so I tried to hibernate now and it seemed to work, but when I restarted it, it just went to the Grub2 boot screen and booted up like it was never hibernated.  Any other suggestions?

---

### Post by farheart on 2010-03-24
I have exact same problem about the Hibernate in Karmic (64bit)

My case is: it seems that hibernate can work, but during the the hibernating process there pops up two errors about USB something (I guess it is because that I am using a usb wireless mouse), but the system finally power off.

When I press the power button to restart it. It just start as a new boot -- exactly as the previous post.

My computer: Lenovo Ideapad Y450, 4GB RAM, Swap : 2GB

output from free command:

             total       used       free     shared    buffers     cached
Mem:       3893716     893504    3000212          0      29608     360096
-/+ buffers/cache:     503800    3389916
Swap:      2096472          0    2096472


Any suggestion will be appreciated!

---

### Post by bcbc on 2010-03-25
> **snyderxc said:**
> Ok, so I tried to hibernate now and it seemed to work, but when I restarted it, it just went to the Grub2 boot screen and booted up like it was never hibernated.  Any other suggestions?

This was what was happening to me - until I updated the /etc/initramfs-tools/conf.d/resume file, setting it to the new swap partition uuid - if you've done that and updated the initramfs, then I'm out of ideas. It will still go to the grub2 boot menu, but it should automatically resume. 

All I can suggest is you double check that the new swap is set up correctly.

---

### Post by bcbc on 2010-03-25
> **farheart said:**
> I have exact same problem about the Hibernate in Karmic (64bit)

My case is: it seems that hibernate can work, but during the the hibernating process there pops up two errors about USB something (I guess it is because that I am using a usb wireless mouse), but the system finally power off.

When I press the power button to restart it. It just start as a new boot -- exactly as the previous post.

My computer: Lenovo Ideapad Y450, 4GB RAM, Swap : 2GB

output from free command:

             total       used       free     shared    buffers     cached
Mem:       3893716     893504    3000212          0      29608     360096
-/+ buffers/cache:     503800    3389916
Swap:      2096472          0    2096472


Any suggestion will be appreciated!

Your swap isn't big enough - it must be at least as big as your RAM i.e. 4GB. Follow the info above once you've increased your swap. If you need help with the swap let me know.

I don't know about your wireless mouse, but I do know that on my one computer that uses ndiswrapper for the wireless driver, I have to remove the module (rmmod) and add it back (modprobe) - otherwise it doesn't work on resume. So you might have to do something similar - but that's just a guess.

---

### Post by snyderxc on 2010-03-25
bcbc,
Thanks so much for all your help! You've done a great job and I am pleased to say that I can hibernate my computer!  I edited: /etc/initramfs-tools/conf.d/resume

and ran: $ sudo update-initramfs -u

I ignored the "More than one resume canidate found" warning, and we're good to go!

Thanks again,
SnyderXC

---

### Post by bcbc on 2010-03-25
> **snyderxc said:**
> bcbc,
Thanks so much for all your help! You've done a great job and I am pleased to say that I can hibernate my computer!  I edited: /etc/initramfs-tools/conf.d/resume

and ran: $ sudo update-initramfs -u

I ignored the "More than one resume canidate found" warning, and we're good to go!

Thanks again,
SnyderXC

Great! You're welcome :)

---

### Post by norseman-has-a-laptop on 2010-03-25
wow ill have to try it out

---

### Post by eaglemystic69 on 2010-03-26
I have a similar issue Im hoping someone can help with . . .

Karmic boot stalls at initramfs command.  Im a GUI guy, so the commands must be simple or spelled out.

I have used: gedit /usr/sbin/update-initramfs, and dont know what to edit.

And this command:~$ sudo update-initramfs -t
You must specify at least one of -c, -u, or -d.

Not sure where to go now.  Im not a skilled commando

---

### Post by farheart on 2010-03-30
Just follow bcbc's suggestion, to increase the swap partition to 4.11GiB, but there still is a problem with the original hibernate function coming with Gnome. So I install the uswsusp and finally it works. 

Thanks a lot for the response.

---

