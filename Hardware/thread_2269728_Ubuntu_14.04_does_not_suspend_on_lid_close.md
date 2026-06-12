---
title: "Ubuntu 14.04 does not suspend on lid close"
date: 2015-03-17
forum: Hardware
---

### Post by geppetto on 2015-03-17
This started about one week ago. The suspend function is configured properly (system settings, power etc.), and works properly when using the "suspend" item in the gear menu. Using Windows the suspend works properly, so it should not be a hardware problem. The only clue I have, is that while the lid is closed, the syslog collects a series of lines like the following:

```
Mar 17 21:38:43 lapLenovo kernel: [ 2390.543638] atkbd serio0: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
Mar 17 21:38:43 lapLenovo kernel: [ 2390.543646] atkbd serio0: Use 'setkeycodes e071 <keycode>' to make it known.
```

My computer is a Lenovo B590, and I have upgraded the OS today (Ubuntu 14.04).

Thank you...

---

### Post by weatherman2 on 2015-03-17
What are the end contents (may be a huge file, so look at only the most recent events at the end) of the file /var/log/pm-suspend.log ?

---

### Post by geppetto on 2015-03-17
Thanks weatherman2
> **weatherman2 said:**
> What are the end contents (may be a huge file, so look at only the most recent events at the end) of the file /var/log/pm-suspend.log ?

Here it is:
```
Mon Mar 16 23:37:02 CET 2015: performing suspend
Tue Mar 17 09:18:27 CET 2015: Awake.
Tue Mar 17 09:18:27 CET 2015: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254
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

Tue Mar 17 09:18:27 CET 2015: Finished.
```

If I close, stay, and reopen, nothing is recorded. And in fact, the last record if 12 hours ago.

---

### Post by geppetto on 2015-03-17
Ah, this is the trace of the suspend before the above trace

```

Mon Mar 16 21:49:20 CET 2015: Finished.
Initial commandline parameters: 
Mon Mar 16 23:37:01 CET 2015: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux lapLenovo 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rndis_wlan             50281  0 
cdc_acm                28803  0 
rndis_host             14503  1 rndis_wlan
cdc_ether              14351  1 rndis_host
cdc_phonet             13369  0 
phonet                 30439  1 cdc_phonet
twofish_generic        16635  0 
twofish_avx_x86_64     46421  0 
ablk_helper            13597  1 twofish_avx_x86_64
twofish_x86_64_3way    27146  1 twofish_avx_x86_64
xts                    12914  1 twofish_x86_64_3way
lrw                    13286  2 twofish_avx_x86_64,twofish_x86_64_3way
gf128mul               14951  2 lrw,xts
glue_helper            13990  2 twofish_avx_x86_64,twofish_x86_64_3way
twofish_x86_64         12907  2 twofish_avx_x86_64,twofish_x86_64_3way
twofish_common         21113  4 twofish_generic,twofish_avx_x86_64,twofish_x86_64_3way,twofish_x86_64
michael_mic            12612  0 
arc4                   12608  0 
qmi_wwan               21699  0 
option                 46743  0 
cdc_wdm                19053  1 qmi_wwan
usb_wwan               20429  1 option
usbnet                 43913  4 rndis_host,rndis_wlan,qmi_wwan,cdc_ether
usbserial              45014  2 option,usb_wwan
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  1 
vboxdrv               339502  8 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 69160  4 
bnep                   19624  2 
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
lib80211_crypt_tkip    17619  0 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  2 wl,rndis_wlan
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
btusb                  32412  0 
bluetooth             391136  11 bnep,btusb,rfcomm
keucr                  72238  0 
thinkpad_acpi          81013  1 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
dm_multipath           22873  0 
scsi_dh                14882  1 dm_multipath
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143148  0 
kvm                   451729  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
cryptd                 20359  2 ghash_clmulni_intel,ablk_helper
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_hda_intel          56451  3 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
joydev                 17381  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
serio_raw              13462  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  2 snd_pcm,snd_seq
mei_me                 18627  0 
mei                    82276  1 mei_me
lpc_ich                21080  0 
shpchp                 37032  0 
snd                    69322  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
i915                  783961  4 
soundcore              12680  1 snd
drm_kms_helper         55071  1 i915
video                  19476  1 i915
wmi                    19177  0 
drm                   303102  5 i915,drm_kms_helper
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
parport_pc             32701  0 
ppdev                  17671  0 
dm_crypt               23177  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
usb_storage            62209  0 
psmouse               106714  0 
ahci                   25819  4 
r8169                  67581  0 
libahci                32716  1 ahci
mii                    13934  2 r8169,usbnet
             total       used       free     shared    buffers     cached
Mem:       8011076    7873068     138008     332284      95636    3397660
-/+ buffers/cache:    4379772    3631304
Swap:     29296636        256   29296380
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
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.

Mon Mar 16 23:37:02 CET 2015: performing suspend
Tue Mar 17 09:18:27 CET 2015: Awake.
```

---

