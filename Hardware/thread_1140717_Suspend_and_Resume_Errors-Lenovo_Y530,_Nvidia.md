---
title: "Suspend and Resume Errors-Lenovo Y530, Nvidia"
date: 2009-04-27
forum: Hardware
---

### Post by meatlover on 2009-04-27
I have a Lenovo Ideapad Y530 model 2PU.  I have managed to get everything working, except for suspending/resuming.

Relevant information about my computer

Graphics Card: Nvidia Geforce 9300M
3gb ddr3 ram
Partition with windows vista
Nvidia driver from the Nvidia website
Compiz Running
Ubuntu 9.04 32bit

When I suspend to ram, my computer suspends quickly and turns the screen off, then in less than a second, it resumes into a blank screen with a blinking cursor.  All keys are locked and no combination works, including the alt + sysrq + r etc. keys.  I checked pm-suspend log and it says it is working correctly:



```
Initial commandline parameters: 
Mon Apr 27 17:43:08 PDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux computer-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
nvidia               7236444  45 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         435636  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
arc4                    9856  2 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ecb                    10752  2 
uvcvideo               63240  0 
snd                    62628  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                100228  0 
iwlcore                93184  1 iwlagn
compat_ioctl32          9344  1 uvcvideo
soundcore              15200  1 snd
psmouse                61972  0 
sdhci_pci              15232  0 
mac80211              217208  2 iwlagn,iwlcore
pcspkr                 10496  0 
serio_raw              13316  0 
intel_agp              34108  0 
agpgart                42696  2 nvidia,intel_agp
video                  25360  0 
asus_laptop            24440  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
sdhci                  23940  1 sdhci_pci
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
led_class              12036  2 iwlcore,asus_laptop
cfg80211               38032  3 iwlagn,iwlcore,mac80211
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       2546444    1595692     950752          0     787744     328480
-/+ buffers/cache:     479468    2066976
Swap:      7462152          0    7462152
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/usr/lib/pm-utils/sleep.d/45iwlist suspend suspend: /sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90chvt suspend suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/etc/pm/sleep.d/99laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Mon Apr 27 17:43:09 PDT 2009: performing suspend

```

Everything seems to be normal in the Syslog at the exact time I call suspend:

```
27 17:43:08 computer-laptop anacron[6361]: Anacron 2.3 started on 2009-04-27
Apr 27 17:43:08 computer-laptop anacron[6361]: Normal exit (0 jobs run)
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  Sleeping... 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (eth0): now unmanaged 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (eth0): cleaning up... 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (eth0): taking down device. 
Apr 27 17:43:08 computer-laptop avahi-daemon[4252]: Withdrawing address record for fe80::224:8cff:fe6f:3496 on eth0.
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (wlan0): now unmanaged 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
Apr 27 17:43:08 computer-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 37). 
Apr 27 17:43:09 computer-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5056 
Apr 27 17:43:09 computer-laptop kernel: [ 4106.673141] wlan0: disassociating by local choice (reason=3)
Apr 27 17:43:09 computer-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Apr 27 17:43:09 computer-laptop avahi-daemon[4252]: Withdrawing address record for 192.168.1.101 on wlan0.
Apr 27 17:43:09 computer-laptop avahi-daemon[4252]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Apr 27 17:43:09 computer-laptop avahi-daemon[4252]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 27 17:43:09 computer-laptop NetworkManager: <info>  (wlan0): cleaning up... 
Apr 27 17:43:09 computer-laptop NetworkManager: <info>  (wlan0): taking down device. 
Apr 27 17:43:09 computer-laptop avahi-daemon[4252]: Withdrawing address record for fe80::222:faff:fe48:f8ce on wlan0.
Apr 27 17:43:09 computer-laptop postfix/master[3954]: reload configuration /etc/postfix
```

However, I believe it may be Nvidia related based on the following messages in the syslog (immediately after hard reboot):

```
27 17:52:04 computer-laptop kernel: [   59.816120] Corrupted low memory at c000fcf4 (fcf4 phys) = 83840000
Apr 27 17:52:04 computer-laptop kernel: [   59.816125] Corrupted low memory at c000fcf8 (fcf8 phys) = 0010000a
Apr 27 17:52:04 computer-laptop kernel: [   59.816132] ------------[ cut here ]------------
Apr 27 17:52:04 computer-laptop kernel: [   59.816135] WARNING: at /build/buildd/linux-2.6.28/arch/x86/kernel/setup.c:719 check_for_bios_corruption+0xc8/0xd0()
Apr 27 17:52:04 computer-laptop kernel: [   59.816137] Memory corruption detected in low memory
Apr 27 17:52:04 computer-laptop kernel: [   59.816139] Modules linked in: nvidia(P) binfmt_misc ppdev bridge stp bnep input_polldev lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm arc4 snd_seq_dummy ecb snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn iwlcore snd_seq uvcvideo snd_timer snd_seq_device compat_ioctl32 mac80211 psmouse intel_agp sdhci_pci snd soundcore videodev serio_raw agpgart iTCO_wdt ricoh_mmc video sdhci pcspkr asus_laptop snd_page_alloc v4l1_compat cfg80211 iTCO_vendor_support output led_class ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
Apr 27 17:52:04 computer-laptop kernel: [   59.816198] Pid: 0, comm: swapper Tainted: P           2.6.28-11-generic #42-Ubuntu
Apr 27 17:52:04 computer-laptop kernel: [   59.816200] Call Trace:
Apr 27 17:52:04 computer-laptop kernel: [   59.816204]  [<c0139ab0>] warn_slowpath+0x60/0x80
Apr 27 17:52:04 computer-laptop kernel: [   59.816208]  [<c013a2f9>] ? release_console_sem+0x1c9/0x200
Apr 27 17:52:04 computer-laptop kernel: [   59.816213]  [<c015aee3>] ? tick_dev_program_event+0x33/0xc0
Apr 27 17:52:04 computer-laptop kernel: [   59.816216]  [<c0500ac6>] ? printk+0x18/0x1a
Apr 27 17:52:04 computer-laptop kernel: [   59.816219]  [<c01079c8>] check_for_bios_corruption+0xc8/0xd0
Apr 27 17:52:04 computer-laptop kernel: [   59.816223]  [<c01079d8>] periodic_check_for_corruption+0x8/0x30
Apr 27 17:52:04 computer-laptop kernel: [   59.816226]  [<c0143b00>] run_timer_softirq+0x130/0x200
Apr 27 17:52:04 computer-laptop kernel: [   59.816229]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
Apr 27 17:52:04 computer-laptop kernel: [   59.816232]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
Apr 27 17:52:04 computer-laptop kernel: [   59.816236]  [<c013f197>] __do_softirq+0x97/0x170
Apr 27 17:52:04 computer-laptop kernel: [   59.816239]  [<c0106f30>] ? timer_interrupt+0x30/0x80
Apr 27 17:52:04 computer-laptop kernel: [   59.816242]  [<c013f2cd>] do_softirq+0x5d/0x60
Apr 27 17:52:04 computer-laptop kernel: [   59.816244]  [<c013f445>] irq_exit+0x55/0x90
Apr 27 17:52:04 computer-laptop kernel: [   59.816247]  [<c0106853>] do_IRQ+0x83/0xa0
Apr 27 17:52:04 computer-laptop kernel: [   59.816250]  [<c01051f3>] common_interrupt+0x23/0x30
Apr 27 17:52:04 computer-laptop kernel: [   59.816253]  [<c0319417>] ? acpi_idle_enter_bm+0x269/0x2b8
Apr 27 17:52:04 computer-laptop kernel: [   59.816257]  [<c040f4df>] cpuidle_idle_call+0x6f/0xd0
Apr 27 17:52:04 computer-laptop kernel: [   59.816260]  [<c010285d>] cpu_idle+0x6d/0xd0
Apr 27 17:52:04 computer-laptop kernel: [   59.816263]  [<c04f110e>] rest_init+0x4e/0x60
Apr 27 17:52:04 computer-laptop kernel: [   59.816265] ---[ end trace 512babe2d9f27f83 ]---
```


As a side issue, any idea what the memory corruption is?  I've seen this on other Y530 Ideapad's but the issue was never resolved.

---

### Post by meatlover on 2009-04-27
I should add that on this particular attempt at suspending, I had pressed ctrl + alt + F1 to get into console mode, to see if the problem also occured there.

---

### Post by meatlover on 2009-04-27
It seems that hibernate has the same sort of problem.  This time I hibernated from directly from X.  Here is the pm-suspend log:

```
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Mon Apr 27 20:42:52 PDT 2009: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux computer-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
nvidia               7236444  39 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  6 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_hda_intel,snd_pcm_oss
arc4                    9856  2 
ecb                    10752  2 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
iwlagn                100228  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlcore                93184  1 iwlagn
uvcvideo               63240  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32          9344  1 uvcvideo
psmouse                61972  0 
snd                    62628  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
videodev               41600  1 uvcvideo
mac80211              217208  2 iwlagn,iwlcore
pcspkr                 10496  0 
asus_laptop            24440  0 
serio_raw              13316  0 
video                  25360  4 
intel_agp              34108  0 
agpgart                42696  2 nvidia,intel_agp
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
v4l1_compat            21764  2 uvcvideo,videodev
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
led_class              12036  2 iwlcore,asus_laptop
cfg80211               38032  3 iwlagn,iwlcore,mac80211
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       2546444     599100    1947344          0      71448     270996
-/+ buffers/cache:     256656    2289788
Swap:      7462152          0    7462152
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/45iwlist hibernate hibernate: /sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90chvt hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/etc/pm/sleep.d/99laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Mon Apr 27 20:42:54 PDT 2009: performing hibernate
Mon Apr 27 20:47:47 PDT 2009: Awake.
Mon Apr 27 20:47:47 PDT 2009: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/etc/pm/sleep.d/99laptop-mode thaw hibernate: Laptop mode disabled, not active
success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: /usr/lib/pm-utils/sleep.d/95hdparm-apm: 50: get_power_status: not found

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
success.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90chvt thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci thaw hibernate: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/45iwlist thaw hibernate: /sbin/iwlist
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:31:8F:E2
                    ESSID:"IAMAMERICA"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=81/100  Signal level:-53 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 000A49414D414D4552494341
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD09001018020010000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000005b43333dc
                    Extra: Last beacon: 5764ms ago
          Cell 02 - Address: 00:16:B6:02:E7:72
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/100  Signal level:-71 dBm  Noise level=-82 dBm
                    Encryption key:off
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000000d8072183
                    Extra: Last beacon: 280ms ago
          Cell 03 - Address: 00:1D:6A:B5:46:3B
                    ESSID:"default"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level:-36 dBm  Noise level=-83 dBm
                    Encryption key:on
                    IE: Unknown: 000764656661756C74
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1013FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336E1013FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070500000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B0001031047001000000000000000000000000000000000102100074169726C696E6B10230006415236373057102400064152363730571042000830303030303030301054000800060050F20400011011000641523637305710080002008E
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=0000005a21ecf743
                    Extra: Last beacon: 9816ms ago

success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
```

Here is the syslog:

```
Apr 27 20:42:52 computer-laptop anacron[7539]: Anacron 2.3 started on 2009-04-27
Apr 27 20:42:52 computer-laptop anacron[7539]: Normal exit (0 jobs run)
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  Sleeping... 
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  (eth0): now unmanaged 
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1 
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  (eth0): cleaning up... 
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  (eth0): taking down device. 
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  (wlan0): now unmanaged 
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 37). 
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 3614 
Apr 27 20:42:52 computer-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Apr 27 20:42:52 computer-laptop avahi-daemon[2975]: Withdrawing address record for 192.168.1.101 on wlan0.
Apr 27 20:42:52 computer-laptop avahi-daemon[2975]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  (wlan0): cleaning up... 
Apr 27 20:42:52 computer-laptop NetworkManager: <info>  (wlan0): taking down device. 
Apr 27 20:42:52 computer-laptop avahi-daemon[2975]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 27 20:42:52 computer-laptop kernel: [10202.071344] wlan0: disassociating by local choice (reason=3)
Apr 27 20:42:52 computer-laptop avahi-daemon[2975]: Withdrawing address record for fe80::222:faff:fe48:f8ce on wlan0.
Apr 27 20:42:52 computer-laptop postfix/master[2676]: reload configuration /etc/postfix
Apr 27 20:42:54 computer-laptop kernel: [10204.368783] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
Apr 27 20:42:54 computer-laptop kernel: [10204.368786] PM: Marking nosave pages: 0000000000007000 - 0000000000010000
Apr 27 20:42:54 computer-laptop kernel: [10204.368789] PM: Marking nosave pages: 0000000000092000 - 0000000000100000
Apr 27 20:42:54 computer-laptop kernel: [10204.368794] PM: Basic memory bitmaps created
Apr 27 20:47:47 computer-laptop kernel: [10204.368796] PM: Syncing filesystems ... done.
Apr 27 20:47:47 computer-laptop kernel: [10204.377492] Freezing user space processes ... (elapsed 0.00 seconds) done.
Apr 27 20:47:47 computer-laptop kernel: [10204.378152] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Apr 27 20:47:47 computer-laptop kernel: [10204.378194] PM: Shrinking memory...  ^H-^H\^H|^Hdone (26489 pages freed)
Apr 27 20:47:47 computer-laptop kernel: [10204.823410] PM: Freed 105956 kbytes in 0.44 seconds (240.80 MB/s)
Apr 27 20:47:47 computer-laptop kernel: [10204.823423] Suspending console(s) (use no_console_suspend to debug)
Apr 27 20:47:47 computer-laptop kernel: [10204.824743] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Apr 27 20:47:47 computer-laptop kernel: [10204.824916] pciehp 0000:00:1c.2:pcie02: pciehp_suspend ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10204.824919] pciehp 0000:00:1c.1:pcie02: pciehp_suspend ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10204.824921] pciehp 0000:00:1c.0:pcie02: pciehp_suspend ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10204.824923] pciehp 0000:00:01.0:pcie02: pciehp_suspend ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10204.826097] ACPI handle has no context!
Apr 27 20:47:47 computer-laptop kernel: [10204.826104] sdhci-pci 0000:07:03.1: PCI INT B disabled
Apr 27 20:47:47 computer-laptop kernel: [10204.826110] ACPI handle has no context!
Apr 27 20:47:47 computer-laptop kernel: [10205.000449] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Apr 27 20:47:47 computer-laptop kernel: [10205.000498] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Apr 27 20:47:47 computer-laptop kernel: [10205.000545] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Apr 27 20:47:47 computer-laptop kernel: [10205.000592] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Apr 27 20:47:47 computer-laptop kernel: [10205.000597] pciehp 0000:00:1c.2:pcie02: pciehp_suspend ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10205.000648] pciehp 0000:00:1c.1:pcie02: pciehp_suspend ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10205.000699] pciehp 0000:00:1c.0:pcie02: pciehp_suspend ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10205.032121] HDA Intel 0000:00:1b.0: PCI INT A disabled
Apr 27 20:47:47 computer-laptop kernel: [10205.049164] ehci_hcd 0000:00:1a.7: PCI INT C disabled
Apr 27 20:47:47 computer-laptop kernel: [10205.049218] uhci_hcd 0000:00:1a.2: PCI INT C disabled
Apr 27 20:47:47 computer-laptop kernel: [10205.049266] uhci_hcd 0000:00:1a.1: PCI INT B disabled
Apr 27 20:47:47 computer-laptop kernel: [10205.049313] uhci_hcd 0000:00:1a.0: PCI INT A disabled
Apr 27 20:47:47 computer-laptop kernel: [10205.049316] pciehp 0000:00:01.0:pcie02: pciehp_suspend ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10205.049820] ACPI: Preparing to enter system sleep state S4
Apr 27 20:47:47 computer-laptop kernel: [10205.053716] Disabling non-boot CPUs ...
Apr 27 20:47:47 computer-laptop kernel: [10205.055962] NOHZ: local_softirq_pending 100
Apr 27 20:47:47 computer-laptop kernel: [10205.156019] CPU 1 is now offline
Apr 27 20:47:47 computer-laptop kernel: [10205.156022] SMP alternatives: switching to UP code
Apr 27 20:47:47 computer-laptop kernel: [10205.288885] CPU0 attaching NULL sched-domain.
Apr 27 20:47:47 computer-laptop kernel: [10205.288887] CPU1 attaching NULL sched-domain.
Apr 27 20:47:47 computer-laptop kernel: [10205.289070] CPU0 attaching NULL sched-domain.
Apr 27 20:47:47 computer-laptop kernel: [10205.289194] CPU1 is down
Apr 27 20:47:47 computer-laptop kernel: [10205.289261] Extended CMOS year: 2000
Apr 27 20:47:47 computer-laptop kernel: [10205.289342] PM: Creating hibernation image: 
Apr 27 20:47:47 computer-laptop kernel: [10205.292919] PM: Need to copy 123226 pages
Apr 27 20:47:47 computer-laptop kernel: [10205.292919] PM: Normal pages needed: 25769 + 1024 + 48, available pages: 200404
Apr 27 20:47:47 computer-laptop kernel: [10205.292919] Extended CMOS year: 2000
Apr 27 20:47:47 computer-laptop kernel: [10205.292919] Enabling non-boot CPUs ...
Apr 27 20:47:47 computer-laptop kernel: [10205.292919] SMP alternatives: switching to SMP code
Apr 27 20:47:47 computer-laptop kernel: [10205.424745] Booting processor 1 APIC 0x1 ip 0x6000
Apr 27 20:47:47 computer-laptop kernel: [10205.288779] Initializing CPU#1
Apr 27 20:47:47 computer-laptop kernel: [10205.288779] Calibrating delay using timer specific routine.. 4000.22 BogoMIPS (lpj=8000443)
Apr 27 20:47:47 computer-laptop kernel: [10205.288779] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 27 20:47:47 computer-laptop kernel: [10205.288779] CPU: L2 cache: 3072K
Apr 27 20:47:47 computer-laptop kernel: [10205.288779] CPU: Physical Processor ID: 0
Apr 27 20:47:47 computer-laptop kernel: [10205.288779] CPU: Processor Core ID: 1
Apr 27 20:47:47 computer-laptop kernel: [10205.512671] CPU1: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz stepping 06
Apr 27 20:47:47 computer-laptop kernel: [10205.512720] CPU0 attaching NULL sched-domain.
Apr 27 20:47:47 computer-laptop kernel: [10205.513220] CPU0 attaching sched-domain:
Apr 27 20:47:47 computer-laptop kernel: [10205.513223]  domain 0: span 0-1 level MC
Apr 27 20:47:47 computer-laptop kernel: [10205.513225]   groups: 0 1
Apr 27 20:47:47 computer-laptop kernel: [10205.513228] CPU1 attaching sched-domain:
Apr 27 20:47:47 computer-laptop kernel: [10205.513230]  domain 0: span 0-1 level MC
Apr 27 20:47:47 computer-laptop kernel: [10205.513231]   groups: 1 0
Apr 27 20:47:47 computer-laptop kernel: [10205.516019] Switched to high resolution mode on CPU 1
Apr 27 20:47:47 computer-laptop kernel: [10205.516029] CPU1 is up
Apr 27 20:47:47 computer-laptop kernel: [10205.516031] ACPI: Waking up from system sleep state S4
Apr 27 20:47:47 computer-laptop kernel: [10205.540113] ACPI: EC: non-query interrupt received, switching to interrupt mode
Apr 27 20:47:47 computer-laptop kernel: [10205.654008] pcieport-driver 0000:00:01.0: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.654013] pciehp 0000:00:01.0:pcie02: pciehp_resume ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10205.654021] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 27 20:47:47 computer-laptop kernel: [10205.654027] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.654078] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr 27 20:47:47 computer-laptop kernel: [10205.654084] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.654134] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Apr 27 20:47:47 computer-laptop kernel: [10205.654140] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.654189] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Apr 27 20:47:47 computer-laptop kernel: [10205.654195] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.668142] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Apr 27 20:47:47 computer-laptop kernel: [10205.668163] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr 27 20:47:47 computer-laptop kernel: [10205.668169] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.852421] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.852426] pciehp 0000:00:1c.0:pcie02: pciehp_resume ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10205.852496] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.852500] pciehp 0000:00:1c.1:pcie02: pciehp_resume ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10205.852571] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.852574] pciehp 0000:00:1c.2:pcie02: pciehp_resume ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10205.852580] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr 27 20:47:47 computer-laptop kernel: [10205.852585] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.852636] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr 27 20:47:47 computer-laptop kernel: [10205.852642] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.852691] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 27 20:47:47 computer-laptop kernel: [10205.852697] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.852746] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr 27 20:47:47 computer-laptop kernel: [10205.852752] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.852846] pci 0000:00:1e.0: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10205.852933] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
Apr 27 20:47:47 computer-laptop kernel: [10205.852973] ahci 0000:00:1f.2: setting latency timer to 64
Apr 27 20:47:47 computer-laptop kernel: [10206.173096] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 27 20:47:47 computer-laptop kernel: [10206.228451] tg3 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)
Apr 27 20:47:47 computer-laptop kernel: [10206.235652] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
Apr 27 20:47:47 computer-laptop kernel: [10206.235656] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 27 20:47:47 computer-laptop kernel: [10206.245304] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
Apr 27 20:47:47 computer-laptop kernel: [10206.245307] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 27 20:47:47 computer-laptop kernel: [10206.249019] ata2.00: configured for UDMA/133
Apr 27 20:47:47 computer-laptop kernel: [10206.293046] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 27 20:47:47 computer-laptop kernel: [10206.294456] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 27 20:47:47 computer-laptop kernel: [10206.294664] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
Apr 27 20:47:47 computer-laptop kernel: [10206.294666] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 27 20:47:47 computer-laptop kernel: [10206.297129] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 27 20:47:47 computer-laptop kernel: [10206.297338] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
Apr 27 20:47:47 computer-laptop kernel: [10206.297341] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 27 20:47:47 computer-laptop kernel: [10206.298199] ata1.00: configured for UDMA/133
Apr 27 20:47:47 computer-laptop kernel: [10206.298210] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
Apr 27 20:47:47 computer-laptop kernel: [10206.298211] ata1: irq_stat 0x00400040, connection status changed
Apr 27 20:47:47 computer-laptop kernel: [10206.300157] ata1.00: configured for UDMA/133
Apr 27 20:47:47 computer-laptop kernel: [10206.300159] ata1: EH complete
Apr 27 20:47:47 computer-laptop kernel: [10206.309084] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 27 20:47:47 computer-laptop kernel: [10206.309102] sd 0:0:0:0: [sda] Write Protect is off
Apr 27 20:47:47 computer-laptop kernel: [10206.309104] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 27 20:47:47 computer-laptop kernel: [10206.309127] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 27 20:47:47 computer-laptop kernel: [10206.312749] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[d3c00000-d3c007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 27 20:47:47 computer-laptop kernel: [10206.332135] sdhci-pci 0000:07:03.1: restoring config space at offset 0x4 (was 0xd3c00b00, writing 0xd3c00a00)
Apr 27 20:47:47 computer-laptop kernel: [10206.332159] sdhci-pci 0000:07:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr 27 20:47:47 computer-laptop kernel: [10206.332162] sdhci-pci 0000:07:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
Apr 27 20:47:47 computer-laptop kernel: [10206.333195] pci 0000:07:03.2: restoring config space at offset 0x4 (was 0xd3c00a00, writing 0xd3c00900)
Apr 27 20:47:47 computer-laptop kernel: [10206.333204] pci 0000:07:03.2: restoring config space at offset 0x0 (was 0x8431180, writing 0x5921180)
Apr 27 20:47:47 computer-laptop kernel: [10206.333239] pci 0000:07:03.3: restoring config space at offset 0x4 (was 0xd3c00900, writing 0xd3c00800)
Apr 27 20:47:47 computer-laptop kernel: [10206.333249] pci 0000:07:03.3: restoring config space at offset 0x0 (was 0x5921180, writing 0x8521180)
Apr 27 20:47:47 computer-laptop kernel: [10206.333279] pciehp 0000:00:01.0:pcie02: pciehp_resume ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10206.333282] pciehp 0000:00:1c.0:pcie02: pciehp_resume ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10206.333284] pciehp 0000:00:1c.1:pcie02: pciehp_resume ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10206.333287] pciehp 0000:00:1c.2:pcie02: pciehp_resume ENTRY
Apr 27 20:47:47 computer-laptop kernel: [10206.333357] sd 0:0:0:0: [sda] Starting disk
Apr 27 20:47:47 computer-laptop kernel: [10206.357044] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
Apr 27 20:47:47 computer-laptop kernel: [10206.357045] ata2: irq_stat 0x40000001
Apr 27 20:47:47 computer-laptop kernel: [10206.367139] ata2.00: configured for UDMA/133
Apr 27 20:47:47 computer-laptop kernel: [10206.367141] ata2: EH complete
Apr 27 20:47:47 computer-laptop kernel: [10206.456973] PM: Image restored successfully.
Apr 27 20:47:47 computer-laptop kernel: [10206.498287] Restarting tasks ... done.
Apr 27 20:47:47 computer-laptop kernel: [10206.516783] PM: Basic memory bitmaps freed
Apr 27 20:47:47 computer-laptop kernel: [10206.821679] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Apr 27 20:47:47 computer-laptop anacron[7776]: Anacron 2.3 started on 2009-04-27
Apr 27 20:47:47 computer-laptop anacron[7776]: Normal exit (0 jobs run)
Apr 27 20:47:47 computer-laptop acpid: client 2930[0:0] has disconnected 
Apr 27 20:47:47 computer-laptop acpid: client 2930[0:0] has disconnected 
Apr 27 20:47:47 computer-laptop acpid: client connected from 2930[0:0] 
Apr 27 20:47:47 computer-laptop NetworkManager: <info>  Waking up... 
Apr 27 20:47:47 computer-laptop NetworkManager: <info>  (eth0): now managed 
Apr 27 20:47:47 computer-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Apr 27 20:47:47 computer-laptop NetworkManager: <info>  (eth0): bringing up device. 
Apr 27 20:47:48 computer-laptop kernel: [10207.140269] tg3 0000:02:00.0: irq 2297 for MSI/MSI-X
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (eth0): preparing device. 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): now managed 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): bringing up device. 
Apr 27 20:47:48 computer-laptop kernel: [10207.193739] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 27 20:47:48 computer-laptop kernel: [10207.227572] Registered led device: iwl-phy0:radio
Apr 27 20:47:48 computer-laptop kernel: [10207.227594] Registered led device: iwl-phy0:assoc
Apr 27 20:47:48 computer-laptop kernel: [10207.227609] Registered led device: iwl-phy0:RX
Apr 27 20:47:48 computer-laptop kernel: [10207.227624] Registered led device: iwl-phy0:TX
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): preparing device. 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Apr 27 20:47:48 computer-laptop kernel: [10207.245499] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 20:47:48 computer-laptop kernel: [10207.257363] wlan0: direct probe to AP 00:16:b6:02:e7:72 try 1
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Apr 27 20:47:48 computer-laptop kernel: [10207.260668] wlan0 direct probe responded
Apr 27 20:47:48 computer-laptop kernel: [10207.260672] wlan0: authenticate with AP 00:16:b6:02:e7:72
Apr 27 20:47:48 computer-laptop kernel: [10207.263097] wlan0: authenticated
Apr 27 20:47:48 computer-laptop kernel: [10207.263099] wlan0: associate with AP 00:16:b6:02:e7:72
Apr 27 20:47:48 computer-laptop kernel: [10207.265361] wlan0: RX AssocResp from 00:16:b6:02:e7:72 (capab=0x401 status=0 aid=8)
Apr 27 20:47:48 computer-laptop kernel: [10207.265363] wlan0: associated
Apr 27 20:47:48 computer-laptop kernel: [10207.266789] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 27 20:47:48 computer-laptop kernel: [10207.282724] wlan0: disassociating by local choice (reason=3)
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
Apr 27 20:47:48 computer-laptop kernel: [10207.334079] phy0: failed to restore operational channel after scan
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto default' 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto default' has security, and secrets exist.  No new secrets needed. 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Config: added 'ssid' value 'default' 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Apr 27 20:47:48 computer-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 27 20:47:48 computer-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating 
Apr 27 20:47:48 computer-laptop kernel: [10207.576519] phy0: failed to restore operational channel after scan
Apr 27 20:47:48 computer-laptop kernel: [10207.576992] wlan0: authenticate with AP 00:16:b6:02:e7:72
Apr 27 20:47:48 computer-laptop kernel: [10207.578801] phy0: failed to restore operational channel after scan
Apr 27 20:47:48 computer-laptop kernel: [10207.579350] wlan0: authenticate with AP 00:1d:6a:b5:46:3b
Apr 27 20:47:48 computer-laptop kernel: [10207.581806] wlan0: authenticated
Apr 27 20:47:48 computer-laptop kernel: [10207.581809] wlan0: associate with AP 00:1d:6a:b5:46:3b
Apr 27 20:47:48 computer-laptop kernel: [10207.585685] wlan0: RX AssocResp from 00:1d:6a:b5:46:3b (capab=0x31 status=0 aid=1)
Apr 27 20:47:48 computer-laptop kernel: [10207.585687] wlan0: associated
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'default'. 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Apr 27 20:47:48 computer-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Apr 27 20:47:48 computer-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Apr 27 20:47:48 computer-laptop dhclient: All rights reserved.
Apr 27 20:47:48 computer-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 27 20:47:48 computer-laptop dhclient: 
Apr 27 20:47:48 computer-laptop dhclient: wmaster0: unknown hardware address type 801
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  dhclient started with pid 7807 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 27 20:47:48 computer-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Apr 27 20:47:48 computer-laptop dhclient: wmaster0: unknown hardware address type 801
Apr 27 20:47:48 computer-laptop dhclient: Listening on LPF/wlan0/00:22:fa:48:f8:ce
Apr 27 20:47:48 computer-laptop dhclient: Sending on   LPF/wlan0/00:22:fa:48:f8:ce
Apr 27 20:47:48 computer-laptop dhclient: Sending on   Socket/fallback
Apr 27 20:47:48 computer-laptop anacron[7859]: Anacron 2.3 started on 2009-04-27
Apr 27 20:47:48 computer-laptop anacron[7859]: Normal exit (0 jobs run)
Apr 27 20:47:49 computer-laptop acpid: client connected from 2930[0:0] 
Apr 27 20:47:49 computer-laptop kernel: [10208.952899] pciehp 0000:00:01.0:pcie02: Card not present on Slot(1)
Apr 27 20:47:49 computer-laptop kernel: [10208.965023] pciehp 0000:00:01.0:pcie02: Card present on Slot(1)
Apr 27 20:47:49 computer-laptop kernel: [10208.968077] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Apr 27 20:47:49 computer-laptop avahi-daemon[2975]: Registering new address record for fe80::222:faff:fe48:f8ce on wlan0.*.
Apr 27 20:47:49 computer-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 27 20:47:50 computer-laptop dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
Apr 27 20:47:50 computer-laptop dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
Apr 27 20:47:50 computer-laptop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Apr 27 20:47:50 computer-laptop dhclient: bound to 192.168.1.101 -- renewal in 243322 seconds.
Apr 27 20:47:50 computer-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>    address 192.168.1.101 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>    gateway 192.168.1.1 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>    nameserver '192.168.1.1' 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>    domain name 'oc.cox.net' 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 27 20:47:50 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 27 20:47:50 computer-laptop avahi-daemon[2975]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Apr 27 20:47:50 computer-laptop avahi-daemon[2975]: New relevant interface wlan0.IPv4 for mDNS.
Apr 27 20:47:50 computer-laptop avahi-daemon[2975]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Apr 27 20:47:51 computer-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Apr 27 20:47:51 computer-laptop NetworkManager: <info>  Policy set 'Auto default' (wlan0) as default for routing and DNS. 
Apr 27 20:47:51 computer-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Apr 27 20:47:51 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 27 20:47:51 computer-laptop postfix/master[2676]: reload configuration /etc/postfix
Apr 27 20:47:52 computer-laptop ntpdate[7943]: step time server 91.189.94.4 offset 0.611644 sec
Apr 27 20:47:59 computer-laptop kernel: [10218.140072] wlan0: no IPv6 routers present
Apr 27 20:48:41 computer-laptop kernel: [10260.000129] Corrupted low memory at c000fcf4 (fcf4 phys) = 83840000
Apr 27 20:48:41 computer-laptop kernel: [10260.000138] Corrupted low memory at c000fcf8 (fcf8 phys) = 0010000a
Apr 27 20:48:41 computer-laptop kernel: [10260.000150] ------------[ cut here ]------------
Apr 27 20:48:41 computer-laptop kernel: [10260.000156] WARNING: at /build/buildd/linux-2.6.28/arch/x86/kernel/setup.c:719 check_for_bios_corruption+0xc8/0xd0()
Apr 27 20:48:41 computer-laptop kernel: [10260.000161] Memory corruption detected in low memory
Apr 27 20:48:41 computer-laptop kernel: [10260.000165] Modules linked in: nvidia(P) binfmt_misc ppdev bridge stp bnep input_polldev joydev lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm arc4 ecb snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn snd_seq iwlcore uvcvideo snd_timer snd_seq_device compat_ioctl32 psmouse snd soundcore videodev mac80211 pcspkr asus_laptop serio_raw video intel_agp agpgart sdhci_pci sdhci v4l1_compat snd_page_alloc iTCO_wdt iTCO_vendor_support output led_class cfg80211 ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
Apr 27 20:48:41 computer-laptop kernel: [10260.000268] Pid: 0, comm: swapper Tainted: P        W  2.6.28-11-generic #42-Ubuntu
Apr 27 20:48:41 computer-laptop kernel: [10260.000273] Call Trace:
Apr 27 20:48:41 computer-laptop kernel: [10260.000282]  [<c0139ab0>] warn_slowpath+0x60/0x80
Apr 27 20:48:41 computer-laptop kernel: [10260.000291]  [<c013a2f9>] ? release_console_sem+0x1c9/0x200
Apr 27 20:48:41 computer-laptop kernel: [10260.000301]  [<c015aee3>] ? tick_dev_program_event+0x33/0xc0
Apr 27 20:48:41 computer-laptop kernel: [10260.000311]  [<c0500ac6>] ? printk+0x18/0x1a
Apr 27 20:48:41 computer-laptop kernel: [10260.000318]  [<c01079c8>] check_for_bios_corruption+0xc8/0xd0
Apr 27 20:48:41 computer-laptop kernel: [10260.000327]  [<c01079d8>] periodic_check_for_corruption+0x8/0x30
Apr 27 20:48:41 computer-laptop kernel: [10260.000335]  [<c0143b00>] run_timer_softirq+0x130/0x200
Apr 27 20:48:41 computer-laptop kernel: [10260.000342]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
Apr 27 20:48:41 computer-laptop kernel: [10260.000350]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
Apr 27 20:48:41 computer-laptop kernel: [10260.000359]  [<c013f197>] __do_softirq+0x97/0x170
Apr 27 20:48:41 computer-laptop kernel: [10260.000366]  [<c0106f30>] ? timer_interrupt+0x30/0x80
Apr 27 20:48:41 computer-laptop kernel: [10260.000373]  [<c013f2cd>] do_softirq+0x5d/0x60
Apr 27 20:48:41 computer-laptop kernel: [10260.000381]  [<c013f445>] irq_exit+0x55/0x90
Apr 27 20:48:41 computer-laptop kernel: [10260.000387]  [<c0106853>] do_IRQ+0x83/0xa0
Apr 27 20:48:41 computer-laptop kernel: [10260.000393]  [<c01051f3>] common_interrupt+0x23/0x30
Apr 27 20:48:41 computer-laptop kernel: [10260.000402]  [<c0319417>] ? acpi_idle_enter_bm+0x269/0x2b8
Apr 27 20:48:41 computer-laptop kernel: [10260.000411]  [<c040f4df>] cpuidle_idle_call+0x6f/0xd0
Apr 27 20:48:41 computer-laptop kernel: [10260.000418]  [<c010285d>] cpu_idle+0x6d/0xd0
Apr 27 20:48:41 computer-laptop kernel: [10260.000426]  [<c04f110e>] rest_init+0x4e/0x60
Apr 27 20:48:41 computer-laptop kernel: [10260.000431] ---[ end trace bcb09d6f3fe2be1e ]---
Apr 27 20:50:01 computer-laptop /USR/SBIN/CRON[8027]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

```

---

### Post by meatlover on 2009-04-28
I formatted my disk and I haven't installed any drivers for nvidia or compiz yet.  I attempted to suspend and my screen turned black then had a cursor for a brief second then the screen turned off but all the hardware buttons were still on.  I tried to make the laptop resume but it would not let me.  There was also no pm-suspend logged for some reason but here is my syslog:

```
Apr 27 08:42:48 computer-laptop syslogd 1.5.0#5ubuntu3: restart.
Apr 27 08:42:48 computer-laptop kernel: Inspecting /boot/System.map-2.6.28-11-generic
Apr 27 08:42:48 computer-laptop kernel: Cannot find map file.
Apr 27 08:42:48 computer-laptop kernel: Loaded 56724 symbols from 52 modules.
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] KERNEL supported cpus:
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   Intel GenuineIntel
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   AMD AuthenticAMD
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   NSC Geode by NSC
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   Centaur CentaurHauls
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000009dc39000 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dc39000 - 000000009dc5b000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dc5b000 - 000000009dc5c000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dc5c000 - 000000009dc60000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dc60000 - 000000009dc7d000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dc7d000 - 000000009dc85000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dc85000 - 000000009dca7000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dca7000 - 000000009dca8000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dca8000 - 000000009dcaa000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dcaa000 - 000000009dcbd000 (ACPI data)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dcbd000 - 000000009dcc8000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dcc8000 - 000000009dccd000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dccd000 - 000000009dcce000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dcce000 - 000000009dcf0000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dcf0000 - 000000009dcf6000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 000000009dcf6000 - 000000009e000000 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] DMI 2.4 present.
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] last_pfn = 0x9e000 max_arch_pfn = 0x100000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Scanning 2 areas for low memory corruption
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] modified physical RAM map:
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000009dc39000 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dc39000 - 000000009dc5b000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dc5b000 - 000000009dc5c000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dc5c000 - 000000009dc60000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dc60000 - 000000009dc7d000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dc7d000 - 000000009dc85000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dc85000 - 000000009dca7000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dca7000 - 000000009dca8000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dca8000 - 000000009dcaa000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dcaa000 - 000000009dcbd000 (ACPI data)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dcbd000 - 000000009dcc8000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dcc8000 - 000000009dccd000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dccd000 - 000000009dcce000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dcce000 - 000000009dcf0000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dcf0000 - 000000009dcf6000 (ACPI NVS)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 000000009dcf6000 - 000000009e000000 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 00000000ffa00000 - 00000000ffc00000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] RAMDISK: 378be000 - 37fef702
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Allocated new RAMDISK: 00881000 - 00fb2702
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fef701 to 00881000 - 00fb2701
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: RSDP 000F03C0, 0024 (r2 LENOVO)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: XSDT 9DCBBE18, 0054 (r1 LENOVO CB-01          DF MSFT    10013)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: FACP 9DCA7A98, 00F4 (r4 LENOVO CB-01          DF MSFT    10013)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: DSDT 9DCAA018, F1A7 (r1 LENOVO CB-01         223 INTL 20051117)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: FACS 9DCC5E40, 0040
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: APIC 9DCBAF18, 005C (r2 LENOVO CB-01          DF MSFT    10013)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: HPET 9DCC6D98, 0038 (r1 HPET   OEMSHPET       DF MSFT        1)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: SLIC 9DCBDC18, 0176 (r1 LENOVO CB-01          DF MSFT        1)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: MCFG 9DCC6D18, 003C (r1 050808 OEMMCFG  20080508 MSFT       97)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: SSDT 9DC5F698, 0655 (r1  PmRef    CpuPm     3000 INTL 20051117)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] 1644MB HIGHMEM available.
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] 883MB LOWMEM available.
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   mapped low ram: 0 - 373fe000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   low ram: 00000000 - 373fe000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   bootmap 00012000 - 00018e80
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   #7 [0000881000 - 0000fb2702]      NEW RAMDISK ==> [0000881000 - 0000fb2702]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Zone PFN ranges:
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   HighMem  0x000373fe -> 0x0009e000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Movable zone start PFN for each node
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] early_node_map[5] active PFN ranges
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x00000007
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x00000092
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0009dc39
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]     0: 0x0009dcf6 -> 0x0009e000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] On node 0 totalpages: 646856
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   DMA zone: 3941 pages, LIFO batch:0
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   Normal zone: 1736 pages used for memmap
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   Normal zone: 220470 pages, LIFO batch:31
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   HighMem zone: 3289 pages used for memmap
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   HighMem zone: 417388 pages, LIFO batch:31
Apr 27 08:42:48 computer-laptop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Allocating PCI resources starting at a0000000 (gap: 9e000000:42000000)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 641799
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Kernel command line: root=UUID=6fa93467-75e7-474b-995e-4c865f8dd77c ro quiet splash 
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Initializing CPU#0
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Extended CMOS year: 2000
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Apr 27 08:42:48 computer-laptop kernel: [    0.000000] Detected 1999.960 MHz processor.
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Console: colour VGA+ 80x25
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] console [tty0] enabled
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] allocated 12943360 bytes of page_cgroup
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Memory: 2537772k/2588672k available (4126k kernel code, 48876k reserved, 2208k data, 532k init, 1682708k highmem)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] virtual kernel memory layout:
Apr 27 08:42:48 computer-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] hpet clockevent registered
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.92 BogoMIPS (lpj=7999840)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Security Framework initialized
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] SELinux:  Disabled at boot.
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] AppArmor: AppArmor initialized
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Mount-cache hash table entries: 512
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Initializing cgroup subsys ns
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Initializing cgroup subsys memory
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Initializing cgroup subsys freezer
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] CPU: L2 cache: 3072K
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] CPU: Processor Core ID: 0
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] using mwait in idle threads.
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Apr 27 08:42:48 computer-laptop kernel: [    0.018481] ACPI: Core revision 20080926
Apr 27 08:42:48 computer-laptop kernel: [    0.023714] ACPI: Checking initramfs for custom DSDT
Apr 27 08:42:48 computer-laptop kernel: [    0.332364] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
Apr 27 08:42:48 computer-laptop kernel: [    0.372436] CPU0: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz stepping 06
Apr 27 08:42:48 computer-laptop kernel: [    0.376001] Booting processor 1 APIC 0x1 ip 0x6000
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Initializing CPU#1
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 4000.12 BogoMIPS (lpj=8000245)
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] CPU: L2 cache: 3072K
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr 27 08:42:48 computer-laptop kernel: [    0.004000] CPU: Processor Core ID: 1
Apr 27 08:42:48 computer-laptop kernel: [    0.460670] CPU1: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz stepping 06
Apr 27 08:42:48 computer-laptop kernel: [    0.460685] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 27 08:42:48 computer-laptop kernel: [    0.464030] Brought up 2 CPUs
Apr 27 08:42:48 computer-laptop kernel: [    0.464033] Total of 2 processors activated (8000.04 BogoMIPS).
Apr 27 08:42:48 computer-laptop kernel: [    0.464085] CPU0 attaching sched-domain:
Apr 27 08:42:48 computer-laptop kernel: [    0.464087]  domain 0: span 0-1 level MC
Apr 27 08:42:48 computer-laptop kernel: [    0.464090]   groups: 0 1
Apr 27 08:42:48 computer-laptop kernel: [    0.464095] CPU1 attaching sched-domain:
Apr 27 08:42:48 computer-laptop kernel: [    0.464097]  domain 0: span 0-1 level MC
Apr 27 08:42:48 computer-laptop kernel: [    0.464099]   groups: 1 0
Apr 27 08:42:48 computer-laptop kernel: [    0.464163] net_namespace: 776 bytes
Apr 27 08:42:48 computer-laptop kernel: [    0.464163] Booting paravirtualized kernel on bare hardware
Apr 27 08:42:48 computer-laptop kernel: [    0.464295] Time: 15:42:32  Date: 04/27/09
Apr 27 08:42:48 computer-laptop kernel: [    0.464295] regulator: core version 0.5
Apr 27 08:42:48 computer-laptop kernel: [    0.464295] NET: Registered protocol family 16
Apr 27 08:42:48 computer-laptop kernel: [    0.464295] EISA bus registered
Apr 27 08:42:48 computer-laptop kernel: [    0.464295] ACPI: bus type pci registered
Apr 27 08:42:48 computer-laptop kernel: [    0.464295] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr 27 08:42:48 computer-laptop kernel: [    0.464295] PCI: MCFG area at e0000000 reserved in E820
Apr 27 08:42:48 computer-laptop kernel: [    0.464295] PCI: Using MMCONFIG for extended config space
Apr 27 08:42:48 computer-laptop kernel: [    0.464295] PCI: Using configuration type 1 for base access
Apr 27 08:42:48 computer-laptop kernel: [    0.468177] ACPI: EC: Look up EC in DSDT
Apr 27 08:42:48 computer-laptop kernel: [    0.473459] ACPI: BIOS _OSI(Linux) query ignored
Apr 27 08:42:48 computer-laptop kernel: [    0.481857] ACPI: Interpreter enabled
Apr 27 08:42:48 computer-laptop kernel: [    0.481860] ACPI: (supports S0 S3 S4 S5)
Apr 27 08:42:48 computer-laptop kernel: [    0.481881] ACPI: Using IOAPIC for interrupt routing
Apr 27 08:42:48 computer-laptop kernel: [    0.502901] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
Apr 27 08:42:48 computer-laptop kernel: [    0.502903] ACPI: EC: driver started in poll mode
Apr 27 08:42:48 computer-laptop kernel: [    0.503186] ACPI: No dock devices found.
Apr 27 08:42:48 computer-laptop kernel: [    0.503311] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 27 08:42:48 computer-laptop kernel: [    0.503397] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.503400] pci 0000:00:01.0: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.503497] pci 0000:00:1a.0: reg 20 io port: [0xd0c0-0xd0df]
Apr 27 08:42:48 computer-laptop kernel: [    0.503579] pci 0000:00:1a.1: reg 20 io port: [0xd0a0-0xd0bf]
Apr 27 08:42:48 computer-laptop kernel: [    0.503661] pci 0000:00:1a.2: reg 20 io port: [0xd080-0xd09f]
Apr 27 08:42:48 computer-laptop kernel: [    0.503745] pci 0000:00:1a.7: reg 10 32bit mmio: [0xd3d04c00-0xd3d04fff]
Apr 27 08:42:48 computer-laptop kernel: [    0.503791] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.503797] pci 0000:00:1a.7: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.503852] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd3d00000-0xd3d03fff]
Apr 27 08:42:48 computer-laptop kernel: [    0.503892] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.503896] pci 0000:00:1b.0: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.503960] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.503965] pci 0000:00:1c.0: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.504035] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.504040] pci 0000:00:1c.1: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.504107] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.504111] pci 0000:00:1c.2: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.504188] pci 0000:00:1d.0: reg 20 io port: [0xd060-0xd07f]
Apr 27 08:42:48 computer-laptop kernel: [    0.504270] pci 0000:00:1d.1: reg 20 io port: [0xd040-0xd05f]
Apr 27 08:42:48 computer-laptop kernel: [    0.504352] pci 0000:00:1d.2: reg 20 io port: [0xd020-0xd03f]
Apr 27 08:42:48 computer-laptop kernel: [    0.504435] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd3d04800-0xd3d04bff]
Apr 27 08:42:48 computer-laptop kernel: [    0.504481] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.504486] pci 0000:00:1d.7: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.504713] pci 0000:00:1f.2: reg 10 io port: [0xd110-0xd117]
Apr 27 08:42:48 computer-laptop kernel: [    0.504720] pci 0000:00:1f.2: reg 14 io port: [0xd100-0xd103]
Apr 27 08:42:48 computer-laptop kernel: [    0.504728] pci 0000:00:1f.2: reg 18 io port: [0xd0f0-0xd0f7]
Apr 27 08:42:48 computer-laptop kernel: [    0.504736] pci 0000:00:1f.2: reg 1c io port: [0xd0e0-0xd0e3]
Apr 27 08:42:48 computer-laptop kernel: [    0.504743] pci 0000:00:1f.2: reg 20 io port: [0xd000-0xd01f]
Apr 27 08:42:48 computer-laptop kernel: [    0.504751] pci 0000:00:1f.2: reg 24 32bit mmio: [0xd3d04000-0xd3d047ff]
Apr 27 08:42:48 computer-laptop kernel: [    0.504770] pci 0000:00:1f.2: PME# supported from D3hot
Apr 27 08:42:48 computer-laptop kernel: [    0.504775] pci 0000:00:1f.2: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.504854] pci 0000:01:00.0: reg 10 32bit mmio: [0xc2000000-0xc2ffffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.504869] pci 0000:01:00.0: reg 14 64bit mmio: [0xb0000000-0xbfffffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.504885] pci 0000:01:00.0: reg 1c 64bit mmio: [0xc0000000-0xc1ffffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.504893] pci 0000:01:00.0: reg 24 io port: [0xc000-0xc07f]
Apr 27 08:42:48 computer-laptop kernel: [    0.504902] pci 0000:01:00.0: reg 30 32bit mmio: [0xc3000000-0xc301ffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.504983] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
Apr 27 08:42:48 computer-laptop kernel: [    0.504986] pci 0000:00:01.0: bridge 32bit mmio: [0xb0000000-0xcfffffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505209] pci 0000:02:00.0: reg 10 64bit mmio: [0xd2800000-0xd280ffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505336] pci 0000:02:00.0: PME# supported from D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.505348] pci 0000:02:00.0: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.505436] pci 0000:00:1c.0: bridge io port: [0xb000-0xbfff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505441] pci 0000:00:1c.0: bridge 32bit mmio: [0xd2800000-0xd3bfffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505560] pci 0000:03:00.0: reg 10 64bit mmio: [0xd1400000-0xd1401fff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505659] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.505681] pci 0000:03:00.0: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.505766] pci 0000:00:1c.1: bridge io port: [0xa000-0xafff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505771] pci 0000:00:1c.1: bridge 32bit mmio: [0xd1400000-0xd27fffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505835] pci 0000:00:1c.2: bridge io port: [0x9000-0x9fff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505840] pci 0000:00:1c.2: bridge 32bit mmio: [0xd0000000-0xd13fffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505893] pci 0000:07:03.0: reg 10 32bit mmio: [0xd3c00000-0xd3c007ff]
Apr 27 08:42:48 computer-laptop kernel: [    0.505940] pci 0000:07:03.0: PME# supported from D0 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.505945] pci 0000:07:03.0: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.505986] pci 0000:07:03.1: reg 10 32bit mmio: [0xd3c00b00-0xd3c00bff]
Apr 27 08:42:48 computer-laptop kernel: [    0.506034] pci 0000:07:03.1: supports D1 D2
Apr 27 08:42:48 computer-laptop kernel: [    0.506035] pci 0000:07:03.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.506040] pci 0000:07:03.1: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.506083] pci 0000:07:03.2: reg 10 32bit mmio: [0xd3c00a00-0xd3c00aff]
Apr 27 08:42:48 computer-laptop kernel: [    0.506130] pci 0000:07:03.2: supports D1 D2
Apr 27 08:42:48 computer-laptop kernel: [    0.506132] pci 0000:07:03.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.506136] pci 0000:07:03.2: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.506177] pci 0000:07:03.3: reg 10 32bit mmio: [0xd3c00900-0xd3c009ff]
Apr 27 08:42:48 computer-laptop kernel: [    0.506225] pci 0000:07:03.3: supports D1 D2
Apr 27 08:42:48 computer-laptop kernel: [    0.506226] pci 0000:07:03.3: PME# supported from D0 D1 D2 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.506231] pci 0000:07:03.3: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.506273] pci 0000:07:03.4: reg 10 32bit mmio: [0xd3c00800-0xd3c008ff]
Apr 27 08:42:48 computer-laptop kernel: [    0.506321] pci 0000:07:03.4: supports D1 D2
Apr 27 08:42:48 computer-laptop kernel: [    0.506322] pci 0000:07:03.4: PME# supported from D0 D1 D2 D3hot D3cold
Apr 27 08:42:48 computer-laptop kernel: [    0.506327] pci 0000:07:03.4: PME# disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.506392] pci 0000:00:1e.0: transparent bridge
Apr 27 08:42:48 computer-laptop kernel: [    0.506400] pci 0000:00:1e.0: bridge 32bit mmio: [0xd3c00000-0xd3cfffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.506434] bus 00 -> node 0
Apr 27 08:42:48 computer-laptop kernel: [    0.506444] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 27 08:42:48 computer-laptop kernel: [    0.506754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP00._PRT]
Apr 27 08:42:48 computer-laptop kernel: [    0.506939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Apr 27 08:42:48 computer-laptop kernel: [    0.507160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 27 08:42:48 computer-laptop kernel: [    0.507322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Apr 27 08:42:48 computer-laptop kernel: [    0.507517] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Apr 27 08:42:48 computer-laptop kernel: [    0.648943] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Apr 27 08:42:48 computer-laptop kernel: [    0.649122] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 27 08:42:48 computer-laptop kernel: [    0.649297] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Apr 27 08:42:48 computer-laptop kernel: [    0.649472] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 27 08:42:48 computer-laptop kernel: [    0.649647] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Apr 27 08:42:48 computer-laptop kernel: [    0.649822] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 27 08:42:48 computer-laptop kernel: [    0.649996] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Apr 27 08:42:48 computer-laptop kernel: [    0.650170] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 27 08:42:48 computer-laptop kernel: [    0.650387] ACPI: WMI: Mapper loaded
Apr 27 08:42:48 computer-laptop kernel: [    0.650421] SCSI subsystem initialized
Apr 27 08:42:48 computer-laptop kernel: [    0.650421] libata version 3.00 loaded.
Apr 27 08:42:48 computer-laptop kernel: [    0.650421] usbcore: registered new interface driver usbfs
Apr 27 08:42:48 computer-laptop kernel: [    0.650421] usbcore: registered new interface driver hub
Apr 27 08:42:48 computer-laptop kernel: [    0.650421] usbcore: registered new device driver usb
Apr 27 08:42:48 computer-laptop kernel: [    0.650421] PCI: Using ACPI for IRQ routing
Apr 27 08:42:48 computer-laptop kernel: [    0.656009] Bluetooth: Core ver 2.13
Apr 27 08:42:48 computer-laptop kernel: [    0.656023] NET: Registered protocol family 31
Apr 27 08:42:48 computer-laptop kernel: [    0.656023] Bluetooth: HCI device and connection manager initialized
Apr 27 08:42:48 computer-laptop kernel: [    0.656023] Bluetooth: HCI socket layer initialized
Apr 27 08:42:48 computer-laptop kernel: [    0.656023] NET: Registered protocol family 8
Apr 27 08:42:48 computer-laptop kernel: [    0.656023] NET: Registered protocol family 20
Apr 27 08:42:48 computer-laptop kernel: [    0.656031] NetLabel: Initializing
Apr 27 08:42:48 computer-laptop kernel: [    0.656032] NetLabel:  domain hash size = 128
Apr 27 08:42:48 computer-laptop kernel: [    0.656034] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 27 08:42:48 computer-laptop kernel: [    0.656045] NetLabel:  unlabeled traffic allowed by default
Apr 27 08:42:48 computer-laptop kernel: [    0.656059] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Apr 27 08:42:48 computer-laptop kernel: [    0.656064] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Apr 27 08:42:48 computer-laptop kernel: [    0.660051] AppArmor: AppArmor Filesystem Enabled
Apr 27 08:42:48 computer-laptop kernel: [    0.664008] Switched to high resolution mode on CPU 0
Apr 27 08:42:48 computer-laptop kernel: [    0.664713] Switched to high resolution mode on CPU 1
Apr 27 08:42:48 computer-laptop kernel: [    0.668009] pnp: PnP ACPI init
Apr 27 08:42:48 computer-laptop kernel: [    0.668016] ACPI: bus type pnp registered
Apr 27 08:42:48 computer-laptop kernel: [    0.671430] pnp: PnP ACPI: found 14 devices
Apr 27 08:42:48 computer-laptop kernel: [    0.671432] ACPI: ACPI bus type pnp unregistered
Apr 27 08:42:48 computer-laptop kernel: [    0.671435] PnPBIOS: Disabled by ACPI PNP
Apr 27 08:42:48 computer-laptop kernel: [    0.671443] system 00:01: ioport range 0x25d-0x25d has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671445] system 00:01: ioport range 0x25c-0x25c has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671448] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671451] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671453] system 00:01: iomem range 0xfec10000-0xfec17fff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671456] system 00:01: iomem range 0xfec18000-0xfec1ffff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671458] system 00:01: iomem range 0xfec20000-0xfec27fff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671461] system 00:01: iomem range 0xfec28000-0xfec2ffff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671463] system 00:01: iomem range 0xfec30000-0xfec37fff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671466] system 00:01: iomem range 0xfec38000-0xfec3ffff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671468] system 00:01: iomem range 0xff000000-0xffffffff could not be reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671474] system 00:02: ioport range 0x240-0x259 has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671482] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671485] system 00:0a: ioport range 0x400-0x47f has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671487] system 00:0a: ioport range 0x500-0x53f has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671493] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671498] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671503] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671506] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671508] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.671511] system 00:0d: iomem range 0x100000-0x9fffffff could not be reserved
Apr 27 08:42:48 computer-laptop kernel: [    0.706205] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Apr 27 08:42:48 computer-laptop kernel: [    0.706208] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Apr 27 08:42:48 computer-laptop kernel: [    0.706211] pci 0000:00:01.0:   MEM window: 0xb0000000-0xcfffffff
Apr 27 08:42:48 computer-laptop kernel: [    0.706214] pci 0000:00:01.0:   PREFETCH window: disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.706219] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Apr 27 08:42:48 computer-laptop kernel: [    0.706222] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
Apr 27 08:42:48 computer-laptop kernel: [    0.706228] pci 0000:00:1c.0:   MEM window: 0xd2800000-0xd3bfffff
Apr 27 08:42:48 computer-laptop kernel: [    0.706233] pci 0000:00:1c.0:   PREFETCH window: disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.706240] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Apr 27 08:42:48 computer-laptop kernel: [    0.706243] pci 0000:00:1c.1:   IO window: 0xa000-0xafff
Apr 27 08:42:48 computer-laptop kernel: [    0.706250] pci 0000:00:1c.1:   MEM window: 0xd1400000-0xd27fffff
Apr 27 08:42:48 computer-laptop kernel: [    0.706254] pci 0000:00:1c.1:   PREFETCH window: disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.706262] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Apr 27 08:42:48 computer-laptop kernel: [    0.706265] pci 0000:00:1c.2:   IO window: 0x9000-0x9fff
Apr 27 08:42:48 computer-laptop kernel: [    0.706271] pci 0000:00:1c.2:   MEM window: 0xd0000000-0xd13fffff
Apr 27 08:42:48 computer-laptop kernel: [    0.706275] pci 0000:00:1c.2:   PREFETCH window: disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.706283] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
Apr 27 08:42:48 computer-laptop kernel: [    0.706285] pci 0000:00:1e.0:   IO window: disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.706291] pci 0000:00:1e.0:   MEM window: 0xd3c00000-0xd3cfffff
Apr 27 08:42:48 computer-laptop kernel: [    0.706295] pci 0000:00:1e.0:   PREFETCH window: disabled
Apr 27 08:42:48 computer-laptop kernel: [    0.706309] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 27 08:42:48 computer-laptop kernel: [    0.706312] pci 0000:00:01.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    0.706320] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 27 08:42:48 computer-laptop kernel: [    0.706325] pci 0000:00:1c.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    0.706334] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr 27 08:42:48 computer-laptop kernel: [    0.706339] pci 0000:00:1c.1: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    0.706348] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 27 08:42:48 computer-laptop kernel: [    0.706353] pci 0000:00:1c.2: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    0.706361] pci 0000:00:1e.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    0.706365] bus: 00 index 0 io port: [0x00-0xffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706367] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706369] bus: 01 index 0 io port: [0xc000-0xcfff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706371] bus: 01 index 1 mmio: [0xb0000000-0xcfffffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706373] bus: 01 index 2 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706375] bus: 01 index 3 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706377] bus: 02 index 0 io port: [0xb000-0xbfff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706379] bus: 02 index 1 mmio: [0xd2800000-0xd3bfffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706380] bus: 02 index 2 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706382] bus: 02 index 3 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706384] bus: 03 index 0 io port: [0xa000-0xafff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706386] bus: 03 index 1 mmio: [0xd1400000-0xd27fffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706388] bus: 03 index 2 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706390] bus: 03 index 3 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706391] bus: 04 index 0 io port: [0x9000-0x9fff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706393] bus: 04 index 1 mmio: [0xd0000000-0xd13fffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706395] bus: 04 index 2 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706396] bus: 04 index 3 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706398] bus: 07 index 0 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706400] bus: 07 index 1 mmio: [0xd3c00000-0xd3cfffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706402] bus: 07 index 2 mmio: [0x0-0x0]
Apr 27 08:42:48 computer-laptop kernel: [    0.706403] bus: 07 index 3 io port: [0x00-0xffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706405] bus: 07 index 4 mmio: [0x000000-0xffffffff]
Apr 27 08:42:48 computer-laptop kernel: [    0.706413] NET: Registered protocol family 2
Apr 27 08:42:48 computer-laptop kernel: [    0.720046] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 27 08:42:48 computer-laptop kernel: [    0.720250] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 27 08:42:48 computer-laptop kernel: [    0.720519] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 27 08:42:48 computer-laptop kernel: [    0.720658] TCP: Hash tables configured (established 131072 bind 65536)
Apr 27 08:42:48 computer-laptop kernel: [    0.720660] TCP reno registered
Apr 27 08:42:48 computer-laptop kernel: [    0.724054] NET: Registered protocol family 1
Apr 27 08:42:48 computer-laptop kernel: [    0.724152] checking if image is initramfs... it is
Apr 27 08:42:48 computer-laptop kernel: [    1.324612] Freeing initrd memory: 7365k freed
Apr 27 08:42:48 computer-laptop kernel: [    1.324794] cpufreq: No nForce2 chipset.
Apr 27 08:42:48 computer-laptop kernel: [    1.324919] audit: initializing netlink socket (disabled)
Apr 27 08:42:48 computer-laptop kernel: [    1.324940] type=2000 audit(1240846952.324:1): initialized
Apr 27 08:42:48 computer-laptop kernel: [    1.332129] highmem bounce pool size: 64 pages
Apr 27 08:42:48 computer-laptop kernel: [    1.332134] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 27 08:42:48 computer-laptop kernel: [    1.333372] VFS: Disk quotas dquot_6.5.1
Apr 27 08:42:48 computer-laptop kernel: [    1.333428] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 27 08:42:48 computer-laptop kernel: [    1.333988] fuse init (API version 7.10)
Apr 27 08:42:48 computer-laptop kernel: [    1.334064] msgmni has been set to 1685
Apr 27 08:42:48 computer-laptop kernel: [    1.334215] alg: No test for stdrng (krng)
Apr 27 08:42:48 computer-laptop kernel: [    1.334225] io scheduler noop registered
Apr 27 08:42:48 computer-laptop kernel: [    1.334227] io scheduler anticipatory registered
Apr 27 08:42:48 computer-laptop kernel: [    1.334229] io scheduler deadline registered
Apr 27 08:42:48 computer-laptop kernel: [    1.334242] io scheduler cfq registered (default)
Apr 27 08:42:48 computer-laptop kernel: [    1.334618] pci 0000:01:00.0: Boot video device
Apr 27 08:42:48 computer-laptop kernel: [    1.338775] pcieport-driver 0000:00:01.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    1.338808] pcieport-driver 0000:00:01.0: found MSI capability
Apr 27 08:42:48 computer-laptop kernel: [    1.338829] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
Apr 27 08:42:48 computer-laptop kernel: [    1.338839] pci_express 0000:00:01.0:pcie00: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.338852] pci_express 0000:00:01.0:pcie02: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.338863] pci_express 0000:00:01.0:pcie03: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.338910] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    1.338957] pcieport-driver 0000:00:1c.0: found MSI capability
Apr 27 08:42:48 computer-laptop kernel: [    1.338988] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
Apr 27 08:42:48 computer-laptop kernel: [    1.339003] pci_express 0000:00:1c.0:pcie00: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.339014] pci_express 0000:00:1c.0:pcie02: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.339026] pci_express 0000:00:1c.0:pcie03: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.339099] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    1.339146] pcieport-driver 0000:00:1c.1: found MSI capability
Apr 27 08:42:48 computer-laptop kernel: [    1.339178] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
Apr 27 08:42:48 computer-laptop kernel: [    1.339193] pci_express 0000:00:1c.1:pcie00: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.339207] pci_express 0000:00:1c.1:pcie02: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.339218] pci_express 0000:00:1c.1:pcie03: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.339288] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    1.339335] pcieport-driver 0000:00:1c.2: found MSI capability
Apr 27 08:42:48 computer-laptop kernel: [    1.339367] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
Apr 27 08:42:48 computer-laptop kernel: [    1.339382] pci_express 0000:00:1c.2:pcie00: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.339394] pci_express 0000:00:1c.2:pcie02: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.339405] pci_express 0000:00:1c.2:pcie03: allocate port service
Apr 27 08:42:48 computer-laptop kernel: [    1.339483] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 27 08:42:48 computer-laptop kernel: [    1.339995] pciehp 0000:00:01.0:pcie02: HPC vendor_id 8086 device_id 2a41 ss_vid 0 ss_did 0
Apr 27 08:42:48 computer-laptop kernel: [    1.340025] pciehp 0000:00:01.0:pcie02: service driver pciehp loaded
Apr 27 08:42:48 computer-laptop kernel: [    1.340518] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 2940 ss_vid 0 ss_did 0
Apr 27 08:42:48 computer-laptop kernel: [    1.340553] pciehp 0000:00:1c.0:pcie02: service driver pciehp loaded
Apr 27 08:42:48 computer-laptop kernel: [    1.341047] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 2942 ss_vid 0 ss_did 0
Apr 27 08:42:48 computer-laptop kernel: [    1.341083] pciehp 0000:00:1c.1:pcie02: service driver pciehp loaded
Apr 27 08:42:48 computer-laptop kernel: [    1.341577] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 2944 ss_vid 0 ss_did 0
Apr 27 08:42:48 computer-laptop kernel: [    1.341615] pciehp 0000:00:1c.2:pcie02: service driver pciehp loaded
Apr 27 08:42:48 computer-laptop kernel: [    1.341623] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 27 08:42:48 computer-laptop kernel: [    1.341829] ACPI: AC Adapter [AC0] (on-line)
Apr 27 08:42:48 computer-laptop kernel: [    1.342296] ACPI: EC: non-query interrupt received, switching to interrupt mode
Apr 27 08:42:48 computer-laptop kernel: [    1.399402] ACPI: Battery Slot [BAT0] (battery present)
Apr 27 08:42:48 computer-laptop kernel: [    1.399470] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Apr 27 08:42:48 computer-laptop kernel: [    1.399473] ACPI: Power Button (FF) [PWRF]
Apr 27 08:42:48 computer-laptop kernel: [    1.399529] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Apr 27 08:42:48 computer-laptop kernel: [    1.402778] ACPI: Lid Switch [LID]
Apr 27 08:42:48 computer-laptop kernel: [    1.402820] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Apr 27 08:42:48 computer-laptop kernel: [    1.402828] ACPI: Sleep Button (CM) [SLPB]
Apr 27 08:42:48 computer-laptop kernel: [    1.403712] ACPI: SSDT 9DC62C98, 0223 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
Apr 27 08:42:48 computer-laptop kernel: [    1.404317] ACPI: SSDT 9DC60798, 06F1 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
Apr 27 08:42:48 computer-laptop kernel: [    1.405968] Monitor-Mwait will be used to enter C-1 state
Apr 27 08:42:48 computer-laptop kernel: [    1.405971] Monitor-Mwait will be used to enter C-2 state
Apr 27 08:42:48 computer-laptop kernel: [    1.405973] Monitor-Mwait will be used to enter C-3 state
Apr 27 08:42:48 computer-laptop kernel: [    1.405986] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 27 08:42:48 computer-laptop kernel: [    1.406008] processor ACPI_CPU:00: registered as cooling_device0
Apr 27 08:42:48 computer-laptop kernel: [    1.406011] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 27 08:42:48 computer-laptop kernel: [    1.406479] ACPI: SSDT 9DC61E18, 01CF (r1  PmRef    ApIst     3000 INTL 20051117)
Apr 27 08:42:48 computer-laptop kernel: [    1.407099] ACPI: SSDT 9DC60F18, 008D (r1  PmRef    ApCst     3000 INTL 20051117)
Apr 27 08:42:48 computer-laptop kernel: [    1.408975] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 27 08:42:48 computer-laptop kernel: [    1.408993] processor ACPI_CPU:01: registered as cooling_device1
Apr 27 08:42:48 computer-laptop kernel: [    1.408997] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 27 08:42:48 computer-laptop kernel: [    1.428185] thermal LNXTHERM:01: registered as thermal_zone0
Apr 27 08:42:48 computer-laptop kernel: [    1.429548] ACPI: Thermal Zone [THRM] (55 C)
Apr 27 08:42:48 computer-laptop kernel: [    1.429602] isapnp: Scanning for PnP cards...
Apr 27 08:42:48 computer-laptop kernel: [    1.785456] isapnp: No Plug & Play device found
Apr 27 08:42:48 computer-laptop kernel: [    1.796260] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Apr 27 08:42:48 computer-laptop kernel: [    1.797273] brd: module loaded
Apr 27 08:42:48 computer-laptop kernel: [    1.797557] loop: module loaded
Apr 27 08:42:48 computer-laptop kernel: [    1.797618] Fixed MDIO Bus: probed
Apr 27 08:42:48 computer-laptop kernel: [    1.797623] PPP generic driver version 2.4.2
Apr 27 08:42:48 computer-laptop kernel: [    1.797675] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Apr 27 08:42:48 computer-laptop kernel: [    1.797700] Driver 'sd' needs updating - please use bus_type methods
Apr 27 08:42:48 computer-laptop kernel: [    1.797709] Driver 'sr' needs updating - please use bus_type methods
Apr 27 08:42:48 computer-laptop kernel: [    1.797744] ahci 0000:00:1f.2: version 3.0
Apr 27 08:42:48 computer-laptop kernel: [    1.797757] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr 27 08:42:48 computer-laptop kernel: [    1.797793] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
Apr 27 08:42:48 computer-laptop kernel: [    1.797857] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
Apr 27 08:42:48 computer-laptop kernel: [    1.797860] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pio slum part ems 
Apr 27 08:42:48 computer-laptop kernel: [    1.797865] ahci 0000:00:1f.2: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    1.798013] scsi0 : ahci
Apr 27 08:42:48 computer-laptop kernel: [    1.798085] scsi1 : ahci
Apr 27 08:42:48 computer-laptop kernel: [    1.798139] scsi2 : ahci
Apr 27 08:42:48 computer-laptop kernel: [    1.798190] scsi3 : ahci
Apr 27 08:42:48 computer-laptop kernel: [    1.798316] ata1: SATA max UDMA/133 abar m2048@0xd3d04000 port 0xd3d04100 irq 2299
Apr 27 08:42:48 computer-laptop kernel: [    1.798320] ata2: SATA max UDMA/133 abar m2048@0xd3d04000 port 0xd3d04180 irq 2299
Apr 27 08:42:48 computer-laptop kernel: [    1.798322] ata3: DUMMY
Apr 27 08:42:48 computer-laptop kernel: [    1.798323] ata4: DUMMY
Apr 27 08:42:48 computer-laptop kernel: [    2.116019] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 27 08:42:48 computer-laptop kernel: [    2.117429] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 27 08:42:48 computer-laptop kernel: [    2.117623] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
Apr 27 08:42:48 computer-laptop kernel: [    2.117626] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 27 08:42:48 computer-laptop kernel: [    2.118433] ata1.00: ATA-8: Hitachi HTS543232L9A300, FB4OC4DC, max UDMA/133
Apr 27 08:42:48 computer-laptop kernel: [    2.118436] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
Apr 27 08:42:48 computer-laptop kernel: [    2.120033] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Apr 27 08:42:48 computer-laptop kernel: [    2.120226] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
Apr 27 08:42:48 computer-laptop kernel: [    2.120228] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 27 08:42:48 computer-laptop kernel: [    2.121066] ata1.00: configured for UDMA/133
Apr 27 08:42:48 computer-laptop kernel: [    2.440017] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 27 08:42:48 computer-laptop kernel: [    2.447493] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
Apr 27 08:42:48 computer-laptop kernel: [    2.447496] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 27 08:42:48 computer-laptop kernel: [    2.451232] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50N, RV06, max UDMA/133
Apr 27 08:42:48 computer-laptop kernel: [    2.457079] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
Apr 27 08:42:48 computer-laptop kernel: [    2.457082] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Apr 27 08:42:48 computer-laptop kernel: [    2.460842] ata2.00: configured for UDMA/133
Apr 27 08:42:48 computer-laptop kernel: [    2.569503] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 FB4O PQ: 0 ANSI: 5
Apr 27 08:42:48 computer-laptop kernel: [    2.569584] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 27 08:42:48 computer-laptop kernel: [    2.569599] sd 0:0:0:0: [sda] Write Protect is off
Apr 27 08:42:48 computer-laptop kernel: [    2.569601] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 27 08:42:48 computer-laptop kernel: [    2.569625] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 27 08:42:48 computer-laptop kernel: [    2.569676] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 27 08:42:48 computer-laptop kernel: [    2.569689] sd 0:0:0:0: [sda] Write Protect is off
Apr 27 08:42:48 computer-laptop kernel: [    2.569691] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 27 08:42:48 computer-laptop kernel: [    2.569714] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 27 08:42:48 computer-laptop kernel: [    2.569717]  sda: sda1 sda2 < sda5 >
Apr 27 08:42:48 computer-laptop kernel: [    2.617402] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 27 08:42:48 computer-laptop kernel: [    2.617439] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 27 08:42:48 computer-laptop kernel: [    2.620395] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50N  RV06 PQ: 0 ANSI: 5
Apr 27 08:42:48 computer-laptop kernel: [    2.952602] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 27 08:42:48 computer-laptop kernel: [    2.952605] Uniform CD-ROM driver Revision: 3.20
Apr 27 08:42:48 computer-laptop kernel: [    2.952678] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 27 08:42:48 computer-laptop kernel: [    2.952710] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 27 08:42:48 computer-laptop kernel: [    2.953358] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 27 08:42:48 computer-laptop kernel: [    2.953375] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Apr 27 08:42:48 computer-laptop kernel: [    2.953386] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    2.953389] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr 27 08:42:48 computer-laptop kernel: [    2.953440] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr 27 08:42:48 computer-laptop kernel: [    2.957344] ehci_hcd 0000:00:1a.7: debug port 1
Apr 27 08:42:48 computer-laptop kernel: [    2.957350] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Apr 27 08:42:48 computer-laptop kernel: [    2.957368] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd3d04c00
Apr 27 08:42:48 computer-laptop kernel: [    2.972008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Apr 27 08:42:48 computer-laptop kernel: [    2.972063] usb usb1: configuration #1 chosen from 1 choice
Apr 27 08:42:48 computer-laptop kernel: [    2.972087] hub 1-0:1.0: USB hub found
Apr 27 08:42:48 computer-laptop kernel: [    2.972094] hub 1-0:1.0: 6 ports detected
Apr 27 08:42:48 computer-laptop kernel: [    2.972195] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr 27 08:42:48 computer-laptop kernel: [    2.972206] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    2.972209] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 27 08:42:48 computer-laptop kernel: [    2.972248] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Apr 27 08:42:48 computer-laptop kernel: [    2.976144] ehci_hcd 0000:00:1d.7: debug port 1
Apr 27 08:42:48 computer-laptop kernel: [    2.976150] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Apr 27 08:42:48 computer-laptop kernel: [    2.976162] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd3d04800
Apr 27 08:42:48 computer-laptop kernel: [    2.992008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr 27 08:42:48 computer-laptop kernel: [    2.992058] usb usb2: configuration #1 chosen from 1 choice
Apr 27 08:42:48 computer-laptop kernel: [    2.992080] hub 2-0:1.0: USB hub found
Apr 27 08:42:48 computer-laptop kernel: [    2.992086] hub 2-0:1.0: 6 ports detected
Apr 27 08:42:48 computer-laptop kernel: [    2.992172] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 27 08:42:48 computer-laptop kernel: [    2.992187] uhci_hcd: USB Universal Host Controller Interface driver
Apr 27 08:42:48 computer-laptop kernel: [    2.992205] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 27 08:42:48 computer-laptop kernel: [    2.992211] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    2.992214] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr 27 08:42:48 computer-laptop kernel: [    2.992252] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Apr 27 08:42:48 computer-laptop kernel: [    2.992284] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d0c0
Apr 27 08:42:48 computer-laptop kernel: [    2.992351] usb usb3: configuration #1 chosen from 1 choice
Apr 27 08:42:48 computer-laptop kernel: [    2.992373] hub 3-0:1.0: USB hub found
Apr 27 08:42:48 computer-laptop kernel: [    2.992379] hub 3-0:1.0: 2 ports detected
Apr 27 08:42:48 computer-laptop kernel: [    2.992464] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr 27 08:42:48 computer-laptop kernel: [    2.992470] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    2.992473] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr 27 08:42:48 computer-laptop kernel: [    2.992512] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Apr 27 08:42:48 computer-laptop kernel: [    2.992544] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d0a0
Apr 27 08:42:48 computer-laptop kernel: [    2.992608] usb usb4: configuration #1 chosen from 1 choice
Apr 27 08:42:48 computer-laptop kernel: [    2.992633] hub 4-0:1.0: USB hub found
Apr 27 08:42:48 computer-laptop kernel: [    2.992638] hub 4-0:1.0: 2 ports detected
Apr 27 08:42:48 computer-laptop kernel: [    2.992712] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Apr 27 08:42:48 computer-laptop kernel: [    2.992718] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    2.992721] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Apr 27 08:42:48 computer-laptop kernel: [    2.992760] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Apr 27 08:42:48 computer-laptop kernel: [    2.992785] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000d080
Apr 27 08:42:48 computer-laptop kernel: [    2.992850] usb usb5: configuration #1 chosen from 1 choice
Apr 27 08:42:48 computer-laptop kernel: [    2.992872] hub 5-0:1.0: USB hub found
Apr 27 08:42:48 computer-laptop kernel: [    2.992877] hub 5-0:1.0: 2 ports detected
Apr 27 08:42:48 computer-laptop kernel: [    2.992960] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr 27 08:42:48 computer-laptop kernel: [    2.992966] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    2.992969] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 27 08:42:48 computer-laptop kernel: [    2.993012] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Apr 27 08:42:48 computer-laptop kernel: [    2.993036] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d060
Apr 27 08:42:48 computer-laptop kernel: [    2.993103] usb usb6: configuration #1 chosen from 1 choice
Apr 27 08:42:48 computer-laptop kernel: [    2.993126] hub 6-0:1.0: USB hub found
Apr 27 08:42:48 computer-laptop kernel: [    2.993131] hub 6-0:1.0: 2 ports detected
Apr 27 08:42:48 computer-laptop kernel: [    2.993208] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr 27 08:42:48 computer-laptop kernel: [    2.993214] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    2.993217] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 27 08:42:48 computer-laptop kernel: [    2.993255] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Apr 27 08:42:48 computer-laptop kernel: [    2.993280] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d040
Apr 27 08:42:48 computer-laptop kernel: [    2.993345] usb usb7: configuration #1 chosen from 1 choice
Apr 27 08:42:48 computer-laptop kernel: [    2.993369] hub 7-0:1.0: USB hub found
Apr 27 08:42:48 computer-laptop kernel: [    2.993375] hub 7-0:1.0: 2 ports detected
Apr 27 08:42:48 computer-laptop kernel: [    2.993450] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr 27 08:42:48 computer-laptop kernel: [    2.993456] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    2.993459] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 27 08:42:48 computer-laptop kernel: [    2.993498] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Apr 27 08:42:48 computer-laptop kernel: [    2.993530] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d020
Apr 27 08:42:48 computer-laptop kernel: [    2.993599] usb usb8: configuration #1 chosen from 1 choice
Apr 27 08:42:48 computer-laptop kernel: [    2.993622] hub 8-0:1.0: USB hub found
Apr 27 08:42:48 computer-laptop kernel: [    2.993627] hub 8-0:1.0: 2 ports detected
Apr 27 08:42:48 computer-laptop kernel: [    2.993744] usbcore: registered new interface driver libusual
Apr 27 08:42:48 computer-laptop kernel: [    2.993770] usbcore: registered new interface driver usbserial
Apr 27 08:42:48 computer-laptop kernel: [    2.993780] USB Serial support registered for generic
Apr 27 08:42:48 computer-laptop kernel: [    2.993795] usbcore: registered new interface driver usbserial_generic
Apr 27 08:42:48 computer-laptop kernel: [    2.993797] usbserial: USB Serial Driver core
Apr 27 08:42:48 computer-laptop kernel: [    2.993847] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 27 08:42:48 computer-laptop kernel: [    2.996039] i8042.c: Detected active multiplexing controller, rev 1.1.
Apr 27 08:42:48 computer-laptop kernel: [    2.997379] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 27 08:42:48 computer-laptop kernel: [    2.997383] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Apr 27 08:42:48 computer-laptop kernel: [    2.997386] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Apr 27 08:42:48 computer-laptop kernel: [    2.997388] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Apr 27 08:42:48 computer-laptop kernel: [    2.997390] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Apr 27 08:42:48 computer-laptop kernel: [    3.001036] mice: PS/2 mouse device common for all mice
Apr 27 08:42:48 computer-laptop kernel: [    3.017065] rtc_cmos 00:07: RTC can wake from S4
Apr 27 08:42:48 computer-laptop kernel: [    3.017093] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Apr 27 08:42:48 computer-laptop kernel: [    3.017122] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Apr 27 08:42:48 computer-laptop kernel: [    3.017175] device-mapper: uevent: version 1.0.3
Apr 27 08:42:48 computer-laptop kernel: [    3.017248] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Apr 27 08:42:48 computer-laptop kernel: [    3.017312] device-mapper: multipath: version 1.0.5 loaded
Apr 27 08:42:48 computer-laptop kernel: [    3.017314] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 27 08:42:48 computer-laptop kernel: [    3.017378] EISA: Probing bus 0 at eisa.0
Apr 27 08:42:48 computer-laptop kernel: [    3.017412] EISA: Detected 0 cards.
Apr 27 08:42:48 computer-laptop kernel: [    3.017515] cpuidle: using governor ladder
Apr 27 08:42:48 computer-laptop kernel: [    3.017623] cpuidle: using governor menu
Apr 27 08:42:48 computer-laptop kernel: [    3.018080] TCP cubic registered
Apr 27 08:42:48 computer-laptop kernel: [    3.018172] NET: Registered protocol family 10
Apr 27 08:42:48 computer-laptop kernel: [    3.018557] lo: Disabled Privacy Extensions
Apr 27 08:42:48 computer-laptop kernel: [    3.018867] NET: Registered protocol family 17
Apr 27 08:42:48 computer-laptop kernel: [    3.018882] Bluetooth: L2CAP ver 2.11
Apr 27 08:42:48 computer-laptop kernel: [    3.018884] Bluetooth: L2CAP socket layer initialized
Apr 27 08:42:48 computer-laptop kernel: [    3.018887] Bluetooth: SCO (Voice Link) ver 0.6
Apr 27 08:42:48 computer-laptop kernel: [    3.018888] Bluetooth: SCO socket layer initialized
Apr 27 08:42:48 computer-laptop kernel: [    3.018914] Bluetooth: RFCOMM socket layer initialized
Apr 27 08:42:48 computer-laptop kernel: [    3.018918] Bluetooth: RFCOMM TTY layer initialized
Apr 27 08:42:48 computer-laptop kernel: [    3.018920] Bluetooth: RFCOMM ver 1.10
Apr 27 08:42:48 computer-laptop kernel: [    3.019277] Marking TSC unstable due to TSC halts in idle
Apr 27 08:42:48 computer-laptop kernel: [    3.020397] Using IPI No-Shortcut mode
Apr 27 08:42:48 computer-laptop kernel: [    3.020454] registered taskstats version 1
Apr 27 08:42:48 computer-laptop kernel: [    3.020556]   Magic number: 5:292:741
Apr 27 08:42:48 computer-laptop kernel: [    3.020636] rtc_cmos 00:07: setting system clock to 2009-04-27 15:42:35 UTC (1240846955)
Apr 27 08:42:48 computer-laptop kernel: [    3.020639] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 27 08:42:48 computer-laptop kernel: [    3.020641] EDD information not available.
Apr 27 08:42:48 computer-laptop kernel: [    3.020875] Freeing unused kernel memory: 532k freed
Apr 27 08:42:48 computer-laptop kernel: [    3.021021] Write protecting the kernel text: 4128k
Apr 27 08:42:48 computer-laptop kernel: [    3.021079] Write protecting the kernel read-only data: 1532k
Apr 27 08:42:48 computer-laptop kernel: [    3.054405] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr 27 08:42:48 computer-laptop kernel: [    3.307069] tg3.c:v3.94 (August 14, 2008)
Apr 27 08:42:48 computer-laptop kernel: [    3.307146] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 27 08:42:48 computer-laptop kernel: [    3.307171] tg3 0000:02:00.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [    3.309079] usb 2-5: new high speed USB device using ehci_hcd and address 2
Apr 27 08:42:48 computer-laptop kernel: [    3.425438] ohci1394 0000:07:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr 27 08:42:48 computer-laptop kernel: [    3.476252] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[d3c00000-d3c007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 27 08:42:48 computer-laptop kernel: [    3.606765] usb 2-5: configuration #1 chosen from 1 choice
Apr 27 08:42:48 computer-laptop kernel: [    3.710681] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:24:8c:6f:34:96
Apr 27 08:42:48 computer-laptop kernel: [    3.710684] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
Apr 27 08:42:48 computer-laptop kernel: [    3.710686] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr 27 08:42:48 computer-laptop kernel: [    4.123145] PM: Starting manual resume from disk
Apr 27 08:42:48 computer-laptop kernel: [    4.123148] PM: Resume from partition 8:5
Apr 27 08:42:48 computer-laptop kernel: [    4.123149] PM: Checking hibernation image.
Apr 27 08:42:48 computer-laptop kernel: [    4.123298] PM: Resume from disk failed.
Apr 27 08:42:48 computer-laptop kernel: [    4.128315] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 27 08:42:48 computer-laptop kernel: [    4.128317] EXT3-fs: write access will be enabled during recovery.
Apr 27 08:42:48 computer-laptop kernel: [    4.500043] Clocksource tsc unstable (delta = -334107454 ns)
Apr 27 08:42:48 computer-laptop kernel: [    4.752527] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001d61699]
Apr 27 08:42:48 computer-laptop kernel: [    5.361852] kjournald starting.  Commit interval 5 seconds
Apr 27 08:42:48 computer-laptop kernel: [    5.361883] EXT3-fs: sda1: orphan cleanup on readonly fs
Apr 27 08:42:48 computer-laptop kernel: [    5.361888] ext3_orphan_cleanup: deleting unreferenced inode 4628503
Apr 27 08:42:48 computer-laptop kernel: [    5.361907] EXT3-fs: sda1: 1 orphan inode deleted
Apr 27 08:42:48 computer-laptop kernel: [    5.361909] EXT3-fs: recovery complete.
Apr 27 08:42:48 computer-laptop kernel: [    5.366986] EXT3-fs: mounted filesystem with ordered data mode.
Apr 27 08:42:48 computer-laptop kernel: [   10.699843] udev: starting version 141
Apr 27 08:42:48 computer-laptop kernel: [   10.925076] cfg80211: Calling CRDA to update world regulatory domain
Apr 27 08:42:48 computer-laptop kernel: [   11.161702] iTCO_vendor_support: vendor-support=0
Apr 27 08:42:48 computer-laptop kernel: [   11.196041] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Apr 27 08:42:48 computer-laptop kernel: [   11.196291] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
Apr 27 08:42:48 computer-laptop kernel: [   11.196370] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 27 08:42:48 computer-laptop kernel: [   11.213530] cfg80211: World regulatory domain updated:
Apr 27 08:42:48 computer-laptop kernel: [   11.213533] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 27 08:42:48 computer-laptop kernel: [   11.213536] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 27 08:42:48 computer-laptop kernel: [   11.213538] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 27 08:42:48 computer-laptop kernel: [   11.213540] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 27 08:42:48 computer-laptop kernel: [   11.213542] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 27 08:42:48 computer-laptop kernel: [   11.213544] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 27 08:42:48 computer-laptop kernel: [   11.292809] Linux agpgart interface v0.103
Apr 27 08:42:48 computer-laptop kernel: [   11.326159] input: PC Speaker as /devices/platform/pcspkr/input/input5
Apr 27 08:42:48 computer-laptop kernel: [   11.407532] sdhci: Secure Digital Host Controller Interface driver
Apr 27 08:42:48 computer-laptop kernel: [   11.407535] sdhci: Copyright(c) Pierre Ossman
Apr 27 08:42:48 computer-laptop kernel: [   11.419606] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Apr 27 08:42:48 computer-laptop kernel: [   11.484508] sdhci-pci 0000:07:03.1: SDHCI controller found [1180:0822] (rev 22)
Apr 27 08:42:48 computer-laptop kernel: [   11.484523] sdhci-pci 0000:07:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr 27 08:42:48 computer-laptop kernel: [   11.485578] sdhci-pci 0000:07:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
Apr 27 08:42:48 computer-laptop kernel: [   11.487632] mmc0: SDHCI controller on PCI [0000:07:03.1] using DMA
Apr 27 08:42:48 computer-laptop kernel: [   11.519308] ricoh-mmc: Ricoh MMC Controller disabling driver
Apr 27 08:42:48 computer-laptop kernel: [   11.519311] ricoh-mmc: Copyright(c) Philip Langdale
Apr 27 08:42:48 computer-laptop kernel: [   11.519329] ricoh-mmc: Ricoh MMC controller found at 0000:07:03.2 [1180:0843] (rev 12)
Apr 27 08:42:48 computer-laptop kernel: [   11.519345] ricoh-mmc: Controller is now disabled.
Apr 27 08:42:48 computer-laptop kernel: [   11.618943] Linux video capture interface: v2.00
Apr 27 08:42:48 computer-laptop kernel: [   11.627479] asus-laptop: Asus Laptop Support version 0.42
Apr 27 08:42:48 computer-laptop kernel: [   11.632889] asus-laptop: BSTS called, 0xff7f returned
Apr 27 08:42:48 computer-laptop kernel: [   11.633634] asus-laptop: Brightness ignored, must be controlled by ACPI video driver
Apr 27 08:42:48 computer-laptop kernel: [   11.698079] acpi device:09: registered as cooling_device2
Apr 27 08:42:48 computer-laptop kernel: [   11.698296] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/device:06/input/input6
Apr 27 08:42:48 computer-laptop kernel: [   11.701388] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
Apr 27 08:42:48 computer-laptop kernel: [   11.841180] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (04f2:b105)
Apr 27 08:42:48 computer-laptop kernel: [   11.844009] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input7
Apr 27 08:42:48 computer-laptop kernel: [   11.845133] usbcore: registered new interface driver uvcvideo
Apr 27 08:42:48 computer-laptop kernel: [   11.845155] USB Video Class driver (v0.1.0)
Apr 27 08:42:48 computer-laptop kernel: [   11.886948] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Apr 27 08:42:48 computer-laptop kernel: [   11.886950] iwlagn: Copyright(c) 2003-2008 Intel Corporation
Apr 27 08:42:48 computer-laptop kernel: [   11.887033] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 27 08:42:48 computer-laptop kernel: [   11.887061] iwlagn 0000:03:00.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [   11.887137] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Apr 27 08:42:48 computer-laptop kernel: [   11.912380] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
Apr 27 08:42:48 computer-laptop kernel: [   11.912452] iwlagn 0000:03:00.0: irq 2298 for MSI/MSI-X
Apr 27 08:42:48 computer-laptop kernel: [   11.914456] phy0: Selected rate control algorithm 'iwl-agn-rs'
Apr 27 08:42:48 computer-laptop kernel: [   12.018431] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr 27 08:42:48 computer-laptop kernel: [   12.018491] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr 27 08:42:48 computer-laptop kernel: [   12.050471] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Apr 27 08:42:48 computer-laptop kernel: [   12.329179] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa580b1, caps: 0xa04711/0x200000
Apr 27 08:42:48 computer-laptop kernel: [   12.370378] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Apr 27 08:42:48 computer-laptop kernel: [   13.053007] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x011f1c00
Apr 27 08:42:48 computer-laptop kernel: [   13.288788] lp: driver loaded but no devices found
Apr 27 08:42:48 computer-laptop kernel: [   13.364580] Adding 7454120k swap on /dev/sda5.  Priority:-1 extents:1 across:7454120k
Apr 27 08:42:48 computer-laptop kernel: [   13.904661] EXT3 FS on sda1, internal journal
Apr 27 08:42:48 computer-laptop kernel: [   14.790513] type=1505 audit(1240846967.267:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2295
Apr 27 08:42:48 computer-laptop kernel: [   14.832714] type=1505 audit(1240846967.308:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2299
Apr 27 08:42:48 computer-laptop kernel: [   14.832791] type=1505 audit(1240846967.308:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2299
Apr 27 08:42:48 computer-laptop kernel: [   14.832831] type=1505 audit(1240846967.308:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2299
Apr 27 08:42:48 computer-laptop kernel: [   14.832870] type=1505 audit(1240846967.308:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2299
Apr 27 08:42:48 computer-laptop kernel: [   14.949713] type=1505 audit(1240846967.428:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2304
Apr 27 08:42:48 computer-laptop kernel: [   14.949858] type=1505 audit(1240846967.428:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2304
Apr 27 08:42:48 computer-laptop kernel: [   14.974586] type=1505 audit(1240846967.452:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2308
Apr 27 08:42:48 computer-laptop acpid: client connected from 2807[111:120] 
Apr 27 08:42:49 computer-laptop bluetoothd[2815]: Bluetooth daemon
Apr 27 08:42:49 computer-laptop bluetoothd[2815]: Starting SDP server
Apr 27 08:42:49 computer-laptop kernel: [   16.601809] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 27 08:42:49 computer-laptop kernel: [   16.601812] Bluetooth: BNEP filters: protocol multicast
Apr 27 08:42:49 computer-laptop bluetoothd[2815]: bridge pan0 created
Apr 27 08:42:49 computer-laptop bluetoothd[2815]: Registered interface org.bluez.Service on path /org/bluez/2815/any
Apr 27 08:42:49 computer-laptop bluetoothd[2815]: Starting experimental netlink support
Apr 27 08:42:49 computer-laptop kernel: [   16.610370] Bridge firewalling registered
Apr 27 08:42:49 computer-laptop bluetoothd[2815]: Failed to find Bluetooth netlink family
Apr 27 08:42:49 computer-laptop acpid: client connected from 2858[0:0] 
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  starting... 
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4237_rfkill_5100AGN_wlan 
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_24_8c_6f_34_96 
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn') 
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_22_fa_48_f8_ce 
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  Trying to start the supplicant... 
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  Trying to start the system settings daemon... 
Apr 27 08:42:50 computer-laptop avahi-daemon[2901]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Apr 27 08:42:50 computer-laptop avahi-daemon[2901]: Successfully dropped root privileges.
Apr 27 08:42:50 computer-laptop avahi-daemon[2901]: avahi-daemon 0.6.23 starting up.
Apr 27 08:42:50 computer-laptop avahi-daemon[2901]: Successfully called chroot().
Apr 27 08:42:50 computer-laptop avahi-daemon[2901]: Successfully dropped remaining capabilities.
Apr 27 08:42:50 computer-laptop nm-system-settings:    SCPlugin-Ifupdown: init!
Apr 27 08:42:50 computer-laptop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Apr 27 08:42:50 computer-laptop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Apr 27 08:42:50 computer-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_24_8c_6f_34_96, iface: eth0): not well known
Apr 27 08:42:50 computer-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_22_fa_48_f8_ce, iface: wlan0): not well known
Apr 27 08:42:50 computer-laptop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Apr 27 08:42:50 computer-laptop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 27 08:42:50 computer-laptop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 27 08:42:50 computer-laptop nm-system-settings:    SCPlugin-Ifupdown: (146483000) ... get_connections.
Apr 27 08:42:50 computer-laptop nm-system-settings:    SCPlugin-Ifupdown: (146483000) ... get_connections (managed=false): return empty list.
Apr 27 08:42:50 computer-laptop avahi-daemon[2901]: No service file found in /etc/avahi/services.
Apr 27 08:42:50 computer-laptop avahi-daemon[2901]: Network interface enumeration completed.
Apr 27 08:42:50 computer-laptop avahi-daemon[2901]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 27 08:42:50 computer-laptop avahi-daemon[2901]: Server startup complete. Host name is computer-laptop.local. Local service cookie is 4238895252.
Apr 27 08:42:50 computer-laptop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Apr 27 08:42:50 computer-laptop kernel: [   17.858219] ppdev: user-space parallel port driver
Apr 27 08:42:50 computer-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
Apr 27 08:42:50 computer-laptop anacron[3013]: Anacron 2.3 started on 2009-04-27
Apr 27 08:42:50 computer-laptop anacron[3013]: Will run job `cron.daily' in 5 min.
Apr 27 08:42:50 computer-laptop anacron[3013]: Will run job `cron.weekly' in 10 min.
Apr 27 08:42:50 computer-laptop anacron[3013]: Will run job `cron.monthly' in 15 min.
Apr 27 08:42:50 computer-laptop anacron[3013]: Jobs will be executed sequentially
Apr 27 08:42:51 computer-laptop /usr/sbin/cron[3056]: (CRON) INFO (pidfile fd = 3)
Apr 27 08:42:51 computer-laptop /usr/sbin/cron[3057]: (CRON) STARTUP (fork ok)
Apr 27 08:42:51 computer-laptop /usr/sbin/cron[3057]: (CRON) INFO (Running @reboot jobs)
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (eth0): bringing up device. 
Apr 27 08:42:54 computer-laptop kernel: [   21.521878] tg3 0000:02:00.0: irq 2297 for MSI/MSI-X
Apr 27 08:42:54 computer-laptop nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_24_8c_6f_34_96
Apr 27 08:42:54 computer-laptop kernel: [   21.574996] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (eth0): preparing device. 
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (wlan0): bringing up device. 
Apr 27 08:42:54 computer-laptop kernel: [   21.581145] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-1.ucode
Apr 27 08:42:54 computer-laptop kernel: [   21.812242] Registered led device: iwl-phy0:radio
Apr 27 08:42:54 computer-laptop kernel: [   21.814674] Registered led device: iwl-phy0:assoc
Apr 27 08:42:54 computer-laptop kernel: [   21.814697] Registered led device: iwl-phy0:RX
Apr 27 08:42:54 computer-laptop kernel: [   21.814712] Registered led device: iwl-phy0:TX
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (wlan0): preparing device. 
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Apr 27 08:42:54 computer-laptop kernel: [   21.821539] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Apr 27 08:42:54 computer-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
Apr 27 08:42:54 computer-laptop console-kit-daemon[2656]: WARNING: Couldn't read /proc/2655/environ: Failed to open file '/proc/2655/environ': No such file or directory 
Apr 27 08:42:55 computer-laptop kernel: [   23.312662] wlan0: authenticate with AP 00:16:b6:02:e7:72
Apr 27 08:42:55 computer-laptop kernel: [   23.314689] wlan0: authenticated
Apr 27 08:42:55 computer-laptop kernel: [   23.314693] wlan0: associate with AP 00:16:b6:02:e7:72
Apr 27 08:42:55 computer-laptop kernel: [   23.357313] wlan0: RX AssocResp from 00:16:b6:02:e7:72 (capab=0x401 status=0 aid=8)
Apr 27 08:42:55 computer-laptop kernel: [   23.357316] wlan0: associated
Apr 27 08:42:55 computer-laptop kernel: [   23.359536] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 27 08:42:55 computer-laptop kernel: [   23.359621] wlan0: disassociating by local choice (reason=3)
Apr 27 08:42:57 computer-laptop avahi-daemon[2901]: Registering new address record for fe80::222:faff:fe48:f8ce on wlan0.*.
Apr 27 08:43:06 computer-laptop kernel: [   34.129040] wlan0: no IPv6 routers present
Apr 27 08:43:32 computer-laptop kernel: [   59.816121] Corrupted low memory at c000fcf4 (fcf4 phys) = 83840000
Apr 27 08:43:32 computer-laptop kernel: [   59.816126] Corrupted low memory at c000fcf8 (fcf8 phys) = 0010000a
Apr 27 08:43:32 computer-laptop kernel: [   59.816133] ------------[ cut here ]------------
Apr 27 08:43:32 computer-laptop kernel: [   59.816136] WARNING: at /build/buildd/linux-2.6.28/arch/x86/kernel/setup.c:719 check_for_bios_corruption+0xc8/0xd0()
Apr 27 08:43:32 computer-laptop kernel: [   59.816138] Memory corruption detected in low memory
Apr 27 08:43:32 computer-laptop kernel: [   59.816140] Modules linked in: binfmt_misc ppdev bridge stp bnep input_polldev lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss arc4 snd_pcm ecb snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn snd_seq uvcvideo iwlcore snd_timer compat_ioctl32 snd_seq_device intel_agp mac80211 video asus_laptop videodev v4l1_compat ricoh_mmc sdhci_pci sdhci snd pcspkr agpgart psmouse serio_raw iTCO_wdt iTCO_vendor_support output led_class soundcore snd_page_alloc cfg80211 ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
Apr 27 08:43:32 computer-laptop kernel: [   59.816200] Pid: 0, comm: swapper Not tainted 2.6.28-11-generic #42-Ubuntu
Apr 27 08:43:32 computer-laptop kernel: [   59.816202] Call Trace:
Apr 27 08:43:32 computer-laptop kernel: [   59.816206]  [<c0139ab0>] warn_slowpath+0x60/0x80
Apr 27 08:43:32 computer-laptop kernel: [   59.816209]  [<c013a2f9>] ? release_console_sem+0x1c9/0x200
Apr 27 08:43:32 computer-laptop kernel: [   59.816214]  [<c015aee3>] ? tick_dev_program_event+0x33/0xc0
Apr 27 08:43:32 computer-laptop kernel: [   59.816218]  [<c0500ac6>] ? printk+0x18/0x1a
Apr 27 08:43:32 computer-laptop kernel: [   59.816221]  [<c01079c8>] check_for_bios_corruption+0xc8/0xd0
Apr 27 08:43:32 computer-laptop kernel: [   59.816224]  [<c01079d8>] periodic_check_for_corruption+0x8/0x30
Apr 27 08:43:32 computer-laptop kernel: [   59.816227]  [<c0143b00>] run_timer_softirq+0x130/0x200
Apr 27 08:43:32 computer-laptop kernel: [   59.816230]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
Apr 27 08:43:32 computer-laptop kernel: [   59.816233]  [<c01079d0>] ? periodic_check_for_corruption+0x0/0x30
Apr 27 08:43:32 computer-laptop kernel: [   59.816237]  [<c013f197>] __do_softirq+0x97/0x170
Apr 27 08:43:32 computer-laptop kernel: [   59.816240]  [<c0106f30>] ? timer_interrupt+0x30/0x80
Apr 27 08:43:32 computer-laptop kernel: [   59.816243]  [<c013f2cd>] do_softirq+0x5d/0x60
Apr 27 08:43:32 computer-laptop kernel: [   59.816246]  [<c013f445>] irq_exit+0x55/0x90
Apr 27 08:43:32 computer-laptop kernel: [   59.816248]  [<c0106853>] do_IRQ+0x83/0xa0
Apr 27 08:43:32 computer-laptop kernel: [   59.816251]  [<c01051f3>] common_interrupt+0x23/0x30
Apr 27 08:43:32 computer-laptop kernel: [   59.816255]  [<c0319417>] ? acpi_idle_enter_bm+0x269/0x2b8
Apr 27 08:43:32 computer-laptop kernel: [   59.816259]  [<c040f4df>] cpuidle_idle_call+0x6f/0xd0
Apr 27 08:43:32 computer-laptop kernel: [   59.816261]  [<c010285d>] cpu_idle+0x6d/0xd0
Apr 27 08:43:32 computer-laptop kernel: [   59.816265]  [<c04f110e>] rest_init+0x4e/0x60
Apr 27 08:43:32 computer-laptop kernel: [   59.816267] ---[ end trace 96382f6005d080d9 ]---
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto default' 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto default' has security, but secrets are required. 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto default' has security, and secrets exist.  No new secrets needed. 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Config: added 'ssid' value 'default' 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Apr 27 08:43:39 computer-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 27 08:43:39 computer-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 27 08:43:39 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 27 08:43:46 computer-laptop kernel: [   74.393955] wlan0: authenticate with AP 00:1d:6a:b5:46:3b
Apr 27 08:43:46 computer-laptop kernel: [   74.394905] wlan0: authenticate with AP 00:1d:6a:b5:46:3b
Apr 27 08:43:46 computer-laptop kernel: [   74.396972] wlan0: authenticated
Apr 27 08:43:46 computer-laptop kernel: [   74.396975] wlan0: associate with AP 00:1d:6a:b5:46:3b
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Apr 27 08:43:46 computer-laptop kernel: [   74.401186] wlan0: RX AssocResp from 00:1d:6a:b5:46:3b (capab=0x31 status=0 aid=1)
Apr 27 08:43:46 computer-laptop kernel: [   74.401189] wlan0: associated
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'default'. 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  dhclient started with pid 3568 
Apr 27 08:43:46 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 27 08:43:46 computer-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Apr 27 08:43:46 computer-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Apr 27 08:43:46 computer-laptop dhclient: All rights reserved.
Apr 27 08:43:46 computer-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 27 08:43:46 computer-laptop dhclient: 
Apr 27 08:43:46 computer-laptop dhclient: wmaster0: unknown hardware address type 801
Apr 27 08:43:47 computer-laptop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Apr 27 08:43:47 computer-laptop dhclient: wmaster0: unknown hardware address type 801
Apr 27 08:43:47 computer-laptop dhclient: Listening on LPF/wlan0/00:22:fa:48:f8:ce
Apr 27 08:43:47 computer-laptop dhclient: Sending on   LPF/wlan0/00:22:fa:48:f8:ce
Apr 27 08:43:47 computer-laptop dhclient: Sending on   Socket/fallback
Apr 27 08:43:48 computer-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Apr 27 08:43:49 computer-laptop dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
Apr 27 08:43:49 computer-laptop dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
Apr 27 08:43:49 computer-laptop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Apr 27 08:43:49 computer-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>    address 192.168.1.101 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>    gateway 192.168.1.1 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>    nameserver '192.168.1.1' 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>    domain name 'oc.cox.net' 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 27 08:43:49 computer-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 27 08:43:49 computer-laptop avahi-daemon[2901]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Apr 27 08:43:49 computer-laptop avahi-daemon[2901]: New relevant interface wlan0.IPv4 for mDNS.
Apr 27 08:43:49 computer-laptop avahi-daemon[2901]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Apr 27 08:43:49 computer-laptop dhclient: bound to 192.168.1.101 -- renewal in 323153 seconds.
```

---

### Post by yoasif on 2009-04-28
you may want to do these steps and file a bug report to linux-source.

[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)
[https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

---

### Post by akarun on 2009-06-24
Hi, even I have a y530 and I have similar problems. 
meatlover: You have got more information on board. Did you file a bug report? Do update this thread if you hit something.

thanks,
Arun

---

### Post by michaelzap on 2009-06-27
Same problem here with a fresh installation of 64-bit Jaunty on a Y530 with an Intel graphics chip, so the problem probably isn't related to nVidia.

---

### Post by nutznboltz on 2010-10-11
Can you please test and report if this works?

memory_corruption_check_size=128K

in the boot options.

The default is

memory_corruption_check_size=64K

but it seems that's not enough for some systems.

Thanks

---

### Post by akarun on 2010-11-10
nutznboltz: I didn't test your previous update. However this fixed the issue for me on lenovo y530.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587457/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/587457/comments/6)

---

