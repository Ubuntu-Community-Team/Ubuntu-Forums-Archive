---
title: "Performance governor even while on battery"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by sistoviejo on 2007-11-02
I'd like to set CPU scaling governor to Performance for showing off desktop effects even while using battery power. 
The problem is when I'm on battery power gnome automatically sets the governor to On demand and I can't change it back to Performance unless I plug back to AC power.
Some desktop effects will run slower when the governor is set to On demand.
Is there a way to permanently set the governor to Performance until I decide to change it regardless if I'm on battery or not?
Thanks!

---

### Post by 444 on 2007-11-02
sudo dpkg-reconfigure gnome-applets
#^^^ it 'll ask to enable cpufreq-selector

Then add the CPU Frequency Scaling applet to a panel, it'll should let you choose the governor.

---

### Post by sistoviejo on 2007-11-02
> **444 said:**
> sudo dpkg-reconfigure gnome-applets
#^^^ it 'll ask to enable cpufreq-selector

Then add the CPU Frequency Scaling applet to a panel, it'll should let you choose the governor.

Thank you. I already did those two things. I am able to change the governor using the Frequency scaling applet. It works only when I'm on AC power. I always set it to "Performance".
But when I unplug AC power and start using battery power it sets it back to "On Demand" and I can't change it to "Performance" until I plug back to AC power. 
Note: I know this will lower my battery life but I still need to do it sometimes. :)

To sum things up, this is what I've unsuccessfully been trying to do: Set performance governor while on battery power.

---

### Post by sistoviejo on 2007-11-02
BTW...  
I googled and searched through this forum for help before posting here.
I tried setting the governor using the CLI command cpufreq-selector with the same results.
I checked and I don't have the powernowd package installed.

UPDATE:
After seeing it again now. I have noticed that the governor is actually set to performance when I'm on battery.
The problem is that for some reason it doesn't use the maximum speed on this governor while it is on battery.
Is there a way to modify the frequancies that the governor is allowed to use while on battery?

UPDATE2: 
I tried running this:
powernowd -l 100 -p 100 -s 18 -d 
But the speed stayed at 88 % as it was before.
Also I a message was displayed on screen saying "can't open scaling_setspeed: no such file or directory"

UPDATE3:
On BIOS the power settings are: "Optimize for battery life" or "Optimize for performance". I have the latter selected.

I still can't get the processor to run at 100% while using the battery. Help! Anyone?

---

### Post by sistoviejo on 2007-11-04
I still haven't been able to set CPU to full speed while on battery,

Please answer this question if you have a laptop with cpu-scaling enabled:
Have you been able to use your laptop at full CPU speed while on battery?

Other questions:
Is there a way to completely disable CPU-scaling and leaving the CPU at full speed at all times?
Is it possible to change the frequencies that cpu-scaling is allowed to use while using battery or AC? ... or while using a specific governor.

I'll appreciate any assistance.

I have an AMD Turion CPU on an HP tx1215nr laptop running Gutsy Gibbon.
3d drivers and wireless card works OK.
Here's the content of some of the cpu-scaling properties:
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq: 800000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq: 1800000
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies: 1800000 1600000 800000

I can only run at 1800000 while on AC power. 
When I'm on battery power the maximum seems to be 1600000. I can't set it to 1800000.

Thanks!

---

### Post by bingoUV on 2007-11-04
I do not have a Turion, so I cannot give you the exact command, but I can guide you to write a simple script that will do it for you. If you have a multi-core CPU, you will have to do the following for all your cores (cpu0, cpu1, ....).

First see what all governors are available for you : 
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```

On my system (a desktop CPU),  it gives 
```

ondemand userspace performance

```

If you want performance governor, do this for all your cores.
```

sudo echo "performance" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

---

### Post by sistoviejo on 2007-11-04
> **bingoUV said:**
> I do not have a Turion, so I cannot give you the exact command, but I can guide you to write a simple script that will do it for you. If you have a multi-core CPU, you will have to do the following for all your cores (cpu0, cpu1, ....).

First see what all governors are available for you : 
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```

On my system (a desktop CPU),  it gives 
```

ondemand userspace performance

```

If you want performance governor, do this for all your cores.
```

sudo echo "performance" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

Thanks.
I am able to set it through the gnome cpu frequency applet. But I tried what you suggested anyway. 
These governors are available in my case: userspace ondemand powersave conservative performance
Setting the governor...
```
root@silvio-laptop:~# sudo echo "performance" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
That command correctly sets the governor:
```
root@silvio-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  
performance

```

BUT THE PROBLEM REMAINS. I can't set the CPU's speed to over 1.6 Ghz when using battery power. Which is 88% of the CPU's rated speed. I should be able to set it to 1.8 Ghz.
This is scaling_max_freq when I'm on battery power:
```
root@silvio-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq 
1600000
```

When I'm on AC power the speed can reach the CPU's "rated" maximum speed of 1.8Ghz
This is scaling_max_freq when I'm AC power:
```
root@silvio-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq 
1800000
```

---

### Post by bingoUV on 2007-11-04
I don't know how to fix it, but you can temporarily get rid of the performance governor. For showing off purposes, just remove the cpufreq module from your kernel, and I think then your CPU should run at its maximum rated frequency. 
```

/sbin/lsmod | grep powernow

```

This should give you the module used for your cpu frequency scaling. Suppose it is powernow-k8. remove this module
```

/sbin/rmmod powernow-k8

```

Load it back when you want to save power again.
```

/sbin/modprobe powernow-k8

```

---

### Post by sistoviejo on 2007-11-04
Thanks for the reply.

It give's me this error:

silvio@silvio-laptop:~$ /sbin/rmmod powernow_k8 
ERROR: Module powernow_k8 is in use

---

### Post by bingoUV on 2007-11-05
> **sistoviejo said:**
> Thanks for the reply.

It give's me this error:

silvio@silvio-laptop:~$ /sbin/rmmod powernow_k8 
ERROR: Module powernow_k8 is in use

Please post the output of /sbin/lsmod. Sorry, I should have asked for this earlier to avoid wasting time.

---

### Post by sistoviejo on 2007-11-05
```
silvio@silvio-laptop:/$ /sbin/lsmod 
Module                  Size  Used by
ipv6                  317192  10 
af_packet              28172  4 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
nfsd                  272552  13 
exportfs                7808  1 nfsd
lockd                  76336  2 nfsd
sunrpc                198536  8 nfsd,lockd
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_userspace       6048  0 
cpufreq_ondemand       10896  1 
cpufreq_powersave       3072  0 
cpufreq_conservative     9608  0 
cpufreq_stats           8160  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
bay                     7936  0 
button                 10400  0 
battery                12424  0 
video                  21140  11 
ac                      7304  0 
sbs                    21520  0 
dock                   12264  1 bay
container               6400  0 
ndiswrapper           236960  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
joydev                 13440  0 
snd_hda_intel         337192  1 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
uvcvideo               52228  0 
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
compat_ioctl32         11136  1 uvcvideo
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videodev               31360  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7013492  36 
k8temp                  7680  0 
i2c_nforce2             7808  0 
snd                    69288  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
psmouse                45596  0 
serio_raw               9092  0 
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
pcspkr                  4608  0 
i2c_core               30208  2 nvidia,i2c_nforce2
evdev                  13056  6 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sd_mod                 32512  5 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
sata_nv                24068  4 
amd74xx                17328  0 [permanent]
ide_core              141200  2 ide_cd,amd74xx
ohci_hcd               25092  0 
ata_generic             9988  0 
libata                138928  2 sata_nv,ata_generic
scsi_mod              172856  3 sg,sd_mod,libata
forcedeth              55048  0 
ehci_hcd               40076  0 
usbcore               161584  5 ndiswrapper,uvcvideo,ohci_hcd,ehci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  5 
apparmor               47008  0 
commoncap               9472  1 apparmor
silvio@silvio-laptop:/$ 


```

---

### Post by bingoUV on 2007-11-06
Some event has caused ref count of the powernow module to increase to 1. I don't know which event, but can you try killing powernowd? Try the following commands. Wait about 5 seconds between the 2 commands.
```

sudo killall powernowd
sudo killall -9 powernowd

```

Then the rmmod should work.

---

### Post by sistoviejo on 2007-11-06
Thank you.
That didn't work either.
It still tells me the same error.

Here's the stuff that's running:

```

root@silvio-laptop:/usr/share/icons# ps xaf 
  PID TTY      STAT   TIME COMMAND
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00  \_ [migration/0]
    4 ?        SN     0:00  \_ [ksoftirqd/0]
    5 ?        S<     0:00  \_ [watchdog/0]
    6 ?        S<     0:00  \_ [migration/1]
    7 ?        SN     0:00  \_ [ksoftirqd/1]
    8 ?        S<     0:00  \_ [watchdog/1]
    9 ?        S<     0:00  \_ [events/0]
   10 ?        S<     0:00  \_ [events/1]
   11 ?        S<     0:00  \_ [khelper]
   30 ?        S<     0:00  \_ [kblockd/0]
   31 ?        S<     0:00  \_ [kblockd/1]
   32 ?        S<     0:00  \_ [kacpid]
   33 ?        S<     0:00  \_ [kacpi_notify]
  192 ?        S<     0:00  \_ [kseriod]
  226 ?        S      0:00  \_ [pdflush]
  227 ?        S      0:00  \_ [pdflush]
  228 ?        S<     0:00  \_ [kswapd0]
  281 ?        S<     0:00  \_ [aio/0]
  282 ?        S<     0:00  \_ [aio/1]
 2237 ?        S<     0:00  \_ [ata/0]
 2238 ?        S<     0:00  \_ [ata/1]
 2239 ?        S<     0:00  \_ [ata_aux]
 2251 ?        S<     0:00  \_ [ksuspend_usbd]
 2252 ?        S<     0:00  \_ [khubd]
 2378 ?        S<     0:00  \_ [scsi_eh_0]
 2379 ?        S<     0:00  \_ [scsi_eh_1]
 2596 ?        S<     0:01  \_ [kjournald]
 3916 ?        S<     0:00  \_ [kpsmoused]
 4186 ?        S<     0:13  \_ [ntos_wq/0]
 4187 ?        S<     0:15  \_ [ntos_wq/1]
 4188 ?        S<     0:00  \_ [ndis_wq]
 4189 ?        S<     0:00  \_ [wrapndis_wq/0]
 4190 ?        S<     0:00  \_ [wrapndis_wq/1]
 4926 ?        S<     0:00  \_ [kondemand/0]
 4927 ?        S<     0:00  \_ [kondemand/1]
 5437 ?        S      0:00  \_ [lockd]
 5438 ?        S<     0:00  \_ [rpciod/0]
 5439 ?        S<     0:00  \_ [rpciod/1]
 5442 ?        S<     0:00  \_ [nfsd4]
 5443 ?        S      0:00  \_ [nfsd]
 5444 ?        S      0:00  \_ [nfsd]
 5445 ?        S      0:00  \_ [nfsd]
 5446 ?        S      0:00  \_ [nfsd]
 5447 ?        S      0:00  \_ [nfsd]
 5448 ?        S      0:00  \_ [nfsd]
 5449 ?        S      0:00  \_ [nfsd]
 5450 ?        S      0:00  \_ [nfsd]
 5682 ?        S<     0:00  \_ [krfcommd]
    1 ?        Ss     0:01 /sbin/init
 2797 ?        S<s    0:00 /sbin/udevd --daemon
 4373 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda5 /media/storage -o rw,umask
 4376 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda1 /media/vista -o rw,umask=0
 4507 ?        Ss     0:00 /sbin/portmap
 4526 ?        Ss     0:00 /sbin/rpc.statd
 4653 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4654 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4656 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4659 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4660 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4661 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4876 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 4987 ?        Ss     0:00 /sbin/syslogd -u syslog
 5043 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 5045 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 5066 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 5082 ?        Ssl    0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkM
 5096 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/ru
 5109 ?        Ss     0:00 /usr/bin/system-tools-backends
 5110 ?        S      0:00  \_ dbus-daemon --session --print-address --nofork
 5129 ?        Ss     0:01 /usr/sbin/hald
 5130 ?        S      0:00  \_ hald-runner
 5208 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/
 5210 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/
 5211 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/
 5212 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/
 5221 ?        S      0:00      \_ hald-addon-acpi: listening on acpid socket /v
 5222 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/
 5229 ?        S      0:04      \_ hald-addon-storage: polling /dev/hda (every 2
 5360 ?        Ss     0:00 /usr/bin/freshclam /var/run/clamav/freshclam.pid -d -
 5454 ?        Ss     0:00 /usr/sbin/rpc.mountd
 5491 ?        Ss     0:00 /usr/sbin/nmbd -D
 5493 ?        Ss     0:00 /usr/sbin/smbd -D
 5660 ?        S      0:00  \_ /usr/sbin/smbd -D
 5538 ?        Ssl    0:00 /usr/sbin/console-kit-daemon
 5625 ?        Ss     0:00 avahi-daemon: running [silvio-laptop.local]
 5626 ?        Ss     0:00  \_ avahi-daemon: chroot helper
 5640 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 6221 ?        S      0:00  \_ /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.wla
 5661 ?        Ss     0:00 /usr/sbin/hcid -x -s
 5676 ?        S      0:00  \_ /usr/lib/bluetooth/bluetoothd-service-audio
 5677 ?        S      0:00  \_ /usr/lib/bluetooth/bluetoothd-service-input
 5715 ?        Ss     0:00 /usr/sbin/gdm
 5718 ?        S      0:00  \_ /usr/sbin/gdm
 5723 tty7     SLs+   2:41      \_ /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm
 5887 ?        Ssl    0:00      \_ x-session-manager
 5924 ?        Ss     0:00          \_ /usr/bin/ssh-agent x-session-manager
 5939 ?        S      0:00          \_ /bin/sh /usr/bin/compiz --sm-client-id de
 6045 ?        S      0:03          |   \_ /usr/bin/emerald --replace
 6046 ?        SL     1:03          |   \_ /usr/bin/compiz.real --ignore-desktop
 5942 ?        S      0:10          \_ gnome-panel --sm-client-id default1
 5943 ?        S      0:09          \_ nautilus --no-default-window --sm-client-
 6051 ?        S      0:00          \_ vino-session --sm-client-id default5
 6052 ?        S      0:00          \_ bluetooth-applet
 6055 ?        S      0:00          \_ update-notifier
 6062 ?        Sl     0:00          \_ /usr/lib/evolution/2.12/evolution-alarm-n
 6064 ?        SNl    0:00          \_ trackerd
 6079 ?        S      0:00          \_ python /usr/share/system-config-printer/a
 6114 ?        S      0:00          \_ nm-applet --sm-disable
 5786 ?        Ss     0:00 /usr/sbin/atd
 5800 ?        Ss     0:00 /usr/sbin/cron
 5926 ?        S      0:01 /usr/lib/libgconf2-4/gconfd-2 6
 5929 ?        SL     0:00 /usr/bin/gnome-keyring-daemon
 5931 ?        Ss     0:00 dbus-daemon --fork --print-address 18 --print-pid 20
 5933 ?        Sl     0:00 /usr/lib/gnome-control-center/gnome-settings-daemon
 5950 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 5952 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5996 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 6047 ?        Ss     0:02 gnome-screensaver
 6061 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 6089 ?        S      0:01 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf
 6091 ?        S      0:00 /usr/lib/gnome-applets/stickynotes_applet --oaf-activ
 6093 ?        Sl     0:00 /usr/bin/python /usr/lib/deskbar-applet/deskbar-apple
 6100 ?        S      0:01 /usr/bin/gnome-brightness-applet --oaf-activate-iid=O
 6105 ?        S      0:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activ
 6107 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 6111 ?        S      0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-app
 6113 ?        S      0:00 /usr/lib/gnome-applets/geyes_applet2 --oaf-activate-i
 6168 ?        Sl     0:00 /usr/lib/evolution/2.12/evolution-exchange-storage --
 6178 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.12 --oaf-a
 6212 ?        S      0:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-globa
 6334 ?        Sl     0:01 gnome-terminal
 6337 ?        S      0:00  \_ gnome-pty-helper
 6338 pts/0    Ss     0:00  \_ bash
 7049 pts/0    S      0:00      \_ bash
 7777 pts/0    R+     0:00          \_ ps xaf
 7007 ?        S      0:00 /usr/lib/notification-daemon/notification-daemon
 7078 ?        S      0:00 /bin/sh /usr/bin/firefox
 7090 ?        S      0:00  \_ /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/
 7094 ?        Sl     0:16      \_ /usr/lib/firefox/firefox-bin
 7174 ?        S      0:02 /usr/bin/python2.5 /usr/bin/update-manager
 7710 ?        Ss     0:00 /usr/sbin/cupsd
root@silvio-laptop:/usr/share/icons# 


```

---

### Post by 444 on 2007-11-06
Last time I saw something like this (a module being used by an invisible something), I ended up preventing the module from loading at startup to begin with, but that isn't a very flexible solution. Perhaps you should take a look at k8fq to manually set the speed...

---

### Post by sistoviejo on 2007-11-07
> **444 said:**
> Last time I saw something like this (a module being used by an invisible something), I ended up preventing the module from loading at startup to begin with, but that isn't a very flexible solution. Perhaps you should take a look at k8fq to manually set the speed...


how do you prevent the module from loading on boot?
about k8fq... is it an alternative module to powernow_k8?
i will try both options later. thx.

---

### Post by 444 on 2007-11-07
You add it to /etc/modprobe.d/blacklist. I'm assuming that you'd want to sometimes go back to lower speeds, which means you'll need to load powernowk8 and you'd be back at square one of being unable to unload it until you reboot.

k8fq isn't a module but it basically does the same thing as powernowk8, in a less convienient way.

---

### Post by sistoviejo on 2007-11-08
> **444 said:**
> You add it to /etc/modprobe.d/blacklist. I'm assuming that you'd want to sometimes go back to lower speeds, which means you'll need to load powernowk8 and you'd be back at square one of being unable to unload it until you reboot.

k8fq isn't a module but it basically does the same thing as powernowk8, in a less convienient way.

thanks.
sadly that didn't stop the module from loading. :(
```

silvio@silvio-laptop:~$ lsmod | grep powernow
powernow_k8            16608  1 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
processor              36232  2 powernow_k8,thermal
silvio@silvio-laptop:~$ tail /etc/modprobe.d/blacklist 

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx

blacklist powernow_k8
silvio@silvio-laptop:~$ 

```

I did reboot after adding the line to blacklist. Twice to be sure.
This line was also added by me following a guide to enable wifi: 
blacklist bcm43xx

---

### Post by 444 on 2007-11-08
Strange. This is after a reboot right? Well the only other thing I think of is moving the module from the directory it's in (/lib/modules/`uname -r`/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko).

---

### Post by sistoviejo on 2007-11-13
I renamed the driver to powernow-k8.ko.old. After restarting I found out the cpu speed was fixed at about 800 mhz while using the battery. Cpu scaling was unsupported so I couldn't change the speed to 1.8 ghz. When the computer is plugged in the CPU does work correctly at 1.8 ghz.
So I still have the same problem... I can't set the CPU to full speed while using the battery. I decided to activate cpu scaling again because the cpu speed was 1.6 ghz which is higher than 800 mhz.

To make this story short:
For some reason cpu scaling doesn't work on my laptop when using the battery. The speed is fixed at 1.6 ghz (real speed is 1.8 ghz). 
When I disable cpu scaling the speed is fixed at 800 mhz (also while using battery). So that doesn't help either.

When the laptop is plugged in cpu scaling actually works fine (which is useless because I don't need to save battery while it's plugged in).

Any other suggestions?
thanks! :)

---

### Post by 444 on 2007-11-13
Only other thing I can think of is forcing a certain speed with k8fq.
(You already looked at the BIOS, right?)

---

### Post by sistoviejo on 2008-01-09
I've removed Ubuntu from the laptop's hard drive because I messed up some things. 
It was really fun for me trying. I still use Ubuntu on my desktop computer.
I will probably try again with Hardy Heron.

---

### Post by TinkerJ on 2008-01-16
I think that your problem may have more to do with the ACPI configs in /etc/laptop-mode/laptop-mode.conf

Specifically the "# CPU frequency scaling and throttling" section.

Seems to work for me.

---

### Post by sistoviejo on 2008-01-16
I didn't even know this existed. Thank you.
I'll reinstall ubuntu and try that.

---

