---
title: "suspend bug - which package to file under?"
date: 2009-11-29
forum: Hardware
---

### Post by tr333 on 2009-11-29
I have a suspend-related bug on my laptop.  When the laptop is in sleep/suspend state with the screen/lid closed and I open the screen, the laptop comes out of suspend and shows the password box for about 1 second before going back to sleep.  Pressing the power button on the laptop after its back in sleep mode brings it back out of sleep as normal with no problems.

[https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage) lists three different packages for suspend-related bugs but I'm not sure which is the appropriate bug to file this report under.  gnome-power-manager, pm-utils, or linux.

---

### Post by FrankNBeans on 2009-12-01
I'm having the exact same problem on my Sony. It didn't start happening until the latest Kernel update. Sometimes it also just locks up when coming out of sleep mode.

---

### Post by FrankNBeans on 2009-12-01
Here is what I get in the pm-suspend.log you can see it even waking up and then going back into suspend.

Tue Dec  1 19:58:47 EST 2009: Awake.
Tue Dec  1 19:58:47 EST 2009: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend: method return sender=:1.81 -> dest=:1.80 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Tue Dec  1 19:58:49 EST 2009: Finished.
Initial commandline parameters: 
Tue Dec  1 19:58:50 EST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-vbe-post 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux michael-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetadp             78344  0 
vboxnetflt             84840  0 
vboxdrv               121160  1 vboxnetflt
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  1 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
arc4                    1660  2 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ecb                     2524  2 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
iptable_filter          3100  0 
iwlagn                109052  0 
joydev                 10272  0 
pcmcia                 36808  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
tifm_7xx1               5372  0 
iwlcore               112508  1 iwlagn
psmouse                56500  0 
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
sony_laptop            31972  0 
uvcvideo               59080  0 
snd                    59204  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
x_tables               16544  1 ip_tables
led_class               4096  1 iwlcore
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
btusb                  11856  2 
tifm_core               7832  1 tifm_7xx1
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
nvidia               9586440  43 
mac80211              181236  2 iwlagn,iwlcore
cfg80211               93052  3 iwlagn,iwlcore,mac80211
usbhid                 38208  0 
ohci1394               29900  0 
video                  19380  0 
output                  2780  1 video
ieee1394               86596  1 ohci1394
sky2                   46560  0 
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp
             total       used       free     shared    buffers     cached
Mem:       2060580     552564    1508016          0      46548     262324
-/+ buffers/cache:     243692    1816888
Swap:      6032368          0    6032368
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Tue Dec  1 19:58:53 EST 2009: performing suspend
Tue Dec  1 19:59:04 EST 2009: Awake.
Tue Dec  1 19:59:04 EST 2009: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend: method return sender=:1.81 -> dest=:1.93 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Tue Dec  1 19:59:05 EST 2009: Finished.

---

### Post by jdunn on 2009-12-01
Heh.  I get a different bug.  When I open the laptop lid, the computer comes out of suspend but the brightness level of the LCD screen is at the lowest level.  I have to change the brightness level manually every time I come out of suspend.

---

### Post by tr333 on 2009-12-03
I'll just file the bug under "linux" and let the bug triagers decide if it's incorrect.

---

### Post by tr333 on 2010-01-30
FYI:  [https://bugs.launchpad.net/bugs/3626](https://bugs.launchpad.net/bugs/3626)

---

