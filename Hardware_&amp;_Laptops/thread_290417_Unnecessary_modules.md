---
title: "Unnecessary modules"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by Salim on 2006-11-01
Hi,
I have a Notebook running Ubuntu 6.10 Edgy on it. I'm forced to use Kontact, because Evolution's Calendar doesn't really support coloured dates... (it doesn't work at least and wont be fixed yet, I've read in the bug-database). But that's not the main problem: I want to have a faster bootup, I've heard the less modules are loaded in the kernel, the faster the bootup will be. So I'm asking, what modules can I remove? How do I?
My Hardware:
Centrino with Pentium M 740
ATI Mobility Radeon X700 with working fglrx proprietary driver...
802.11b/g wireless lan
1GB DDR2

I think that's the most important stuff. And now what lsmod gives me:
```
$ sudo lsmod
Module                  Size  Used by
battery                11652  0 
ac                      6788  0 
thermal                15624  0 
fan                     6020  0 
button                  7952  0 
ipw2200               115652  0 
ieee80211              35272  1 ipw2200
tg3                   107652  0 
fglrx                 406988  8 
binfmt_misc            13448  1 
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
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
asus_acpi              17688  0 
nls_utf8                3200  1 
ntfs                  112116  1 
nls_iso8859_1           5248  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
reiserfs              263936  2 
ext3                  142728  1 
jbd                    62228  1 ext3
ipv6                  272288  12 
af_packet              24584  4 
sbp2                   24584  0 
scsi_mod              144648  1 sbp2
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
arc4                    3200  2 
ieee80211_crypt_wep     6528  1 
joydev                 11200  0 
pcmcia                 40380  0 
snd_intel8x0           34844  5 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
tsdev                   9152  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  2 snd_pcm_oss
usbhid                 45152  0 
ieee80211_crypt         7552  2 ieee80211,ieee80211_crypt_wep
tifm_7xx1               9472  0 
tifm_core              10496  1 tifm_7xx1
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  11392  1 
irda                  214332  0 
shpchp                 42144  0 
snd_pcm                84612  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
snd                    58372  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  2 snd
psmouse                41352  0 
serio_raw               8452  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pci_hotplug            32828  1 shpchp
crc_ccitt               3200  1 irda
intel_agp              26012  1 
agpgart                34888  2 fglrx,intel_agp
xfs                   621272  1 
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  8 
piix                   11780  1 
generic                 5764  0 
processor              31560  2 thermal,speedstep_centrino
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

Are there any other great methods, to speed up bootup time?

Thanks for help

Salim

---

### Post by swamytk on 2006-11-01
Ubuntu is good in hardware detection and loading modules. Yours seems to be intact. I use to speed up boot time by disabling the unnecessary services started while booting. Why can't you try? Check with /etc/init.d for services installed in your system.

---

### Post by xyz on 2006-11-01
To speed up boot time, chek this out:
[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)
I find this a risky way to speed it up. So be careful.
There are other ways but I can't find the links at the moment.
Hope it helps.

---

### Post by louistan3 on 2006-11-01
the link that xyz gave works.. ive done it before.. :D

reprofiling your readahead can help too..

---

### Post by Salim on 2006-11-01
These are the files in /etc/init.d:
```
:/etc/init.d$ ls
acpid              hostname.sh                      rcS
acpi-support       hotkey-setup                     readahead
alsa-utils         hplip                            readahead-desktop
anacron            hwclock.sh                       README
apmd               inetutils-inetd                  reboot
apport             keyboard-setup                   rmnologin
atd                killprocs                        rsync
atieventsd         klogd                            screen
avahi-daemon       laptop-mode                      sendsigs
binfmt-support     linux-restricted-modules-common  single
bluetooth          loopback                         skeleton
bootclean          makedev                          stop-bootlogd
bootlogd           module-init-tools                stop-bootlogd-single
bootmisc.sh        mountall-bootclean.sh            stop-readahead
brltty             mountall.sh                      sysklogd
checkfs.sh         mountdevsubfs.sh                 udev
checkroot.sh       mountkernfs.sh                   umountfs
console-screen.sh  mountnfs-bootclean.sh            umountnfs.sh
console-setup      mtab.sh                          umountroot
cron               networking                       undervolt
cupsys             nvidia-kernel                    urandom
dbus               pcmciautils                      usplash
dns-clean          powernowd                        vbesave
festival           powernowd.early                  waitnfs.sh
gdm                pppd-dns                         wpa-ifupdown
glibc.sh           procps.sh                        x11-common
halt               rc
hdparm             rc.local
```
Which of these is unnecessary?

---

### Post by swamytk on 2006-11-03
1. If your BIOS supports APM, acpid* are unnecessary and vice versa for apmd.
2. If you don't want bug buddy apport is unnecessary
3. anacron, cron and atd are scheduler programs which are unnecessary if don't use anyone. I don't use any of them (Warning: Some program may use indirectly)
4. bluetooth is unnecessary if you don't have any device
5. brltty is not needed for all (accessibility)
6. festival - speech related - not needed for normal work
7. hplip - no need when it is not a HP machine
8. linux-restricted-modules are not needed if you don't rely on any proprietory drivers
9. pcmciautils, *nfs*, nvidia-kernel, rsync are not needed if you don't have any specific PCMCIA device, NFS file system access, NVIDIA chipset, and rsync protocol to syncronize the file system respectively.

Note: Even before Edgy (with Dapper) my PIII/192MB use to boot in 30 seconds with this technique + i686 kernel. Now edgy does that kernel part automatically.

---

