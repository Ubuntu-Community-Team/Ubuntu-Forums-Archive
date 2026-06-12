---
title: "crash on suspend"
date: 2010-04-25
forum: Hardware
---

### Post by marbertone on 2010-04-25
Hello,
Ubuntu sometimes crashes on suspend. It happens frequently when I am at my parents'house, and I use a wired connection. In my modest opinion it could be a internet-related issue. I report two suspend logs: the first one in a successful one, while the second is a log related to the crash. This kind of system crash is kernel panic: everything is locked, caps lock and num lock blinking and not even REISUB works.
Please tell me what to do, it is something that disappoints me a bit, and tempts me to do a clean install of Lucid (even if I think I will encounter for sure problems w/ webcam and internet key, which I solved after two weeks on Karmic.
Thank you guys, tell me if you need some other logs.

Success suspend:
```

Fri Apr 23 11:26:01 CEST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-s3-bios --quirk-s3-mode 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux berto 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
usbhid                 38208  0 
pcmcia                 36808  0 
btusb                  11856  2 
arc4                    1660  2 
ecb                     2524  2 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
joydev                 10240  0 
tpm_infineon            8200  0 
tpm                    15680  1 tpm_infineon
tpm_bios                6268  1 tpm
sony_laptop            31972  0 
snd_hda_codec_idt      59876  1 
iwl3945                77372  0 
iwlcore               112796  1 iwl3945
mac80211              181140  2 iwl3945,iwlcore
led_class               4096  2 iwl3945,iwlcore
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_7xx1               5372  0 
tifm_core               7832  1 tifm_7xx1
psmouse                56500  0 
serio_raw               5280  0 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
cfg80211               93052  3 iwl3945,iwlcore,mac80211
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
sky2                   46560  0 
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
             total       used       free     shared    buffers     cached
Mem:       2052344    1237996     814348          0      80384     714404
-/+ buffers/cache:     443208    1609136
Swap:      6008268          0    6008268
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55wicd suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Fri Apr 23 11:26:03 CEST 2010: performing suspend
Fri Apr 23 12:09:33 CEST 2010: Awake.
Fri Apr 23 12:09:33 CEST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: Returned exit code 1.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55wicd resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.

```

Failed suspend w/ kernel panic:

```

Initial commandline parameters: 
Sun Apr 25 21:25:14 CEST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-s3-bios --quirk-s3-mode 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux berto 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
xt_TCPMSS               3868  1 
xt_tcpmss               1852  1 
xt_tcpudp               2780  1 
iptable_mangle          3452  1 
pppoe                  11076  2 
pppox                   3016  1 pppoe
binfmt_misc             8356  1 
ppdev                   6688  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
joydev                 10240  0 
bridge                 47952  0 
stp                     2272  1 bridge
arc4                    1660  2 
bnep                   12060  2 
ecb                     2524  2 
pcmcia                 36808  0 
btusb                  11856  2 
snd_hda_codec_idt      59876  1 
iwl3945                77372  0 
iwlcore               112796  1 iwl3945
mac80211              181140  2 iwl3945,iwlcore
led_class               4096  2 iwl3945,iwlcore
iptable_filter          3100  0 
ip_tables              11692  

```

you see, "ip_tables" is the last called command. It looks like IT creates problems.

---

### Post by marbertone on 2010-04-25
I did another suspend without being connected to the internet: same thing (kernel panic). In both the cases my usb mouse (trust mouse) was connected. I remind that also Vista gave me some problems when suspending w/ the mouse connected, even if it wasn't kernel panic. I deduce it is because of the usb mouse.
Mario Alberto

---

### Post by marbertone on 2010-04-26
Guys, 
it happened also on shutdown...
I read /var/log/messages but I didn't find anything 'suspect'... i attach:

```

Apr 26 17:28:36 berto pppd[2433]: Connected to 00:1d:a2:86:71:3c via interface eth0
Apr 26 17:28:36 berto pppd[2433]: Using interface ppp0
Apr 26 17:28:36 berto pppd[2433]: Connect: ppp0 <--> eth0
Apr 26 17:28:36 berto pppd[2433]: PAP authentication succeeded
Apr 26 17:28:36 berto pppd[2433]: peer from calling number 00:1D:A2:86:71:3C authorized
Apr 26 17:28:36 berto pppd[2433]: replacing old default route to eth0 [192.168.1.1]
Apr 26 17:28:36 berto pppd[2433]: local  IP address xx.xx.xx.xx
Apr 26 17:28:36 berto pppd[2433]: remote IP address xx.xx.xx.xx
Apr 26 17:28:36 berto pppd[2433]: primary   DNS address xx.xx.xx.xx
Apr 26 17:28:36 berto pppd[2433]: secondary DNS address xx.xx.xx.xx
Apr 26 17:28:48 berto kernel: [   71.560425] CE: hpet increasing min_delta_ns to 15000 nsec
Apr 26 17:29:54 berto kernel: [  136.854147] CE: hpet increasing min_delta_ns to 22500 nsec
Apr 26 17:35:14 berto kernel: [  456.924107] usb 2-1: new high speed USB device using ehci_hcd and address 4
Apr 26 17:35:14 berto kernel: [  457.057200] usb 2-1: configuration #1 chosen from 1 choice
Apr 26 17:35:14 berto kernel: [  457.205459] Initializing USB Mass Storage driver...
Apr 26 17:35:14 berto kernel: [  457.213191] scsi4 : SCSI emulation for USB Mass Storage devices
Apr 26 17:35:14 berto kernel: [  457.213470] usbcore: registered new interface driver usb-storage
Apr 26 17:35:14 berto kernel: [  457.213478] USB Mass Storage support registered.
Apr 26 17:35:19 berto kernel: [  462.220935] scsi 4:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
Apr 26 17:35:19 berto kernel: [  462.221773] sd 4:0:0:0: Attached scsi generic sg2 type 0
Apr 26 17:35:19 berto kernel: [  462.237159] sd 4:0:0:0: [sdb] 2068992 512-byte logical blocks: (1.05 GB/1010 MiB)
Apr 26 17:35:19 berto kernel: [  462.237771] sd 4:0:0:0: [sdb] Write Protect is off
Apr 26 17:35:19 berto kernel: [  462.239517]  sdb: sdb1
Apr 26 17:35:19 berto kernel: [  462.266910] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Apr 26 17:35:31 berto kernel: [  473.922006] usb 2-1: USB disconnect, address 4
Apr 26 17:35:51 berto kernel: Kernel logging (proc) stopped.


```

---

### Post by kubz on 2010-05-14
Hi,
 I'm facing a similar problem with fresh Ubuntu 10.04 on IBM R50 laptop. Hibernation works in 9 of 10 cases. I also thought it is peripheral related, but plugging/unplugging network cable or USB mouse do not reproduce the problem. The /var/log/messages ends with several errors and the "Kernel logging (proc) stopped".

 well, IMHO the best way is to find your problem among reported bugs here: [http://bugs.launchpad.net/](http://bugs.launchpad.net/) AND click the "affects me icon", so it draws devels attention.

 From similar bugs I read there about, fresh installs are affected too. So I would not do that. Try to figure out what programs do you run and what reproduces the error. I also have problems with sound server "pulseaudio" and consider uninstalling it.

---

### Post by marbertone on 2010-05-25
It didn't really happen anymore... I mark it as "solved" !
See you guys!
Mario Alberto:popcorn:

---

