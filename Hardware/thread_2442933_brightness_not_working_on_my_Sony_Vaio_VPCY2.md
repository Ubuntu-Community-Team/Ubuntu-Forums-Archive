---
title: "brightness not working on my Sony Vaio VPCY2"
date: 2020-05-09
forum: Hardware
---

### Post by deenoo-g on 2020-05-09
Hello guys,

I have some issues with my Sony Vaio VPCY2 and Ubuntu 20.04 LTS, with the brightness oof my disaply as it is not working:
- [Fn] + F5/F6  - does activae the animation showing me the bigthness is changing up or down but in reality the luminosity of the display it doesn't change at all


I've been following this old closed thread: [https://ubuntuforums.org/showthread.php?t=2086359](https://ubuntuforums.org/showthread.php?t=2086359) but I didn't succeed yet, I think I'm close the solve it but there are some thing that I'm missing.
Bellow are the debug commands and the scripts I've created based on the old thread.

```


cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-5.4.0-29-generic root=UUID=90229dd1-c6a2-47fb-a038-991c40ec52a6 ro quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7
lsmod
Module                  Size  Used by
ccm                    20480  9
snd_hda_codec_hdmi     61440  1
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_intel          53248  3
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              475136  2 ath9k_common,ath9k
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
ath                    36864  3 ath9k_common,ath9k,ath9k_hw
uvcvideo               98304  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
mac80211              843776  1 ath9k
videobuf2_v4l2         24576  1 uvcvideo
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
videodev              225280  3 videobuf2_v4l2,uvcvideo,videobuf2_common
intel_powerclamp       20480  0
i915                 1986560  4
mc                     53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
coretemp               20480  0
snd_timer              36864  2 snd_seq,snd_pcm
intel_cstate           20480  0
input_leds             16384  0
joydev                 24576  0
sparse_keymap          16384  0
snd                    90112  17 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
wmi_bmof               16384  0
serio_raw              20480  0
cfg80211              704512  4 ath9k_common,ath9k,ath,mac80211
drm_kms_helper        184320  1 i915
intel_ips              28672  0
mei_me                 40960  0
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
mei                   106496  1 mei_me
libarc4                16384  1 mac80211
syscopyarea            16384  1 drm_kms_helper
soundcore              16384  1 snd
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
sony_laptop            61440  0
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
drm                   491520  5 drm_kms_helper,i915
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   131072  2 usbhid,hid_generic
ahci                   40960  2
firewire_ohci          40960  0
psmouse               155648  0
libahci                32768  1 ahci
lpc_ich                24576  0
atl1c                  53248  0
firewire_core          65536  1 firewire_ohci
sdhci_pci              53248  0
i2c_i801               32768  0
cqhci                  28672  1 sdhci_pci
crc_itu_t              16384  1 firewire_core
sdhci                  65536  1 sdhci_pci
wmi                    32768  1 wmi_bmof
video                  49152  2 i915,sony_laptop
sudo lspci -vnn  |grep -A10 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Core Processor Integrated Graphics Controller [104d:9076]
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5050 [size=8]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

```


```

for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/intel_backlight
4882
4882
4882
/sys/class/backlight/sony
6
-1
7

```

```

pastebinit /var/log/dmesg
[https://paste.ubuntu.com/p/7ysPsWbFJH/](https://paste.ubuntu.com/p/7ysPsWbFJH/)
pastebinit /var/log/Xorg.0.log
Unable to read from: /var/log/Xorg.0.log

```


```

sudo acpi_listen

video/brightnessup BRTUP 00000086 00000000 K
sony/hotkey SNY5001:00 00000001 00000011
sony/hotkey SNY5001:00 00000001 0000003b
video/brightnessdown BRTDN 00000087 00000000 K
sony/hotkey SNY5001:00 00000001 00000010
sony/hotkey SNY5001:00 00000001 0000003b

```

I've adapted the scripts based on the above debug output:

```

cat /etc/acpi/events/sony-brightness-up
event=sony/hotkey SNY5001:00 00000001 00000011
action=/etc/acpi/brightup.sh
cat /etc/acpi/events/sony-brightness-down 
event=sony/otkey SNY5001:00 00000001 00000010
action=/etc/acpi/brightdown.sh

```

```

cat  /etc/acpi/brightdown.sh
#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 406 ]; then
   curr=$((curr-406));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi

```

```

cat  /etc/acpi/brightup.sh
#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4477 ]; then
   curr=$((curr+406));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi

```

```

ll /etc/acpi/events/sony-brightness-up; ll /etc/acpi/events/sony-brightness-down ; ll /etc/acpi/brightup.sh; ll /etc/acpi/brightdown.sh 
-rwxr-xr-x 1 root root 76 mai  9 14:30 /etc/acpi/events/sony-brightness-up*
-rwxr-xr-x 1 root root 77 mai  9 14:30 /etc/acpi/events/sony-brightness-down*
-rwxr-xr-x 1 root root 198 mai  9 14:08 /etc/acpi/brightup.sh*
-rwxr-xr-x 1 root root 197 mai  9 14:08 /etc/acpi/brightdown.sh*

```

Now, these scripts /etc/acpi/brightup.sh and /etc/acpi/brightdown.sh does seem to work, only if I execute them as root (or with sudo) not with a regular user.
When executed with root/sudo the luminosity does change in reality up and down.
When trying to execute the same scripts with regular user I get Permission Denied to change anything in the /sys/class/backlight/intel_backlight/brightness file (as it is own by root and write rights only for root).

But using the key combination Fn+F5/F6 activates the animation but luminosity doesn't change.

Can you please help me, what do I miss here, please?

---

### Post by deenoo-g on 2020-05-09
In /var/log/syslog I can see these, while pressing Fn+F5/F6

```

May  9 17:10:32 dinu-VPCY21S1E gnome-shell[1614]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
May  9 17:10:32 dinu-VPCY21S1E gnome-shell[1614]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
May  9 17:10:32 dinu-VPCY21S1E gnome-shell[1614]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
May  9 17:10:32 dinu-VPCY21S1E gnome-shell[1614]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
May  9 17:10:32 dinu-VPCY21S1E gnome-shell[1614]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
May  9 17:10:32 dinu-VPCY21S1E gnome-shell[1614]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
May  9 17:10:32 dinu-VPCY21S1E gnome-shell[1614]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
May  9 17:10:32 dinu-VPCY21S1E gnome-shell[1614]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
May  9 17:10:32 dinu-VPCY21S1E gnome-shell[1614]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).

```

---

### Post by deenoo-g on 2020-05-09
Based on the above debug info, I had a clue that the issue might be caused by Gnmome desktop (by overwriting the binding keys for Fn+F5/F6), 
so,
I've installed Unity Desktop and now the brightness is working fine using Fn+F5/F6 keys :)

---

