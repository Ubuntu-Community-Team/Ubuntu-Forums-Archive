---
title: "Thinkpad T60 Suspend lockup on Lucid"
date: 2011-08-10
forum: Hardware
---

### Post by Avoozl on 2011-08-10
I know suspend problems are a common issue and I've googled a lot but I just can't figure this out.

A fresh install of Lucid on my thinkpad t60 was able to suspend without problems.  At some point after installing updates and configuring things to my liking, my laptop fails to suspend properly.  The "sleep" led blinks continuously and the hard drive never spins down.  It locks up hard and I have to power cycle.

The T60 is dual core.  I found that if I disable one core in the bios the laptop will suspend with no problems (however it was not necessary to do this before applying updates).  I would like to figure out a way to get suspend working without having to run with one core permanently disabled.  I know it should be possible since it works on a fresh lucid.

I also tried disabling frequency scaling but that didn't seem to work.

---

### Post by Toz on 2011-08-10
A couple of suggestions.

1. Try updating your bios to the newest version, if possible.

2. Since it worked initially and doesn't now, there's a good chance the kernel was updated and broke something. You can either revert back to the original kernel or look at installing the newest lucid mainline kernel (see: [https://wiki.ubuntu.com/Kernel/MainlineBuilds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")). The newest version for Lucid appears to be 2.6.32-41 (see: [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D") and specifically [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.41-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.41-lucid/")). The instructions for installing the kernel are in the first link.

---

### Post by matt_symes on 2011-08-10
Hi

What do your log files say ?

```
cat /var/log/pm-suspend
```

```
cat /var/log/syslog
```

Kind regards

---

### Post by Avoozl on 2011-08-10
I couldn't figure out if there was a newer version of my bios.  There didn't seem to be one on Lenovo's website and mine says it's from 2009 so it might be the latest version already.

Okay, I tried a few different kernels, both older and newer.  They didn't work, but when I tried suspending with a newer kernel backported from natty (I think) it showed a few messages on the screen, something like:

```
iwl3945 error setting Tx power (-5)
loading cpufreq kernel modules
```

With the other kernels when it fails to suspend I only get a blank screen.


Anyway, here are the relevant parts of my logs:

pm-suspend
```

Wed Aug 10 22:10:04 EDT 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux Rodin 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
pci_stub                1102  1 
vboxpci                14531  0 
vboxnetadp              6808  0 
vboxnetflt             16652  0 
vboxdrv               249542  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_analog    58598  1 
snd_hda_intel          22069  2 
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
font                    7557  1 fbcon
thinkpad_acpi          68083  0 
bitblit                 4707  1 fbcon
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
softcursor              1189  1 bitblit
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vga16fb                11385  0 
arc4                    1153  2 
snd_seq_dummy           1338  0 
vgastate                8961  1 vga16fb
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
btusb                  11053  0 
iwl3945                68727  0 
snd_rawmidi            19056  1 snd_seq_midi
bluetooth              49892  1 btusb
iwlcore               106149  1 iwl3945
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i915                  288611  3 
lp                      7028  0 
pcmcia                 30784  0 
mac80211              205402  2 iwl3945,iwlcore
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29329  1 i915
parport                32635  2 ppdev,lp
drm                   162377  4 i915,drm_kms_helper
intel_agp              24375  2 i915
joydev                  8740  0 
i2c_algo_bit            5028  1 i915
yenta_socket           20408  1 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         10015  1 yenta_socket
cfg80211              126144  3 iwl3945,iwlcore,mac80211
agpgart                31724  2 drm,intel_agp
snd                    54244  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,thinkpad_acpi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_tis                 7488  0 
tpm                    13936  1 tpm_tis
psmouse                63677  0 
irda                  186844  0 
crc_ccitt               1339  1 irda
soundcore               6620  1 snd
led_class               2864  3 thinkpad_acpi,iwl3945,iwlcore
serio_raw               3978  0 
video                  17375  1 i915
output                  1871  1 video
nvram                   6203  1 thinkpad_acpi
tpm_bios                5266  1 tpm
usbhid                 36110  0 
hid                    67288  1 usbhid
e1000e                119888  0 
             total       used       free     shared    buffers     cached
Mem:       1017184     507928     509256          0      69472     246380
-/+ buffers/cache:     192076     825108
Swap:      2977784          0    2977784
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Wed Aug 10 22:10:06 EDT 2011: performing suspend

```



syslog
```

Aug 10 22:10:04 Rodin anacron[2049]: Anacron 2.3 started on 2011-08-10
Aug 10 22:10:04 Rodin anacron[2049]: Normal exit (0 jobs run)
Aug 10 22:10:05 Rodin NetworkManager: <info>  Sleeping...
Aug 10 22:10:05 Rodin NetworkManager: <info>  (eth0): now unmanaged
Aug 10 22:10:05 Rodin NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Aug 10 22:10:05 Rodin NetworkManager: <info>  (eth0): cleaning up...
Aug 10 22:10:05 Rodin NetworkManager: <info>  (eth0): taking down device.
Aug 10 22:10:05 Rodin kernel: [  322.817114] usb 5-1: USB disconnect, address 2
Aug 10 22:10:05 Rodin NetworkManager: <info>  (wlan0): now unmanaged
Aug 10 22:10:05 Rodin NetworkManager: <info>  (wlan0): device state change: 8 -> 1 (reason 37)
Aug 10 22:10:05 Rodin NetworkManager: <info>  (wlan0): deactivating device (reason: 37).
Aug 10 22:10:06 Rodin NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1890
Aug 10 22:10:06 Rodin NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Aug 10 22:10:06 Rodin kernel: [  323.121104] wlan0: deauthenticating from 00:26:f3:8c:f9:38 by local choice (reason=3)
Aug 10 22:10:06 Rodin NetworkManager: <info>  (wlan0): cleaning up...
Aug 10 22:10:06 Rodin NetworkManager: <info>  (wlan0): taking down device.
Aug 10 22:10:06 Rodin kernel: [  323.179633] ------------[ cut here ]------------
Aug 10 22:10:06 Rodin wpa_supplicant[1035]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 10 22:10:06 Rodin kernel: [  323.179667] WARNING: at /build/buildd/linux-2.6.32/net/wireless/core.c:614 wdev_cleanup_work+0xa7/0xd0 [cfg80211]()
Aug 10 22:10:06 Rodin kernel: [  323.179674] Hardware name: 1951C2U
Aug 10 22:10:06 Rodin kernel: [  323.179677] Modules linked in: aes_i586 aes_generic binfmt_misc ppdev pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv snd_hda_codec_analog snd_hda_intel fbcon tileblit snd_hda_codec snd_hwdep font thinkpad_acpi bitblit snd_pcm_oss snd_mixer_oss softcursor snd_pcm vga16fb arc4 snd_seq_dummy vgastate snd_seq_oss snd_seq_midi btusb iwl3945 snd_rawmidi bluetooth iwlcore snd_seq_midi_event i915 lp pcmcia mac80211 snd_seq drm_kms_helper parport drm intel_agp joydev i2c_algo_bit yenta_socket snd_timer snd_seq_device rsrc_nonstatic cfg80211 agpgart snd snd_page_alloc pcmcia_core tpm_tis tpm psmouse irda crc_ccitt soundcore led_class serio_raw video output nvram tpm_bios usbhid hid e1000e
Aug 10 22:10:06 Rodin kernel: [  323.179796] Pid: 9, comm: events/0 Not tainted 2.6.32-33-generic #72-Ubuntu
Aug 10 22:10:06 Rodin kernel: [  323.179801] Call Trace:
Aug 10 22:10:06 Rodin kernel: [  323.179817]  [<c014d0e2>] warn_slowpath_common+0x72/0xa0
Aug 10 22:10:06 Rodin kernel: [  323.179832]  [<f853fdd7>] ? wdev_cleanup_work+0xa7/0xd0 [cfg80211]
Aug 10 22:10:06 Rodin kernel: [  323.179848]  [<f853fdd7>] ? wdev_cleanup_work+0xa7/0xd0 [cfg80211]
Aug 10 22:10:06 Rodin kernel: [  323.179856]  [<c014d12a>] warn_slowpath_null+0x1a/0x20
Aug 10 22:10:06 Rodin kernel: [  323.179873]  [<f853fdd7>] wdev_cleanup_work+0xa7/0xd0 [cfg80211]
Aug 10 22:10:06 Rodin kernel: [  323.179883]  [<c01644be>] run_workqueue+0x8e/0x150
Aug 10 22:10:06 Rodin kernel: [  323.179900]  [<f853fd30>] ? wdev_cleanup_work+0x0/0xd0 [cfg80211]
Aug 10 22:10:06 Rodin kernel: [  323.179908]  [<c0164604>] worker_thread+0x84/0xe0
Aug 10 22:10:06 Rodin kernel: [  323.179917]  [<c01685a0>] ? autoremove_wake_function+0x0/0x50
Aug 10 22:10:06 Rodin kernel: [  323.179925]  [<c0164580>] ? worker_thread+0x0/0xe0
Aug 10 22:10:06 Rodin kernel: [  323.179932]  [<c0168314>] kthread+0x74/0x80
Aug 10 22:10:06 Rodin kernel: [  323.179938]  [<c01682a0>] ? kthread+0x0/0x80
Aug 10 22:10:06 Rodin kernel: [  323.179947]  [<c0104087>] kernel_thread_helper+0x7/0x10
Aug 10 22:10:06 Rodin kernel: [  323.179953] ---[ end trace 22d33b15e204bf5e ]--
```

There's some bad looking stuff at the end there, but I don't know what any of it means...

---

### Post by matt_symes on 2011-08-11
Hi

cfg80211 is the wireless API.

[http://linuxwireless.org/en/developers/Documentation/cfg80211](http://linuxwireless.org/en/developers/Documentation/cfg80211)

It looks like it is killing your kernel and hence the lockup.

Have you tried unloading your wireless drivers and so forth before suspending ?

What is the output of

```
sudo lshw -C network
```

Post the results back here.

Kind regards

---

### Post by Avoozl on 2011-08-11
```
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:58:a7:6b
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:ee000000-ee01ffff ioport:2000(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:71:59:31
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.0.6 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:edf00000-edf00fff

```

Every time I reboot after a failed suspend the wireless is disabled and I have to right click and check "enable networking" to get it started again.

Does unloading the driver mean the same thing as removing the iwl3945 module?  I did try that and it didn't work.  I also tried suspending with networking disabled as described and it didn't work.  I was thinking it has something to do with my CPUs or power management since it currently works with one of my CPUs disabled.

---

### Post by matt_symes on 2011-08-12
Hi

> Does unloading the driver mean the same thing as removing the iwl3945 module? I did try that and it didn't work. 

That depends. Did you try something like..

```
sudo rmmod iwl13945
```

Did it suspend correctly after that ? There is an issue with your wireless and suspend buth that may not be the whole cause.

> I was thinking it has something to do with my CPUs or power management since it currently works with one of my CPUs disabled.

That is interesting. Did you try suspending directly ?

```
sudo bash -c "echo mem > /sys/power/state"
```

And also from here [http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram](http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram) (which could well tie-in in with the uniprocessor issue).

> Hangs on "switching to UP code"
You may be using a frequency scaling governor such as "conservative" or "ondemand", which sometimes have problems with suspending. Switching to a governor such as "powersave" or "performance" before suspending may solve this problem.

Kind regards

---

### Post by Avoozl on 2011-08-13
None of those things worked.  Suspend fails every time.  When I tried suspending directly with the line you gave 

```
sudo bash -c "echo mem > /sys/power/state"
```

It froze up hard again but the screen never went black as I never closed the laptop lid.

Ugh, this is so frustrating.  I'm thinking about reinstalling the whole system and installing updates one at a time until I find out which one breaks my suspend ability.

---

### Post by Avoozl on 2011-08-14
Alright, thanks for trying to help but I reinstalled a fresh 10.04.3.  Suspending works again.  I'm gonna track this sucker down by slowly installing updates a few at a time and suspending after each.  I'll post again once I find the bug.

So far no problem with any of the standard updates, lucid-backports or lucid-proposed.  This is quite curious.

---

### Post by Avoozl on 2011-08-14
FOUND IT.


I used Ubuntu Tweak to enable the offical virtualbox repo (not OSE edition).  Virtualbox 4.1 is the culprit.  After installing it suspend hangs and locks up the lappy.  I completely removed only the virtualbox-4.1 package and suspend works perfectly again.  


A few more things before I let this thread rest:

1. Can anybody explain why having this version of virtualbox installed could break suspend?  That doesn't make any sense to me. (Especially since suspend still works with virtualbox 4.1 installed if I disable one of my CPU cores in the bios).

2. Is there anywhere I should report this?  

3.  How do I mark this thread as solved?  (I might be able to figure this one out in a minute.)


P.S. Virtualbox 4.0.12 works without trouble.

---

