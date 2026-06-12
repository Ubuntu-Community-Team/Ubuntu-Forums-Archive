---
title: "Can resume form manual suspend but not from timeout suspend"
date: 2014-12-12
forum: Hardware
---

### Post by neil.the.blue on 2014-12-12
I have a strange resume from suspend issue. 

I have ubuntu 14.10 (3.16.0-28-generic) on a desktop. If I use the suspend button on my keyboard, the system goes into suspend and will resume normally. However if I enter suspend from the system menu or allow suspend from timeout, resume from suspend fails and I have to power cycle the system to reboot.

This has been a problem from about the past 5 kernel updates, but before upgrading to 14.10 I was able to use an older kernel image.

Please can anyone make a suggestion. If I can find out what command is run in response to the keyboard 'sleep' button it may be a start, but I am surprised it behaves differently to the menu or timeout. I have not had any problem with suspend on this machine for the past 4 years.

Thanks for reading
Neil

---

### Post by weatherman2 on 2014-12-12
What's the output of the file /var/log/pm-suspend.log ?

This could be a huge file with entries for each suspend/resume, so maybe trim all but the end of the file.  If you can try to look at the dates/times in the file and point out one set of lines that correspond to a successful suspend/resume (via keyboard)  and one that correspond to a failed suspend/resume, that might help.

---

### Post by neil.the.blue on 2014-12-12
Thanks for the response weatherman2.

Here are the last two suspend entries. The first one was successful, the second one seemed to hand during suspend and didn't recover.

> Initial commandline parameters: 
Sat Dec 13 01:16:50 GMT 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux hex 3.16.0-28-generic #37-Ubuntu SMP Mon Dec 8 17:15:28 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23256  0 
vboxnetadp             25670  0 
vboxnetflt             27605  0 
vboxdrv               418013  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 69509  8 
bnep                   19543  2 
nfsd                  283335  2 
auth_rpcgss            59115  1 nfsd
nfs_acl                12837  1 nfsd
nfs                   245527  0 
binfmt_misc            17468  1 
lockd                  93740  2 nfs,nfsd
sunrpc                294292  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                63723  1 nfs
btusb                  32448  0 
bluetooth             446190  22 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
kvm_amd                60329  0 
snd_hda_codec_via      31956  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_via
radeon               1416486  4 
kvm                   459835  1 kvm_amd
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_hda_codec_hdmi     47547  1 
snd_hda_intel          30379  7 
snd_hda_controller     35152  1 snd_hda_intel
snd_hda_codec         139675  5 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
serio_raw              13434  0 
snd_pcm               104102  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
edac_core              56549  0 
edac_mce_amd           22578  0 
k10temp                13144  0 
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
sp5100_tco             13999  0 
snd_timer              29513  2 snd_pcm,snd_seq
i2c_piix4              22159  0 
ppdev                  17671  0 
snd                    87611  24 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ttm                    89406  1 radeon
parport_pc             32741  1 
drm_kms_helper         61627  1 radeon
soundcore              15052  2 snd,snd_hda_codec
drm                   310919  7 ttm,drm_kms_helper,radeon
asus_atk0110           18659  0 
i2c_algo_bit           13406  1 radeon
shpchp                 37040  0 
mac_hid                13227  0 
wmi                    19193  0 
hwmon_vid              12783  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12559  0 
usbhid                 52574  0 
hid                   110426  2 hid_generic,usbhid
uas                    23215  0 
usb_storage            66398  1 uas
pata_acpi              13053  0 
psmouse               106548  0 
ahci                   34062  2 
r8169                  71471  0 
pata_atiixp            13279  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:      16174580    3565520   12609060      72740     104112     896300
-/+ buffers/cache:    2565108   13609472
Swap:            0          0          0
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Sat Dec 13 01:16:50 GMT 2014: performing suspend
Sat Dec 13 01:17:04 GMT 2014: Awake.
Sat Dec 13 01:17:04 GMT 2014: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


Sat Dec 13 01:17:05 GMT 2014: Finished.
Initial commandline parameters: 
Sat Dec 13 01:18:32 GMT 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux hex 3.16.0-28-generic #37-Ubuntu SMP Mon Dec 8 17:15:28 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23256  0 
vboxnetadp             25670  0 
vboxnetflt             27605  0 
vboxdrv               418013  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 69509  8 
bnep                   19543  2 
nfsd                  283335  2 
auth_rpcgss            59115  1 nfsd
nfs_acl                12837  1 nfsd
nfs                   245527  0 
binfmt_misc            17468  1 
lockd                  93740  2 nfs,nfsd
sunrpc                294292  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
fscache                63723  1 nfs
btusb                  32448  0 
bluetooth             446190  22 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
kvm_amd                60329  0 
snd_hda_codec_via      31956  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_via
radeon               1416486  4 
kvm                   459835  1 kvm_amd
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_hda_codec_hdmi     47547  1 
snd_hda_intel          30379  7 
snd_hda_controller     35152  1 snd_hda_intel
snd_hda_codec         139675  5 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
serio_raw              13434  0 
snd_pcm               104102  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
edac_core              56549  0 
edac_mce_amd           22578  0 
k10temp                13144  0 
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
sp5100_tco             13999  0 
snd_timer              29513  2 snd_pcm,snd_seq
i2c_piix4              22159  0 
ppdev                  17671  0 
snd                    87611  24 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ttm                    89406  1 radeon
parport_pc             32741  1 
drm_kms_helper         61627  1 radeon
soundcore              15052  2 snd,snd_hda_codec
drm                   310919  7 ttm,drm_kms_helper,radeon
asus_atk0110           18659  0 
i2c_algo_bit           13406  1 radeon
shpchp                 37040  0 
mac_hid                13227  0 
wmi                    19193  0 
hwmon_vid              12783  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12559  0 
usbhid                 52574  0 
hid                   110426  2 hid_generic,usbhid
uas                    23215  0 
usb_storage            66398  1 uas
pata_acpi              13053  0 
psmouse               106548  0 
ahci                   34062  2 
r8169                  71471  0 
pata_atiixp            13279  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
             total       used       free     shared    buffers     cached
Mem:      16174580    3562528   12612052      72788     104212     896480
-/+ buffers/cache:    2561836   13612744
Swap:            0          0          0
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Sat Dec 13 01:18:32 GMT 2014: performing suspend


---

### Post by neil.the.blue on 2014-12-13
I have now found that suspend/resume seems to work fine with kernel 3.13.0-36-generic.

---

