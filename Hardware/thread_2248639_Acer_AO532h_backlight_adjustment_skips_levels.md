---
title: "Acer AO532h backlight adjustment skips levels"
date: 2014-10-15
forum: Hardware
---

### Post by Maximus559 on 2014-10-15
I have Xubuntu 14.04 installed on my Acer Aspire One AO532h netbook. Everything works perfectly except for backlight adjustment: when I use the keyboard to change backlight levels, one keystroke results in three jumps in brightness. I should have at least nine backlight levels, but I only have access to three of them.

I've tried a few solutions described in other forum posts, but nothing has worked satisfactorily so far. Any ideas?

---

### Post by Toz on 2014-10-16
Which solutions have you tried?

Can you open a terminal window, type in the following commands and post back the results:

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Info about your video card(s) and drivers:
```
lspci -k | grep -A2 VGA
```

3. Info about the recognized backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

4. Your currently loaded kernel modules:
```
lsmod
```

5. What, if anything, xorg says about backlight:
```
cat /var/log/Xorg.0.log | grep -i backlight
```

---

### Post by Maximus559 on 2014-10-17
Thanks for the response. I tried fiddling with /etc/default/grub and the Xfce settings editor. Got close, but not quite the solution I was hoping for. That may have created some suspend/resume problems as well, but it might have been incidental.

BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=662c6ed5-8939-4810-b890-cfd43a9e627c ro quiet splash vt.handoff=7

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
    Subsystem: Acer Incorporated [ALI] Device 0349
    Kernel driver in use: i915

 /sys/class/backlight/acpi_video0
3
9
3

Module                  Size  Used by
ctr                    12905  2 
ccm                    17496  2 
snd_hda_codec_realtek    55163  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
arc4                   12536  2 
bnep                   18895  2 
rfcomm                 53664  4 
bluetooth             342208  10 bnep,rfcomm
uvcvideo               71309  0 
ath9k                 144602  0 
videobuf2_vmalloc      13048  1 uvcvideo
ath9k_common           13359  1 ath9k
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
videobuf2_memops       13170  1 videobuf2_vmalloc
ath9k_hw              438205  2 ath9k_common,ath9k
videobuf2_core         39258  1 uvcvideo
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
videodev              108503  2 uvcvideo,videobuf2_core
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  709755  4 
coretemp               13195  0 
mac80211              546051  1 ath9k
snd_rawmidi            25135  1 snd_seq_midi
joydev                 17101  0 
drm_kms_helper         48868  1 i915
serio_raw              13230  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
cfg80211              409394  3 ath,ath9k,mac80211
drm                   244037  5 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
lpc_ich                16864  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60939  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
parport_pc             31981  0 
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
ppdev                  17391  0 
video                  18903  2 i915,acer_wmi
wmi                    18673  1 acer_wmi
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                91329  0 
ahci                   25579  2 
libahci                27214  1 ahci
atl1c                  40949  0 

[    31.024] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')

---

### Post by Toz on 2014-10-18
Everything looks okay there.

If you manually try to adjust brightness, do you get access to all 9 levels?
```
echo 9 | sudo tee /sys/class/backlight/acpi_video0/brightness 
echo 8 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 6 | sudo tee /sys/class/backlight/acpi_video0/brightness
...etc
```

---

### Post by Maximus559 on 2014-10-28
Yes, the manual adjustment works.

---

### Post by Toz on 2014-10-28
Can you try the **video.use_native_backlight=1** kernel parameter? Once booted with it, can you post back the results again as per post #2?

I believe this will give you a second "intel_backlight" interface. If it does, you can then create the [/usr/share/X11/xorg.conf.d/80-backlight.conf]("/usr/share/X11/xorg.conf.d/80-backlight.conf") file as shown in that link to force the system to use this backlight interface. (Note: you'll need to log out and back in again for that file to take effect).

---

### Post by Maximus559 on 2014-11-01
After adding the **video.use_native_backlight=1** kernel parameter:

BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic root=UUID=662c6ed5-8939-4810-b890-cfd43a9e627c ro quiet splash video.use_native_backlight=1 vt.handoff=7

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
    Subsystem: Acer Incorporated [ALI] Device 0349
    Kernel driver in use: i915

 /sys/class/backlight/acpi_video0
0
9
0

Module                  Size  Used by
ctr                    12905  2 
ccm                    17496  2 
snd_hda_codec_realtek    59259  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
rfcomm                 53664  4 
snd_seq_midi_event     14475  1 snd_seq_midi
bnep                   18895  2 
arc4                   12536  2 
bluetooth             342208  10 bnep,rfcomm
snd_rawmidi            25135  1 snd_seq_midi
ath9k                 144602  0 
uvcvideo               71309  0 
ath9k_common           13359  1 ath9k
coretemp               13195  0 
ath9k_hw              438205  2 ath9k_common,ath9k
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
videodev              108503  2 uvcvideo,videobuf2_core
joydev                 17101  0 
mac80211              546051  1 ath9k
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
i915                  709887  4 
serio_raw              13230  0 
snd                    60939  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         48868  1 i915
cfg80211              409394  3 ath,ath9k,mac80211
lpc_ich                16864  0 
drm                   244037  5 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
parport_pc             31981  0 
acer_wmi               31735  0 
ppdev                  17391  0 
sparse_keymap          13708  1 acer_wmi
mac_hid                13037  0 
wmi                    18673  1 acer_wmi
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
video                  18903  2 i915,acer_wmi
psmouse                91357  0 
ahci                   25579  2 
libahci                27214  1 ahci
atl1c                  40949  0 

[    33.702] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic root=UUID=662c6ed5-8939-4810-b890-cfd43a9e627c ro quiet splash video.use_native_backlight=1 vt.handoff=7
[    34.044] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')

EDIT: this seemed to make no practical difference

---

### Post by Toz on 2014-11-02
"video.use_native_backlight=1" didn't make a difference. Can you try **acpi_backlight=vendor** and post back the results again?

---

### Post by Maximus559 on 2014-11-06
Making progress! With **acpi_backlight=vendor**, brightness now changes two levels at a time.

This is as far as I got before. I couldn't progress further without screwing up the brightness indicator popups, which didn't seem ideal.

BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic root=UUID=662c6ed5-8939-4810-b890-cfd43a9e627c ro quiet splash acpi_backlight=vendor vt.handoff=7

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
	Subsystem: Acer Incorporated [ALI] Device 0349
	Kernel driver in use: i915

 /sys/class/backlight/acer-wmi
0
9
0

Module                  Size  Used by
ctr                    12905  2 
ccm                    17496  2 
snd_hda_codec_realtek    59259  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
acer_wmi               31735  0 
arc4                   12536  2 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
sparse_keymap          13708  1 acer_wmi
snd_seq_midi           13132  0 
i915                  709887  4 
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k_hw              438205  2 ath9k_common,ath9k
snd_rawmidi            25135  1 snd_seq_midi
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
bnep                   18895  2 
rfcomm                 53664  4 
bluetooth             342208  10 bnep,rfcomm
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
mac80211              546051  1 ath9k
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 17101  0 
videodev              108503  2 uvcvideo,videobuf2_core
snd_timer              28584  2 snd_pcm,snd_seq
coretemp               13195  0 
serio_raw              13230  0 
drm_kms_helper         48868  1 i915
snd                    60939  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                16864  0 
soundcore              12600  1 snd
cfg80211              409394  3 ath,ath9k,mac80211
drm                   244037  5 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
wmi                    18673  1 acer_wmi
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
video                  18903  2 i915,acer_wmi
psmouse                91357  0 
ahci                   25579  2 
libahci                27214  1 ahci
atl1c                  40949  0 

[    33.817] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic root=UUID=662c6ed5-8939-4810-b890-cfd43a9e627c ro quiet splash acpi_backlight=vendor vt.handoff=7
[    34.124] (--) intel(0): found backlight control interface acer-wmi (type 'platform')

---

### Post by Toz on 2014-11-06
Its strange that you are not getting an intel_backlight interface. 

Can we try one more thing? First, remove the "acpi_backlight=vendor" kernel parameter and reboot. On reboot, post back:
```
cat /proc/cmdline
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

Then, unload the acer_wmi kernel module:
```
sudo modprobe -r acer_wmi
```
...and post back again:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

Then try the function keys again.

---

### Post by Maximus559 on 2014-11-06
Function keys still change backlight levels in increments of three.

BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic root=UUID=662c6ed5-8939-4810-b890-cfd43a9e627c ro quiet splash vt.handoff=7

 /sys/class/backlight/acpi_video0
0
9
0

sudo modprobe -r acer_wmi

 /sys/class/backlight/acpi_video0
0
9
0

---

### Post by Toz on 2014-11-07
Does issuing the command:
```
echo 0 | sudo tee /sys/module/video/parameters/brightness_switch_enabled
```
make the brightness increment by one step?

To confirm the command:
```
cat /sys/module/video/parameters/brightness_switch_enabled
```

---

### Post by Maximus559 on 2014-11-09
No, the command doesn't seem to do anything.

---

### Post by Maximus559 on 2015-02-01
Respectfully bumping this rather old thread... never did find a complete solution for this problem.

---

