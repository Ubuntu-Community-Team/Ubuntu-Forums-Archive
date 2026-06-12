---
title: "Power Management/Acpid/Battery problem"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by shat on 2006-11-25
Hello all,

I'm running Edgy on an Acer laptop, and today, my battery management applet disappeared.  Acpi still sees a battery, but the ubuntu battery management now doesn't believe I have a battery.  

I was messing around with services a while back (via the menu) and may have started and stopped a few.  I'm sure I have acpid and apm still on, however.  I was also messing with Beryl's dbus, but now have turned it all off.  

The power management option from the Ubuntu menu only has two tabs now, when it once had three, AC options, battery options, and general- now there are no battery options.  When I ask the power management icon to display in the notification area, it just acts like my computer is connected to AC power.  The gnome panel applet will not recognize my battery either.  

Typing acpi -t gives me this..
```
lucas@lucas-laptop:~$ acpi -t
     Battery 1: charging, 94%, 00:00:13 until charged
     Thermal 1: ok, 56.0 degrees C
lucas@lucas-laptop:~$ 
```

Trying to start the daemon gives me this..  Until hald is stopped, which then allows ACPI to start correctly.
```
lucas@lucas-laptop:~$ sudo /etc/init.d/acpid start
 * Loading ACPI modules...                                               [ ok ] 
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: Device or resource busy
lucas@lucas-laptop:~$ 
```

Finally, lsmod:
```
lucas@lucas-laptop:~$ lsmod
Module                  Size  Used by
vmnet                  41900  13 
vmmon                 118668  0 
binfmt_misc            13448  1 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dock                    8716  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  14 
fglrx                 406988  41 
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
af_packet              24584  4 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
pcmcia                 40380  0 
joydev                 11200  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
tifm_7xx1               9472  0 
ipw3945               124576  1 
sg                     37404  0 
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
tifm_core              10496  1 tifm_7xx1
tsdev                   9152  0 
ieee80211              35272  1 ipw3945
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211_crypt         7552  1 ieee80211
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
tg3                   107652  0 
intel_agp              26012  1 
agpgart                34888  2 fglrx,intel_agp
irda                  214332  0 
evdev                  11392  1 
crc_ccitt               3200  1 irda
psmouse                41352  0 
serio_raw               8452  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
ide_generic             2432  0 
sr_mod                 18212  0 
cdrom                  38944  1 sr_mod
sd_mod                 22656  3 
generic                 5764  0 
ata_piix               11780  2 
libata                 74892  1 ata_piix
scsi_mod              144648  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
```

Thanks in advance!

---

### Post by shat on 2006-11-25
It's probably something stupid I'm missing, or I turned on/off by accident and forgot about.. Hmm..

---

### Post by pdietric on 2006-11-26
Maybe your problem has to do with the order of the scripts starting during boot, at least I experienced a similar behavior when I had acpid starting too late.
Could you post the result of ```
 ls -l /etc/rc2.d/
```

Bye

---

### Post by shat on 2006-11-26
Sure thing,

```
lucas@lucas-laptop:~$ ls -l /etc/rc2.d
total 4
lrwxrwxrwx 1 root root  18 2006-11-06 13:39 K08vmware -> /etc/init.d/vmware
-rw-r--r-- 1 root root 556 2006-10-06 06:34 README
lrwxrwxrwx 1 root root  16 2006-10-28 18:57 S01apport -> ../init.d/apport
lrwxrwxrwx 1 root root  17 2006-10-28 18:57 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  25 2006-10-28 18:57 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root  18 2006-10-28 18:57 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  15 2006-10-28 18:57 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  13 2006-10-28 18:57 S13gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  16 2006-10-28 18:57 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  15 2006-10-28 18:57 S19hplip -> ../init.d/hplip
lrwxrwxrwx 1 root root  22 2006-11-15 16:47 S20boinc-client -> ../init.d/boinc-client
lrwxrwxrwx 1 root root  14 2006-10-28 18:57 S20dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  22 2006-10-28 18:57 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  17 2006-10-28 18:57 S20makedev -> ../init.d/makedev
lrwxrwxrwx 1 root root  23 2006-10-28 18:57 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  19 2006-10-28 18:57 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2006-10-28 18:57 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  16 2006-11-06 13:29 S20xinetd -> ../init.d/xinetd
lrwxrwxrwx 1 root root  19 2006-10-28 18:57 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  15 2006-11-25 00:11 S50acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  20 2006-11-24 23:57 S50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx 1 root root  14 2006-11-25 00:45 S50apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  22 2006-11-23 12:38 S50avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  15 2006-11-24 23:57 S50inetd -> ../init.d/inetd
lrwxrwxrwx 1 root root  17 2006-10-28 18:57 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2006-10-28 18:57 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2006-10-28 18:57 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  24 2006-10-28 18:57 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  18 2006-11-06 13:39 S90vmware -> /etc/init.d/vmware
lrwxrwxrwx 1 root root  17 2006-10-28 18:57 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2006-10-28 18:57 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  18 2006-10-28 18:57 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2006-10-28 18:57 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root  24 2006-10-28 18:57 S99stop-readahead -> ../init.d/stop-readahead

```

---

### Post by pdietric on 2006-11-26
Ok, I don't know, if the following will solve your problem, but it's not unlikely since, telling from the dates, you have "messed" a lot with those scripts.

Go to the relevant directory: ```
cd /etc/rc2.d
```

Deactivate the symbolic link S50acpid: ```
sudo mv S50acpid _S50acpid
``` Just don't let its name start with an S or K

Then create a link that starts acpid at position 10 (that was the default on my system): ```
sudo ln -s /etc/init.d/acpid S10acpid
```

Now restart your system and see, if that changed you situation (it did in my case).

---

### Post by shat on 2006-11-26
That was my problem, thanks a lot!  Solved!

I think the problem was how System->Administration->Services handled turning on and off services.

Thanks again!

---

