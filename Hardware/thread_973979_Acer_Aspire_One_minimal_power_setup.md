---
title: "Acer Aspire One minimal power setup"
date: 2008-11-07
forum: Hardware
---

### Post by FunEye on 2008-11-07
Hi, I'm trying to get my Acer Aspire One running 8.10 using as little power as possible. My main goal is to have as few modules and services running, while still being able to play movies in VLC from one of the card readers. Wifi, USB and other devices will not be needed.

My experience with Linux isn't all that great, although I'm picking up a lot of tips & tricks reading these forums. 

I've already applied most of the tweaks mentioned in [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) and [https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L), as well as some other tricks I've found.

By disabling networking, reducing brightness and slashing a few modules(like ehci_hcd, uhci_hcd etc.) I've managed to get an IDLE load of about 7.5W-8.0W, and about 9.5W running VLC. All values obtained from Powertop.

Any thoughts on how to improve this, which modules/services to disable, or am I about to hit a brick wall?
A little quirk I'm curious about. Examining the Power History graph in Gnome Power Manager shows a slight increase in power usage over time. I typically get a steady rise from 9W to 10-11W over a period of 3-4 hours. Any explanation to this?

Attaching print outs of loaded modules, service and running processes.

Modules:
```
Module                  Size  Used by
cifs                  254964  0 
i915                   38144  2 
drm                    86056  3 i915
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
af_packet              25728  0 
binfmt_misc            16904  1 
autofs4                27652  1 
acpi_cpufreq           15500  1 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
cpufreq_userspace      11396  0 
container              11520  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
fuse                   60828  0 
joydev                 18368  0 
mmc_block              17924  2 
acer_wmi               18880  0 
led_class              12164  1 acer_wmi
compat_ioctl32          9344  0 
videodev               41344  0 
v4l1_compat            22404  1 videodev
evdev                  17696  10 
video                  25104  0 
snd_hda_intel         381488  3 
output                 11008  1 video
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
wmi                    14504  1 acer_wmi
psmouse                45200  0 
serio_raw              13444  0 
snd_seq_dummy          10884  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  2 mmc_block,sdhci
snd_seq_oss            38528  0 
ac                     12292  0 
button                 14224  0 
battery                18436  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
pcspkr                 10624  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext2                   72456  1 
mbcache                16004  1 ext2
sd_mod                 42264  2 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
ata_piix               24580  1 
pata_acpi              12160  0 
libata                177312  3 ata_generic,ata_piix,pata_acpi
scsi_mod              155212  3 sd_mod,sg,libata
dock                   16656  1 libata
r8169                  35972  0 
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Services:
```
 * acpid is running.
Configured Mount Points:
------------------------
/usr/sbin/automount --timeout=300 --ghost /mbshares file /etc/auto.mbshares 

Active Mount Points:
--------------------
/usr/sbin/automount --pid-file=/var/run/autofs/_mbshares.pid --timeout=300 --ghost /mbshares file /etc/auto.mbshares
Avahi mDNS/DNS-SD Daemon is running
Usage: /etc/init.d/console-setup {start|reload|restart|force-reload|stop}
Status of Common Unix Printing System: cupsd is running.
 * dbus is running.
 * gdm is running.
 * hald is running.
 * Usage: hwclock.sh {start|stop|reload|force-reload|show}
 *        start sets kernel (system) clock from hardware (RTC) clock
 *        stop and reload set hardware (RTC) clock from kernel (system) clock
 * Usage: hwclock.sh {start|stop|reload|force-reload|show}
 *        start sets kernel (system) clock from hardware (RTC) clock
 *        stop and reload set hardware (RTC) clock from kernel (system) clock
Usage: /etc/init.d/keyboard-setup {start|reload|restart|force-reload|stop}
 * klogd is not running.
Usage: /etc/init.d/linux-restricted-modules-common {start}
Usage: /etc/init.d/loopback {start|stop|restart|force-reload}
 * Loading kernel modules...
 * Loading manual drivers...
   ...done.
Usage: /etc/init.d/networking {start|stop|restart|force-reload}
all daemons running
 * No PCMCIA bridge module specified
 * portmap is running.
Usage: /etc/init.d/readahead {start|stop|restart|force-reload}
Usage: /etc/init.d/readahead {start|stop|restart|force-reload}
 * syslogd is not running.
Usage: /etc/init.d/udev {start|stop|restart|reload|force-reload}
Usage: /etc/init.d/udev {start|stop|restart|reload|force-reload}
 * winbind is running.
```

Processes:
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   3056  1888 ?        Ss   10:00   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   10:00   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   10:00   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   10:00   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   10:00   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   10:00   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   10:00   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   10:00   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   10:00   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   10:00   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   10:00   0:00 [khelper]
root        51  0.0  0.0      0     0 ?        S<   10:00   0:00 [kintegrityd/0]
root        52  0.0  0.0      0     0 ?        S<   10:00   0:00 [kintegrityd/1]
root        54  0.0  0.0      0     0 ?        S<   10:00   0:00 [kblockd/0]
root        55  0.0  0.0      0     0 ?        S<   10:00   0:00 [kblockd/1]
root        57  0.0  0.0      0     0 ?        S<   10:00   0:00 [kacpid]
root        58  0.0  0.0      0     0 ?        S<   10:00   0:00 [kacpi_notify]
root       136  0.0  0.0      0     0 ?        S<   10:00   0:00 [cqueue]
root       140  0.0  0.0      0     0 ?        S<   10:00   0:00 [kseriod]
root       185  0.0  0.0      0     0 ?        S    10:00   0:00 [pdflush]
root       187  0.0  0.0      0     0 ?        S<   10:00   0:00 [kswapd0]
root       229  0.0  0.0      0     0 ?        S<   10:00   0:00 [aio/0]
root       230  0.0  0.0      0     0 ?        S<   10:00   0:00 [aio/1]
root      1427  0.0  0.0      0     0 ?        S<   10:00   0:00 [ata/0]
root      1428  0.0  0.0      0     0 ?        S<   10:00   0:00 [ata/1]
root      1429  0.0  0.0      0     0 ?        S<   10:00   0:00 [ata_aux]
root      2136  0.0  0.0      0     0 ?        S<   10:00   0:00 [scsi_eh_0]
root      2137  0.0  0.0      0     0 ?        S<   10:00   0:00 [scsi_eh_1]
root      2550  0.0  0.0   2520  1012 ?        S<s  10:00   0:01 /sbin/udevd --daemon
root      2935  0.0  0.0      0     0 ?        S<   10:00   0:00 [kmmcd]
root      3011  0.0  0.0      0     0 ?        S<   10:00   0:00 [kpsmoused]
root      4011  0.0  0.0      0     0 ?        S<   10:00   0:00 [mmcqd]
daemon    4902  0.0  0.0   1912   524 ?        Ss   10:00   0:00 /sbin/portmap
statd     4931  0.0  0.0   1976   748 ?        Ss   10:00   0:00 /sbin/rpc.statd
root      5054  0.0  0.0   1780   540 tty4     Ss+  10:00   0:00 /sbin/getty 38400 tty4
root      5056  0.0  0.0   1780   536 tty5     Ss+  10:00   0:00 /sbin/getty 38400 tty5
root      5062  0.0  0.0   1780   540 tty2     Ss+  10:00   0:00 /sbin/getty 38400 tty2
root      5063  0.0  0.0   1780   536 tty3     Ss+  10:00   0:00 /sbin/getty 38400 tty3
root      5064  0.0  0.0   1780   536 tty6     Ss+  10:00   0:00 /sbin/getty 38400 tty6
root      5264  0.0  0.0      0     0 ?        S<   10:00   0:00 [kondemand/0]
root      5265  0.0  0.0      0     0 ?        S<   10:00   0:00 [kondemand/1]
root      5417  0.0  0.1   2308  1220 ?        Ss   10:00   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
106       5452  0.0  0.1   2984  1336 ?        Ss   10:00   0:03 /bin/dbus-daemon --system
avahi     5487  0.0  0.1   2888  1444 ?        Ss   10:00   0:00 avahi-daemon: running [jo-laptop.local]
avahi     5488  0.0  0.0   2888   500 ?        Ss   10:00   0:00 avahi-daemon: chroot helper
root      5590  0.0  0.0   1948   744 ?        Ss   10:00   0:00 /usr/sbin/automount --pid-file=/var/run/autofs/_mbshares.pid --timeout=300 --ghost /mbshares file /etc/auto.mbshares
mail      5736  0.0  0.0   2952   564 ?        S    10:00   0:00 /usr/sbin/nullmailer-send -d
root      5781  0.0  0.2   6432  2372 ?        Ss   10:00   0:00 /usr/sbin/cupsd
root      5789  0.0  0.1   9216  1400 ?        Ss   10:00   0:00 /usr/sbin/winbindd
root      5800  0.0  0.1   9216  1212 ?        S    10:00   0:00 /usr/sbin/winbindd
109       5820  0.0  0.4   6300  4244 ?        Ss   10:00   0:03 /usr/sbin/hald
root      5826  0.0  0.2  18504  2612 ?        Ssl  10:00   0:00 /usr/sbin/console-kit-daemon
root      5828  0.0  0.1   3364  1108 ?        S    10:00   0:00 hald-runner
root      5932  0.0  0.1   3464  1240 ?        S    10:00   0:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event8 /dev/input/event4 /dev/input/event5 /dev/input/event6 /dev/input/event1
root      5969  0.0  0.1   3448  1040 ?        S    10:00   0:00 /usr/lib/hal/hald-addon-cpufreq
109       5970  0.0  0.0   2296   900 ?        S    10:00   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      6058  0.0  0.2  14752  2600 ?        Ssl  10:00   0:00 /usr/sbin/NetworkManager
root      6085  0.0  0.1   4240  1880 ?        S    10:00   0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      6089  0.0  0.2   6772  2984 ?        S    10:00   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      6120  0.0  0.1   4336  1152 ?        Ss   10:00   0:00 /usr/bin/system-tools-backends
root      6180  0.0  0.1  14240  1772 ?        Ss   10:00   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      6627  0.0  0.0   1780   532 tty1     Ss+  10:01   0:00 /sbin/getty 38400 tty1
root      6811  0.0  0.3  14780  3224 ?        S    10:04   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      6815 13.8  1.6  23796 16532 tty7     Rs+  10:04  19:22 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
jo        6840  0.0  0.1  14700  2024 ?        S    10:04   0:00 /usr/bin/gnome-keyring-daemon -d --login
jo        6850  0.0  0.5  24760  5708 ?        Ssl  10:04   0:00 x-session-manager
jo        6925  0.0  0.0   3124   672 ?        S    10:04   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
jo        6926  0.0  0.1   2904  1068 ?        Ss   10:04   0:01 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
jo        6929 16.8  0.4  28948  4168 ?        Ssl  10:04  23:27 /usr/bin/pulseaudio -D --log-target=syslog
jo        6932  0.0  0.2   7528  2556 ?        S    10:04   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
jo        6934  0.0  0.4   7548  4536 ?        S    10:04   0:02 /usr/lib/libgconf2-4/gconfd-2
jo        6940  0.0  0.6  17708  6320 ?        Ss   10:04   0:00 /usr/bin/seahorse-agent --execute x-session-manager
jo        6942  0.0  0.3  13916  3648 ?        S    10:04   0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
jo        6948  0.0  0.2   5556  2164 ?        S    10:04   0:00 /usr/lib/gvfs/gvfsd
jo        6951  0.0  1.2  43680 13220 ?        Ssl  10:04   0:02 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
jo        6952  0.0  1.2  21652 13032 ?        S    10:04   0:03 metacity
jo        6959  0.1  2.3  47492 23920 ?        S    10:04   0:11 gnome-panel
jo        6962  0.0  1.9  50484 20124 ?        S    10:04   0:03 nautilus --no-desktop --browser
jo        6964  0.0  0.3  41620  3416 ?        Ssl  10:04   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
jo        6969  0.0  1.4  24300 14652 ?        S    10:04   0:03 nm-applet --sm-disable
jo        6972  0.0  1.3  25768 14016 ?        S    10:04   0:01 update-notifier
jo        6973  0.0  0.3  12592  3724 ?        S    10:04   0:00 devilspie /etc/devilspie.cfg
jo        6987  0.0  1.4  29516 15188 ?        Ss   10:04   0:06 gnome-power-manager
jo        6993  0.2  0.3  21212  3280 ?        Ss   10:04   0:21 gnome-screensaver
jo        6995  0.0  0.2   5940  2916 ?        S    10:04   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
jo        6998  0.0  0.2   5564  2220 ?        S    10:04   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
jo        7012  0.0  0.2  22192  2668 ?        S    10:05   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.7 /org/gtk/gvfs/exec_spaw/0
jo        7028  0.0  1.1  24564 12108 ?        S    10:05   0:04 /usr/lib/gnome-applets/cpufreq-applet --oaf-activate-iid=OAFIID:GNOME_CPUFreqApplet_Factory --oaf-ior-fd=20
jo        7030  0.0  1.6  46084 16804 ?        Sl   10:05   0:01 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=26
root      7074  0.0  0.0   3124   680 ?        S    10:05   0:00 dbus-launch --autolaunch 65d89330209cb2790ad78395490b0f24 --binary-syntax --close-stderr
root      7075  0.0  0.0   2640   760 ?        Ss   10:05   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root      7085  0.0  0.0      0     0 ?        S<   10:05   0:00 [cifsoplockd]
root      7088  0.0  0.0      0     0 ?        S<   10:05   0:00 [cifsdnotifyd]
jo        7378  0.0  1.4  24544 14512 ?        S    10:22   0:01 /usr/lib/notification-daemon/notification-daemon
jo        7600  0.0  2.1  91360 22304 ?        Sl   10:50   0:02 gnome-terminal
jo        7603  0.0  0.0   2912   760 ?        S    10:50   0:00 gnome-pty-helper
jo        7604  0.0  0.2   4784  2128 pts/0    Ss   10:50   0:00 bash
root      8123  0.0  0.0      0     0 ?        S    12:23   0:00 [pdflush]
jo        8137  0.0  0.0   2744  1012 pts/0    R+   12:24   0:00 ps aux
```

Any help would be greatly appreciated! :)

---

### Post by thor2002ro on 2008-11-08
try power top should tell you what programs/processes are using more power

---

### Post by FunEye on 2008-11-10
Here are printouts of Powertop collecting data over 10 minutes.

Idle:
```
PowerTOP 1.10    (C) 2007, 2008 Intel Corporation 

Collecting data for 600 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.8%)
polling		  0.0ms ( 0.0%)
C1 halt		  0.0ms ( 0.0%)
C2		  0.7ms ( 0.0%)
C3		 25.9ms (99.2%)
P-states (frequencies)
  1.60 Ghz     0.0%
  1333 Mhz     0.0%
  1066 Mhz     0.0%
   800 Mhz   100.0%
Wakeups-from-idle per second : 38.4	interval: 600.0s
Power usage (ACPI estimate): 7.9W (3.5 hours) 
Top causes for wakeups:
  37.2% ( 12.3)       <interrupt> : extra timer interrupt 
  27.6% (  9.1)   gnome-power-man : do_nanosleep (hrtimer_wakeup) 
   6.3% (  2.1)              hald : schedule_timeout (process_timeout) 
   5.4% (  1.8)      <kernel IPI> : Rescheduling interrupts 
   4.9% (  1.6)    gnome-terminal : schedule_timeout (process_timeout) 
   4.1% (  1.3)       <interrupt> : acpi 
   3.8% (  1.2)              Xorg : schedule_timeout (process_timeout) 
   3.0% (  1.0)    cpufreq-applet : schedule_timeout (process_timeout) 
   1.5% (  0.5)        pulseaudio : schedule_timeout (process_timeout) 
   1.4% (  0.5)   gnome-screensav : schedule_timeout (process_timeout) 
   0.8% (  0.3)       gnome-panel : schedule_timeout (process_timeout) 
   0.8% (  0.3)   netbook-launche : schedule_timeout (process_timeout) 
   0.8% (  0.2)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.7% (  0.2)   gnome-power-man : schedule_timeout (process_timeout) 
   0.6% (  0.2)   update-notifier : schedule_timeout (process_timeout) 
   0.3% (  0.1)      <kernel IPI> : function call interrupts 
   0.3% (  0.1)         ssh-agent : schedule_timeout (process_timeout) 
   0.1% (  0.0)       <interrupt> : ata_piix 
   0.1% (  0.0)     <kernel core> : page_writeback_init (wb_timer_fn) 
   0.1% (  0.0)          winbindd : schedule_timeout (process_timeout) 
   0.1% (  0.0)          gconfd-2 : schedule_timeout (process_timeout) 
   0.1% (  0.0)     <kernel core> : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)     <kernel core> : inet_initpeers (peer_check_expire) 
   0.0% (  0.0)     <kernel core> : laptop_io_completion (laptop_timer_fn) 
   0.0% (  0.0)   <kernel module> : __hrtick_start (hrtick) 
   0.0% (  0.0)              Xorg : do_setitimer (it_real_fn) 
   0.0% (  0.0)       dbus-daemon : schedule_timeout (process_timeout) 
   0.0% (  0.0)         nm-applet : schedule_timeout (process_timeout) 
   0.0% (  0.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   0.0% (  0.0)              Xorg : hrtick_start_fair (hrtick) 
   0.0% (  0.0)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer) 
   0.0% (  0.0)          nautilus : schedule_timeout (process_timeout) 
   0.0% (  0.0)   gnome-settings- : schedule_timeout (process_timeout) 
   0.0% (  0.0)           pdflush : blk_plug_device (blk_unplug_timeout) 
   0.0% (  0.0)     <kernel core> : inet_frags_init (inet_frag_secret_rebuild) 
   0.0% (  0.0)     <kernel core> : flow_cache_init (flow_cache_new_hashrnd) 
   0.0% (  0.0)     <kernel core> : rif_init (rif_check_expire) 
   0.0% (  0.0)     <kernel core> : con_init (blank_screen_t) 
   0.0% (  0.0)    jockey-backend : schedule_timeout (process_timeout) 

Recent USB suspend statistics
Active  Device name

```

Running VLC:
```
PowerTOP 1.10    (C) 2007, 2008 Intel Corporation 

Collecting data for 600 seconds 


Cn	          Avg residency
C0 (cpu running)        (34.9%)
polling		  0.0ms ( 0.0%)
C1 halt		  1.0ms ( 0.0%)
C2		  0.7ms ( 0.8%)
C3		  1.8ms (64.3%)
P-states (frequencies)
  1.60 Ghz     0.0%
  1333 Mhz     0.0%
  1066 Mhz     0.0%
   800 Mhz   100.0%
Wakeups-from-idle per second : 376.8	interval: 600.0s
Power usage (ACPI estimate): 10.1W (2.5 hours) 
Top causes for wakeups:
  31.2% (202.1)      <kernel IPI> : Rescheduling interrupts 
  27.3% (177.0)               vlc : do_nanosleep (hrtimer_wakeup) 
  15.2% ( 98.5)       <interrupt> : HDA Intel, i915@pci:0000:00:02.0 
  11.6% ( 75.3)      <kernel IPI> : function call interrupts 
  10.2% ( 66.0)       <interrupt> : extra timer interrupt 
   2.0% ( 13.0)               vlc : schedule_timeout (process_timeout) 
   0.6% (  4.2)      <kernel IPI> : TLB shootdowns 
   0.5% (  2.9)       <interrupt> : mmc0 
   0.3% (  2.1)              hald : schedule_timeout (process_timeout) 
   0.2% (  1.4)       <interrupt> : acpi 
   0.2% (  1.1)              Xorg : schedule_timeout (process_timeout) 
   0.2% (  1.0)    cpufreq-applet : schedule_timeout (process_timeout) 
   0.1% (  0.9)               vlc : blk_plug_device (blk_unplug_timeout) 
   0.0% (  0.3)        pulseaudio : schedule_timeout (process_timeout) 
   0.0% (  0.3)   gnome-power-man : schedule_timeout (process_timeout) 
   0.0% (  0.3)       gnome-panel : schedule_timeout (process_timeout) 
   0.0% (  0.3)   netbook-launche : schedule_timeout (process_timeout) 
   0.0% (  0.2)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.0% (  0.2)   update-notifier : schedule_timeout (process_timeout) 
   0.0% (  0.2)              Xorg : do_setitimer (it_real_fn) 
   0.0% (  0.1)         ssh-agent : schedule_timeout (process_timeout) 
   0.0% (  0.1)       <interrupt> : ata_piix 
   0.0% (  0.1)               vlc : futex_wait (hrtimer_wakeup) 
   0.0% (  0.1)               vlc : hrtick_start_fair (hrtick) 
   0.0% (  0.1)               vlc : __hrtick_start (hrtick) 
   0.0% (  0.0)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer) 
   0.0% (  0.0)          winbindd : schedule_timeout (process_timeout) 
   0.0% (  0.0)          gconfd-2 : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : page_writeback_init (wb_timer_fn) 
   0.0% (  0.0)              Xorg : hrtick_start_fair (hrtick) 
   0.0% (  0.0)           pdflush : blk_plug_device (blk_unplug_timeout) 
   0.0% (  0.0)     <kernel core> : queue_delayed_work (delayed_work_timer_fn) 
   0.0% (  0.0)       dbus-daemon : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : inet_initpeers (peer_check_expire) 
   0.0% (  0.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   0.0% (  0.0)              Xorg : __hrtick_start (hrtick) 
   0.0% (  0.0)     <kernel core> : rif_init (rif_check_expire) 
   0.0% (  0.0)         nm-applet : schedule_timeout (process_timeout) 
   0.0% (  0.0)   <kernel module> : hrtick_start_fair (hrtick) 
   0.0% (  0.0)   netbook-launche : hrtick_start_fair (hrtick) 
   0.0% (  0.0)   netbook-launche : __hrtick_start (hrtick) 
   0.0% (  0.0)   gnome-settings- : schedule_timeout (process_timeout) 
   0.0% (  0.0)          nautilus : schedule_timeout (process_timeout) 
   0.0% (  0.0)     <kernel core> : inet_frags_init (inet_frag_secret_rebuild) 
   0.0% (  0.0)     <kernel core> : flow_cache_init (flow_cache_new_hashrnd) 
   0.0% (  0.0)   gnome-screensav : schedule_timeout (process_timeout) 

Recent USB suspend statistics
Active  Device name

```

This is after applying all my power saving skills. :)
Don't really get much out of these numbers. Have no idea how to reduce the "Rescheduling interrupts" and such.. Of course I can't do anything about the vlc and HDA Intel entries, but what about the others?

Which services and modules should I unload?

---

### Post by thor2002ro on 2008-11-10
i don't see anything you could unload.... I think the next step is 6sell bat :lolflag:

---

### Post by FunEye on 2008-11-11
Already got the 6 cell battery.. ;)

Getting about 5-6 hours running VLC on this setup.. 
Probably got all I can out of it.

Thanks anyway!

---

### Post by thor2002ro on 2008-11-11
ooo i soo what to get one of those :(

---

