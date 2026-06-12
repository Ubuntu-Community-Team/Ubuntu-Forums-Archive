---
title: "My jaunty won't suspend/ Weird problem"
date: 2009-06-13
forum: Hardware
---

### Post by lapalorky on 2009-06-13
I can't get my Laptop to suspend. Hibernate doesn't work either but that comes later. The weird thing is that everything looks fine to me in the log file (pm-suspend.log), that is I get 'Success' on everything. Just at the point where the machine is supposed to suspend, it resumes immediately!

Here my pm-suspend.log (rather large, so I marked the essentially part in bold red):
```
Initial commandline parameters: --quirk-vbemode-restore
--quirk-vbe-post
Sat Jun 13 13:03:12 CEST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux elaja 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
ecb                    10752  1 
nfs                   266344  1 
lockd                  74156  1 nfs
nfs_acl                11136  1 nfs
sunrpc                195424  10 nfs,lockd,nfs_acl
binfmt_misc            16776  1 
lp                     17156  0 
radeon                342816  2 
drm                    96296  3 radeon
vmnet                  47812  0 
ppdev                  15620  0 
parport_pc             40100  0 
parport                42220  3 lp,ppdev,parport_pc
vmblock                20900  3 
vmci                   58324  0 
vmmon                  76912  0 
autofs4                32516  1 
input_polldev          11912  0 
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
pcmcia                 44748  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
joydev                 18368  0 
i2c_piix4              18448  0 
gspca_m5602            78988  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
k8temp                 12416  0 
shpchp                 40212  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
gspca_main             29952  1 gspca_m5602
pcspkr                 10496  0 
videodev               41600  1 gspca_main
acer_wmi               24260  0 
led_class              12036  1 acer_wmi
psmouse                61972  0 
video                  25360  0 
output                 11008  1 video
serio_raw              13316  0 
v4l1_compat            21764  1 videodev
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
vesafb                 13828  1 
fbcon                  46112  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:        895864     763728     132136          0      24712     191396
-/+ buffers/cache:     547620     348244
Swap:      1951888      70096    1881792
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/usr/lib/pm-utils/sleep.d/45iwlist suspend suspend: /sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt suspend suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: not applicable.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
[B][COLOR=Red]Sat Jun 13 13:03:16 CEST 2009: performing suspend
Sat Jun 13 13:03:37 CEST 2009: Awake.[/COLOR][/B]  *[0.21 seconds after 'performing suspend' the machine is 'Awake']*
Sat Jun 13 13:03:37 CEST 2009: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/etc/pm/sleep.d/99laptop-mode resume suspend: Laptop mode disabled, not active
success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: /usr/lib/pm-utils/sleep.d/95hdparm-apm: 50: get_power_status: not found

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
success.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt resume suspend: success.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/45iwlist resume suspend: /sbin/iwlist
success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Sat Jun 13 13:03:41 CEST 2009: Finished.
```Glad for any hints on this. I want this to work.

---

### Post by lapalorky on 2009-06-13
The issue is solved. I found out that a screenlet was causing the problem. More specifically it was the 'sysmonitor' screenlet.

---

