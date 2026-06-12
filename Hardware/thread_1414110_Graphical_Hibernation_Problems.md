---
title: "Graphical Hibernation Problems"
date: 2010-02-23
forum: Hardware
---

### Post by naz37 on 2010-02-23
Have UNR 9.10 on a eeepc 1000.

I am having graphical glitches every time it enters and exits hibernation. 

*Entering Hibernating;*
The screen flickers black and then returns to the desktop, except everything has frozen. It does successfully enter hibernation but it would appear for the ~30s its entering hibernation that it has just hung, the only indication it is active is the flashing HD LED on the front of the netbook.

*Resuming from Hibernation;*
When transitioning from the loading screen to the desktop, the screen becomes black with scrambled horizontal lines for several seconds. After this Ubuntu resumes normally and everything works. Visually this looks really bad.

These issues would seem to be related to the intel graphics driver and/or KMS

Anyone got any ideas for fixing or further troubleshooting this?

---

### Post by naz37 on 2010-02-23
*/var/log/pm-suspend.log*
> Initial commandline parameters: 
Tue Feb 23 16:03:06 GMT 2010: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux abaigeal-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
iptable_filter          3100  0 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
btusb                  11856  2 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
psmouse                56500  0 
serio_raw               5280  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
rt2860sta             522456  1 
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
eeepc_laptop           13936  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
atl1e                  31824  0 
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
             total       used       free     shared    buffers     cached
Mem:       1018080     418792     599288          0      59744     192468
-/+ buffers/cache:     166580     851500
Swap:      1502036          0    1502036
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Tue Feb 23 16:03:08 GMT 2010: performing hibernate
Tue Feb 23 16:04:36 GMT 2010: Awake.
Tue Feb 23 16:04:36 GMT 2010: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: Returned exit code 1.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.

Note;
> /usr/lib/pm-utils/sleep.d/99video thaw hibernate: Returned exit code 1.

/usr/lib/pm-utils/sleep.d/99video seems to be throwing a error when leaving hibernation. Any ideas?

---

