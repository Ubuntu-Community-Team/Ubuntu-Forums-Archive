---
title: "suspend stopped working after kernel update (12.10)"
date: 2013-01-20
forum: Hardware
---

### Post by aa-hcl on 2013-01-20
I have just updated the kernel to 

aa@aa-E6530:~$ uname -a
Linux aa-E6530 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


and my suspend stopped working.

The last part of the file /var/log/pm-suspend.log is:

```
Sat Jan 19 23:58:25 GMT 2013: performing suspend
Sat Jan 19 23:58:34 GMT 2013: Awake.
Sat Jan 19 23:58:34 GMT 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
mem_write: address 0x7ffff3437748 out of range!
halt_sys: file, line -754538752
Segmentation fault (core dumped)
mem_write: address 0x7fff5d76d238 out of range!
halt_sys: file, line 36038400
Segmentation fault (core dumped)
Initial commandline parameters: 
Sun Jan 20 01:49:34 GMT 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:

/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux aa-E6530 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12623  1 
vboxpci                23195  0 
vboxnetadp             25671  0 
vboxnetflt             23480  0 
vboxdrv               320372  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 46620  12 
bnep                   18141  2 
joydev                 17458  0 
snd_hda_codec_hdmi     32049  4 
snd_hda_codec_idt      70210  1 
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
coretemp               13401  0 
arc4                   12530  2 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlwifi               386874  0 
snd_seq_midi           13325  0 
kvm_intel             132760  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
btusb                  22475  0 
lp                     17760  0 
dell_wmi               12682  0 
ppdev                  17074  0 
kvm                   414071  1 kvm_intel
snd_timer              29426  2 snd_pcm,snd_seq
mac80211              539958  1 iwlwifi
parport_pc             32689  0 
parport                46346  3 lp,ppdev,parport_pc
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78921  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15048  1 snd
psmouse                90217  0 
cfg80211              206797  2 iwlwifi,mac80211
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
bluetooth             209249  22 rfcomm,bnep,btusb
sparse_keymap          13891  1 dell_wmi
mac_hid                13206  0 
wmi                    19071  1 dell_wmi
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
video                  19336  0 
lpc_ich                17062  0 
dell_laptop            17370  0 
serio_raw              13216  0 
aes_x86_64             17256  1 aesni_intel
mei                    40691  0 
dcdbas                 14439  1 dell_laptop
microcode              22804  0 
e1000e                199273  0 
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       8118660     968644    7150016          0      92012     328812
-/+ buffers/cache:     547820    7570840
Swap:     15624188          0   15624188

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
No quirk database entry for this system, using default.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Jan 20 01:49:36 GMT 2013: performing suspend
Initial commandline parameters: 
Sun Jan 20 10:34:49 GMT 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:

/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux aa-E6530 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12623  1 
vboxpci                23195  0 
vboxnetadp             25671  0 
vboxnetflt             23480  0 
vboxdrv               320372  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18141  2 
rfcomm                 46620  12 
joydev                 17458  0 
snd_hda_codec_hdmi     32049  4 
snd_hda_codec_idt      70210  1 
arc4                   12530  2 
iwlwifi               386874  0 
snd_hda_intel          33492  7 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
coretemp               13401  0 
btusb                  22475  0 
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              539958  1 iwlwifi
kvm_intel             132760  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
kvm                   414071  1 kvm_intel
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                90217  0 
snd                    78921  23 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              206797  2 iwlwifi,mac80211
bluetooth             209249  22 bnep,rfcomm,btusb
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
video                  19336  0 
lp                     17760  0 
mei                    40691  0 
lpc_ich                17062  0 
ghash_clmulni_intel    13221  0 
ppdev                  17074  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
serio_raw              13216  0 
aes_x86_64             17256  1 aesni_intel
mac_hid                13206  0 
wmi                    19071  1 dell_wmi
dell_laptop            17370  0 
parport_pc             32689  0 
parport                46346  3 lp,ppdev,parport_pc
dcdbas                 14439  1 dell_laptop
microcode              22804  0 
e1000e                199273  0 
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       8118660     984488    7134172          0      84432     334568
-/+ buffers/cache:     565488    7553172
Swap:     15624188          0   15624188

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
'SUSPEND' command timed out.

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
No quirk database entry for this system, using default.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Jan 20 10:35:02 GMT 2013: performing suspend
Sun Jan 20 10:35:10 GMT 2013: Awake.
Sun Jan 20 10:35:10 GMT 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
mem_write: address 0x7fff370a8c58 out of range!
halt_sys: file, line -1855637760
Segmentation fault (core dumped)
mem_write: address 0x7fffeb294158 out of range!
halt_sys: file, line 1028552448
Segmentation fault (core dumped)
aa@aa-E6530:~$ 
```


How can I fix it? It was previously working fine with previous version of the kernel.

Many thanks!

---

### Post by Toz on 2013-01-23
Probably best to boot and run the previous kernel and open a bug report for this kernel over at [https://bugs.launchpad.net/](https://bugs.launchpad.net/). You can create a bug report by running:
```
apport-bug linux
```
...from a terminal prompt.

Also moving this thread to the Hardware forum.

---

### Post by aa-hcl on 2013-01-30
Hi,

I finally resolved the problem.

It was the nvidia driver that stopped working and therefore was preventing the system from proper wake-up and apparently causing the 99video module to crash.

I found it because I noticed that the nvidia driver was no longer loaded at start-up (its logo was not briefly displayed!).

Solution: removed the nvidia driver completely and then re-installed it.

The suspend is now working!

So, it is not a bug in the kernel, it was nvidia driver not loaded properly for whatever reason, which might be totaly unrelated to the new kernel upgrade.

Many thanks!

---

### Post by Toz on 2013-01-30
Thanks for posting back the resolution. If you don't mind, can you mark this thread Solved (from the Thread Tools link above) so that others can benefit from your finding. Thanks.

---

