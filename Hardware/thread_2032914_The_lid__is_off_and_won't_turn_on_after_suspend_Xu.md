---
title: "The lid  is off and won't turn on after suspend Xubuntu 12.04"
date: 2012-07-24
forum: Hardware
---

### Post by denar50 on 2012-07-24
Hi all!

Well I've just moved to the OpenSource world and I really like it. I installed Xubuntu 12.04 on my laptop and everything worked fine except the suspend and the hibernate feature.
But I only care about the suspension mode! If I click in suspend it "suspends" normally but when I try to turn it on again the lid is totally off but the computer seems to be working. I triend ctrl + alt + (any F key) but nothing happens. Please help me because I'm really frustrated with it :( it's my personal laptop and I need it for working!

Thanks for reading! 
PD: I tried some solutions on the internet where a script needs to be created and executed but it didn't work.

---

### Post by jonnyboysmithy on 2012-07-24
What graphics driver are you using?

---

### Post by denar50 on 2012-07-25
Sorry I'm kinda newbie... how do I know that? I first installed Catalyst drivers and in my desperation also installed the fglrx drivers later, but I'd appreciate if you gave me any command to find out which graphic driver is loaded.

Thanks.

---

### Post by Toz on 2012-07-25
To get the graphics driver and info about your video card, enter the following command at a terminal prompt and post back the results:
```
sudo lspci -vnn | grep -A10 VGA
```

The make/model of your computer would also be helpful as well as the contents of the /var/log/pm-suspend.log file:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated

---

### Post by jonnyboysmithy on 2012-07-25
EDIT: Toz, you bet me too it! :) thanks for jumping in here. Too late I already posted. Perhaps delete this post?


To be honest,  I don't really know. I'm not very experienced.

Lets find out what driver you have loaded, and take it from there.
```
sudo lshw -c video | grep "driver"

```

---

### Post by denar50 on 2012-07-25
here's the output of :  sudo lspci -vnn | grep -A10 VGA
```

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320] [1002:9806] (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device [144d:c600]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
--
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64

00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
    Subsystem: Samsung Electronics Co Ltd Device [144d:c600]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb48000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0


```And here's the output of pastebinit /var/log/pm-suspend.log
 I used cat instead of pastebinit coz the latter didn't show any result.
```

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /etc/pm/sleep.d/00blank_screen_fix resume suspend:

/etc/pm/sleep.d/00blank_screen_fix resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Jul 20 15:35:09 COT 2012: FinisInitial commandline parameters: 
Fri Jul 20 18:21:23 COT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /etc/pm/sleep.d/00blank_screen_fix suspend suspend:

/etc/pm/sleep.d/00blank_screen_fix suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux denar 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
vesafb                 13516  1 
joydev                 17393  0 
parport_pc             32114  0 
bnep                   17830  2 
rfcomm                 38139  16 
ppdev                  12849  0 
lib80211_crypt_tkip    17240  0 
wl                   2646601  0 
binfmt_misc            17292  1 
psmouse                87213  0 
serio_raw              13027  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
k10temp                12990  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
sp5100_tco             13495  0 
i2c_piix4              13093  0 
btusb                  17912  2 
bluetooth             158438  23 bnep,rfcomm,btusb
snd_hda_codec_realtek   174055  1 
fglrx                2909855  65 
snd_hda_codec_hdmi     31775  1 
snd_hda_intel          32765  9 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19068  0 
snd                    62064  27 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
             total       used       free     shared    buffers     cached
Mem:       1799108    1667416     131692          0     623892     735508
-/+ buffers/cache:     308016    1491092
Swap:      4881404         96    4881308

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
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jul 20 18:21:28 COT 2012: performing suspend
Initial commandline parameters: 
Fri Jul 20 23:25:16 COT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /etc/pm/sleep.d/00blank_screen_fix suspend suspend:

/etc/pm/sleep.d/00blank_screen_fix suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux denar 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
vesafb                 13516  1 
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
lib80211_crypt_tkip    17240  0 
psmouse                87213  0 
serio_raw              13027  0 
snd_hda_codec_hdmi     31775  1 
wl                   2646601  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_hda_intel          32765  7 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
k10temp                12990  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
snd_hwdep              13276  1 snd_hda_codec
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
rfcomm                 38139  16 
bnep                   17830  2 
btusb                  17912  3 
parport_pc             32114  0 
snd_rawmidi            25424  1 snd_seq_midi
ppdev                  12849  0 
bluetooth             158438  25 rfcomm,bnep,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            17292  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
video                  19068  0 
fglrx                2909855  79 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    62064  24 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
             total       used       free     shared    buffers     cached
Mem:       1799240     960928     838312          0      76440     501180
-/+ buffers/cache:     383308    1415932
Swap:      4881404          0    4881404

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
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
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
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jul 20 23:25:20 COT 2012: performing suspend
Fri Jul 20 23:25:29 COT 2012: Awake.
Fri Jul 20 23:25:29 COT 2012: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resInitial commandline parameters: 
Fri Jul 20 23:31:07 COT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /etc/pm/sleep.d/00blank_screen_fix suspend suspend:

/etc/pm/sleep.d/00blank_screen_fix suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux denar 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
vesafb                 13516  1 
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_codec_hdmi     31775  1 
lib80211_crypt_tkip    17240  0 
snd_hda_intel          32765  7 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
wl                   2646601  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  0 
psmouse                87213  0 
ppdev                  12849  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  16 
serio_raw              13027  0 
k10temp                12990  0 
bnep                   17830  2 
snd_timer              28931  2 snd_seq,snd_pcm
fglrx                2909855  77 
uvcvideo               67203  0 
sp5100_tco             13495  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
videodev               86588  1 uvcvideo
i2c_piix4              13093  0 
snd                    62064  24 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_pcm,snd_seq_device,snd_timer
btusb                  17912  2 
binfmt_misc            17292  1 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
bluetooth             158438  23 rfcomm,bnep,btusb
video                  19068  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
             total       used       free     shared    buffers     cached
Mem:       1799240     748112    1051128          0      88592     335344
-/+ buffers/cache:     324176    1475064
Swap:      4881404          0    4881404

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
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
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
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jul 20 23:31:11 COT 2012: performing suspend
Fri Jul 20 23:31:18 COT 2012: Awake.
Fri Jul 20 23:31:18 COT 2012: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd resume suspend:
Initial commandline parameters: 
Fri Jul 20 23:42:13 COT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /etc/pm/sleep.d/00blank_screen_fix suspend suspend:

/etc/pm/sleep.d/00blank_screen_fix suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux denar 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
vesafb                 13516  1 
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_codec_hdmi     31775  1 
lib80211_crypt_tkip    17240  0 
snd_seq_midi           13132  0 
wl                   2646601  0 
snd_hda_intel          32765  7 
snd_rawmidi            25424  1 snd_seq_midi
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hwdep              13276  1 snd_hda_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                87213  0 
k10temp                12990  0 
serio_raw              13027  0 
rfcomm                 38139  16 
bnep                   17830  2 
uvcvideo               67203  0 
parport_pc             32114  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
btusb                  17912  2 
ppdev                  12849  0 
sp5100_tco             13495  0 
videodev               86588  1 uvcvideo
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28931  2 snd_seq,snd_pcm
i2c_piix4              13093  0 
bluetooth             158438  23 rfcomm,bnep,btusb
snd                    62064  24 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
binfmt_misc            17292  1 
fglrx                2909855  90 
soundcore              14635  1 snd
video                  19068  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
             total       used       free     shared    buffers     cached
Mem:       1799108    1003476     795632          0      58668     512420
-/+ buffers/cache:     432388    1366720
Swap:      4881404          0    4881404

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
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
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
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jul 20 23:42:17 COT 2012: performing suspend
Fri Jul 20 23:42:34 COT 2012: Awake.
Fri Jul 20 23:42:34 COT 2012: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd resume suspend:
Initial commandline parameters: 
Tue Jul 24 22:50:30 COT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /etc/pm/sleep.d/00blank_screen_fix suspend suspend:

/etc/pm/sleep.d/00blank_screen_fix suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux denar 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:46:35 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
rfcomm                 38139  16 
bnep                   17830  2 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13516  1 
snd_hda_codec_realtek   174134  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_intel          32765  7 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211_crypt_tkip    17240  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
wl                   2646601  0 
sp5100_tco             13495  0 
fglrx                2909855  62 
i2c_piix4              13093  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
samsung_laptop         13353  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd                    62064  24 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  17912  2 
bluetooth             158438  23 rfcomm,bnep,btusb
k10temp                12990  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  19068  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
mac_hid                13077  0 
psmouse                87213  0 
serio_raw              13027  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
             total       used       free     shared    buffers     cached
Mem:       1799240     514072    1285168          0      47700     225084
-/+ buffers/cache:     241288    1557952
Swap:      4881404          0    4881404

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
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jul 24 22:50:33 COT 2012: performing suspend
Tue Jul 24 22:50:42 COT 2012: Awake.
Tue Jul 24 22:50:42 COT 2012: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd resume suspend:
Initial commandline parameters: 
Wed Jul 25 04:12:46 COT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /etc/pm/sleep.d/00blank_screen_fix suspend suspend:

/etc/pm/sleep.d/00blank_screen_fix suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux denar 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:46:35 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
vesafb                 13516  1 
snd_hda_codec_realtek   174134  1 
snd_hda_codec_hdmi     31775  1 
parport_pc             32114  0 
snd_hda_intel          32765  7 
ppdev                  12849  0 
rfcomm                 38139  16 
bnep                   17830  2 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
fglrx                2909855  84 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  24 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
samsung_laptop         13353  0 
lib80211_crypt_tkip    17240  0 
wl                   2646601  0 
psmouse                87213  0 
serio_raw              13027  0 
sp5100_tco             13495  0 
uvcvideo               67203  0 
mac_hid                13077  0 
videodev               86588  1 uvcvideo
soundcore              14635  1 snd
btusb                  17912  2 
video                  19068  0 
bluetooth             158438  23 rfcomm,bnep,btusb
i2c_piix4              13093  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
k10temp                12990  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
r8169                  56321  0 
             total       used       free     shared    buffers     cached
Mem:       1799108     884712     914396          0      54940     423580
-/+ buffers/cache:     406192    1392916
Swap:      4881404          0    4881404

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
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Jul 25 04:12:50 COT 2012: performing suspend
Wed Jul 25 04:45:09 COT 2012: Awake.
Wed Jul 25 04:45:09 COT 2012: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd resume suspend:

```

PD: It's not solved yet, but shall I mark it as solved?

---

### Post by Toz on 2012-07-25
Ok. Lets get some more information. 

1. The first command didn't yield enough information, so can you try:
```
sudo lspci -vnn | grep -A15 VGA
```

2. What is the make/model of your laptop?

3. Can you post the contents of /etc/pm/sleep.d/20_custom-ehci_hcd and the results of:
```
ls /sys/bus/pci/drivers/ehci_hcd/
```

4. Can you post back the contents of /etc/pm/sleep.d/00blank_screen_fix as well?

5. What happens if you try to suspend without this file (/etc/pm/sleep.d/20_custom-ehci_hcd)?

6. The "mark as solved" is in my signature as a reminder to posters to mark solved threads as solved. So no need to mark this thread solved until is actually solved. :)

---

### Post by denar50 on 2012-07-25
1. This is the output of 
sudo lspci -vnn | grep -A15 VGA```

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320] [1002:9806] (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device [144d:c600]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310] [1002:1314]
    Subsystem: Samsung Electronics Co Ltd Device [144d:c600]
--
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64

00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
    Subsystem: Samsung Electronics Co Ltd Device [144d:c600]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb48000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:15.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 0000000080c00000-0000000080dfffff
    Capabilities: [50] Power Management version 3


```2.  My laptop is a SAMSUNG NP305U1A-A05CO

3.  the contents of /etc/pm/sleep.d/20_custom-ehci_hcd is
```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
TMPLIST=/tmp/ehci-dev-list

case "${1}" in
        hibernate|suspend)

        ;;
        resume|thaw)

     chvt 1
     chvt 7
        ;;
esac


```Here I wanna tell you that this is the second time I edit that file since I tried the other solution in one of these forums (the one with more instructions than this one) and none of them worked.

the Output of 
ls /sys/bus/pci/drivers/ehci_hcd/ is:

```

0000:00:12.2  0000:00:13.2  bind  module  new_id  remove_id  uevent  unbind


```4. The output of /etc/pm/sleep.d/00blank_screen_fix
```

#!/bin/sh
#
case "$1" in
   suspend)
   ;;
   resume)
      sleep 5
      vbetool dpms off
      vbetool dpms on
   ;;
   *) exit $NA
   ;;


```

5. Regarding suspending without that file, nothing happens (apparently) still the same problem the lid completely off.

---

### Post by Toz on 2012-07-25
You stated earlier that you installed catalyst drivers and then fglrx drivers. How did you do this?

If you go the Additional Drivers application, are any of them shown as activated? (See: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1025616]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1025616"))

---

### Post by denar50 on 2012-07-25
I installed the Catalyst drivers first and installed the Fglrx drivers later using the "additional drivers" option where you can "activate the driver".

---

### Post by Toz on 2012-07-25
Perhaps a purge and reinstall of the fglrx drivers would help. See this link for more information: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Using_the_Ubuntu_repositories_.28alternate_command_line_method.2C_including_hardware_acceleration.29]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Using_the_Ubuntu_repositories_.28alternate_command_line_method.2C_including_hardware_acceleration.29").

I would also recommend delete the two files that you've created in /etc/pm/sleep.d to make sure they're not interfering.

---

### Post by denar50 on 2012-07-26
Hi there. Well first of all thanks for your attention.
I proved unistalling the fglrx drivers I installed using the "additional drivers" option. I rebooted and I could suspend my computer successfully but the graphics were not good and I didn't have the catalyst center anymore. So I proved Installing the Catalyst driver (from the webpage version 12.6) and also the Fglrx drivers from additional drivers and both drivers have the sleep issue. :( without any of them the computer just sleeps fine and wakes fine. Sigh :(... what's next ?

---

### Post by Toz on 2012-07-26
At least we've narrowed it down to a problem with the proprietary drivers.

There appears to be a whole thread here devoted to issues with the 6320. See: [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911").

It might be worthwhile to file a bug report.

---

### Post by denar50 on 2012-07-29
I've gone back to Xubuntu 11.04 and will stay here until another distro of Xubuntu comes out. It works fine on Xubuntu 11.04, I installed the Catalyst drivers and everything works fine. Hopefully these bugs can be solved but I just gave it up! hhehehe

Thank you all for your help.

---

