---
title: "Installation fails - Stale NFS file handle"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by freddan on 2009-05-02
Fellow Ubuntuers,

I can't install or update my system any more. I get the following error message. When trying to open the file "debianutils.list" it returns the same error message as below.

```
netbook:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apport apport-gtk python-apport python-problem-report
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/326kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `debianutils': Stale NFS file handle
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Anyone got ay ideas on how to resolve it?

Cheers!
/F

---

### Post by johan.ekblad on 2009-05-06
I get the same with 9.04 and Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux (I'm using ext3), but I get a sligthly different error message when I do:

$ sudo apt-get install php5-cli

I get:

...
Selecting previously deselected package php5-cli.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `libsamplerate0': Stale NFS file handle
E: Sub-process /usr/bin/dpkg returned an error code (2)

This is my story:

First I upgraded from 8.10. After a while I got strange problems. Everythings just freeze and I'm forced to run fsck next boot. (One time it didn't even boot, so I had to use the rescue disk, and another time my home directory was rescured in the lost+found) Naturally I suspected that my hard drive where going to die, so I bought a new bigger one and used ddrescue to copy the whole drive to the new one. But the thing is that the problems still persist with the new drive.  (OS-related?) Today I was'nt even able to install new package (got the error above) but I think this has to do with some file beeing corrupt, a strace reveals:

open("/dev/ptmx", O_RDWR)               = 26
statfs("/dev/pts", {f_type="DEVPTS_SUPER_MAGIC", f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096}) = 0
ioctl(26, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(26, TIOCGPTN, [3])                = 0
stat("/dev/pts/3", {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 3), ...}) = 0
statfs("/dev/pts/3", {f_type="DEVPTS_SUPER_MAGIC", f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096}) = 0
ioctl(26, TIOCSPTLCK, [0])              = 0
ioctl(26, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(26, TIOCGPTN, [3])                = 0
stat("/dev/pts/3", {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 3), ...}) = 0
open("/dev/pts/3", O_RDWR|O_NOCTTY)     = 27
ioctl(27, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(27, SNDCTL_TMR_CONTINUE or TCSETSF, {B38400 opost isig icanon echo ...}) = 0
ioctl(27, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(27, TIOCSWINSZ, {ws_row=24, ws_col=168, ws_xpixel=0, ws_ypixel=0}) = 0
rt_sigprocmask(SIG_BLOCK, [TTOU], [], 8) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_CONTINUE or TCSETSF, {B38400 -opost -isig -icanon -echo ...}) = 0
                                                                                     ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 -opost -isig -icanon -echo ...}) = 0
 rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
                                             clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f94ddf94790) = 11520
                                                                                                                                                             close(25)                               = 0
                                close(27)                               = 0
                                                                           rt_sigprocmask(SIG_BLOCK, [], [], 8)    = 0
                                                                                                                      wait4(11520, 0x7fffe5fb6e58, WNOHANG, NULL) = 0
                                                                                                                                                                     pselect6(27, [0 24 26], NULL, NULL, {1, 0}, {[], 8}) = 1 (in [26], left {0, 931921306})
                                                                                    read(26, "V\303\244ljer tidigare ej valt paket ph"..., 1024) = 64 # (yes I had LANG=sv.SE here) 
                                                                                                                                                     write(1, "V\303\244ljer tidigare ej valt paket ph"..., 64Väljer tidigare ej valt paket php5-cli.
(Läser databasen ... ) = 64
                           wait4(11520, 0x7fffe5fb6e58, WNOHANG, NULL) = 0
                                                                          pselect6(27, [0 24 26], NULL, NULL, {1, 0}, {[], 8}) = 1 (in [26], left {0, 999931346})
                                                                                                                                                                 read(26, "dpkg: o\303\245terkalleligt \303\266desdigert"..., 1024) = 136
                                                                 write(1, "dpkg: o\303\245terkalleligt \303\266desdigert"..., 136dpkg: oåterkalleligt ödesdigert fel, avbryter:
 kunde inte öppna fillistan för paketet "libsamplerate0": Förlegat NFS-filhandtag
) = 136
       wait4(11520, 0x7fffe5fb6e58, WNOHANG, NULL) = 0
                                                      pselect6(27, [0 24 26], NULL, NULL, {1, 0}, {[], 8}) = 2 (in [24 26], left {0, 998597588})
                                                                                                                                                --- SIGCHLD (Child exited) @ 0 (0) ---
              read(26, 0x7fffe5fa64d0, 1024)          = -1 EIO (Input/output error)
                                                                                   nanosleep({0, 500000000}, NULL)         = 0
                                                                                                                              read(24, ""..., 1024)                   = 0

----------------

lspci: 

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller

lsmod: 

Module                  Size  Used by
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
joydev                 20864  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
arc4                   10240  2 
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
ecb                    11392  2 
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                114820  0 
iwlcore               106496  1 iwlagn
led_class              13064  1 iwlcore
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               69512  0 
mac80211              251144  2 iwlagn,iwlcore
soundcore              16800  1 snd
psmouse                64028  0 
intel_agp              39408  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
video                  29204  5 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
pcspkr                 11136  0 
serio_raw              14468  0 
sdhci_pci              16896  0 
sdhci                  27396  1 sdhci_pci
v4l1_compat            23940  2 uvcvideo,videodev
cfg80211               43168  3 iwlagn,iwlcore,mac80211
output                 11648  1 video
usbhid                 47040  0 
nvidia               8123768  32 
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

--------------

Will try to burn a cdimage and reinstall + use ext4 this time

---

### Post by johan.ekblad on 2009-05-07
fixed the freeze problem by adding "nohz=off" as boot argument in /boot/grub/menu.lst

But I reinstalled ubuntu 9.04 and didn't try to fix the repo problem.

---

