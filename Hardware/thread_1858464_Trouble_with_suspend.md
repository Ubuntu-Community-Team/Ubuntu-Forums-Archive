---
title: "Trouble with suspend?"
date: 2011-10-12
forum: Hardware
---

### Post by mma8x on 2011-10-12
I've had this desktop for about 2 years, and have been able to suspend to ram without issue.  About a month ago, it stopped waking up, requiring a hard reset.  Going through my logs, it doesn't appear that I messed with any software/updates when it started malfunctioning.  I've tried unplugging all usb accessories, re-formatting hard drive/fresh install of natty, unplugging HD and attempting to suspend from a USB install, messing with BIOS settings/resetting BIOS, etc.  It's driving me crazy.  Can't figure out where to start troubleshooting; everything on the web deals with laptops or is way out of date.  It appears from my pm-suspend log that it isn't even trying to wake up, or isn't getting a wake signal.  It hibernates fine.  I've attached a log showing both a suspend and hibernate cycle.  Prior to this issue, my suspend log showed a wake cycle similar to the one here with hibernate.  I'm wondering if this could be a hardware issue?

```
Initial commandline parameters: 
Wed Oct 12 08:17:02 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux abatzis 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  0 
arc4                   12529  2 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
ath9k_htc              61400  0 
mac80211              294370  1 ath9k_htc
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_common           13851  1 ath9k_htc
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ath9k_hw              323077  2 ath9k_htc,ath9k_common
ath                    23773  2 ath9k_htc,ath9k_hw
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  3 ath9k_htc,mac80211,ath
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 37297  0 
edac_core              53845  0 
sp5100_tco             13744  0 
i2c_piix4              13303  0 
edac_mce_amd           23464  0 
k10temp                13119  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
radeon                982197  2 
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
usb_storage            53538  0 
uas                    17996  0 
drm                   227495  4 radeon,ttm,drm_kms_helper
ahci                   25951  2 
libahci                26642  1 ahci
i2c_algo_bit           13400  1 radeon
atl1e                  37715  0 
pata_atiixp            13165  0 
             total       used       free     shared    buffers     cached
Mem:       3799160    1323352    2475808          0      83760     481200
-/+ buffers/cache:     758392    3040768
Swap:      3930108          0    3930108

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:

/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Wed Oct 12 08:17:03 EDT 2011: performing suspend
Initial commandline parameters: 
Wed Oct 12 10:35:00 EDT 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux abatzis 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  0 
arc4                   12529  2 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k_htc              61400  0 
mac80211              294370  1 ath9k_htc
ath9k_common           13851  1 ath9k_htc
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
ath9k_hw              323077  2 ath9k_htc,ath9k_common
ath                    23773  2 ath9k_htc,ath9k_hw
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178528  3 ath9k_htc,mac80211,ath
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53845  0 
sp5100_tco             13744  0 
k10temp                13119  0 
edac_mce_amd           23464  0 
shpchp                 37297  0 
i2c_piix4              13303  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
radeon                982197  2 
ttm                    76664  1 radeon
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  2 
drm_kms_helper         42136  1 radeon
drm                   227495  4 radeon,ttm,drm_kms_helper
atl1e                  37715  0 
i2c_algo_bit           13400  1 radeon
libahci                26642  1 ahci
pata_atiixp            13165  0 
             total       used       free     shared    buffers     cached
Mem:       3799160    1633572    2165588          0      66108     605260
-/+ buffers/cache:     962204    2836956
Swap:      3930108          0    3930108

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Wed Oct 12 10:35:02 EDT 2011: performing hibernate
Wed Oct 12 10:36:13 EDT 2011: Awake.
Wed Oct 12 10:36:13 EDT 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:
method return sender=:1.67 -> dest=:1.66 reply_serial=2

/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= off

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= off

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.3 -> dest=:1.69 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Wed Oct 12 10:36:16 EDT 2011: Finished.
```

---

