---
title: "My battery will not charge on hoary, works on suse"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by antikristian on 2005-03-31
What can possibly be wrong, everything works, acpi suspend, +++ This must be the best distro I've ever tried (I only miss an administration tool like yast (ok, I miss yast))

running a kubuntu setup, and have updated the distro with smart update today (also installed it today)

I get a flashing light on my laptop indicating battery failure, it refuses to charge properly, but claims to have 100% battery capacity. This does not happen on suse 9.2 (dual install, suse 9.2 and hoary)

my lsmod output is:

```
 
Module                  Size  Used by
speedstep_centrino      8052  1
proc_intf               4004  0
cpufreq_powersave       1632  0
cpufreq_userspace       4348  1
cpufreq_ondemand        6300  0
freq_table              4036  1 speedstep_centrino
pcmcia                 22692  2
i915                   20224  1
drm                    67284  2 i915
video                  15940  0
battery                 9988  0
container               4320  0
button                  6480  0
pcc_acpi               11008  0
sony_acpi               5928  0
ac                      4676  0
ipv6                  265984  8
af_packet              22504  2
e100                   34976  0
mii                     4960  1 e100
ipw2100                87100  0
firmware_class         10176  1 ipw2100
ieee80211              23844  1 ipw2100
ieee80211_crypt         5736  1 ieee80211
yenta_socket           22048  0
pcmcia_core            59936  2 pcmcia,yenta_socket
snd_intel8x0           33280  1
snd_ac97_codec         77088  1 snd_intel8x0
snd_pcm_oss            54212  0
snd_mixer_oss          20320  1 snd_pcm_oss
snd_pcm                98280  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25828  1 snd_pcm
snd                    56900  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc          9956  2 snd_intel8x0,snd_pcm
pci_hotplug            34480  0
ehci_hcd               33732  0
uhci_hcd               34000  0
usbcore               122552  3 ehci_hcd,uhci_hcd
intel_agp              22652  1
agpgart                34600  3 drm,intel_agp
pcspkr                  3496  0
rtc                    12696  0
md                     48720  0
tsdev                   7680  0
dm_mod                 62204  1
evdev                   9536  0
capability              4648  0
commoncap               7872  1 capability
psmouse                21992  0
mousedev               11608  1
parport_pc             37860  1
lp                     11656  0
parport                37800  2 parport_pc,lp
ide_cd                 42756  0
cdrom                  41500  1 ide_cd
reiserfs              270864  3
ide_generic             1312  0
ide_disk               21056  5
piix                   10628  1
ide_core              133068  4 ide_cd,ide_generic,ide_disk,piix
unix                   28884  446
thermal                13288  0
processor              22420  2 speedstep_centrino,thermal
fan                     4388  0
fbcon                  38592  0
font                    8160  1 fbcon
bitblit                 5632  1 fbcon
vesafb                  6788  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               2912  1 vesafb
cfbfillrect             3616  1 vesafb

```

and my ps -e output is 

```
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
   16 ?        00:00:00 kacpid
  127 ?        00:00:00 kblockd/0
  158 ?        00:00:00 pdflush
  159 ?        00:00:00 pdflush
  161 ?        00:00:00 aio/0
  160 ?        00:00:00 kswapd0
  748 ?        00:00:00 kseriod
 1105 ?        00:00:00 reiserfs/0
 1134 ?        00:00:00 udevd
 3614 ?        00:00:00 khubd
 4811 ?        00:00:00 pccardd
 4947 ?        00:00:00 ipw2100/0
 5229 ?        00:00:00 dhclient3
 5598 ?        00:00:00 syslogd
 5613 ?        00:00:00 dd
 5615 ?        00:00:00 klogd
 5649 ?        00:00:00 kdm
 5665 ?        00:00:00 cupsd
 5675 ?        00:03:32 Xorg
 5736 ?        00:00:00 kdm
 6009 ?        00:00:00 acpid
 6071 ?        00:00:00 dbus-daemon-1
 6083 ?        00:00:01 hald
 6099 ?        00:00:00 inetd
 6349 ?        00:00:00 cardmgr
 6410 ?        00:00:00 master
 6423 ?        00:00:00 pickup
 6424 ?        00:00:00 qmgr
 6585 ?        00:00:00 powernowd
 6606 ?        00:00:00 atd
 6617 ?        00:00:00 cron
 6777 tty1     00:00:00 getty
 6778 tty2     00:00:00 getty
 6779 tty3     00:00:00 getty
 6780 tty4     00:00:00 getty
 6781 tty5     00:00:00 getty
 6782 tty6     00:00:00 getty
 6925 ?        00:00:00 startkde
 7100 ?        00:00:00 gpg-agent
 7103 ?        00:00:00 ssh-agent
 7108 ?        00:00:00 dbus-launch
 7109 ?        00:00:00 dbus-daemon-1
 7141 ?        00:00:00 kdeinit
 7146 ?        00:00:00 dcopserver
 7148 ?        00:00:00 klauncher
 7153 ?        00:00:38 kded
 7159 ?        00:00:00 gam_server
 7363 ?        00:00:01 artsd
 7522 ?        00:00:00 kwrapper
 7523 ?        00:00:00 kaccess
 7525 ?        00:00:00 ksmserver
 7526 ?        00:00:04 kwin
 7561 ?        00:00:02 kdesktop
 7563 ?        00:00:07 kicker
 7565 ?        00:00:00 klipper
 7568 ?        00:00:00 kmix
 7569 ?        00:00:00 kio_file
 7573 ?        00:00:00 knotify
 7574 ?        00:00:00 kio_uiserver
 7579 ?        00:03:17 opera
 7747 ?        00:00:00 kdesu
 7749 ?        00:00:00 kdesud
 7751 pts/1    00:00:00 sudo
 7753 ?        00:00:00 sudo <defunct>
 7758 pts/2    00:00:00 kdesu_stub
 7761 ?        00:00:19 synaptic
 7762 ?        00:00:00 gnome-pty-helpe
 8201 ?        00:00:03 gnome-terminal
 8203 ?        00:00:00 gconfd-2
 8205 ?        00:00:00 bonobo-activati
 8206 ?        00:00:00 gnome-pty-helpe
 8207 pts/3    00:00:00 bash
 8222 pts/3    00:00:00 man
 8227 pts/3    00:00:00 sh
 8230 pts/3    00:00:00 tbl
 8231 pts/3    00:00:00 nroff
 8232 pts/3    00:00:00 pager
 8235 pts/3    00:00:00 groff
 8236 pts/3    00:00:00 troff
 8237 pts/3    00:00:00 grotty
 8270 pts/3    00:00:00 ps

```

any clues?

---

### Post by soul_rebel on 2005-04-01
Nope...
check if there are bios updates and/or try a more recent kernel if possible.
(consider this as an UP  ;-) )

---

