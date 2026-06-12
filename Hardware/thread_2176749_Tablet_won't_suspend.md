---
title: "Tablet won't suspend"
date: 2013-09-25
forum: Hardware
---

### Post by roli100 on 2013-09-25
I have just installed Xubuntu 13.04 on my tablet - Fujitsu Stylistic Q550 and I am having problems with suspend. It has an Intel Atom with the dreaded GMA600 graphics card (which is probably the cause of all this). So if I click suspend the screen goes blank (but doesn't turn off) and the tablet doesn't go to sleep. It won't wake up either. I've also had it just display a bunch of colored lines and freeze on that. I've tried using the "sudo pm-suspend --quirk-vbemode-restore" and  "sudo pm-suspend -quirk-vbemode-restore" which apparently help with GMA500. With the first one the screen flashes (I think it tries to go to sleep but wakes up) and the screen gets garbled (it stretches over the actual borders). With the second command I get the same flash when it tries to sleep but doesn't mess up the screen. But I can't get the thing to sleep. Any ideas on what I should do?

---

### Post by Toz on 2013-09-25
Out of curiosity, what does /var/log/pm-suspend.log say? 

Also:
```
cat /var/log/syslog | grep PM:
```

---

### Post by roli100 on 2013-09-25
The first one doesn't indicate any problems - just success. 
A small cut-out:
```
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux roli-tablet 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:54:42 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  16 
bnep                   17669  2 
ext2                   63166  1 
coretemp               13131  0 
joydev                 17097  0 
arc4                   12543  2 
rt2800usb              22366  0 
rt2x00usb              19979  1 rt2800usb
rt2800lib              60947  1 rt2800usb
rt2x00lib              48522  3 rt2x00usb,rt2800lib,rt2800usb
qmi_wwan               12910  0 
snd_hda_codec_realtek    63791  1 
cdc_wdm                17663  1 qmi_wwan
mac80211              526519  3 rt2x00lib,rt2x00usb,rt2800lib
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
tpm_infineon           17194  0 
usbnet                 26567  1 qmi_wwan
btusb                  17986  0 
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
cfg80211              436177  2 mac80211,rt2x00lib
fujitsu_tablet         12922  0 
qcserial               12602  0 
microcode              18286  0 
snd_hda_intel          38307  3 
bluetooth             202109  22 bnep,btusb,rfcomm
crc_ccitt              12627  1 rt2800lib
usb_wwan               14830  1 qcserial
snd_hda_codec         117617  2 snd_hda_codec_realtek,snd_hda_intel
hid_ntrig              18494  0 
videodev               95806  2 uvcvideo,videobuf2_core
tpm_tis                18203  0 
psmouse                81065  0 
serio_raw              13031  0 
mac_hid                13037  0 
usbserial              27423  2 qcserial,usb_wwan
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
fujitsu_laptop         18467  0 
gma500_gfx            167832  2 
video                  18894  1 gma500_gfx
drm_kms_helper         47545  1 gma500_gfx
snd                    56485  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_intel_mid          13111  0 
intel_mid_dma          17713  0 
drm                   228489  3 drm_kms_helper,gma500_gfx
soundcore              12600  1 snd
i2c_designware_pci     12872  1 
i2c_designware_core    14030  1 i2c_designware_pci
i2c_algo_bit           13197  1 gma500_gfx
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_apple              13045  0 
usbhid                 41805  1 hid_ntrig
hid                    82666  3 usbhid,hid_apple,hid_ntrig
sdhci_pci              18158  0 
ahci                   25507  2 
libahci                26108  1 ahci
sdhci                  31824  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       2042620     449788    1592832          0      29296     241736
-/+ buffers/cache:     178756    1863864
Swap:      2076668          0    2076668

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
Selected interface 'wlan0'
OK

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
Using quirks passed as parameters.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
&#269;et sep 26 03:18:43 CEST 2013: performing suspend
&#269;et sep 26 03:18:44 CEST 2013: Awake.
&#269;et sep 26 03:18:44 CEST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Selected interface 'wlan0'
OK

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
&#269;et sep 26 03:18:46 CEST 2013: Finished.

```

The other one is more interesting though:
```
Sep 26 02:50:00 roli-tablet kernel: [ 1157.656511] PM: Syncing filesystems ... done.
Sep 26 02:50:00 roli-tablet kernel: [ 1157.866419] PM: Device 0000:09:14.0 failed to suspend async: error -5
Sep 26 02:50:00 roli-tablet kernel: [ 1157.880350] PM: Some devices failed to suspend
Sep 26 02:50:00 roli-tablet kernel: [ 1158.737698] PM: resume of devices complete after 857.332 msecs
Sep 26 02:51:09 roli-tablet kernel: [ 1226.608779] PM: Syncing filesystems ... done.
Sep 26 02:51:09 roli-tablet kernel: [ 1226.818809] PM: Device 0000:09:14.0 failed to suspend async: error -5
Sep 26 02:51:09 roli-tablet kernel: [ 1226.832329] PM: Some devices failed to suspend
Sep 26 02:51:09 roli-tablet kernel: [ 1227.734004] PM: resume of devices complete after 901.659 msecs
Sep 26 02:53:09 roli-tablet kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Sep 26 02:53:09 roli-tablet kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Sep 26 02:53:09 roli-tablet kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 26 02:53:09 roli-tablet kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 26 02:53:09 roli-tablet kernel: [    0.108512] PM: Registering ACPI NVS region [mem 0x7f44f000-0x7f59efff] (1376256 bytes)
Sep 26 03:03:53 roli-tablet kernel: [  652.146500] PM: Syncing filesystems ... done.
Sep 26 03:03:53 roli-tablet kernel: [  652.342716] PM: Device 0000:09:14.0 failed to suspend async: error -5
Sep 26 03:03:53 roli-tablet kernel: [  652.356342] PM: Some devices failed to suspend
Sep 26 03:03:53 roli-tablet kernel: [  653.231910] PM: resume of devices complete after 875.551 msecs
Sep 26 03:18:44 roli-tablet kernel: [ 1543.820986] PM: Syncing filesystems ... done.
Sep 26 03:18:44 roli-tablet kernel: [ 1544.026700] PM: Device 0000:09:14.0 failed to suspend async: error -5
Sep 26 03:18:44 roli-tablet kernel: [ 1544.026745] PM: Device 0000:08:13.0 failed to suspend async: error -5
Sep 26 03:18:44 roli-tablet kernel: [ 1544.040334] PM: Some devices failed to suspend
Sep 26 03:18:44 roli-tablet kernel: [ 1544.920084] PM: resume of devices complete after 879.729 msecs

```

---

### Post by roli100 on 2013-09-25
Oh and according to the lspci those devices in question are:
```
08:13.0 Communication controller: Intel Corporation Moorestown I2C 1 (rev 01)
09:14.0 Communication controller: Intel Corporation Moorestown I2C 2 (rev 01)
```

---

### Post by Toz on 2013-09-25
> **roli100 said:**
> Oh and according to the lspci those devices in question are:
```
08:13.0 Communication controller: Intel Corporation Moorestown I2C 1 (rev 01)
09:14.0 Communication controller: Intel Corporation Moorestown I2C 2 (rev 01)
```
Which kernel modules are they using? Try using lscpi with -k parameter:
```
lspci -k | grep -A3 "08:13.0"
lspci -k | grep -A3 "09:14.0"
```

---

### Post by roli100 on 2013-09-26
```
roli@roli-tablet:~$ lspci -k | grep -A3 "08:13.0"
08:13.0 Communication controller: Intel Corporation Moorestown I2C 1 (rev 01)
	Subsystem: Fujitsu Limited. Device 166c
	Kernel driver in use: i2c-designware-pci
09:14.0 Communication controller: Intel Corporation Moorestown I2C 2 (rev 01)
roli@roli-tablet:~$ lspci -k | grep -A3 "09:14.0"
09:14.0 Communication controller: Intel Corporation Moorestown I2C 2 (rev 01)
	Subsystem: Fujitsu Limited. Device 166d
	Kernel driver in use: i2c-designware-pci
0b:15.0 Audio device: Intel Corporation Moorestown Audio Ctrl
```

I'm guessing one of those things is a fingerprint reader and the other a smart-card reader. But that is just a guess because those things are a bit more exotic.

---

### Post by Toz on 2013-09-26
Can you try manually unloading that module:
```
sudo modprobe -r i2c-designware-pci
```
...then suspending:
```
sudo pm-suspend
```
...to see if suspending works without the module running? If so, we can automate its unloading and reloading.

Note: to reload the module without rebooting:
```
sudo modprobe i2c-designware-pci
```

---

### Post by roli100 on 2013-09-26
I can't unload it. 
```
FATAL: Module i2c_designware_pci is in use.
```

---

### Post by Toz on 2013-09-26
> **roli100 said:**
> I can't unload it. 
```
FATAL: Module i2c_designware_pci is in use.
```

Try removing both that module and the one that is using it:
```
sudo modprobe -r i2c_designware_core i2c_designware_pci
```

---

### Post by roli100 on 2013-09-26
Still the same problem. Although now with i2c_designware_core.
```
FATAL: Module i2c_designware_core is in use.
```

---

### Post by Toz on 2013-09-26
Can you post back:
```
lsmod
```

---

### Post by roli100 on 2013-09-26
Here it is.

```
Module                  Size  Used by
coretemp               13131  0 
joydev                 17097  0 
arc4                   12543  2 
uvcvideo               71279  0 
snd_hda_codec_realtek    63791  1 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_hda_intel          38307  1 
snd_hda_codec         117617  2 snd_hda_codec_realtek,snd_hda_intel
rt2800usb              22366  0 
snd_hwdep              13272  1 snd_hda_codec
rt2x00usb              19979  1 rt2800usb
rt2800lib              60947  1 rt2800usb
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
rt2x00lib              48522  3 rt2x00usb,rt2800lib,rt2800usb
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              526519  3 rt2x00lib,rt2x00usb,rt2800lib
qmi_wwan               12910  0 
videobuf2_core         39161  1 uvcvideo
snd_rawmidi            25114  1 snd_seq_midi
cdc_wdm                17663  1 qmi_wwan
videodev               95806  2 uvcvideo,videobuf2_core
microcode              18286  0 
usbnet                 26567  1 qmi_wwan
cfg80211              436177  2 mac80211,rt2x00lib
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
qcserial               12602  0 
crc_ccitt              12627  1 rt2800lib
psmouse                81065  0 
rfcomm                 37420  12 
bnep                   17669  2 
btusb                  17986  0 
serio_raw              13031  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
hid_ntrig              18494  0 
bluetooth             202109  22 bnep,btusb,rfcomm
usb_wwan               14830  1 qcserial
usbserial              27423  2 qcserial,usb_wwan
snd                    56485  11 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
tpm_infineon           17194  0 
intel_mid_dma          17713  0 
fujitsu_tablet         12922  0 
tpm_tis                18203  0 
mac_hid                13037  0 
ext2                   63166  1 
fujitsu_laptop         18467  0 
gma500_gfx            167832  2 
i2c_intel_mid          13111  0 
video                  18894  1 gma500_gfx
drm_kms_helper         47545  1 gma500_gfx
i2c_designware_pci     12872  1 
drm                   228489  3 drm_kms_helper,gma500_gfx
i2c_designware_core    14030  1 i2c_designware_pci
i2c_algo_bit           13197  1 gma500_gfx
lp                     13299  0 
parport                40753  1 lp
usbhid                 41805  1 hid_ntrig
hid                    82666  2 usbhid,hid_ntrig
sdhci_pci              18158  0 
sdhci                  31824  1 sdhci_pci
ahci                   25507  2 
libahci                26108  1 ahci

```

---

### Post by Toz on 2013-09-26
> 
Module                  Size  Used by
.....
i2c_designware_pci     12872  [COLOR="#FF0000"]1[/COLOR] 
i2c_designware_core    14030  1 i2c_designware_pci
.....
Hmm. Somethings using i2c_designware_pci but it doesn't list what. 

Does
```
cat /proc/modules
```
...show something different?

Can you also post back you dmesg log?
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

One other thing you might want to try is to temporarily blacklist those kernel modules on the kernel boot line while booting. Hold down the shift key to bring up the grub screen, and select the option to edit the command line then add in **i2c_designware_pci.blacklist=yes i2c_designware_core.blacklist=yes** and boot. See what doesn't work and try suspending. If there are any problems, just reboot to get things back to normal.

---

### Post by roli100 on 2013-09-26
cat /proc/modules:
```
coretemp 13131 0 - Live 0x00000000
joydev 17097 0 - Live 0x00000000 (F)
arc4 12543 2 - Live 0x00000000 (F)
uvcvideo 71279 0 - Live 0x00000000
snd_hda_codec_realtek 63791 1 - Live 0x00000000
videobuf2_vmalloc 12920 1 uvcvideo, Live 0x00000000
videobuf2_memops 13042 1 videobuf2_vmalloc, Live 0x00000000
snd_hda_intel 38307 1 - Live 0x00000000
snd_hda_codec 117617 2 snd_hda_codec_realtek,snd_hda_intel, Live 0x00000000
rt2800usb 22366 0 - Live 0x00000000
snd_hwdep 13272 1 snd_hda_codec, Live 0x00000000 (F)
rt2x00usb 19979 1 rt2800usb, Live 0x00000000
rt2800lib 60947 1 rt2800usb, Live 0x00000000
snd_pcm 80890 2 snd_hda_intel,snd_hda_codec, Live 0x00000000 (F)
rt2x00lib 48522 3 rt2800usb,rt2x00usb,rt2800lib, Live 0x00000000
snd_page_alloc 14230 2 snd_hda_intel,snd_pcm, Live 0x00000000 (F)
snd_seq_midi 13132 0 - Live 0x00000000 (F)
snd_seq_midi_event 14475 1 snd_seq_midi, Live 0x00000000 (F)
mac80211 526519 3 rt2x00usb,rt2800lib,rt2x00lib, Live 0x00000000
qmi_wwan 12910 0 - Live 0x00000000
videobuf2_core 39161 1 uvcvideo, Live 0x00000000
snd_rawmidi 25114 1 snd_seq_midi, Live 0x00000000 (F)
cdc_wdm 17663 1 qmi_wwan, Live 0x00000000
videodev 95806 2 uvcvideo,videobuf2_core, Live 0x00000000
microcode 18286 0 - Live 0x00000000 (F)
usbnet 26567 1 qmi_wwan, Live 0x00000000
cfg80211 436177 2 rt2x00lib,mac80211, Live 0x00000000
snd_seq 51280 2 snd_seq_midi,snd_seq_midi_event, Live 0x00000000 (F)
qcserial 12602 0 - Live 0x00000000
crc_ccitt 12627 1 rt2800lib, Live 0x00000000 (F)
psmouse 81065 0 - Live 0x00000000 (F)
rfcomm 37420 12 - Live 0x00000000
bnep 17669 2 - Live 0x00000000
btusb 17986 0 - Live 0x00000000
serio_raw 13031 0 - Live 0x00000000 (F)
snd_seq_device 14137 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x00000000 (F)
snd_timer 24411 2 snd_pcm,snd_seq, Live 0x00000000 (F)
hid_ntrig 18494 0 - Live 0x00000000
bluetooth 202109 22 rfcomm,bnep,btusb, Live 0x00000000
usb_wwan 14830 1 qcserial, Live 0x00000000
usbserial 27423 2 qcserial,usb_wwan, Live 0x00000000
snd 56485 11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_seq_device,snd_timer, Live 0x00000000 (F)
soundcore 12600 1 snd, Live 0x00000000 (F)
tpm_infineon 17194 0 - Live 0x00000000
intel_mid_dma 17713 0 - Live 0x00000000
fujitsu_tablet 12922 0 - Live 0x00000000
tpm_tis 18203 0 - Live 0x00000000
mac_hid 13037 0 - Live 0x00000000
ext2 63166 1 - Live 0x00000000 (F)
fujitsu_laptop 18467 0 - Live 0x00000000
gma500_gfx 167832 2 - Live 0x00000000
i2c_intel_mid 13111 0 - Live 0x00000000
video 18894 1 gma500_gfx, Live 0x00000000 (F)
drm_kms_helper 47545 1 gma500_gfx, Live 0x00000000
i2c_designware_pci 12872 1 - Live 0x00000000
drm 228489 3 gma500_gfx,drm_kms_helper, Live 0x00000000
i2c_designware_core 14030 1 i2c_designware_pci, Live 0x00000000
i2c_algo_bit 13197 1 gma500_gfx, Live 0x00000000
lp 13299 0 - Live 0x00000000 (F)
parport 40753 1 lp, Live 0x00000000 (F)
usbhid 41805 1 hid_ntrig, Live 0x00000000
hid 82666 2 hid_ntrig,usbhid, Live 0x00000000
sdhci_pci 18158 0 - Live 0x00000000
sdhci 31824 1 sdhci_pci, Live 0x00000000
ahci 25507 2 - Live 0x00000000 (F)
libahci 26108 1 ahci, Live 0x00000000 (F)

```

The link: [http://paste.ubuntu.com/6159778/](http://paste.ubuntu.com/6159778/)

I've tried booting as you've suggested. Nothing seemed to break (at least nothing that was working before). But it still won't go to sleep - still problem actually (some devices failed to suspend). Actually I think that the modules still got loaded somehow because they are still there. 

Oh, also worth mentioning is that I've replaced the Xubuntu with Lubuntu a while back because of performance issues. Problem is the same though.

---

### Post by Toz on 2013-09-26
Can you give this a try just to see if it works?

As root, create the file **/etc/pm/config.d/modules** with the following content:
```
SUSPEND_MODULES="i2c_designware_pci i2c_designware_core"
```
...save the file and try to suspend again.

Review **/var/log/pm-suspend.log** and the results of:
```
cat /var/log/syslog | grep PM:
```
...to see if there are any changes.

---

### Post by roli100 on 2013-09-26
I did. It doesn't seem to have any effect. Doesn't suspend and the logs still show the same things as before.

---

### Post by Toz on 2013-09-26
I'm afraid I'm out of ideas. It may be best to create a bug report.
```
ubuntu-bug linux
```

---

### Post by roli100 on 2013-09-26
Well thank you very much for your support.

It seems like I have a decision to make now. Live with non working suspend (although the whole thing does boot in 30s which is great) and other unrelated issues like terrible pen/touch support or back to Windows. Sadly Ubuntu based distributions have been the only ones that actually boot on this thing (because of the graphic driver) so I don't really have that much choice.

---

