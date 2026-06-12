---
title: "closing screen lid not turn off monitor power (ubuntu 10.04)"
date: 2011-07-11
forum: Hardware
---

### Post by linux83 on 2011-07-11
Hello Friends,

could some one help me to resolve this issue, i have laptop hp nc 6320,
with Ubuntu 10.04. when i close screen lid, it's not power of the monitor power.

maximum i found is that to create a luncher for this command:

xset dpms force off

and click it when i need to close the monitor.

this is not practical.

thanks a lot for your help.


linux83.

---

### Post by linux83 on 2011-07-13
Hello Freinds,

any help please.

---

### Post by matt_symes on 2011-07-13
Hi

Can you post the log file

```
cat  /var/log/pm-suspend.log
```That might give some clues. If not it might be worth looking in the syslog after (it has suspend information far more detailed than the log above).

Can you suspend correctly (power off the monitor) from the suspend option in the menu ? Is it only when you close the lid (and not from the menu) that the monitor will not power down ?

What version of Ubuntu are you using ?

Please post the output of (this will tell us)

```
uname -r
cat /etc/lsb-release
```Kind regards

---

### Post by linux83 on 2011-07-14
Hi, thanks for reply, yes i can suspend and every thing is ok excep power off monitor is not working when i 
close the lid, it's only blank screen as per the options.

med@workss:~$ cat  /var/log/pm-suspend.log

Initial commandline parameters: 
Tue Jul  5 01:44:59 AST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux workss 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
8021q                  18564  0 
garp                    6284  1 8021q
stp                     1655  1 garp
binfmt_misc             6587  1 
vboxnetadp              6808  0 
vboxnetflt             18753  0 
vboxdrv               230336  2 vboxnetadp,vboxnetflt
snd_hda_codec_si3054     3396  1 
snd_hda_codec_analog    58598  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
tpm_infineon            8001  0 
arc4                    1153  2 
pcmcia                 30912  0 
snd_hda_intel          22165  6 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  7 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                68919  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288642  3 
iwlcore               106594  1 iwl3945
ppdev                   5259  0 
tifm_7xx1               3690  0 
drm_kms_helper         29329  1 i915
tpm_tis                 7584  0 
yenta_socket           20536  1 
rsrc_nonstatic         10559  1 yenta_socket
mac80211              205402  2 iwl3945,iwlcore
psmouse                63245  0 
serio_raw               3978  0 
parport_pc             26250  1 
snd                    54244  22 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core               6045  1 tifm_7xx1
tpm                    13936  2 tpm_infineon,tpm_tis
tpm_bios                5266  1 tpm
sdhci_pci               5502  0 
sdhci                  15654  1 sdhci_pci
led_class               2864  3 iwl3945,iwlcore,sdhci
intel_agp              24671  2 i915
drm                   163066  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
pcmcia_core            32996  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  17375  1 i915
cfg80211              126144  3 iwl3945,iwlcore,mac80211
output                  1871  1 video
agpgart                31788  2 intel_agp,drm
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
hid                    67096  1 usbhid
ohci1394               27238  0 
tg3                   109580  0 
ieee1394               81213  1 ohci1394
ahci                   32392  3 
             total       used       free     shared    buffers     cached
Mem:       3347144    1454812    1892332          0     114064    1074452
-/+ buffers/cache:     266296    3080848
Swap:      1951736          0    1951736
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon hibernate hibernate:Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... none found.
success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Tue Jul  5 01:45:01 AST 2011: performing hibernate
Tue Jul  5 01:45:56 AST 2011: Awake.
Tue Jul  5 01:45:58 AST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon thaw hibernate:Starting SmartLink Modem driver for: hw:0,6.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Tue Jul  5 01:46:31 AST 2011: Finished.
Initial commandline parameters: 
Wed Jul  6 13:31:45 AST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux workss 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
vboxnetadp              6808  0 
vboxnetflt             18753  0 
vboxdrv               230336  2 vboxnetadp,vboxnetflt
snd_hda_codec_si3054     3396  1 
snd_hda_codec_analog    58598  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
tpm_infineon            8001  0 
joydev                  8740  0 
arc4                    1153  2 
snd_hda_intel          22165  6 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
pcmcia                 30912  0 
snd_pcm                70918  7 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                68919  0 
i915                  288642  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 i915
iwlcore               106594  1 iwl3945
tpm_tis                 7584  0 
ppdev                   5259  0 
mac80211              205402  2 iwl3945,iwlcore
yenta_socket           20536  1 
rsrc_nonstatic         10559  1 yenta_socket
sdhci_pci               5502  0 
sdhci                  15654  1 sdhci_pci
tifm_7xx1               3690  0 
parport_pc             26250  1 
tpm                    13936  2 tpm_infineon,tpm_tis
tifm_core               6045  1 tifm_7xx1
tpm_bios                5266  1 tpm
drm                   163066  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
snd                    54244  22 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            32996  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               2864  3 iwl3945,iwlcore,sdhci
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126144  3 iwl3945,iwlcore,mac80211
intel_agp              24671  2 i915
video                  17375  1 i915
output                  1871  1 video
agpgart                31788  2 drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
ohci1394               27238  0 
hid                    67096  1 usbhid
ieee1394               81213  1 ohci1394
tg3                   109580  0 
ahci                   32392  3 
             total       used       free     shared    buffers     cached
Mem:       3347144     397032    2950112          0      59360     183292
-/+ buffers/cache:     154380    3192764
Swap:      1951736          0    1951736
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon suspend suspend:Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... none found.
success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Wed Jul  6 13:31:47 AST 2011: performing suspend
Wed Jul  6 13:31:59 AST 2011: Awake.
Wed Jul  6 13:31:59 AST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon resume suspend:Starting SmartLink Modem driver for: hw:0,6.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Wed Jul  6 13:32:00 AST 2011: Finished.
Initial commandline parameters: 
Mon Jul 11 04:18:59 AST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux workss 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
ipt_REJECT              1928  0 
ipt_LOG                 4542  0 
xt_limit                1382  0 
xt_tcpudp               2011  0 
ipt_addrtype            1599  0 
xt_state                1098  0 
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_nat                 15560  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10346  2 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
nf_conntrack_ftp        5381  1 nf_nat_ftp
nf_conntrack           60943  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1369  1 
ip_tables               9899  1 iptable_filter
ip6table_filter         1248  1 
ip6_tables             11102  1 ip6table_filter
x_tables               14175  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip_tables,ip6_tables
rfcomm                 33421  0 
sco                     7917  0 
binfmt_misc             6587  1 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  0 
l2cap                  30624  4 rfcomm,bnep
vboxnetadp              6808  0 
vboxnetflt             18753  0 
vboxdrv               230336  2 vboxnetadp,vboxnetflt
snd_hda_codec_si3054     3396  1 
snd_hda_codec_analog    58598  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
btusb                  10989  0 
joydev                  8740  0 
tpm_infineon            8001  0 
snd_hda_intel          22165  5 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 30912  0 
arc4                    1153  2 
iwl3945                68919  0 
bluetooth              49892  5 rfcomm,sco,bnep,l2cap,btusb
iwlcore               106594  1 iwl3945
i915                  288642  3 
tpm_tis                 7584  0 
snd                    54244  21 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
drm_kms_helper         29329  1 i915
tpm                    13936  2 tpm_infineon,tpm_tis
mac80211              205402  2 iwl3945,iwlcore
tifm_7xx1               3690  0 
yenta_socket           20536  1 
parport_pc             26250  1 
tpm_bios                5266  1 tpm
soundcore               6620  1 snd
drm                   163066  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
sdhci_pci               5502  0 
serio_raw               3978  0 
tifm_core               6045  1 tifm_7xx1
sdhci                  15654  1 sdhci_pci
rsrc_nonstatic         10559  1 yenta_socket
led_class               2864  3 iwl3945,iwlcore,sdhci
video                  17375  1 i915
pcmcia_core            32996  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211              126144  3 iwl3945,iwlcore,mac80211
intel_agp              24671  2 i915
output                  1871  1 video
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
agpgart                31788  2 drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
hid                    67096  1 usbhid
ohci1394               27238  0 
ieee1394               81213  1 ohci1394
tg3                   109580  0 
ahci                   32392  3 
             total       used       free     shared    buffers     cached
Mem:       3347144    1096400    2250744          0      75792     767436
-/+ buffers/cache:     253172    3093972
Swap:      1951736          0    1951736
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon suspend suspend:Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... none found.
success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Mon Jul 11 04:19:00 AST 2011: performing suspend
Mon Jul 11 04:19:10 AST 2011: Awake.
Mon Jul 11 04:19:10 AST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.100 -> dest=:1.99 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon resume suspend:Starting SmartLink Modem driver for: hw:0,6.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Mon Jul 11 04:19:11 AST 2011: Finished.
Initial commandline parameters: 
Mon Jul 11 04:40:08 AST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux workss 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
ipt_REJECT              1928  0 
ipt_LOG                 4542  0 
xt_limit                1382  0 
xt_tcpudp               2011  0 
ipt_addrtype            1599  0 
xt_state                1098  0 
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_nat                 15560  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10346  2 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
nf_conntrack_ftp        5381  1 nf_nat_ftp
nf_conntrack           60943  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1369  1 
ip_tables               9899  1 iptable_filter
ip6table_filter         1248  1 
ip6_tables             11102  1 ip6table_filter
x_tables               14175  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip_tables,ip6_tables
rfcomm                 33421  0 
sco                     7917  0 
binfmt_misc             6587  1 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  0 
l2cap                  30624  4 rfcomm,bnep
vboxnetadp              6808  0 
vboxnetflt             18753  0 
vboxdrv               230336  2 vboxnetadp,vboxnetflt
snd_hda_codec_si3054     3396  1 
snd_hda_codec_analog    58598  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
btusb                  10989  0 
joydev                  8740  0 
tpm_infineon            8001  0 
snd_hda_intel          22165  6 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  7 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 30912  0 
arc4                    1153  2 
iwl3945                68919  0 
bluetooth              49892  5 rfcomm,sco,bnep,l2cap,btusb
iwlcore               106594  1 iwl3945
i915                  288642  3 
tpm_tis                 7584  0 
snd                    54244  22 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
drm_kms_helper         29329  1 i915
tpm                    13936  2 tpm_infineon,tpm_tis
mac80211              205402  2 iwl3945,iwlcore
tifm_7xx1               3690  0 
yenta_socket           20536  1 
parport_pc             26250  1 
tpm_bios                5266  1 tpm
soundcore               6620  1 snd
drm                   163066  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
sdhci_pci               5502  0 
serio_raw               3978  0 
tifm_core               6045  1 tifm_7xx1
sdhci                  15654  1 sdhci_pci
rsrc_nonstatic         10559  1 yenta_socket
led_class               2864  3 iwl3945,iwlcore,sdhci
video                  17375  1 i915
pcmcia_core            32996  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211              126144  3 iwl3945,iwlcore,mac80211
intel_agp              24671  2 i915
output                  1871  1 video
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
agpgart                31788  2 drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
hid                    67096  1 usbhid
ohci1394               27238  0 
ieee1394               81213  1 ohci1394
tg3                   109580  0 
ahci                   32392  3 
             total       used       free     shared    buffers     cached
Mem:       3347144    1055872    2291272          0      78136     776320
-/+ buffers/cache:     201416    3145728
Swap:      1951736          0    1951736
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon hibernate hibernate:Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... none found.
success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Mon Jul 11 04:40:09 AST 2011: performing hibernate
Mon Jul 11 15:32:19 AST 2011: Awake.
Mon Jul 11 15:32:21 AST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:method return sender=:1.123 -> dest=:1.122 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon thaw hibernate:Starting SmartLink Modem driver for: hw:0,6.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Mon Jul 11 15:32:44 AST 2011: Finished.
Initial commandline parameters: 
Tue Jul 12 04:02:01 AST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux workss 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  7 
ipt_addrtype            1599  4 
xt_state                1098  7 
ip6table_filter         1248  1 
ip6_tables             11102  1 ip6table_filter
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_nat                 15560  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10346  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
nf_conntrack_ftp        5381  1 nf_nat_ftp
nf_conntrack           60943  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1369  1 
ip_tables               9899  1 iptable_filter
x_tables               14175  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
binfmt_misc             6587  1 
vboxnetadp              6808  0 
vboxnetflt             18753  0 
vboxdrv               230336  2 vboxnetadp,vboxnetflt
snd_hda_codec_si3054     3396  1 
snd_hda_codec_analog    58598  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
tpm_infineon            8001  0 
pcmcia                 30912  0 
snd_hda_intel          22165  6 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  7 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1153  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                68919  0 
iwlcore               106594  1 iwl3945
tpm_tis                 7584  0 
i915                  288642  3 
ppdev                   5259  0 
tifm_7xx1               3690  0 
mac80211              205402  2 iwl3945,iwlcore
yenta_socket           20536  1 
rsrc_nonstatic         10559  1 yenta_socket
sdhci_pci               5502  0 
tpm                    13936  2 tpm_infineon,tpm_tis
drm_kms_helper         29329  1 i915
parport_pc             26250  1 
tifm_core               6045  1 tifm_7xx1
snd                    54244  22 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  15654  1 sdhci_pci
tpm_bios                5266  1 tpm
led_class               2864  3 iwl3945,iwlcore,sdhci
pcmcia_core            32996  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126144  3 iwl3945,iwlcore,mac80211
drm                   163066  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
video                  17375  1 i915
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
output                  1871  1 video
intel_agp              24671  2 i915
agpgart                31788  2 drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
ohci1394               27238  0 
hid                    67096  1 usbhid
ieee1394               81213  1 ohci1394
tg3                   109580  0 
ahci                   32392  3 
             total       used       free     shared    buffers     cached
Mem:       3347144    1519040    1828104          0     140992     918872
-/+ buffers/cache:     459176    2887968
Swap:      1951736          0    1951736
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon suspend suspend:Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... none found.
success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Tue Jul 12 04:02:03 AST 2011: performing suspend
Tue Jul 12 04:02:16 AST 2011: Awake.
Tue Jul 12 04:02:16 AST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.89 -> dest=:1.88 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon resume suspend:Starting SmartLink Modem driver for: hw:0,6.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Tue Jul 12 04:02:17 AST 2011: Finished.
Initial commandline parameters: 
Tue Jul 12 04:02:36 AST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux workss 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  7 
ipt_addrtype            1599  4 
xt_state                1098  7 
ip6table_filter         1248  1 
ip6_tables             11102  1 ip6table_filter
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_nat                 15560  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10346  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
nf_conntrack_ftp        5381  1 nf_nat_ftp
nf_conntrack           60943  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1369  1 
ip_tables               9899  1 iptable_filter
x_tables               14175  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
binfmt_misc             6587  1 
vboxnetadp              6808  0 
vboxnetflt             18753  0 
vboxdrv               230336  2 vboxnetadp,vboxnetflt
snd_hda_codec_si3054     3396  1 
snd_hda_codec_analog    58598  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
tpm_infineon            8001  0 
pcmcia                 30912  0 
snd_hda_intel          22165  5 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1153  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                68919  0 
iwlcore               106594  1 iwl3945
tpm_tis                 7584  0 
i915                  288642  3 
ppdev                   5259  0 
tifm_7xx1               3690  0 
mac80211              205402  2 iwl3945,iwlcore
yenta_socket           20536  1 
rsrc_nonstatic         10559  1 yenta_socket
sdhci_pci               5502  0 
tpm                    13936  2 tpm_infineon,tpm_tis
drm_kms_helper         29329  1 i915
parport_pc             26250  1 
tifm_core               6045  1 tifm_7xx1
snd                    54244  21 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  15654  1 sdhci_pci
tpm_bios                5266  1 tpm
led_class               2864  3 iwl3945,iwlcore,sdhci
pcmcia_core            32996  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126144  3 iwl3945,iwlcore,mac80211
drm                   163066  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
video                  17375  1 i915
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
output                  1871  1 video
intel_agp              24671  2 i915
agpgart                31788  2 drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
ohci1394               27238  0 
hid                    67096  1 usbhid
ieee1394               81213  1 ohci1394
tg3                   109580  0 
ahci                   32392  3 
             total       used       free     shared    buffers     cached
Mem:       3347144    1525396    1821748          0     141120     926708
-/+ buffers/cache:     457568    2889576
Swap:      1951736          0    1951736
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon suspend suspend:Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... none found.
success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Tue Jul 12 04:02:38 AST 2011: performing suspend
Tue Jul 12 04:02:46 AST 2011: Awake.
Tue Jul 12 04:02:46 AST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.89 -> dest=:1.108 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon resume suspend:Starting SmartLink Modem driver for: hw:0,6.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Tue Jul 12 04:02:47 AST 2011: Finished.
Initial commandline parameters: 
Tue Jul 12 04:03:16 AST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux workss 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  7 
ipt_addrtype            1599  4 
xt_state                1098  7 
ip6table_filter         1248  1 
ip6_tables             11102  1 ip6table_filter
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_nat                 15560  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10346  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
nf_conntrack_ftp        5381  1 nf_nat_ftp
nf_conntrack           60943  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1369  1 
ip_tables               9899  1 iptable_filter
x_tables               14175  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
binfmt_misc             6587  1 
vboxnetadp              6808  0 
vboxnetflt             18753  0 
vboxdrv               230336  2 vboxnetadp,vboxnetflt
snd_hda_codec_si3054     3396  1 
snd_hda_codec_analog    58598  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
tpm_infineon            8001  0 
pcmcia                 30912  0 
snd_hda_intel          22165  5 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1153  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                68919  0 
iwlcore               106594  1 iwl3945
tpm_tis                 7584  0 
i915                  288642  3 
ppdev                   5259  0 
tifm_7xx1               3690  0 
mac80211              205402  2 iwl3945,iwlcore
yenta_socket           20536  1 
rsrc_nonstatic         10559  1 yenta_socket
sdhci_pci               5502  0 
tpm                    13936  2 tpm_infineon,tpm_tis
drm_kms_helper         29329  1 i915
parport_pc             26250  1 
tifm_core               6045  1 tifm_7xx1
snd                    54244  21 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  15654  1 sdhci_pci
tpm_bios                5266  1 tpm
led_class               2864  3 iwl3945,iwlcore,sdhci
pcmcia_core            32996  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126144  3 iwl3945,iwlcore,mac80211
drm                   163066  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
video                  17375  1 i915
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
output                  1871  1 video
intel_agp              24671  2 i915
agpgart                31788  2 drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36206  0 
ohci1394               27238  0 
hid                    67096  1 usbhid
ieee1394               81213  1 ohci1394
tg3                   109580  0 
ahci                   32392  3 
             total       used       free     shared    buffers     cached
Mem:       3347144    1524144    1823000          0     141212     925736
-/+ buffers/cache:     457196    2889948
Swap:      1951736          0    1951736
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon suspend suspend:Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... none found.
success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Tue Jul 12 04:03:17 AST 2011: performing suspend
Tue Jul 12 04:03:26 AST 2011: Awake.
Tue Jul 12 04:03:26 AST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.89 -> dest=:1.125 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/15sl-modem-daemon resume suspend:Starting SmartLink Modem driver for: hw:0,6.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Tue Jul 12 04:03:27 AST 2011: Finished.

---

### Post by matt_symes on 2011-07-14
Hi

There is nothing in your pm-suspend.log to indicate a problem. I would like to check your settings.

Open a terminal and copy and paste

```
gconftool-2 -R /apps/gnome-power-manager/buttons
```Post the results back here. 

Kind regards

---

### Post by linux83 on 2011-07-14
hello freind:

med@workss:~$ gconftool-2 -R /apps/gnome-power-manager/buttons
 lid_battery = blank
 hibernate = hibernate
 suspend = suspend
 lid_ac = blank
 power = interactive


thanks alot.

---

### Post by matt_symes on 2011-07-14
Hi

> med@workss:~$ gconftool-2 -R /apps/gnome-power-manager/buttons
 lid_battery = blank
 hibernate = hibernate
 suspend = suspend
 lid_ac = blank
 power = interactiveWhen you close the lid of your laptop, it is configured to blank the screen only, both when the power adapter is connected and also when it is running on battery.

Do you want it to suspend properly and turn off the monitor as well when you suspend ?

If so then type these commands at the terminal.
```

gconftool-2 -s -t string /apps/gnome-power-manager/buttons/lid_ac suspend
gconftool-2 -s -t string /apps/gnome-power-manager/buttons/lid_battery suspend
```These two commands will suspend the machine when the lid is closed when running on both battery power and ac power. They will also turn off the monitor.

You can change the word suspend to hibernate for either or both command if you want to. As you can see the original setting is blank

Either that or use the power management GUI.

Hopefully that should fix it.

Kind regards

---

### Post by linux83 on 2011-07-15
thanks for reply, i don't need blank screen or suspend, i need only to power off the screen when i close the lid.

---

### Post by matt_symes on 2011-07-16
Hi

> **linux83 said:**
> thanks for reply, i don't need blank screen or suspend, i need only to power off the screen when i close the lid.

Right. I think i am with you. You want to turn the monitor off when you close the lid and not suspend or blank the screen. 

This is non standard behaviour but i am pretty sure it's possible. I have not tried it myself though. You will need to do some research.

Have a look at the files.

```
/etc/acpi/events/lidbtn
```and 

```
/etc/acpi/lid.sh
```Also take a look at 

```
man acpid
man upower
man gnome-power-manager
```Hopefully these pointers will give you a place to start your research. It may just be a case of editing /etc/acpi/lid.sh to call xset.

Make a backup of any system files you change before you edit them.

Kind regards

---

