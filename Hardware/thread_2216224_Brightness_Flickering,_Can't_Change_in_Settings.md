---
title: "Brightness Flickering, Can't Change in Settings"
date: 2014-04-10
forum: Hardware
---

### Post by 0dyss3us on 2014-04-10
Hey all,

I just installed 13.10 on an older laptop and I'm having some strange screen problems. Most noticeably, I can't change Brightness through the System Settings. Any time I touch the Brightness slider, the screen flickers like crazy and the slider hops all over the continuum. This continues until I hit the gear icon in the panel, then the brightness level stays wherever it randomly happened to be right when I clicked the gear. This same behavior also happens when I attempt to use the keyboard buttons to change brightness.

Possibly related, I also have problems with the screen locking after being idle. It starts to dim after the time limit set in System Settings, but as soon as it gets dark, it flashes right back up to the desktop and restarts the idle timer completely bypassing the lock screen and the password entry to unlock. On some occasions, maybe 20% of the time, the screen will actually stay dark, but nothing will awaken it. No key presses, touchpad movement, CTRL+ALT+Delete, nothing. It requires pressing and holding the power button for a full shutdown. And on even rarer occasions, maybe 5%, the screen will turn off at the right time and it will actually lock like its supposed to. A key press or touchpad swipe will wake it back as normal and password entry will open it right where I left off.

Moral of the story, I don't know if this is a graphics issue or a power management issue. If it helps, the laptop is using an Intel GM965/GL960 Integrated Graphics Controller (although this Display Controller is listed as secondary to the VGA Controller in the lspci output... does that mean something?).

Thanks for the help!

---

### Post by Toz on 2014-04-10
Let's get some more detail about your system. For most of these, open a terminal window, type in the command, and post back the results inbetween **[noparse]```
 
```[/noparse]** tags:

1. The make and model of your computer.

2. The current kernel command line:
```
cat /proc/cmdline
```

3. Info about your video card(s):
```
lspci -k | grep -iA2 VGA
```

4. Info about your recognized backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

5. A list of your currently loaded kernel modules:
```
lsmod
```

6. What X says about backlight:
```
cat /var/log/Xorg.0.log | grep -i backlight
```

---

### Post by 0dyss3us on 2014-04-15
1) It was a laptop made by a local computer store for my company. So no make or model, sorry
2) ```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-19-generic root=UUID=4a26d1e6-97e3-4d3d-bda3-9074fadfc1e7 ro quiet splash vt.handoff=7
```
3) ```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 3ff3
    Kernel driver in use: i915
```
4) ```
 /sys/class/backlight/acpi_video0
1
8
1
```
5) ```
Module                  Size  Used by
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18959  2 
bluetooth             323656  10 bnep,rfcomm
coretemp               13195  0 
kvm_intel             128218  0 
kvm                   368975  1 kvm_intel
gpio_ich               13229  0 
snd_hda_codec_realtek    50315  1 
joydev                 17097  0 
arc4                   12536  2 
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
iwl4965               106818  0 
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
uvcvideo               71309  0 
iwlegacy               88016  1 iwl4965
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
mac80211              517444  2 iwl4965,iwlegacy
snd_seq_midi           13132  0 
videobuf2_vmalloc      13048  1 uvcvideo
i915                  594442  4 
snd_seq_midi_event     14475  1 snd_seq_midi
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
snd_rawmidi            25094  1 snd_seq_midi
videodev              107508  2 uvcvideo,videobuf2_core
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
cfg80211              401762  3 iwl4965,iwlegacy,mac80211
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper         46867  1 i915
snd_timer              24447  2 snd_pcm,snd_seq
drm                   242400  5 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
microcode              18894  0 
pcmcia                 51368  0 
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
psmouse                90642  0 
soundcore              12600  1 snd
serio_raw              13189  0 
yenta_socket           40193  0 
pcmcia_rsrc            18319  1 yenta_socket
lp                     13299  0 
lpc_ich                16864  0 
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
mac_hid                13037  0 
video                  18777  1 i915
parport                40795  3 lp,ppdev,parport_pc
firewire_ohci          35463  0 
firewire_core          57656  1 firewire_ohci
sdhci_pci              18456  0 
crc_itu_t              12627  1 firewire_core
sdhci                  37644  1 sdhci_pci
r8169                  61562  0 
mii                    13654  1 r8169
```
6) ```
[    25.357] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
```

---

### Post by Toz on 2014-04-15
> 1) It was a laptop made by a local computer store for my company. So no make or model, sorry
What do the following commands return:
```
sudo dmidecode -s system-manufacturer
sudo dmidecode -s system-product-name
sudo dmidecode -s system-version
```

Can you change the brightness by directly manipulating the backlight interface:
```
echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 8 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

And finally, can I have a look at your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated. If pasebinit is not installed, you can install it via:
```
sudo apt-get install pastebinit
```

---

### Post by 0dyss3us on 2014-04-18
```


sudo dmidecode -s system-manufacturer
Micro-Star International

sudo dmidecode -s system-product-name
MSI Notebook PR600

sudo dmidecode -s system-version
Ver 1.000


```

As for directly changing the backlight, I can effect it but it's not the expected behavior. Echoing a value between 1 and 7 just alternates the brightness back and forth between min and max. For example, brightness starts at max value, echo 4 responds with a quick but gradual incremental decrease in brightness to min value. Echo 4 again sets it to max brightness with the same gradual increase from 4 to max. Echoing min or max, 0 or 8,sets it appropriately.

Here's the link: [http://paste.ubuntu.com/7276355/](http://paste.ubuntu.com/7276355/)

And thanks for the help so far, I appreciate it. Sorry I've been taking awhile to respond, too. Wish I had more time to fiddle with this!

---

### Post by Toz on 2014-04-18
No worries. I'd like you to try temporarily booting with the **acpi_backlight=vendor** kernel parameter. To do so, follow the "Temporarily Add a Kernel Boot Parameter for Testing" from the [Kernel Boot Parameters wiki]("https://wiki.ubuntu.com/Kernel/KernelBootParameters").

Once you've booted with this parameter, can you once again post back the results from the commands from post #2?

Also, try the brightness slider again.

---

### Post by 0dyss3us on 2014-04-18
```

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4a26d1e6-97e3-4d3d-bda3-9074fadfc1e7 ro quiet splash vt.handoff=7 acpi_backlight=vendor

lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device 3ff3
	Kernel driver in use: i915

for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory

lsmod
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
gpio_ich               13229  0 
joydev                 17101  0 
snd_hda_codec_realtek    51029  1 
arc4                   12536  2 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
coretemp               13195  0 
kvm_intel             132549  0 
snd_rawmidi            25135  1 snd_seq_midi
pcmcia                 51828  0 
kvm                   388083  1 kvm_intel
iwl4965               106859  0 
iwlegacy               88016  1 iwl4965
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
mac80211              545990  2 iwl4965,iwlegacy
psmouse                91033  0 
serio_raw              13230  0 
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
yenta_socket           40201  0 
lpc_ich                16864  0 
pcmcia_rsrc            18319  1 yenta_socket
i915                  705396  3 
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
soundcore              12600  1 snd
cfg80211              409394  3 iwl4965,iwlegacy,mac80211
drm_kms_helper         46907  1 i915
drm                   243792  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
video                  18903  1 i915
parport_pc             31981  0 
mac_hid                13037  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
firewire_ohci          35529  0 
sdhci_pci              18535  0 
firewire_core          61867  1 firewire_ohci
sdhci                  37779  1 sdhci_pci
r8169                  61562  0 
crc_itu_t              12627  1 firewire_core
mii                    13654  1 r8169

cat /var/log/Xorg.0.log | grep -i backlight
[    25.965] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4a26d1e6-97e3-4d3d-bda3-9074fadfc1e7 ro quiet splash vt.handoff=7 acpi_backlight=vendor


```

Tried to test brightness slider, but it disappeared. It is no longer there under system settings. The Function keys no longer work either. Nor does editing the backlight values through the terminal like previously tested.

---

### Post by Toz on 2014-04-18
Yep, that didn't work at all. Can you try the:

**acpi_osi=**

kernel parameter instead? Lets see what it does with the backlight interfaces. Post back the results again.


----------
EDIT: After you try that one, can you also try:
**video.use_bios_initial_backlight=0**
...and post back the results.

---

### Post by 0dyss3us on 2014-04-18
I assume you mean acpi_osi=**vendor**, correct?

```

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4a26d1e6-97e3-4d3d-bda3-9074fadfc1e7 ro quiet splash vt.handoff=7 acpi_osi=vendor

lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 3ff3
    Kernel driver in use: i915

for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
 /sys/class/backlight/acpi_video0
8
8
8

lsmod
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
joydev                 17101  0 
gpio_ich               13229  0 
snd_hda_codec_realtek    51029  1 
arc4                   12536  2 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
snd_hda_intel          42730  3 
coretemp               13195  0 
kvm_intel             132549  0 
iwl4965               106859  0 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
pcmcia                 51828  0 
kvm                   388083  1 kvm_intel
iwlegacy               88016  1 iwl4965
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
i915                  705396  3 
mac80211              545990  2 iwl4965,iwlegacy
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
psmouse                91033  0 
serio_raw              13230  0 
drm_kms_helper         46907  1 i915
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
yenta_socket           40201  0 
snd_rawmidi            25135  1 snd_seq_midi
cfg80211              409394  3 iwl4965,iwlegacy,mac80211
pcmcia_rsrc            18319  1 yenta_socket
lpc_ich                16864  0 
drm                   243792  4 i915,drm_kms_helper
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
parport_pc             31981  0 
video                  18903  1 i915
ppdev                  17391  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18535  0 
sdhci                  37779  1 sdhci_pci
r8169                  61562  0 
mii                    13654  1 r8169

cat /var/log/Xorg.0.log | grep -i backlight
[    27.293] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')

```

Back to the original behavior. I'll reboot with the next kernel parameter you mentioned and post the output in a minute.

---

### Post by 0dyss3us on 2014-04-18
Using **video.use_bios_initial_backlight=0** didn't help either. Same behavior all around.

```

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4a26d1e6-97e3-4d3d-bda3-9074fadfc1e7 ro quiet splash vt.handoff=7 video.use_bios_initial_backlight=0

lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 3ff3
    Kernel driver in use: i915

for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
 /sys/class/backlight/acpi_video0
8
8
8

lsmod
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
joydev                 17101  0 
gpio_ich               13229  0 
snd_hda_codec_realtek    51029  1 
arc4                   12536  2 
uvcvideo               71309  0 
coretemp               13195  0 
videobuf2_vmalloc      13048  1 uvcvideo
kvm_intel             132549  0 
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
kvm                   388083  1 kvm_intel
pcmcia                 51828  0 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
iwl4965               106859  0 
psmouse                91033  0 
serio_raw              13230  0 
yenta_socket           40201  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
pcmcia_rsrc            18319  1 yenta_socket
iwlegacy               88016  1 iwl4965
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
mac80211              545990  2 iwl4965,iwlegacy
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              409394  3 iwl4965,iwlegacy,mac80211
i915                  705396  3 
drm_kms_helper         46907  1 i915
lpc_ich                16864  0 
drm                   243792  4 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
video                  18903  1 i915
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
sdhci_pci              18535  0 
crc_itu_t              12627  1 firewire_core
sdhci                  37779  1 sdhci_pci
r8169                  61562  0 
mii                    13654  1 r8169

cat /var/log/Xorg.0.log | grep -i backlight
[    25.143] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4a26d1e6-97e3-4d3d-bda3-9074fadfc1e7 ro quiet splash vt.handoff=7 video.use_bios_initial_backlight=0
[    26.604] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')


```

---

### Post by Toz on 2014-04-18
> **0dyss3us said:**
> I assume you mean acpi_osi=**vendor**, correct?

```

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4a26d1e6-97e3-4d3d-bda3-9074fadfc1e7 ro quiet splash vt.handoff=7 acpi_osi=vendor

lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 3ff3
    Kernel driver in use: i915

for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
 /sys/class/backlight/acpi_video0
8
8
8

lsmod
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
joydev                 17101  0 
gpio_ich               13229  0 
snd_hda_codec_realtek    51029  1 
arc4                   12536  2 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
snd_hda_intel          42730  3 
coretemp               13195  0 
kvm_intel             132549  0 
iwl4965               106859  0 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
pcmcia                 51828  0 
kvm                   388083  1 kvm_intel
iwlegacy               88016  1 iwl4965
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
i915                  705396  3 
mac80211              545990  2 iwl4965,iwlegacy
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
psmouse                91033  0 
serio_raw              13230  0 
drm_kms_helper         46907  1 i915
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
yenta_socket           40201  0 
snd_rawmidi            25135  1 snd_seq_midi
cfg80211              409394  3 iwl4965,iwlegacy,mac80211
pcmcia_rsrc            18319  1 yenta_socket
lpc_ich                16864  0 
drm                   243792  4 i915,drm_kms_helper
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
parport_pc             31981  0 
video                  18903  1 i915
ppdev                  17391  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18535  0 
sdhci                  37779  1 sdhci_pci
r8169                  61562  0 
mii                    13654  1 r8169

cat /var/log/Xorg.0.log | grep -i backlight
[    27.293] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')

```

Back to the original behavior. I'll reboot with the next kernel parameter you mentioned and post the output in a minute.

Actually, just **acpi_osi=** (no vendor keyword, but include the equals sign). Can you try this one again just to see. Post back results again to confirm.

---------

If it doesn't work, boot normally again and try the following commands to see if the affect brightness without the flickering:
```
sudo setpci -s 00:02.0 F4.B=FF
sudo setpci -s 00:02.0 F4.B=80
```

---

### Post by 0dyss3us on 2014-04-19
oh, my apologies. with **acpi_osi=** the function keys work as expected. one press changes the brightness by one increment, no flicker and no gradual change to min or max brightness. However, when i attempt to change it via the system settings slider, the original behavior shows again. although this time i can stop the flicker using the function keys as well as pressing the gear icon.

here's the output:
```

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4a26d1e6-97e3-4d3d-bda3-9074fadfc1e7 ro quiet splash vt.handoff=7 acpi_osi=

lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 3ff3
    Kernel driver in use: i915

for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
 /sys/class/backlight/acpi_video0
8
8
8

lsmod
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
joydev                 17101  0 
gpio_ich               13229  0 
snd_hda_codec_realtek    51029  1 
arc4                   12536  2 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
coretemp               13195  0 
kvm_intel             132549  0 
kvm                   388083  1 kvm_intel
pcmcia                 51828  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
iwl4965               106859  0 
iwlegacy               88016  1 iwl4965
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
yenta_socket           40201  0 
psmouse                91033  0 
lpc_ich                16864  0 
i915                  705396  3 
pcmcia_rsrc            18319  1 yenta_socket
serio_raw              13230  0 
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac80211              545990  2 iwl4965,iwlegacy
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
drm_kms_helper         46907  1 i915
drm                   243792  4 i915,drm_kms_helper
cfg80211              409394  3 iwl4965,iwlegacy,mac80211
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
video                  18903  1 i915
parport                40836  3 lp,ppdev,parport_pc
mac_hid                13037  0 
firewire_ohci          35529  0 
sdhci_pci              18535  0 
firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  61562  0 
sdhci                  37779  1 sdhci_pci
mii                    13654  1 r8169

cat /var/log/Xorg.0.log | grep -i backlight
[    27.202] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')

```

---

### Post by 0dyss3us on 2014-04-19
> **Toz said:**
> If it doesn't work, boot normally again and try the following commands to see if the affect brightness without the flickering:
```
sudo setpci -s 00:02.0 F4.B=FF
sudo setpci -s 00:02.0 F4.B=80
```

These commands had no effect. No error message either.

---

### Post by Toz on 2014-04-19
**acpi_osi=** may be your best bet for now - at least the function keys work with it. You'll probably have to create a bug report to get the brightness slider to work.

---

### Post by 0dyss3us on 2014-04-19
Alrighty, thanks for your help, Toz. I appreciate it. When I file the bug, should I mention the problem with the screen staying dark while trying to wake from suspend? Or do you think the problems are unrelated?

---

### Post by Toz on 2014-04-19
> **0dyss3us said:**
> Alrighty, thanks for your help, Toz. I appreciate it. When I file the bug, should I mention the problem with the screen staying dark while trying to wake from suspend? Or do you think the problems are unrelated?
The screen staying blank is a known bug thats being worked on, so no need to report it. The problems are unrelated anyways.

---

### Post by bernovy on 2015-03-17
Dear Toz & Ubuntu community, I am at the end of my Ubuntu knowledge (and my patience ](*,)) and I am really hoping that you can help me fix my auto brightness issue on my XE700T. Same as 0dyss3us (and so many other Ubuntu users) I can't control the brightness from my settings or by manually changing the values in ../intel_backlight/brightness. 
My auto brightness seems to have a mind of its own and unfortunately for me I can't fix it with the "acpi_osi=" trick. Since the auto brightness flickers up and down every few seconds, its so frustrating that I can barely use my tablet. I tried my best to fix in the last 3 days but regardless of what I tried, I simply can't stabilize it, nevermind control it. At this state I would be delighted if I could just set it to one value at boot.
Please see below for details. Any help / guidance/ advice would be sincerely appreciated. Thank you! 

1. The make and model of my computer:
```
sudo dmidecode -s system-manufacturer
SAMSUNG ELECTRONICS CO., LTD.
sudo dmidecode -s system-product-name
700T1C
sudo dmidecode -s system-version
P10AAT
```

2. My current kernel:
```
cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.16.0-31-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro acpi_osi=Linux quiet splash acpi_backlight=vendor vt.handoff=7
```

3. Video card info:
```
lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device c0e1
    Kernel driver in use: i915
```

4. Recognized backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
 /sys/class/backlight/intel_backlight
3300
4648
3300
```

5. Currently loaded kernel modules:
```
lsmod
Module                  Size  Used by
hidp                   23741  1 
ipt_MASQUERADE         12880  3 
iptable_nat            12970  1 
nf_nat_ipv4            13263  1 iptable_nat
xt_CHECKSUM            12549  1 
iptable_mangle         12695  1 
bridge                116190  0 
stp                    12976  1 bridge
llc                    14396  2 stp,bridge
ctr                    13049  0 
ccm                    17773  0 
nfnetlink_queue        18233  1 
nfnetlink              14606  2 nfnetlink_queue
nvram                  14411  0 
msr                    12865  0 
ebtable_nat            12807  0 
ebtables               35009  1 ebtable_nat
xt_iprange             12783  0 
xt_mark                12563  6 
xt_NFQUEUE             12697  3 
dm_crypt               23216  1 
rfcomm                 69509  8 
bnep                   19624  2 
xt_hl                  12521  6 
ip6t_rt                13537  3 
nf_conntrack_ipv6      18894  8 
nf_defrag_ipv6         34768  1 nf_conntrack_ipv6
ip6t_REJECT            12939  3 
xt_LOG                 17718  10 
xt_limit               12711  13 
xt_tcpudp              12884  28 
xt_addrtype            12635  4 
nf_conntrack_ipv4      14806  13 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  20 
ipt_REJECT             12541  6 
ip6table_filter        12815  1 
ip6_tables             27026  1 ip6table_filter
ax88179_178a           18412  0 
usbnet                 43913  1 ax88179_178a
mii                    13934  2 usbnet,ax88179_178a
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12770  0 
nf_nat                 22050  4 nf_nat_ftp,ipt_MASQUERADE,nf_nat_ipv4,iptable_nat
nf_conntrack_ftp       18638  1 nf_nat_ftp
nf_conntrack          105081  11 nf_nat_ftp,nf_conntrack_netbios_ns,ipt_MASQUERADE,nf_nat,nf_nat_ipv4,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,iptable_nat,nf_conntrack_ipv4,nf_conntrack_ipv6
hid_sensor_accel_3d    13280  0 
iptable_filter         12810  1 
ip_tables              27240  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               34059  20 ip6table_filter,xt_iprange,xt_mark,xt_hl,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_NFQUEUE,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ebtables,ip6t_rt,ipt_REJECT,iptable_mangle,ip6_tables,xt_addrtype,ip6t_REJECT
hid_sensor_gyro_3d     13267  0 
hid_sensor_magn_3d     13267  0 
hid_sensor_incl_3d     13267  0 
hid_sensor_rotation    13387  0 
hid_sensor_trigger     13134  10 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d
industrialio_triggered_buffer    12882  5 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d
kfifo_buf              13432  1 industrialio_triggered_buffer
industrialio           54850  8 hid_sensor_trigger,hid_sensor_gyro_3d,industrialio_triggered_buffer,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,kfifo_buf,hid_sensor_magn_3d
nls_iso8859_1          12713  1 
hid_sensor_iio_common    14309  5 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
dm_multipath           22843  0 
snd_hda_codec_hdmi     47548  1 
arc4                   12608  2 
scsi_dh                14882  1 dm_multipath
snd_hda_codec_realtek    73089  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  614 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  309 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
iwldvm                232283  0 
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
mac80211              652718  1 iwldvm
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
serio_raw              13483  0 
uvcvideo               81073  0 
hid_multitouch         17419  0 
hid_sensor_hub         19877  7 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d,hid_sensor_iio_common
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
media                  21903  2 uvcvideo,videodev
wacom                  67184  0 
joydev                 17393  0 
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
btusb                  32497  0 
bluetooth             446409  27 bnep,hidp,btusb,rfcomm
iwlwifi               179412  1 iwldvm
6lowpan_iphc           18702  1 bluetooth
cfg80211              494330  3 iwlwifi,mac80211,iwldvm
shpchp                 37047  0 
lpc_ich                21093  0 
soundcore              15047  2 snd,snd_hda_codec
mei_me                 19696  0 
mei                    87875  1 mei_me
uas                    23159  0 
usb_storage            66545  1 uas
parport_pc             32741  0 
ppdev                  17671  0 
tpm_infineon           17131  0 
mac_hid                13227  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  5 hidp,hid_multitouch,hid_generic,hid_sensor_hub,usbhid
i915                  905954  3 
i2c_algo_bit           13413  1 i915
drm_kms_helper         61574  1 i915
drm                   311018  5 i915,drm_kms_helper
ahci                   34062  3 
libahci                32424  1 ahci
wmi                    19193  0 
video                  20128  1 i915
```

6. What X says about backlight:
```
cat /var/log/Xorg.0.log | grep -i backlight
[     7.084] Kernel command line: BOOT_IMAGE=/vmlinuz-3.16.0-31-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro acpi_osi=Linux quiet splash acpi_backlight=vendor vt.handoff=7
[     7.147] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
```

7. My rc.local:
```
cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 3300 > /sys/class/backlight/intel_backlight/brightness
fstrim /
exit 0
```

```
cat /sys/class/backlight/intel_backlight/brightness
3300
cat /sys/class/backlight/intel_backlight/actual_brightness
3300
```

8. My grub:
```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="3"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_DISABLE_OS_PROBER="true"
```

9. My fstab:
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
# Root partition (LVM)
/dev/mapper/ubuntu--vg-root /   ext4 noatime,discard,commit=60,errors=remount-ro   0   1
#
# Encrypted SWAP
# UUID="3a3b3783-f8db-4e6c-aaec-694e904a733f"
#/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
#
# /boot was on /dev/sda2 during installation
UUID=7077384a-26fc-4f8a-9b6d-dd2e33432d47 /boot           ext2    defaults        0       2
#
# /boot/efi was on /dev/sda1 during installation
UUID=326C-79D9  /boot/efi       vfat    defaults        0       1
```

10. My brightness slider does slide left and right but it doesnt change the brightness of the screen. The slider and the echo command below, are only changeing the values in /sys/class/backlight/intel_backlight/brightness and ../actual_brightness but without a physical effect on the screen. The physical screen brightness seems to have a mind of its own as it changes up and down by itself..
```

echo 4648 | sudo tee /sys/class/backlight/intel_backlight/brightness
4648
cat /sys/class/backlight/intel_backlight/actual_brightness
4648

```

---

### Post by Toz on 2015-03-17
@bernovy, What happens if you manually load the "samsung_laptop" module?
```
sudo modprobe samsung_laptop
```

Post back:
```
lsmod
```
```
dmesg | grep -i samsung_laptop
```
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

Then log out and back in again (don't restart) and post back the same info again plus:
```
cat /var/log/Xorg.0.log | grep -i backlight
```

---

### Post by bernovy on 2015-03-17
@Toz Thank you so much for your reply! Please see my results below. 

Before & after re-login:
```
sudo modprobe samsung_laptop
modprobe: ERROR: could not insert 'samsung_laptop': No such device
```

lsmod:
```
lsmod
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
hidp                   23741  1 
ipt_MASQUERADE         12880  3 
iptable_nat            12970  1 
nf_nat_ipv4            13263  1 iptable_nat
xt_CHECKSUM            12549  1 
iptable_mangle         12695  1 
bridge                116190  0 
stp                    12976  1 bridge
llc                    14396  2 stp,bridge
nfnetlink_queue        18233  1 
nfnetlink              14606  2 nfnetlink_queue
nvram                  14411  0 
msr                    12865  0 
ebtable_nat            12807  0 
ebtables               35009  1 ebtable_nat
xt_iprange             12783  0 
xt_mark                12563  6 
xt_NFQUEUE             12697  3 
dm_crypt               23216  1 
xt_hl                  12521  6 
ip6t_rt                13537  3 
nf_conntrack_ipv6      18894  8 
nf_defrag_ipv6         34768  1 nf_conntrack_ipv6
ip6t_REJECT            12939  3 
xt_LOG                 17718  10 
xt_limit               12711  13 
xt_tcpudp              12884  28 
xt_addrtype            12635  4 
nf_conntrack_ipv4      14806  13 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  20 
hid_sensor_magn_3d     13267  0 
hid_sensor_accel_3d    13280  0 
hid_sensor_rotation    13387  0 
hid_sensor_gyro_3d     13267  0 
hid_sensor_incl_3d     13267  0 
ipt_REJECT             12541  6 
hid_sensor_trigger     13134  10 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d
industrialio_triggered_buffer    12882  5 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d
kfifo_buf              13432  1 industrialio_triggered_buffer
industrialio           54850  8 hid_sensor_trigger,hid_sensor_gyro_3d,industrialio_triggered_buffer,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,kfifo_buf,hid_sensor_magn_3d
hid_sensor_iio_common    14309  5 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d
ip6table_filter        12815  1 
ip6_tables             27026  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12770  0 
nf_nat                 22050  4 nf_nat_ftp,ipt_MASQUERADE,nf_nat_ipv4,iptable_nat
nf_conntrack_ftp       18638  1 nf_nat_ftp
nf_conntrack          105081  11 nf_nat_ftp,nf_conntrack_netbios_ns,ipt_MASQUERADE,nf_nat,nf_nat_ipv4,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,iptable_nat,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
ip_tables              27240  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               34059  20 ip6table_filter,xt_iprange,xt_mark,xt_hl,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_NFQUEUE,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ebtables,ip6t_rt,ipt_REJECT,iptable_mangle,ip6_tables,xt_addrtype,ip6t_REJECT
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  1426 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  715 ghash_clmulni_intel,aesni_intel,ablk_helper
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
bnep                   19624  2 
snd_hda_codec_hdmi     47548  1 
media                  21903  2 uvcvideo,videodev
snd_hda_codec_realtek    73089  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
rfcomm                 69509  8 
btusb                  32497  0 
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
bluetooth             446409  27 bnep,hidp,btusb,rfcomm
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
uas                    23159  0 
snd_hwdep              17698  1 snd_hda_codec
6lowpan_iphc           18702  1 bluetooth
usb_storage            66545  1 uas
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
joydev                 17393  0 
arc4                   12608  2 
ax88179_178a           18412  0 
usbnet                 43913  1 ax88179_178a
hid_sensor_hub         19877  7 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d,hid_sensor_iio_common
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mii                    13934  2 usbnet,ax88179_178a
wacom                  67184  0 
iwldvm                232283  0 
mac80211              652718  1 iwldvm
serio_raw              13483  0 
snd_rawmidi            30876  1 snd_seq_midi
iwlwifi               179412  1 iwldvm
cfg80211              494330  3 iwlwifi,mac80211,iwldvm
lpc_ich                21093  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
hid_multitouch         17419  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 37047  0 
soundcore              15047  2 snd,snd_hda_codec
mei_me                 19696  0 
mei                    87875  1 mei_me
parport_pc             32741  0 
tpm_infineon           17131  0 
mac_hid                13227  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
nls_iso8859_1          12713  1 
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  5 hidp,hid_multitouch,hid_generic,hid_sensor_hub,usbhid
i915                  905954  3 
i2c_algo_bit           13413  1 i915
drm_kms_helper         61574  1 i915
ahci                   34062  3 
drm                   311018  5 i915,drm_kms_helper
libahci                32424  1 ahci
wmi                    19193  0 
video                  20128  1 i915
```

I don't get anything for:
```
dmesg | grep -i samsung_laptop
~$
```

Before re-login:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/intel_backlight
3300
4648
3300
```

After re-login:
```
 /sys/class/backlight/intel_backlight
4648
4648
4648
```


Before re-login:
```
cat /var/log/Xorg.0.log | grep -i backlight
[     7.473] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
```

After re-login:
```
cat /var/log/Xorg.0.log | grep -i backlight
[ 13946.014] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
```

So after re-login the flickering seems to have stopped but while the settings value shows my screen at max brightness, its definitely not as bright as in Windows. (and I definitely don't want to use Windows as my main OS, don't even have it installed at the moment).

Therefore when you get the chance, please let me know what should I do next abt this brightness issue. Thank you so much for your time & advice Toz!

---

### Post by Toz on 2015-03-17
> **bernovy said:**
> ```
sudo modprobe samsung_laptop
modprobe: ERROR: could not insert 'samsung_laptop': No such device
```

You should create a bug report against the linux kernel to get this addressed.

---

### Post by bernovy on 2015-03-17
> **Toz said:**
> You should create a bug report against the linux kernel to get this addressed.

Done:
[LIST]
[*][https://bugzilla.kernel.org/show_bug.cgi?id=95021](https://bugzilla.kernel.org/show_bug.cgi?id=95021) 
[*][https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1433410](https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1433410) 
[/LIST]

@Toz: Thanks for your help.

Edit: I updated to 3.19.1 kernel. My screen is now much brighter but the original problem is still here. I still can't control the screen brightness from Power Settings menu and the manual value update in intel_backlight makes no difference (however I do have different minimum values now):

```
cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.19.1-031901-generic root=/dev/mapper/ubuntu--vg-root ro acpi_osi=Linux quiet splash vt.handoff=7
```

```
/sys/class/backlight/intel_backlight
2928
4648
2928
```

modprobe result is the same on 3.19.1:
```
sudo modprobe samsung_laptop
modprobe: ERROR: could not insert 'samsung_laptop': No such device
```

---

