---
title: "Weird resume problems on Acer 1810T"
date: 2009-11-18
forum: Hardware
---

### Post by robogock on 2009-11-18
I have a shiny new blue Acer Aspire 1810T-8679 laptop. I shrank the OEM windows 7 partition and installed 64-bit Karmic, kernel 2.6.31-14.

Most everything works beautifully out-of-the-box.

Booting took forever until I added the "libata.noncq=force" kernel option. Something about the SATA drive.

However, I have a really weird suspend/resume problem. At first glance, it seems to go just fine: suspend puts everything to sleep and even the orange hardware LED pulses. Resuming gives me a password box which successfully unlocks to gnome.

But: wireless networking never comes back on; I get a message that I'm disconnected, and the gnome-network-manager gui hangs.

Weirder still is that all terminals hang, including gnome-terminal, xterm, and aterm. They stop accepting any keyboard input.

Neither gnome nor the keyboard are hung, though. I can go to the applications menu and open OpenOffice, and type away. I just can't type at any terminals, which makes the problem darn hard to debug.

/var/log/pm-suspend.log from my last suspend:
```

Initial commandline parameters: 
Wed Nov 18 11:10:44 EST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux wool 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
Module                  Size  Used by
cryptd                  8008  0 
aes_x86_64              8992  1 
aes_generic            28480  1 aes_x86_64
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_intelhdmi    14880  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
arc4                    2144  2 
ecb                     3296  2 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
bridge                 56384  0 
stp                     3012  1 bridge
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
bnep                   15168  2 
snd_rawmidi            27360  1 snd_seq_midi
joydev                 13088  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
iwlagn                124768  0 
lp                     11908  0 
acer_wmi               18504  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
btusb                  14260  2 
iwlcore               134820  1 iwlagn
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
psmouse                57124  0 
led_class               5256  2 acer_wmi,iwlcore
serio_raw               6596  0 
atl1c                  36516  0 
parport                40528  2 ppdev,lp
snd_timer              26992  2 snd_pcm,snd_seq
iptable_filter          3872  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              21200  1 iptable_filter
snd                    77096  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               25832  1 ip_tables
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
mac80211              243360  2 iwlagn,iwlcore
cfg80211              152424  3 iwlagn,iwlcore,mac80211
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
i915                  246984  3 
drm                   193856  3 i915
i2c_algo_bit            7076  1 i915
intel_agp              32816  2 i915
video                  23612  1 i915
output                  3680  1 video
             total       used       free     shared    buffers     cached
Mem:       3961380    1040172    2921208          0      35024     556472
-/+ buffers/cache:     448676    3512704
Swap:      5719100          0    5719100
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Wed Nov 18 11:10:45 EST 2009: performing suspend
Switching from vt7 to vt1
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7
Wed Nov 18 11:11:05 EST 2009: Awake.
Wed Nov 18 11:11:05 EST 2009: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Wed Nov 18 11:11:06 EST 2009: Finished.

```

/var/log/syslog from the same time:
```

Nov 18 11:10:44 wool kernel: [  814.359781] CPU0 attaching NULL sched-domain.
Nov 18 11:10:44 wool kernel: [  814.359792] CPU1 attaching NULL sched-domain.
Nov 18 11:10:44 wool kernel: [  814.400429] CPU0 attaching sched-domain:
Nov 18 11:10:44 wool kernel: [  814.400439]  domain 0: span 0-1 level MC
Nov 18 11:10:44 wool kernel: [  814.400445]   groups: 0 1
Nov 18 11:10:44 wool kernel: [  814.400459] CPU1 attaching sched-domain:
Nov 18 11:10:44 wool kernel: [  814.400463]  domain 0: span 0-1 level MC
Nov 18 11:10:44 wool kernel: [  814.400469]   groups: 1 0
Nov 18 11:10:45 wool NetworkManager: <info>  Sleeping...
Nov 18 11:10:45 wool NetworkManager: <info>  (eth0): now unmanaged
Nov 18 11:10:45 wool NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Nov 18 11:10:45 wool NetworkManager: <info>  (eth0): cleaning up...
Nov 18 11:10:45 wool NetworkManager: <info>  (eth0): taking down device.
Nov 18 11:10:45 wool NetworkManager: <info>  (wlan0): now unmanaged
Nov 18 11:10:45 wool NetworkManager: <info>  (wlan0): device state change: 8 -> 1 (reason 37)
Nov 18 11:10:45 wool NetworkManager: <info>  (wlan0): deactivating device (reason: 37).
Nov 18 11:10:45 wool NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1752
Nov 18 11:10:45 wool NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Nov 18 11:10:45 wool NetworkManager: <info>  (wlan0): cleaning up...
Nov 18 11:10:45 wool NetworkManager: <info>  (wlan0): taking down device.
Nov 18 11:10:45 wool avahi-daemon[726]: Withdrawing address record for 192.168.1.6 on wlan0.
Nov 18 11:10:45 wool avahi-daemon[726]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.6.
Nov 18 11:10:45 wool kernel: [  815.280238] wlan0: deauthenticating from 00:18:01:ff:21:19 by local choice (reason=3)
Nov 18 11:10:45 wool avahi-daemon[726]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov 18 11:10:45 wool avahi-daemon[726]: Withdrawing address record for fe80::222:fbff:fe64:8a0c on wlan0.
Nov 18 11:10:45 wool init: anacron main process (2367) killed by TERM signal
Nov 18 11:11:04 wool kernel: [  816.407973] PM: Syncing filesystems ... done.
Nov 18 11:11:04 wool bluetoothd[902]: Stopping security manager 0
Nov 18 11:11:04 wool kernel: [  816.586476] PM: Preparing system for mem sleep
Nov 18 11:11:04 wool kernel: [  816.586482] Freezing user space processes ... (elapsed 1.25 seconds) done.
Nov 18 11:11:04 wool bluetoothd[902]: HCI dev 0 down
Nov 18 11:11:04 wool kernel: [  817.841571] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Nov 18 11:11:04 wool kernel: [  817.841616] PM: Entering mem sleep
Nov 18 11:11:04 wool bluetoothd[902]: Adapter /org/bluez/899/hci0 has been disabled
Nov 18 11:11:04 wool kernel: [  817.841627] Suspending console(s) (use no_console_suspend to debug)
Nov 18 11:11:04 wool kernel: [  817.902732] btusb_bulk_complete: hci0 urb ffff880138f06240 failed to resubmit (1)
Nov 18 11:11:04 wool bluetoothd[902]: HCI dev 0 unregistered
Nov 18 11:11:04 wool kernel: [  817.903726] btusb_bulk_complete: hci0 urb ffff880138f06180 failed to resubmit (1)
Nov 18 11:11:04 wool kernel: [  817.904728] btusb_intr_complete: hci0 urb ffff880138f069c0 failed to resubmit (1)
Nov 18 11:11:04 wool bluetoothd[902]: Unregister path: /org/bluez/899/hci0
Nov 18 11:11:04 wool kernel: [  817.940116] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov 18 11:11:04 wool acpid: client 1166[0:0] has disconnected
Nov 18 11:11:04 wool kernel: [  817.940242] sd 0:0:0:0: [sda] Stopping disk
Nov 18 11:11:04 wool kernel: [  818.880212] atl1c 0000:01:00.0: wake-up capability disabled by ACPI
Nov 18 11:11:04 wool kernel: [  818.880220] atl1c 0000:01:00.0: PME# disabled
Nov 18 11:11:04 wool kernel: [  818.880229] atl1c 0000:01:00.0: PCI INT A disabled
Nov 18 11:11:04 wool kernel: [  819.000106] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Nov 18 11:11:04 wool kernel: [  819.000116] uhci_hcd 0000:00:1d.2: PCI INT D disabled
Nov 18 11:11:04 wool kernel: [  819.000128] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Nov 18 11:11:04 wool kernel: [  819.000139] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Nov 18 11:11:04 wool kernel: [  819.110244] HDA Intel 0000:00:1b.0: PCI INT A disabled
Nov 18 11:11:04 wool kernel: [  819.110307] ACPI handle has no context!
Nov 18 11:11:04 wool kernel: [  819.130171] ehci_hcd 0000:00:1a.7: PCI INT D disabled
Nov 18 11:11:04 wool kernel: [  819.130180] uhci_hcd 0000:00:1a.0: PCI INT A disabled
Nov 18 11:11:04 wool kernel: [  819.191422] PM: suspend devices took 1.350 seconds
Nov 18 11:11:04 wool kernel: [  819.191656] ehci_hcd 0000:00:1d.7: PME# disabled
Nov 18 11:11:04 wool kernel: [  819.211562] ehci_hcd 0000:00:1a.7: PME# disabled
Nov 18 11:11:04 wool kernel: [  819.230755] ACPI: Preparing to enter system sleep state S3
Nov 18 11:11:04 wool kernel: [  819.231045] Disabling non-boot CPUs ...
Nov 18 11:11:04 wool kernel: [  819.340031] CPU 1 is now offline
Nov 18 11:11:04 wool kernel: [  819.340036] SMP alternatives: switching to UP code
Nov 18 11:11:04 wool kernel: [  819.350185] CPU0 attaching NULL sched-domain.
Nov 18 11:11:04 wool kernel: [  819.350190] CPU1 attaching NULL sched-domain.
Nov 18 11:11:04 wool kernel: [  819.350202] CPU0 attaching NULL sched-domain.
Nov 18 11:11:04 wool kernel: [  819.350449] CPU1 is down
Nov 18 11:11:04 wool kernel: [  819.350460] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 18 11:11:04 wool kernel: [  819.350460] Back to C!
Nov 18 11:11:04 wool kernel: [  819.350460] CPU0: Thermal LVT vector (0xfa) already installed
Nov 18 11:11:04 wool kernel: [  819.350460] Enabling non-boot CPUs ...
Nov 18 11:11:04 wool kernel: [  819.350460] SMP alternatives: switching to SMP code
Nov 18 11:11:04 wool bluetoothd[902]: HCI dev 0 registered
Nov 18 11:11:04 wool kernel: [  819.360498] Booting processor 1 APIC 0x1 ip 0x6000
Nov 18 11:11:04 wool kernel: [  819.349936] Initializing CPU#1
Nov 18 11:11:04 wool kernel: [  819.349936] Calibrating delay using timer specific routine.. 2593.54 BogoMIPS (lpj=12967705)
Nov 18 11:11:04 wool kernel: [  819.349936] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 18 11:11:04 wool kernel: [  819.349936] CPU: L2 cache: 3072K
Nov 18 11:11:04 wool kernel: [  819.349936] CPU 1/0x1 -> Node 0
Nov 18 11:11:04 wool kernel: [  819.349936] CPU: Physical Processor ID: 0
Nov 18 11:11:04 wool kernel: [  819.349936] CPU: Processor Core ID: 1
Nov 18 11:11:04 wool kernel: [  819.349936] mce: CPU supports 6 MCE banks
Nov 18 11:11:04 wool kernel: [  819.349936] CPU1: Thermal monitoring enabled (TM2)
Nov 18 11:11:04 wool kernel: [  819.349936] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Nov 18 11:11:04 wool kernel: [  819.522162] CPU1: Genuine Intel(R) CPU           U7300  @ 1.30GHz stepping 0a
Nov 18 11:11:04 wool kernel: [  819.522249] CPU0 attaching NULL sched-domain.
Nov 18 11:11:04 wool kernel: [  819.530024] Switched to high resolution mode on CPU 1
Nov 18 11:11:04 wool kernel: [  819.560029] CPU0 attaching sched-domain:
Nov 18 11:11:04 wool kernel: [  819.560033]  domain 0: span 0-1 level MC
Nov 18 11:11:04 wool kernel: [  819.560036]   groups: 0 1
Nov 18 11:11:04 wool kernel: [  819.560042] CPU1 attaching sched-domain:
Nov 18 11:11:04 wool kernel: [  819.560045]  domain 0: span 0-1 level MC
Nov 18 11:11:04 wool kernel: [  819.560048]   groups: 1 0
Nov 18 11:11:04 wool kernel: [  819.561270] CPU1 is up
Nov 18 11:11:04 wool kernel: [  819.561274] ACPI: Waking up from system sleep state S3
Nov 18 11:11:04 wool kernel: [  821.105598] i915 0000:00:02.0: restoring config space at offset 0x6 (was 0xc, writing 0xc000000c)
Nov 18 11:11:04 wool kernel: [  821.105608] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
Nov 18 11:11:04 wool kernel: [  821.105679] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Nov 18 11:11:04 wool kernel: [  821.105735] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
Nov 18 11:11:04 wool kernel: [  821.105761] ehci_hcd 0000:00:1a.7: PME# disabled
Nov 18 11:11:04 wool kernel: [  821.105802] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0x4, writing 0xd4500004)
Nov 18 11:11:04 wool kernel: [  821.105808] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Nov 18 11:11:04 wool kernel: [  821.105817] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100004, writing 0x100002)
Nov 18 11:11:04 wool kernel: [  821.105855] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
Nov 18 11:11:04 wool kernel: [  821.105870] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xd131d041)
Nov 18 11:11:04 wool kernel: [  821.105877] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xd440d350)
Nov 18 11:11:04 wool kernel: [  821.105884] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x2020)
Nov 18 11:11:04 wool kernel: [  821.105896] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Nov 18 11:11:04 wool kernel: [  821.105905] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Nov 18 11:11:04 wool kernel: [  821.105961] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x4ff)
Nov 18 11:11:04 wool kernel: [  821.105976] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xd231d141)
Nov 18 11:11:04 wool kernel: [  821.105983] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xd340d250)
Nov 18 11:11:04 wool kernel: [  821.105990] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x1010)
Nov 18 11:11:04 wool kernel: [  821.106002] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Nov 18 11:11:04 wool kernel: [  821.106010] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Nov 18 11:11:04 wool kernel: [  821.106082] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Nov 18 11:11:04 wool kernel: [  821.106129] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Nov 18 11:11:04 wool kernel: [  821.106175] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Nov 18 11:11:04 wool kernel: [  821.106230] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
Nov 18 11:11:04 wool kernel: [  821.106254] ehci_hcd 0000:00:1d.7: PME# disabled
Nov 18 11:11:04 wool kernel: [  821.106274] pci 0000:00:1e.0: restoring config space at offset 0xa (was 0x0, writing 0xffffffff)
Nov 18 11:11:04 wool kernel: [  821.106281] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Nov 18 11:11:04 wool kernel: [  821.106288] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
Nov 18 11:11:04 wool kernel: [  821.106294] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
Nov 18 11:11:04 wool kernel: [  821.106309] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Nov 18 11:11:04 wool kernel: [  821.106419] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
Nov 18 11:11:04 wool kernel: [  821.106518] atl1c 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Nov 18 11:11:04 wool kernel: [  821.106556] atl1c 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Nov 18 11:11:04 wool kernel: [  821.106625] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Nov 18 11:11:04 wool kernel: [  821.106664] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd2500004)
Nov 18 11:11:04 wool kernel: [  821.106680] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
Nov 18 11:11:04 wool kernel: [  822.644774] i915 0000:00:02.0: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.706085] [drm] LVDS-8: set mode 1366x768 18
Nov 18 11:11:04 wool kernel: [  822.726393] pci 0000:00:02.1: PME# disabled
Nov 18 11:11:04 wool kernel: [  822.726406] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 18 11:11:04 wool kernel: [  822.726414] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.726442] usb usb3: root hub lost power or was reset
Nov 18 11:11:04 wool kernel: [  822.726465] ehci_hcd 0000:00:1a.7: PME# disabled
Nov 18 11:11:04 wool kernel: [  822.726471] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Nov 18 11:11:04 wool kernel: [  822.726478] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.726491] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 18 11:11:04 wool kernel: [  822.726499] HDA Intel 0000:00:1b.0: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.726537] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 18 11:11:04 wool kernel: [  822.726545] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.726572] usb usb4: root hub lost power or was reset
Nov 18 11:11:04 wool kernel: [  822.726595] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 18 11:11:04 wool kernel: [  822.726603] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.726630] usb usb5: root hub lost power or was reset
Nov 18 11:11:04 wool kernel: [  822.726650] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Nov 18 11:11:04 wool kernel: [  822.726658] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.726686] usb usb6: root hub lost power or was reset
Nov 18 11:11:04 wool kernel: [  822.726709] ehci_hcd 0000:00:1d.7: PME# disabled
Nov 18 11:11:04 wool kernel: [  822.726716] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 18 11:11:04 wool kernel: [  822.726726] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.726740] pci 0000:00:1e.0: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.726755] ahci 0000:00:1f.2: setting latency timer to 64
Nov 18 11:11:04 wool kernel: [  822.726824] atl1c 0000:01:00.0: wake-up capability disabled by ACPI
Nov 18 11:11:04 wool kernel: [  822.726834] atl1c 0000:01:00.0: PME# disabled
Nov 18 11:11:04 wool kernel: [  822.726837] atl1c 0000:01:00.0: wake-up capability disabled by ACPI
Nov 18 11:11:04 wool kernel: [  822.726845] atl1c 0000:01:00.0: PME# disabled
Nov 18 11:11:04 wool kernel: [  823.090117] ata5: SATA link down (SStatus 0 SControl 300)
Nov 18 11:11:04 wool kernel: [  823.110109] ata6: SATA link down (SStatus 0 SControl 300)
Nov 18 11:11:04 wool kernel: [  823.130108] ata2: SATA link down (SStatus 0 SControl 300)
Nov 18 11:11:04 wool kernel: [  823.250105] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 18 11:11:04 wool kernel: [  823.251610] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 18 11:11:04 wool kernel: [  823.260857] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 succeeded
Nov 18 11:11:04 wool kernel: [  823.261155] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 succeeded
Nov 18 11:11:04 wool kernel: [  823.261159] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Nov 18 11:11:04 wool kernel: [  823.261447] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 succeeded
Nov 18 11:11:04 wool kernel: [  823.261742] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 18 11:11:04 wool kernel: [  823.264743] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 18 11:11:04 wool kernel: [  823.264748] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Nov 18 11:11:04 wool kernel: [  823.265049] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
Nov 18 11:11:04 wool kernel: [  823.265270] ata1.00: configured for UDMA/133
Nov 18 11:11:04 wool kernel: [  823.405995] sd 0:0:0:0: [sda] Starting disk
Nov 18 11:11:04 wool kernel: [  823.540104] usb 2-5: reset high speed USB device using ehci_hcd and address 2
Nov 18 11:11:04 wool kernel: [  823.840101] usb 6-2: reset full speed USB device using uhci_hcd and address 2
Nov 18 11:11:04 wool kernel: [  823.999203] btusb 6-2:1.0: no reset_resume for driver btusb?
Nov 18 11:11:04 wool kernel: [  823.999207] btusb 6-2:1.1: no reset_resume for driver btusb?
Nov 18 11:11:04 wool kernel: [  824.740096] __ratelimit: 1 callbacks suppressed
Nov 18 11:11:04 wool kernel: [  824.740099] ACPI: EC: missing confirmations, switch off interrupt mode.
Nov 18 11:11:04 wool kernel: [  825.040109] ACPI Error (dswload-0790): [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS
Nov 18 11:11:04 wool kernel: [  825.040117] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog 20090521 psloop-227
Nov 18 11:11:04 wool kernel: [  825.040124] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.WMID.WMBA] (Node ffff88013ba4f160), AE_ALREADY_EXISTS
Nov 18 11:11:04 wool kernel: [  825.040141] ACPI: Marking method WMBA as Serialized because of AE_ALREADY_EXISTS error
Nov 18 11:11:04 wool kernel: [  825.120618] PM: resume devices took 4.020 seconds
Nov 18 11:11:04 wool kernel: [  825.120671] PM: Finishing wakeup.
Nov 18 11:11:05 wool bluetoothd[902]: HCI dev 0 up
Nov 18 11:11:05 wool bluetoothd[902]: Starting security manager 0
Nov 18 11:11:05 wool kernel: [  825.120673] Restarting tasks ... done.
Nov 18 11:11:05 wool acpid: client connected from 1166[0:0]
Nov 18 11:11:05 wool bluetoothd[902]: Parsing /etc/bluetooth/serial.conf failed: No such file or directory
Nov 18 11:11:05 wool bluetoothd[902]: Adapter /org/bluez/899/hci0 has been enabled
Nov 18 11:11:05 wool anacron[2499]: Anacron 2.3 started on 2009-11-18
Nov 18 11:11:05 wool anacron[2499]: Will run job `cron.daily' in 5 min.
Nov 18 11:11:05 wool anacron[2499]: Jobs will be executed sequentially
Nov 18 11:11:05 wool NetworkManager: <info>  Waking up...
Nov 18 11:11:05 wool NetworkManager: <info>  (eth0): now managed
Nov 18 11:11:05 wool NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov 18 11:11:05 wool kernel: [  825.361660] atl1c 0000:01:00.0: irq 29 for MSI/MSI-X
Nov 18 11:11:05 wool kernel: [  825.362563] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 11:11:05 wool NetworkManager: <info>  (eth0): bringing up device.
Nov 18 11:11:05 wool NetworkManager: <info>  (eth0): preparing device.
Nov 18 11:11:05 wool NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov 18 11:11:05 wool NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 18 11:11:05 wool NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): now managed
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): bringing up device.
Nov 18 11:11:05 wool kernel: [  825.395405] Registered led device: iwl-phy0::radio
Nov 18 11:11:05 wool kernel: [  825.395452] Registered led device: iwl-phy0::assoc
Nov 18 11:11:05 wool kernel: [  825.395492] Registered led device: iwl-phy0::RX
Nov 18 11:11:05 wool kernel: [  825.395532] Registered led device: iwl-phy0::TX
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): preparing device.
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Nov 18 11:11:05 wool kernel: [  825.432681] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 18 11:11:05 wool bluetoothd[902]: Inquiry Failed with status 0x12
Nov 18 11:11:05 wool wpa_supplicant[1059]: CTRL-EVENT-SCAN-RESULTS 
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Nov 18 11:11:05 wool wpa_supplicant[1059]: CTRL-EVENT-SCAN-RESULTS 
Nov 18 11:11:05 wool NetworkManager: <info>  Activation (wlan0) starting connection 'Auto REDBEAK'
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov 18 11:11:05 wool NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 18 11:11:05 wool NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 18 11:11:05 wool NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 18 11:11:05 wool NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 18 11:11:05 wool NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov 18 11:11:05 wool NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto REDBEAK' has security, but secrets are required.
Nov 18 11:11:05 wool NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Nov 18 11:11:05 wool NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 18 11:11:06 wool init: anacron main process (2499) killed by TERM signal
Nov 18 11:11:06 wool kernel: [  826.861207] CPU0 attaching NULL sched-domain.
Nov 18 11:11:06 wool kernel: [  826.861220] CPU1 attaching NULL sched-domain.
Nov 18 11:11:06 wool kernel: [  826.900182] CPU0 attaching sched-domain:
Nov 18 11:11:06 wool kernel: [  826.900188]  domain 0: span 0-1 level MC
Nov 18 11:11:06 wool kernel: [  826.900192]   groups: 0 1
Nov 18 11:11:06 wool kernel: [  826.900199]   domain 1: span 0-1 level CPU
Nov 18 11:11:06 wool kernel: [  826.900209]    groups: 0-1 (__cpu_power = 2048)
Nov 18 11:11:06 wool kernel: [  826.900217] CPU1 attaching sched-domain:
Nov 18 11:11:06 wool kernel: [  826.900220]  domain 0: span 0-1 level MC
Nov 18 11:11:06 wool kernel: [  826.900223]   groups: 1 0
Nov 18 11:11:06 wool kernel: [  826.900228]   domain 1: span 0-1 level CPU
Nov 18 11:11:06 wool kernel: [  826.900232]    groups: 0-1 (__cpu_power = 2048)
Nov 18 11:11:11 wool wpa_supplicant[1059]: Failed to initiate AP scan.
Nov 18 11:11:21 wool NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> inactive
Nov 18 11:11:31 wool wpa_supplicant[1059]: Failed to initiate AP scan.
Nov 18 11:11:31 wool NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Nov 18 11:11:41 wool NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> inactive
Nov 18 11:12:11 wool wpa_supplicant[1059]: Failed to initiate AP scan.
Nov 18 11:12:11 wool NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Nov 18 11:12:21 wool NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> inactive
Nov 18 11:13:11 wool wpa_supplicant[1059]: Failed to initiate AP scan.
Nov 18 11:13:11 wool NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Nov 18 11:13:20 wool kernel: [  960.750254] INFO: task events/0:9 blocked for more than 120 seconds.
Nov 18 11:13:20 wool kernel: [  960.750263] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 18 11:13:20 wool kernel: [  960.750269] events/0      D 00000000ffffffff     0     9      2 0x00000000
Nov 18 11:13:20 wool kernel: [  960.750281]  ffff88013bac9a40 0000000000000046 ffff88013bac99c0 0000000000015880
Nov 18 11:13:20 wool kernel: [  960.750292]  ffff88013babde70 0000000000015880 0000000000015880 0000000000015880
Nov 18 11:13:20 wool kernel: [  960.750301]  0000000000015880 ffff88013babde70 0000000000015880 0000000000015880
Nov 18 11:13:20 wool kernel: [  960.750311] Call Trace:
Nov 18 11:13:20 wool kernel: [  960.750329]  [<ffffffff81527935>] schedule_timeout+0x1d5/0x230
Nov 18 11:13:20 wool kernel: [  960.750342]  [<ffffffff812d289b>] ? acpi_ut_delete_internal_obj+0x193/0x19b
Nov 18 11:13:20 wool kernel: [  960.750352]  [<ffffffff812c8c85>] ? acpi_ns_search_one_scope+0x1d/0x46
Nov 18 11:13:20 wool kernel: [  960.750361]  [<ffffffff812c8d69>] ? acpi_ns_search_and_enter+0xbb/0x186
Nov 18 11:13:20 wool kernel: [  960.750369]  [<ffffffff815287e6>] __down_timeout+0x76/0xd0
Nov 18 11:13:20 wool kernel: [  960.750379]  [<ffffffff8107d739>] down_timeout+0x59/0x60
Nov 18 11:13:20 wool kernel: [  960.750387]  [<ffffffff812affa2>] acpi_os_wait_semaphore+0x49/0x57
Nov 18 11:13:20 wool kernel: [  960.750396]  [<ffffffff812c4f18>] acpi_ex_system_wait_mutex+0x3c/0x4e
Nov 18 11:13:20 wool kernel: [  960.750403]  [<ffffffff8107d71d>] ? down_timeout+0x3d/0x60
Nov 18 11:13:20 wool kernel: [  960.750412]  [<ffffffff812bc195>] acpi_ds_begin_method_execution+0xe0/0x16e
Nov 18 11:13:20 wool kernel: [  960.750420]  [<ffffffff812cda81>] acpi_ps_execute_method+0x33/0x2a2
Nov 18 11:13:20 wool kernel: [  960.750429]  [<ffffffff812c9931>] acpi_ns_evaluate+0xe1/0x1a8
Nov 18 11:13:20 wool kernel: [  960.750437]  [<ffffffff812c93b1>] acpi_evaluate_object+0xf9/0x1f2
Nov 18 11:13:20 wool kernel: [  960.750448]  [<ffffffff814196c7>] wmi_evaluate_method+0x107/0x120
Nov 18 11:13:20 wool kernel: [  960.750457]  [<ffffffff81053d90>] ? wake_up_process+0x10/0x20
Nov 18 11:13:20 wool kernel: [  960.750464]  [<ffffffff81052119>] ? update_curr+0x189/0x190
Nov 18 11:13:20 wool kernel: [  960.750471]  [<ffffffff8105225b>] ? dequeue_entity+0x1b/0x240
Nov 18 11:13:20 wool kernel: [  960.750494]  [<ffffffffa01fd7b0>] ? acer_rfkill_update+0x0/0xa0 [acer_wmi]
Nov 18 11:13:20 wool kernel: [  960.750505]  [<ffffffffa01fd17a>] WMI_execute_u32+0x4a/0x90 [acer_wmi]
Nov 18 11:13:20 wool kernel: [  960.750517]  [<ffffffffa01fd608>] get_u32+0x88/0x100 [acer_wmi]
Nov 18 11:13:20 wool kernel: [  960.750528]  [<ffffffffa01fd7b0>] ? acer_rfkill_update+0x0/0xa0 [acer_wmi]
Nov 18 11:13:20 wool kernel: [  960.750538]  [<ffffffffa01fd7e8>] acer_rfkill_update+0x38/0xa0 [acer_wmi]
Nov 18 11:13:20 wool kernel: [  960.750549]  [<ffffffff810737a5>] run_workqueue+0x95/0x170
Nov 18 11:13:20 wool kernel: [  960.750558]  [<ffffffff81073924>] worker_thread+0xa4/0x120
Nov 18 11:13:20 wool kernel: [  960.750567]  [<ffffffff81078b30>] ? autoremove_wake_function+0x0/0x40
Nov 18 11:13:20 wool kernel: [  960.750575]  [<ffffffff81073880>] ? worker_thread+0x0/0x120
Nov 18 11:13:20 wool kernel: [  960.750583]  [<ffffffff81078746>] kthread+0xa6/0xb0
Nov 18 11:13:20 wool kernel: [  960.750591]  [<ffffffff810130ea>] child_rip+0xa/0x20
Nov 18 11:13:20 wool kernel: [  960.750609]  [<ffffffff810786a0>] ? kthread+0x0/0xb0
Nov 18 11:13:20 wool kernel: [  960.750615]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
Nov 18 11:13:20 wool kernel: [  960.750657] INFO: task nm-applet:1688 blocked for more than 120 seconds.
Nov 18 11:13:20 wool kernel: [  960.750661] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 18 11:13:20 wool kernel: [  960.750666] nm-applet     D 00000000ffffffff     0  1688   1468 0x00000000
Nov 18 11:13:20 wool kernel: [  960.750676]  ffff880132d5fd38 0000000000000086 ffff880132d5fcb8 0000000000015880
Nov 18 11:13:20 wool kernel: [  960.750686]  ffff88013a4283b0 0000000000015880 0000000000015880 0000000000015880
Nov 18 11:13:20 wool kernel: [  960.750695]  0000000000015880 ffff88013a4283b0 0000000000015880 0000000000015880
Nov 18 11:13:20 wool kernel: [  960.750704] Call Trace:
Nov 18 11:13:20 wool kernel: [  960.750713]  [<ffffffff81527935>] schedule_timeout+0x1d5/0x230
Nov 18 11:13:20 wool kernel: [  960.750722]  [<ffffffff81053b38>] ? try_to_wake_up+0x118/0x340
Nov 18 11:13:20 wool kernel: [  960.750730]  [<ffffffff815275e5>] wait_for_common+0xd5/0x170
Nov 18 11:13:20 wool kernel: [  960.750738]  [<ffffffff81053d60>] ? default_wake_function+0x0/0x10
Nov 18 11:13:20 wool kernel: [  960.750746]  [<ffffffff81527718>] wait_for_completion+0x18/0x20
Nov 18 11:13:20 wool kernel: [  960.750755]  [<ffffffff81074004>] flush_work+0x74/0xc0
Nov 18 11:13:20 wool kernel: [  960.750763]  [<ffffffff81073f50>] ? wq_barrier_func+0x0/0x10
Nov 18 11:13:20 wool kernel: [  960.750771]  [<ffffffff81075053>] schedule_on_each_cpu+0xc3/0x100
Nov 18 11:13:20 wool kernel: [  960.750781]  [<ffffffff810e4f70>] lru_add_drain_all+0x10/0x20
Nov 18 11:13:20 wool kernel: [  960.750790]  [<ffffffff810fa5a5>] sys_mlock+0x45/0x100
Nov 18 11:13:20 wool kernel: [  960.750799]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
Nov 18 11:13:21 wool NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> inactive

```

There you can see some weird stuff going on with wpa_supplicant and "INFO: task events/0:9 blocked for more than 120 seconds." I don't exactly know what those mean, though.

Any theories? Anything I should try? Or more information I could provide?

---

### Post by robogock on 2009-11-18
Also, I've now determined that neither bluetooth nor sound work after a resume, either. So basically, all hardware-specific stuff is borked, except video, keyboard, and touchpad.

Suspend/resume works fine in windows, though...

---

### Post by robogock on 2009-11-19
(bump)

Any ideas? I'm really stuck here... :(

---

### Post by robogock on 2009-11-19
Ooh! Hey! I may have just fixed things! I selected the "karmic-proposed" repository in synaptic, and installed all the available updates. No idea which fixed things; I'm guessing the upgrade to kernel 2.6.31-15 (from -14).

I'm going to tentatively update this to SOLVED, though I admittedly haven't tested much yet. Two suspend/resume cycles have left me with what appears to be a fully-functioning system, anyway.

---

### Post by robogock on 2009-11-23
...Aaaand, updates today broke suspend again. I think the only updates were nautilus-related. Any idea why that might have broken suspend/resume?

---

### Post by robogock on 2009-11-25
I realize I'm talking to myself here, but I've added "no_console_suspend" to the boot options, and suspend/resume seems to be working once again. I'm keeping my fingers crossed...

---

### Post by RabidNelson on 2009-11-27
You are not alone! I'm so glad I finally found somebody with the exact same symptoms as me. I was beginning to think I was going insane.

I have an Acer Aspire 1410 AS1410-Kk22 bought in Japan. Pretty much every detail of your problem has been the same for me.

How is "no_console_suspend" working out for you? I haven't tried it, but I found another cleaner solution. If you look at your errors, you're mostly getting them from the "acer-wmi" module. Our hardware actually doesn't need it, so just disable it!

In the file "/etc/modprobe.d/blacklist.conf" I added the line "blacklist acer-wmi". Then just reboot, and everything should be solved. I've been unable to find a single disadvantage in removing this module. Like I said, it's worthless.

Hope this information to helpful to someone out there.

---

### Post by robogock on 2009-11-28
"no_console_suspend" mostly worked, though sound didn't properly come back after a suspend.

However, your fix seems to work perfectly! Hooray! Thanks so much for that!

---

### Post by robogock on 2009-11-30
I take back my "works perfectly" comment... my problem now is that it takes 2-3 tries to resume. As in: I suspend the laptop (by closing the lid or by selecting it from the menu; the results are the same), then when I hit a key to resume it wakes up, gives me the password window... and immediately suspends again. It takes two or three tries (varies) before it stays awake.

Since it hasn't yet completely refused to wake up, and once it does wake up everything works like it should, I can live with this state. But if anyone has any ideas how to keep it from immediately suspending after a resume, let me know...

---

### Post by RabidNelson on 2009-11-30
Hm, that's strange. It's perfectly fine for me, although I'm using a different model laptop.

Have you tried undoing some of the changes you did earlier trying to fix it? On my computer my BIOS and my packages are up-to-date, but besides that everything is default, even boot options.

---

### Post by PatrickVogeli on 2009-11-30
I have a 1810TZ and suspend is working fine here. I'm using a 2.6.31.6 vanilla kernel, but I think the standard ubuntu worked too.

PD: what BIOS version do you have?

---

### Post by robogock on 2009-11-30
Bios is 3115. Looks like Acer has up to version 3303, so I guess I can try to upgrade, once I figure out how to do that. :)

I tried removing the "libata.force=noncq" from my boot prompt, and went back to taking forever to boot; with that option, it boots in under 30 seconds. Maybe the updated bios will fix that? The drive is a Hitachi HTS545032B9A300, according to the bios.

Currently the system takes 2 tries to resume from a suspend caused by closing the lid, but resumes correctly if I suspend from the menu or from Fn-F4.

I'm still running the 2.6.31-15 kernel. I guess I could update that, as well... are later versions in the karmic-proposed repository? I'm nervous about other things breaking if I use that.

---

### Post by PatrickVogeli on 2009-11-30
I don't know if updating the bios will help. I have a Toshiba Hard drive and I never had to use the noncq fix. 

Mi girlfriend's Packard Bell 1810 clone had to use that noncq fix, but after flashing the bios with newest version (v3303) and the updating to Karmic solved it.

---

### Post by robogock on 2009-11-30
Updating the bios let me boot in a reasonable amount of time without the noncq option, but didn't change the sleep issue. Hrm. I guess I should just get in the habit of sleeping with Fn-F4 before closing the lid, and/or waking it twice...

---

### Post by fondle-em on 2009-11-30
> **robogock said:**
> I suspend the laptop (by closing the lid or by selecting it from the menu; the results are the same), then when I hit a key to resume it wakes up, gives me the password window... and immediately suspends again.

I have this exact issue on a Dell 1420, but it's not consistent at all - sometimes suspend/resume works fine, and other times it acts like it's resuming, then stops accepting keyboard and mouse input, then goes back into suspend.  Pressing the power button will then reliably wake it from this second, unwanted suspend.  This is not a major deal-breaker sort of issue as it always wakes back up eventually and never loses any data in the process... but it's pretty annoying.

---

### Post by bob94025 on 2009-12-12
I had the same problem reported by the original poster on my 1810TZ (bios 3303). It would resume from suspend, but most of the hardware wouldn't work and I couldn't type anything into a console. Adding "blacklist acer-wmi" to /etc/modprobe.d/blacklist.conf as suggested by RabidNelson completely fixed it. Suspend/resume works perfecctly now! Thanks!

---

### Post by linuxcss on 2009-12-17
thanks for the blacklist tip,
i was wrestling with this a lot and without it even the bios at 3305 did not resume networking nor allow typing in terminal windows ... at least preliminary testing seems to work

now if we could only get the internal microphone to work in sound recorder and skype... 
any one have tips for that?

---

### Post by lokman on 2009-12-28
The blacklist tip worked perfectly on my Acer 1410.

A bit of history:
I installed Karmic Koala 2.6.31-14 a month ago and everything worked fine. I then accepted the updates and wireless no longer worked. Terminal also hang, exactly as described. Tried to google the solution but couldn't find any. I had no choice but to reinstall. Luckily I used a different partition for home, so it wasn't so bad. 

3 days ago I installed tinymce and bluefish and unfortunately experienced the same symptoms all over again. I've been searching high and low for this solution and finally found this. Now my 1410 worked beautifully again.

Thanks for the tip. I wish I had found this the first time around.

---

### Post by mh17 on 2010-01-05
Thank you very much for the blacklist-tip. I've got an Acer Aspire 1810T with exactly the same problems. I had to use Windows for several weeks, because I really need suspend-to-ram at work. Now I can use Ubuntu again. It's a good day!! :):):)

---

### Post by tition on 2010-01-31
I have the same problem here. All symptoms were previously described: the system does not restore properly after being suspended. I am using the latest Ubuntu version as updated by the software center.

---

### Post by jb68 on 2010-02-17
Hi,
Having a 1810TZ I got the same issue with booting forever and I fixed it by changing in BIOS HD type to IDE from AHCI. 

I have bios 3115

---

### Post by fishbulb1022 on 2010-02-27
Where did you get your BIOS upgrades? I would assume acer's site, but they didn't have much info there, at least not for my model (Aspire 7740-6656). My computer won't come back from sleep at all. It looks like its about to, backlight seems to turn on, then it hangs. Also, I'm having some trouble with the brightness. Using fn and the right and left arrows, I get the little brightness indicator pop up in the upper left of my screen, but the brightness doesn't actually change. Any tips?

---

