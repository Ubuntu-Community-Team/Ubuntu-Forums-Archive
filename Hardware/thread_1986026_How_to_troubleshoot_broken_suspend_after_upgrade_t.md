---
title: "How to troubleshoot broken suspend after upgrade to 12.04"
date: 2012-05-24
forum: Hardware
---

### Post by moteprime on 2012-05-24
Hi.
I got Ubuntu 12.04 Desktop AMD64 on Ideapad s205 AMD E-450.
After upgrading to 12.04 suspend stopped working, it just locks up my laptop and I have to unplug it and remove the battery to get it back up and running.
The newest kernels don't fix it, and I reported a bug on launchpad that haven't caught anybodies attention.
AMD Catalyst Centre causes the bug when I installed it on 11.10, but after upgrading to 12.04 it also locks up when using the Radeon driver. 


What can I do to get it to work, it a bother to have to shut it down all the time.
Thanks.

---

### Post by moteprime on 2012-05-24
Here are my pm-suspend.log


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux mote-Ideapad-S205 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
vesafb                 13844  1 
joydev                 17693  0 
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
acer_wmi               28418  0 
psmouse                87692  0 
serio_raw              13211  0 
rt3090sta             961553  0 
uvcvideo               72627  0 
sp5100_tco             13791  0 
videodev               98259  1 uvcvideo
snd_hda_codec_conexant    62128  1 
k10temp                13166  0 
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec_hdmi     32474  1 
ext2                   73795  1 
i2c_piix4              13301  0 
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
ideapad_laptop         18234  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
fglrx                3263966  118 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18288  2 
bluetooth             180104  23 rfcomm,bnep,btusb
snd                    78855  18 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19596  0 
wmi                    19256  1 acer_wmi
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       3639372    1616600    2022772          0      68200     569352
-/+ buffers/cache:     979048    2660324
Swap:      2047996          0    2047996

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
Thu May 24 11:07:06 CEST 2012: performing suspend

---

### Post by moteprime on 2012-06-11
Nobody ?  :-(

---

### Post by sjs2 on 2012-12-01
In my Novatech laptop (actually a rebadged Clevo W76K) hibernate/suspend stopped working sometime during 12.04. I tried all the fixes I could find on the web, but the only thing that worked was to downgrade the kernel to the most recent version that I knew worked (3.0.0-28 ). This seems to be OK on both 12.04 and 12.10, without any problems in functionality, as far as I can see.

On the other hand my daughter has a Dell Inspiron 1546 which hibernates but just won't suspend whatever I do.

---

