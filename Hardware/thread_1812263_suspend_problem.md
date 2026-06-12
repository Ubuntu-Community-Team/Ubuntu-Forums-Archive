---
title: "suspend problem"
date: 2011-07-26
forum: Hardware
---

### Post by skief on 2011-07-26
Hi,

I'm running Ubuntu 10.04 on a Gateway EC5809u laptop. Every time I try to come out of suspend, my computer shuts down. This is very annoying. I suppose there must be something somewhere executing a command to shut my computer down. Does anyone know where this might be?

Thanks.

---

### Post by skief on 2011-07-26
Does anyone know anything about /etc/default/acpi-support, and whether this could be used to solve this problem?

My laptop goes into suspend okay.

But then opening the lid fails to wake it. Pressing the power button or any key on the keyboard makes it appear to start waking, but then it simply shuts off.

Please help!

---

### Post by skief on 2011-08-06
Hi again, I bring more data for keen power systems problem solvers! <nudge, nudge>....  :)

Okay, so my system uses the pm-suspend script (/usr/sbin/pm-suspend) to suspend.

The computer suspends just fine, and when you go into /var/log/pm-suspend.log, you see that every expected log entry is there, right up to the 'performing suspend' line, after it has run all the sleep hooks from /usr/lib/pm-utils/sleep.d.

But on resume -- doesn't seem to matter if I press the (soft) power button or any key on the keyboard to wake it -- then /var/log/pm-suspend.log NEVER EVEN MAKES IT TO THE 'Awake.' LINE!

Why would this be?
```

```
'Awake', I note, is supposed to be logged by the VERY NEXT LINE in /usr/sbin/pm-suspend, right after the sleep, so it seems that this process is not even resuming at all!

Here is the relevant bit of the pm-suspend script:
```

# run the sleep hooks
log "$(date): Running hooks for $ACTION."
if run_hooks sleep "$ACTION $METHOD"; then
        # Sleep only if we know how and if a hook did not inhibit us.
	log "$(date): performing $METHOD"
	sync
	"do_$METHOD" || r=128
	log "$(date): Awake."
else
	log "$(date): Inhibit found, will not perform $METHOD"
fi
log "$(date): Running hooks for $REVERSE"
# run the sleep hooks in reverse with the wakeup action
if run_hooks sleep "$REVERSE $METHOD" reverse; then
        log "$(date): Finished."
else 
        exit $((r+1))
fi
exit $r

```

And here is a typical entry in my pm-suspend.log:
```

Initial commandline parameters: 
Thu Aug  4 11:57:27 PDT 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux skubuntwo 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
usb_storage            50377  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279008  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11104  0 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
arc4                    1473  2 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
ip6table_filter         1712  1 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ip6_tables             19428  1 ip6table_filter
snd_seq_dummy           1782  0 
nf_nat_irc              1577  0 
nf_conntrack_irc        4429  1 nf_nat_irc
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
nf_nat_ftp              2513  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_rawmidi            23420  1 snd_seq_midi
nf_conntrack_ipv4      12742  9 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1841  1 
iwlagn                123060  0 
ip_tables              18201  1 iptable_filter
iwlcore               125250  1 iwlagn
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
mac80211              238896  2 iwlagn,iwlcore
led_class               3764  1 iwlcore
uvcvideo               62851  0 
i915                  324711  3 
drm_kms_helper         30742  1 i915
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
cfg80211              148341  3 iwlagn,iwlcore,mac80211
psmouse                65040  0 
serio_raw               4918  0 
snd                    71283  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
atl1c                  32975  0 
drm                   198886  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29319  2 i915
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
             total       used       free     shared    buffers     cached
Mem:       3961156     731316    3229840          0      63668     290484
-/+ buffers/cache:     377164    3583992
Swap:      5707768          0    5707768
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Thu Aug  4 11:57:28 PDT 2011: performing suspend

```

So anyway, after I wake the computer, it sits there for a few seconds, I hear some disk noises, the screen's backlight does not come on at all, the thing shuts off.

Ideas?

---

### Post by skief on 2011-08-06
Hrm... well, maybe if the hard drive hasn't been woken yet, then pm-suspend is writing out its 'Awake.' line, but this can't be committed to hard disk before the computer shuts off, so I never get to see it in the log file?

I don't know. Any thoughts?

---

### Post by Toz on 2011-08-14
Can you try another suspend and after you restart to recover, post back only the relevant sections of /var/log/syslog (from time of suspend start onwards). Lets have a look in there first. And maybe post back the relevant entry from pm-suspend.log again.

You said in your other post that this problem just started recently. Do you recall when and what might have changed to the laptop? When it was working before, were you able to just open the lid to resume?

---

### Post by Toz on 2011-08-14
Just doing some research.

Can you try the following kernel parameters:
- acpi_sleep=nonvs
- i8042.reset=1

---

### Post by skief on 2011-08-15
Toz: Thanks for your reply, and your valuable time! :biggrin:

Here's my /var/log/syslog. I did pm-suspend at 20:54:04, and tried to wake at 20:54:25. The laptop did its usual thing: check the DVD drive a bit, then promptly shut off. I restarted at 20:55:00.

```

Aug 14 20:54:04 skubuntwo anacron[2037]: Anacron 2.3 started on 2011-08-14
Aug 14 20:54:04 skubuntwo anacron[2037]: Normal exit (0 jobs run)
Aug 14 20:54:04 skubuntwo kernel: [  711.666724] CPU0 attaching NULL sched-domain.
Aug 14 20:54:04 skubuntwo kernel: [  711.666736] CPU1 attaching NULL sched-domain.
Aug 14 20:54:04 skubuntwo kernel: [  711.721693] CPU0 attaching sched-domain:
Aug 14 20:54:04 skubuntwo kernel: [  711.721703]  domain 0: span 0-1 level MC
Aug 14 20:54:04 skubuntwo kernel: [  711.721709]   groups: 0 1
Aug 14 20:54:04 skubuntwo kernel: [  711.721724] CPU1 attaching sched-domain:
Aug 14 20:54:04 skubuntwo kernel: [  711.721729]  domain 0: span 0-1 level MC
Aug 14 20:54:04 skubuntwo kernel: [  711.721735]   groups: 1 0
Aug 14 20:55:35 skubuntwo kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug 14 20:55:35 skubuntwo rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="771" x-info="http://www.rsyslog.com"] (re)start
Aug 14 20:55:35 skubuntwo rsyslogd: rsyslogd's groupid changed to 103
Aug 14 20:55:35 skubuntwo rsyslogd: rsyslogd's userid changed to 101
Aug 14 20:55:35 skubuntwo rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Linux version 2.6.32-33-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011 (Ubuntu 2.6.32-33.71-generic 2.6.32.41+drm33.18)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=4333d8a0-3d0a-4922-b9b0-1afae1ba0b43 ro quiet splash
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] KERNEL supported cpus:
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   Intel GenuineIntel
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   AMD AuthenticAMD
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   Centaur CentaurHauls
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000b9e53000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000b9e53000 - 00000000b9ebf000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000b9ebf000 - 00000000b9f71000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000b9f71000 - 00000000b9fbf000 (ACPI NVS)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000b9fbf000 - 00000000b9fde000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000b9fde000 - 00000000b9ff7000 (ACPI data)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000b9ff7000 - 00000000ba000000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000ba000000 - 00000000c0000000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] DMI 2.6 present.
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] MTRR default type: uncachable
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] MTRR fixed ranges enabled:
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   00000-9FFFF write-back
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   A0000-BFFFF uncachable
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   C0000-DFFFF write-protect
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   E0000-EFFFF uncachable
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   F0000-FFFFF write-protect
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] MTRR variable ranges enabled:
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   4 base 0BA000000 mask FFE000000 uncachable
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   5 base 100000000 mask FC0000000 write-back
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   6 disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   7 disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] last_pfn = 0xba000 max_arch_pfn = 0x400000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Scanning 1 areas for low memory corruption
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] modified physical RAM map:
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 0000000000100000 - 00000000b9e53000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000b9e53000 - 00000000b9ebf000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000b9ebf000 - 00000000b9f71000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000b9f71000 - 00000000b9fbf000 (ACPI NVS)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000b9fbf000 - 00000000b9fde000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000b9fde000 - 00000000b9ff7000 (ACPI data)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000b9ff7000 - 00000000ba000000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000ba000000 - 00000000c0000000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] initial memory mapped : 0 - 20000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000ba000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] NX (Execute Disable) protection: active
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  0000000000 - 00ba000000 page 2M
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] kernel direct mapping tables up to ba000000 @ 8000-c000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] NX (Execute Disable) protection: active
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  0100000000 - 0140000000 page 2M
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] kernel direct mapping tables up to 140000000 @ a000-10000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] RAMDISK: 377f3000 - 37fef25b
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 ACRSYS)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: XSDT 00000000b9ff6120 00084 (v01 ACRSYS ACRPRDCT 00000001      01000013)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: FACP 00000000b9ff4000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: DSDT 00000000b9fe6000 09BCA (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: FACS 00000000b9f7e000 00040
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: DMAR 00000000b9ff5000 000A0 (v01               ? 00000001      00000000)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: HPET 00000000b9ff3000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: APIC 00000000b9ff2000 0006C (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: MCFG 00000000b9ff1000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: ASF! 00000000b9ff0000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: SLIC 00000000b9fe5000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: BOOT 00000000b9fe4000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: SSDT 00000000b9fe3000 000C3 (v01 ACRSYS ACRPRDCT 00001000 1025 20051117)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: SSDT 00000000b9fe0000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: SSDT 00000000b9fdf000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20051117)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: SSDT 00000000b9fde000 0020F (v01  PmRef    ApTst 00003000 INTL 20051117)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] No NUMA configuration found
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Faking a node at 0000000000000000-0000000140000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   bootmap [0000000000010000 -  0000000000037fff] pages 28
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   #2 [0001000000 - 0001a30a64]    TEXT DATA BSS ==> [0001000000 - 0001a30a64]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   #3 [00377f3000 - 0037fef25b]          RAMDISK ==> [00377f3000 - 0037fef25b]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   #5 [0001a31000 - 0001a31314]              BRK ==> [0001a31000 - 0001a31314]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Zone PFN ranges:
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   Normal   0x00100000 -> 0x00140000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Movable zone start PFN for each node
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] early_node_map[7] active PFN ranges
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]     0: 0x00000006 -> 0x0000009e
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]     0: 0x00000100 -> 0x000b9e53
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]     0: 0x000b9ebf -> 0x000b9f71
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]     0: 0x000b9fbf -> 0x000b9fde
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]     0: 0x000b9ff7 -> 0x000ba000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] On node 0 totalpages: 1023686
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   DMA zone: 104 pages reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   DMA zone: 3833 pages, LIFO batch:0
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   DMA32 zone: 743269 pages, LIFO batch:31
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   Normal zone: 3584 pages used for memmap
Aug 14 20:55:35 skubuntwo kernel: [    0.000000]   Normal zone: 258560 pages, LIFO batch:31
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] nr_irqs_gsi: 24
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000b9e53000 - 00000000b9ebf000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000b9f71000 - 00000000b9fbf000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000b9fde000 - 00000000b9ff7000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000ba000000 - 00000000c0000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f8000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91864 r8192 d22824 u524288
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] pcpu-alloc: s91864 r8192 d22824 u524288 alloc=1*2097152
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1005662
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Policy zone: Normal
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=4333d8a0-3d0a-4922-b9b0-1afae1ba0b43 ro quiet splash
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Initializing CPU#0
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Checking aperture...
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] No AGP bridge found
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Memory: 3952088k/5242880k available (5412k kernel code, 1148136k absent, 142656k reserved, 2981k data, 888k init)
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Hierarchical RCU implementation.
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Console: colour VGA+ 80x25
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] console [tty0] enabled
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] hpet clockevent registered
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Fast TSC calibration using PIT
Aug 14 20:55:35 skubuntwo kernel: [    0.000000] Detected 1296.944 MHz processor.
Aug 14 20:55:35 skubuntwo kernel: [    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 2593.88 BogoMIPS (lpj=12969440)
Aug 14 20:55:35 skubuntwo kernel: [    0.010044] Security Framework initialized
Aug 14 20:55:35 skubuntwo kernel: [    0.010073] AppArmor: AppArmor initialized
Aug 14 20:55:35 skubuntwo kernel: [    0.010671] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Aug 14 20:55:35 skubuntwo kernel: [    0.013366] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Aug 14 20:55:35 skubuntwo kernel: [    0.014624] Mount-cache hash table entries: 256
Aug 14 20:55:35 skubuntwo kernel: [    0.014830] Initializing cgroup subsys ns
Aug 14 20:55:35 skubuntwo kernel: [    0.014837] Initializing cgroup subsys cpuacct
Aug 14 20:55:35 skubuntwo kernel: [    0.014843] Initializing cgroup subsys memory
Aug 14 20:55:35 skubuntwo kernel: [    0.014853] Initializing cgroup subsys devices
Aug 14 20:55:35 skubuntwo kernel: [    0.014857] Initializing cgroup subsys freezer
Aug 14 20:55:35 skubuntwo kernel: [    0.014860] Initializing cgroup subsys net_cls
Aug 14 20:55:35 skubuntwo kernel: [    0.014893] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 14 20:55:35 skubuntwo kernel: [    0.014897] CPU: L2 cache: 3072K
Aug 14 20:55:35 skubuntwo kernel: [    0.014901] CPU 0/0x0 -> Node 0
Aug 14 20:55:35 skubuntwo kernel: [    0.014905] CPU: Physical Processor ID: 0
Aug 14 20:55:35 skubuntwo kernel: [    0.014907] CPU: Processor Core ID: 0
Aug 14 20:55:35 skubuntwo kernel: [    0.014912] mce: CPU supports 6 MCE banks
Aug 14 20:55:35 skubuntwo kernel: [    0.014923] CPU0: Thermal monitoring handled by SMI
Aug 14 20:55:35 skubuntwo kernel: [    0.014929] using mwait in idle threads.
Aug 14 20:55:35 skubuntwo kernel: [    0.014931] Performance Events: Core2 events, Intel PMU driver.
Aug 14 20:55:35 skubuntwo kernel: [    0.014940] ... version:                2
Aug 14 20:55:35 skubuntwo kernel: [    0.014942] ... bit width:              40
Aug 14 20:55:35 skubuntwo kernel: [    0.014944] ... generic registers:      2
Aug 14 20:55:35 skubuntwo kernel: [    0.014947] ... value mask:             000000ffffffffff
Aug 14 20:55:35 skubuntwo kernel: [    0.014949] ... max period:             000000007fffffff
Aug 14 20:55:35 skubuntwo kernel: [    0.014952] ... fixed-purpose events:   3
Aug 14 20:55:35 skubuntwo kernel: [    0.014954] ... event mask:             0000000700000003
Aug 14 20:55:35 skubuntwo kernel: [    0.022642] ACPI: Core revision 20090903
Aug 14 20:55:35 skubuntwo kernel: [    0.050016] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug 14 20:55:35 skubuntwo kernel: [    0.050024] ftrace: allocating 22478 entries in 89 pages
Aug 14 20:55:35 skubuntwo kernel: [    0.060076] Setting APIC routing to flat
Aug 14 20:55:35 skubuntwo kernel: [    0.060443] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 14 20:55:35 skubuntwo kernel: [    0.163123] CPU0: Genuine Intel(R) CPU           U7300  @ 1.30GHz stepping 0a
Aug 14 20:55:35 skubuntwo kernel: [    0.170000] Booting processor 1 APIC 0x1 ip 0x6000
Aug 14 20:55:35 skubuntwo kernel: [    0.020000] Initializing CPU#1
Aug 14 20:55:35 skubuntwo kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 14 20:55:35 skubuntwo kernel: [    0.020000] CPU: L2 cache: 3072K
Aug 14 20:55:35 skubuntwo kernel: [    0.020000] CPU 1/0x1 -> Node 0
Aug 14 20:55:35 skubuntwo kernel: [    0.020000] CPU: Physical Processor ID: 0
Aug 14 20:55:35 skubuntwo kernel: [    0.020000] CPU: Processor Core ID: 1
Aug 14 20:55:35 skubuntwo kernel: [    0.020000] CPU1: Thermal monitoring handled by SMI
Aug 14 20:55:35 skubuntwo kernel: [    0.320109] CPU1: Genuine Intel(R) CPU           U7300  @ 1.30GHz stepping 0a
Aug 14 20:55:35 skubuntwo kernel: [    0.320120] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 14 20:55:35 skubuntwo kernel: [    0.330026] Brought up 2 CPUs
Aug 14 20:55:35 skubuntwo kernel: [    0.330029] Total of 2 processors activated (5187.69 BogoMIPS).
Aug 14 20:55:35 skubuntwo kernel: [    0.331847] CPU0 attaching sched-domain:
Aug 14 20:55:35 skubuntwo kernel: [    0.331852]  domain 0: span 0-1 level MC
Aug 14 20:55:35 skubuntwo kernel: [    0.331856]   groups: 0 1
Aug 14 20:55:35 skubuntwo kernel: [    0.331864] CPU1 attaching sched-domain:
Aug 14 20:55:35 skubuntwo kernel: [    0.331867]  domain 0: span 0-1 level MC
Aug 14 20:55:35 skubuntwo kernel: [    0.331871]   groups: 1 0
Aug 14 20:55:35 skubuntwo kernel: [    0.331962] devtmpfs: initialized
Aug 14 20:55:35 skubuntwo kernel: [    0.331962] regulator: core version 0.5
Aug 14 20:55:35 skubuntwo kernel: [    0.331962] Time: 20:55:11  Date: 08/14/11
Aug 14 20:55:35 skubuntwo kernel: [    0.331962] NET: Registered protocol family 16
Aug 14 20:55:35 skubuntwo kernel: [    0.331962] Trying to unpack rootfs image as initramfs...
Aug 14 20:55:35 skubuntwo kernel: [    0.331962] ACPI: bus type pci registered
Aug 14 20:55:35 skubuntwo kernel: [    0.331962] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Aug 14 20:55:35 skubuntwo kernel: [    0.331962] PCI: MCFG area at f8000000 reserved in E820
Aug 14 20:55:35 skubuntwo kernel: [    0.334032] PCI: Using MMCONFIG at f8000000 - fbffffff
Aug 14 20:55:35 skubuntwo kernel: [    0.334035] PCI: Using configuration type 1 for base access
Aug 14 20:55:35 skubuntwo kernel: [    0.340100] bio: create slab <bio-0> at 0
Aug 14 20:55:35 skubuntwo kernel: [    0.342394] ACPI: EC: Look up EC in DSDT
Aug 14 20:55:35 skubuntwo kernel: [    0.346030] ACPI: Executed 1 blocks of module-level executable AML code
Aug 14 20:55:35 skubuntwo kernel: [    0.350404] ACPI: BIOS _OSI(Linux) query ignored
Aug 14 20:55:35 skubuntwo kernel: [    0.352067] ACPI: Interpreter enabled
Aug 14 20:55:35 skubuntwo kernel: [    0.352071] ACPI: (supports S0 S3 S4 S5)
Aug 14 20:55:35 skubuntwo kernel: [    0.352119] ACPI: Using IOAPIC for interrupt routing
Aug 14 20:55:35 skubuntwo kernel: [    0.365406] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
Aug 14 20:55:35 skubuntwo kernel: [    0.366165] ACPI: No dock devices found.
Aug 14 20:55:35 skubuntwo kernel: [    0.366961] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 14 20:55:35 skubuntwo kernel: [    0.367100] pci 0000:00:02.0: reg 10 64bit mmio: [0xe0000000-0xe03fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.367111] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.367118] pci 0000:00:02.0: reg 20 io port: [0x3110-0x3117]
Aug 14 20:55:35 skubuntwo kernel: [    0.367175] pci 0000:00:02.1: reg 10 64bit mmio: [0xe2400000-0xe24fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.367337] pci 0000:00:1a.0: reg 20 io port: [0x30e0-0x30ff]
Aug 14 20:55:35 skubuntwo kernel: [    0.367467] pci 0000:00:1a.1: reg 20 io port: [0x30c0-0x30df]
Aug 14 20:55:35 skubuntwo kernel: [    0.367576] pci 0000:00:1a.7: reg 10 32bit mmio: [0xe4505c00-0xe4505fff]
Aug 14 20:55:35 skubuntwo kernel: [    0.367657] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Aug 14 20:55:35 skubuntwo kernel: [    0.367664] pci 0000:00:1a.7: PME# disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.367729] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe4500000-0xe4503fff]
Aug 14 20:55:35 skubuntwo kernel: [    0.367800] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug 14 20:55:35 skubuntwo kernel: [    0.367806] pci 0000:00:1b.0: PME# disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.367912] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug 14 20:55:35 skubuntwo kernel: [    0.367918] pci 0000:00:1c.0: PME# disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.368030] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Aug 14 20:55:35 skubuntwo kernel: [    0.368036] pci 0000:00:1c.2: PME# disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.368145] pci 0000:00:1d.0: reg 20 io port: [0x30a0-0x30bf]
Aug 14 20:55:35 skubuntwo kernel: [    0.368276] pci 0000:00:1d.1: reg 20 io port: [0x3080-0x309f]
Aug 14 20:55:35 skubuntwo kernel: [    0.368403] pci 0000:00:1d.2: reg 20 io port: [0x3060-0x307f]
Aug 14 20:55:35 skubuntwo kernel: [    0.368538] pci 0000:00:1d.3: reg 20 io port: [0x3040-0x305f]
Aug 14 20:55:35 skubuntwo kernel: [    0.368657] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe4505800-0xe4505bff]
Aug 14 20:55:35 skubuntwo kernel: [    0.368736] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug 14 20:55:35 skubuntwo kernel: [    0.368743] pci 0000:00:1d.7: PME# disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.369016] pci 0000:00:1f.2: reg 10 io port: [0x3108-0x310f]
Aug 14 20:55:35 skubuntwo kernel: [    0.369025] pci 0000:00:1f.2: reg 14 io port: [0x311c-0x311f]
Aug 14 20:55:35 skubuntwo kernel: [    0.369034] pci 0000:00:1f.2: reg 18 io port: [0x3100-0x3107]
Aug 14 20:55:35 skubuntwo kernel: [    0.369044] pci 0000:00:1f.2: reg 1c io port: [0x3118-0x311b]
Aug 14 20:55:35 skubuntwo kernel: [    0.369053] pci 0000:00:1f.2: reg 20 io port: [0x3020-0x303f]
Aug 14 20:55:35 skubuntwo kernel: [    0.369063] pci 0000:00:1f.2: reg 24 32bit mmio: [0xe4505000-0xe45057ff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369115] pci 0000:00:1f.2: PME# supported from D3hot
Aug 14 20:55:35 skubuntwo kernel: [    0.369121] pci 0000:00:1f.2: PME# disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.369166] pci 0000:00:1f.3: reg 10 64bit mmio: [0xe4506000-0xe45060ff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369188] pci 0000:00:1f.3: reg 20 io port: [0x3000-0x301f]
Aug 14 20:55:35 skubuntwo kernel: [    0.369263] pci 0000:00:1f.6: reg 10 64bit mmio: [0xe4504000-0xe4504fff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369421] pci 0000:01:00.0: reg 10 64bit mmio: [0xe3500000-0xe3501fff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369538] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
Aug 14 20:55:35 skubuntwo kernel: [    0.369546] pci 0000:01:00.0: PME# disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.369634] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369640] pci 0000:00:1c.0: bridge 32bit mmio: [0xe3500000-0xe44fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369650] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xe0400000-0xe13fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369727] pci 0000:02:00.0: reg 10 64bit mmio: [0xe2500000-0xe253ffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369739] pci 0000:02:00.0: reg 18 io port: [0x1000-0x107f]
Aug 14 20:55:35 skubuntwo kernel: [    0.369826] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 14 20:55:35 skubuntwo kernel: [    0.369834] pci 0000:02:00.0: PME# disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.369916] pci 0000:00:1c.2: bridge io port: [0x1000-0x1fff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369922] pci 0000:00:1c.2: bridge 32bit mmio: [0xe2500000-0xe34fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.369932] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xe1400000-0xe23fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.370019] pci 0000:00:1e.0: transparent bridge
Aug 14 20:55:35 skubuntwo kernel: [    0.370064] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 14 20:55:35 skubuntwo kernel: [    0.370588] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Aug 14 20:55:35 skubuntwo kernel: [    0.370765] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
Aug 14 20:55:35 skubuntwo kernel: [    0.399526] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Aug 14 20:55:35 skubuntwo kernel: [    0.399761] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
Aug 14 20:55:35 skubuntwo kernel: [    0.399990] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Aug 14 20:55:35 skubuntwo kernel: [    0.400234] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Aug 14 20:55:35 skubuntwo kernel: [    0.400462] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Aug 14 20:55:35 skubuntwo kernel: [    0.400691] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
Aug 14 20:55:35 skubuntwo kernel: [    0.400922] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
Aug 14 20:55:35 skubuntwo kernel: [    0.401149] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
Aug 14 20:55:35 skubuntwo kernel: [    0.401362] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Aug 14 20:55:35 skubuntwo kernel: [    0.401385] vgaarb: loaded
Aug 14 20:55:35 skubuntwo kernel: [    0.401551] SCSI subsystem initialized
Aug 14 20:55:35 skubuntwo kernel: [    0.401675] libata version 3.00 loaded.
Aug 14 20:55:35 skubuntwo kernel: [    0.401784] usbcore: registered new interface driver usbfs
Aug 14 20:55:35 skubuntwo kernel: [    0.401807] usbcore: registered new interface driver hub
Aug 14 20:55:35 skubuntwo kernel: [    0.401847] usbcore: registered new device driver usb
Aug 14 20:55:35 skubuntwo kernel: [    0.402165] ACPI: WMI: Mapper loaded
Aug 14 20:55:35 skubuntwo kernel: [    0.402168] PCI: Using ACPI for IRQ routing
Aug 14 20:55:35 skubuntwo kernel: [    0.402420] NetLabel: Initializing
Aug 14 20:55:35 skubuntwo kernel: [    0.402423] NetLabel:  domain hash size = 128
Aug 14 20:55:35 skubuntwo kernel: [    0.402426] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 14 20:55:35 skubuntwo kernel: [    0.402452] NetLabel:  unlabeled traffic allowed by default
Aug 14 20:55:35 skubuntwo kernel: [    0.402499] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Aug 14 20:55:35 skubuntwo kernel: [    0.402507] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 14 20:55:35 skubuntwo kernel: [    0.402515] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Aug 14 20:55:35 skubuntwo kernel: [    0.410178] Switching to clocksource tsc
Aug 14 20:55:35 skubuntwo kernel: [    0.412668] AppArmor: AppArmor Filesystem Enabled
Aug 14 20:55:35 skubuntwo kernel: [    0.412687] pnp: PnP ACPI init
Aug 14 20:55:35 skubuntwo kernel: [    0.412706] ACPI: bus type pnp registered
Aug 14 20:55:35 skubuntwo kernel: [    0.414538] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.2 BAR 13 (0x1000-0x1fff), disabling
Aug 14 20:55:35 skubuntwo kernel: [    0.422794] pnp: PnP ACPI: found 9 devices
Aug 14 20:55:35 skubuntwo kernel: [    0.422797] ACPI: ACPI bus type pnp unregistered
Aug 14 20:55:35 skubuntwo kernel: [    0.422815] system 00:01: ioport range 0x600-0x60f has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422820] system 00:01: ioport range 0x610-0x610 has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422824] system 00:01: ioport range 0x800-0x80f has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422828] system 00:01: ioport range 0x810-0x817 has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422832] system 00:01: ioport range 0x820-0x823 has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422837] system 00:01: ioport range 0x400-0x47f has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422841] system 00:01: ioport range 0x500-0x53f has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422846] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422851] system 00:01: iomem range 0xfeb00000-0xfeb00fff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422856] system 00:01: iomem range 0xfeb01000-0xfeb01fff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422860] system 00:01: iomem range 0xfeb02000-0xfeb02fff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422869] system 00:01: iomem range 0xfeb03000-0xfeb03fff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422874] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422878] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422883] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422887] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422892] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422896] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422901] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422905] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.422910] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
Aug 14 20:55:35 skubuntwo kernel: [    0.427751] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Aug 14 20:55:35 skubuntwo kernel: [    0.427756] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
Aug 14 20:55:35 skubuntwo kernel: [    0.427764] pci 0000:00:1c.0:   MEM window: 0xe3500000-0xe44fffff
Aug 14 20:55:35 skubuntwo kernel: [    0.427771] pci 0000:00:1c.0:   PREFETCH window: 0x000000e0400000-0x000000e13fffff
Aug 14 20:55:35 skubuntwo kernel: [    0.427781] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
Aug 14 20:55:35 skubuntwo kernel: [    0.427786] pci 0000:00:1c.2:   IO window: 0x1000-0x1fff
Aug 14 20:55:35 skubuntwo kernel: [    0.427793] pci 0000:00:1c.2:   MEM window: 0xe2500000-0xe34fffff
Aug 14 20:55:35 skubuntwo kernel: [    0.427799] pci 0000:00:1c.2:   PREFETCH window: 0x000000e1400000-0x000000e23fffff
Aug 14 20:55:35 skubuntwo kernel: [    0.427809] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Aug 14 20:55:35 skubuntwo kernel: [    0.427812] pci 0000:00:1e.0:   IO window: disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.427819] pci 0000:00:1e.0:   MEM window: disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.427825] pci 0000:00:1e.0:   PREFETCH window: disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.427847]   alloc irq_desc for 17 on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.427850]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.427857] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 14 20:55:35 skubuntwo kernel: [    0.427865] pci 0000:00:1c.0: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.427877]   alloc irq_desc for 18 on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.427879]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.427884] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 14 20:55:35 skubuntwo kernel: [    0.427890] pci 0000:00:1c.2: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.427899] pci 0000:00:1e.0: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.427906] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427909] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427913] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427917] pci_bus 0000:01: resource 1 mem: [0xe3500000-0xe44fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427921] pci_bus 0000:01: resource 2 pref mem [0xe0400000-0xe13fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427924] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427928] pci_bus 0000:02: resource 1 mem: [0xe2500000-0xe34fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427931] pci_bus 0000:02: resource 2 pref mem [0xe1400000-0xe23fffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427935] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427939] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
Aug 14 20:55:35 skubuntwo kernel: [    0.427986] NET: Registered protocol family 2
Aug 14 20:55:35 skubuntwo kernel: [    0.428250] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 14 20:55:35 skubuntwo kernel: [    0.430087] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Aug 14 20:55:35 skubuntwo kernel: [    0.435207] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Aug 14 20:55:35 skubuntwo kernel: [    0.435860] TCP: Hash tables configured (established 524288 bind 65536)
Aug 14 20:55:35 skubuntwo kernel: [    0.435863] TCP reno registered
Aug 14 20:55:35 skubuntwo kernel: [    0.436027] NET: Registered protocol family 1
Aug 14 20:55:35 skubuntwo kernel: [    0.436059] pci 0000:00:02.0: Boot video device
Aug 14 20:55:35 skubuntwo kernel: [    0.479499] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
Aug 14 20:55:35 skubuntwo kernel: [    0.479503] Simple Boot Flag at 0x44 set to 0x1
Aug 14 20:55:35 skubuntwo kernel: [    0.479758] Scanning for low memory corruption every 60 seconds
Aug 14 20:55:35 skubuntwo kernel: [    0.479963] audit: initializing netlink socket (disabled)
Aug 14 20:55:35 skubuntwo kernel: [    0.479978] type=2000 audit(1313355310.479:1): initialized
Aug 14 20:55:35 skubuntwo kernel: [    0.495459] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Aug 14 20:55:35 skubuntwo kernel: [    0.497626] VFS: Disk quotas dquot_6.5.2
Aug 14 20:55:35 skubuntwo kernel: [    0.497711] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Aug 14 20:55:35 skubuntwo kernel: [    0.498597] fuse init (API version 7.13)
Aug 14 20:55:35 skubuntwo kernel: [    0.498720] msgmni has been set to 7718
Aug 14 20:55:35 skubuntwo kernel: [    0.499010] alg: No test for stdrng (krng)
Aug 14 20:55:35 skubuntwo kernel: [    0.499086] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 14 20:55:35 skubuntwo kernel: [    0.499090] io scheduler noop registered
Aug 14 20:55:35 skubuntwo kernel: [    0.499093] io scheduler anticipatory registered
Aug 14 20:55:35 skubuntwo kernel: [    0.499096] io scheduler deadline registered
Aug 14 20:55:35 skubuntwo kernel: [    0.499162] io scheduler cfq registered (default)
Aug 14 20:55:35 skubuntwo kernel: [    0.499379]   alloc irq_desc for 24 on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.499382]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.499415] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Aug 14 20:55:35 skubuntwo kernel: [    0.499429] pcieport 0000:00:1c.0: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.499624]   alloc irq_desc for 25 on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.499627]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.499639] pcieport 0000:00:1c.2: irq 25 for MSI/MSI-X
Aug 14 20:55:35 skubuntwo kernel: [    0.499652] pcieport 0000:00:1c.2: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.499781] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 14 20:55:35 skubuntwo kernel: [    0.499969] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 14 20:55:35 skubuntwo kernel: [    0.500389] ACPI: AC Adapter [ADP1] (on-line)
Aug 14 20:55:35 skubuntwo kernel: [    0.500511] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Aug 14 20:55:35 skubuntwo kernel: [    0.500516] ACPI: Power Button [PWRB]
Aug 14 20:55:35 skubuntwo kernel: [    0.500580] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Aug 14 20:55:35 skubuntwo kernel: [    0.599570] ACPI: Lid Switch [LID0]
Aug 14 20:55:35 skubuntwo kernel: [    0.599668] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Aug 14 20:55:35 skubuntwo kernel: [    0.599673] ACPI: Sleep Button [SLPB]
Aug 14 20:55:35 skubuntwo kernel: [    0.599796] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Aug 14 20:55:35 skubuntwo kernel: [    0.599800] ACPI: Power Button [PWRF]
Aug 14 20:55:35 skubuntwo kernel: [    0.601191] ACPI: SSDT 00000000b9e6ec98 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Aug 14 20:55:35 skubuntwo kernel: [    0.602123] ACPI: SSDT 00000000b9e6c598 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Aug 14 20:55:35 skubuntwo kernel: [    0.605714] Monitor-Mwait will be used to enter C-1 state
Aug 14 20:55:35 skubuntwo kernel: [    0.605764] Monitor-Mwait will be used to enter C-2 state
Aug 14 20:55:35 skubuntwo kernel: [    0.605800] Monitor-Mwait will be used to enter C-3 state
Aug 14 20:55:35 skubuntwo kernel: [    0.605808] Marking TSC unstable due to TSC halts in idle
Aug 14 20:55:35 skubuntwo kernel: [    0.605891] processor LNXCPU:00: registered as cooling_device0
Aug 14 20:55:35 skubuntwo kernel: [    0.606670] ACPI: SSDT 00000000b9e6de18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
Aug 14 20:55:35 skubuntwo kernel: [    0.607485] ACPI: SSDT 00000000b9e6ef18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
Aug 14 20:55:35 skubuntwo kernel: [    0.608754] Switching to clocksource hpet
Aug 14 20:55:35 skubuntwo kernel: [    0.621520] processor LNXCPU:01: registered as cooling_device1
Aug 14 20:55:35 skubuntwo kernel: [    0.627776] thermal LNXTHERM:01: registered as thermal_zone0
Aug 14 20:55:35 skubuntwo kernel: [    0.627787] ACPI: Thermal Zone [TZ00] (27 C)
Aug 14 20:55:35 skubuntwo kernel: [    0.630086] Linux agpgart interface v0.103
Aug 14 20:55:35 skubuntwo kernel: [    0.630136] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug 14 20:55:35 skubuntwo kernel: [    0.632034] brd: module loaded
Aug 14 20:55:35 skubuntwo kernel: [    0.632745] loop: module loaded
Aug 14 20:55:35 skubuntwo kernel: [    0.632862] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Aug 14 20:55:35 skubuntwo kernel: [    0.633441] Fixed MDIO Bus: probed
Aug 14 20:55:35 skubuntwo kernel: [    0.633487] PPP generic driver version 2.4.2
Aug 14 20:55:35 skubuntwo kernel: [    0.633533] tun: Universal TUN/TAP device driver, 1.6
Aug 14 20:55:35 skubuntwo kernel: [    0.633536] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 14 20:55:35 skubuntwo kernel: [    0.633654] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 14 20:55:35 skubuntwo kernel: [    0.633690]   alloc irq_desc for 19 on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.633694]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.633702] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug 14 20:55:35 skubuntwo kernel: [    0.633726] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.633731] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Aug 14 20:55:35 skubuntwo kernel: [    0.633776] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Aug 14 20:55:35 skubuntwo kernel: [    0.633828] ehci_hcd 0000:00:1a.7: debug port 1
Aug 14 20:55:35 skubuntwo kernel: [    0.637717] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Aug 14 20:55:35 skubuntwo kernel: [    0.637737] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xe4505c00
Aug 14 20:55:35 skubuntwo kernel: [    0.644524] Freeing initrd memory: 8176k freed
Aug 14 20:55:35 skubuntwo kernel: [    0.670067] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Aug 14 20:55:35 skubuntwo kernel: [    0.670278] usb usb1: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    0.670328] hub 1-0:1.0: USB hub found
Aug 14 20:55:35 skubuntwo kernel: [    0.670341] hub 1-0:1.0: 4 ports detected
Aug 14 20:55:35 skubuntwo kernel: [    0.670429]   alloc irq_desc for 23 on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.670433]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.670443] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 14 20:55:35 skubuntwo kernel: [    0.670483] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.670491] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 14 20:55:35 skubuntwo kernel: [    0.670597] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Aug 14 20:55:35 skubuntwo kernel: [    0.670647] ehci_hcd 0000:00:1d.7: debug port 1
Aug 14 20:55:35 skubuntwo kernel: [    0.672346] ACPI: Battery Slot [BAT0] (battery present)
Aug 14 20:55:35 skubuntwo kernel: [    0.674535] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Aug 14 20:55:35 skubuntwo kernel: [    0.674562] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe4505800
Aug 14 20:55:35 skubuntwo kernel: [    0.700018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug 14 20:55:35 skubuntwo kernel: [    0.700121] usb usb2: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    0.700163] hub 2-0:1.0: USB hub found
Aug 14 20:55:35 skubuntwo kernel: [    0.700173] hub 2-0:1.0: 8 ports detected
Aug 14 20:55:35 skubuntwo kernel: [    0.700260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 14 20:55:35 skubuntwo kernel: [    0.700285] uhci_hcd: USB Universal Host Controller Interface driver
Aug 14 20:55:35 skubuntwo kernel: [    0.700334]   alloc irq_desc for 16 on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.700337]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.700343] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 14 20:55:35 skubuntwo kernel: [    0.700355] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.700359] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Aug 14 20:55:35 skubuntwo kernel: [    0.700413] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Aug 14 20:55:35 skubuntwo kernel: [    0.700456] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000030e0
Aug 14 20:55:35 skubuntwo kernel: [    0.700582] usb usb3: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    0.700624] hub 3-0:1.0: USB hub found
Aug 14 20:55:35 skubuntwo kernel: [    0.700633] hub 3-0:1.0: 2 ports detected
Aug 14 20:55:35 skubuntwo kernel: [    0.700696]   alloc irq_desc for 21 on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.700699]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.700705] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Aug 14 20:55:35 skubuntwo kernel: [    0.700714] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.700719] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Aug 14 20:55:35 skubuntwo kernel: [    0.700764] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Aug 14 20:55:35 skubuntwo kernel: [    0.700805] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000030c0
Aug 14 20:55:35 skubuntwo kernel: [    0.700933] usb usb4: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    0.700973] hub 4-0:1.0: USB hub found
Aug 14 20:55:35 skubuntwo kernel: [    0.700982] hub 4-0:1.0: 2 ports detected
Aug 14 20:55:35 skubuntwo kernel: [    0.701052] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 14 20:55:35 skubuntwo kernel: [    0.701061] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.701066] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 14 20:55:35 skubuntwo kernel: [    0.701124] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Aug 14 20:55:35 skubuntwo kernel: [    0.701157] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000030a0
Aug 14 20:55:35 skubuntwo kernel: [    0.701282] usb usb5: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    0.701318] hub 5-0:1.0: USB hub found
Aug 14 20:55:35 skubuntwo kernel: [    0.701326] hub 5-0:1.0: 2 ports detected
Aug 14 20:55:35 skubuntwo kernel: [    0.701393] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 14 20:55:35 skubuntwo kernel: [    0.701402] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.701406] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 14 20:55:35 skubuntwo kernel: [    0.701461] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Aug 14 20:55:35 skubuntwo kernel: [    0.701494] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003080
Aug 14 20:55:35 skubuntwo kernel: [    0.701619] usb usb6: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    0.701655] hub 6-0:1.0: USB hub found
Aug 14 20:55:35 skubuntwo kernel: [    0.701664] hub 6-0:1.0: 2 ports detected
Aug 14 20:55:35 skubuntwo kernel: [    0.701728] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Aug 14 20:55:35 skubuntwo kernel: [    0.701737] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.701742] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 14 20:55:35 skubuntwo kernel: [    0.701788] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Aug 14 20:55:35 skubuntwo kernel: [    0.701825] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00003060
Aug 14 20:55:35 skubuntwo kernel: [    0.701957] usb usb7: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    0.701994] hub 7-0:1.0: USB hub found
Aug 14 20:55:35 skubuntwo kernel: [    0.702003] hub 7-0:1.0: 2 ports detected
Aug 14 20:55:35 skubuntwo kernel: [    0.702068] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 14 20:55:35 skubuntwo kernel: [    0.702077] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.702082] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug 14 20:55:35 skubuntwo kernel: [    0.702128] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
Aug 14 20:55:35 skubuntwo kernel: [    0.702169] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00003040
Aug 14 20:55:35 skubuntwo kernel: [    0.702297] usb usb8: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    0.702338] hub 8-0:1.0: USB hub found
Aug 14 20:55:35 skubuntwo kernel: [    0.702349] hub 8-0:1.0: 2 ports detected
Aug 14 20:55:35 skubuntwo kernel: [    0.702479] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 14 20:55:35 skubuntwo kernel: [    0.706408] i8042.c: Detected active multiplexing controller, rev 1.1.
Aug 14 20:55:35 skubuntwo kernel: [    0.708719] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 14 20:55:35 skubuntwo kernel: [    0.708729] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Aug 14 20:55:35 skubuntwo kernel: [    0.708733] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Aug 14 20:55:35 skubuntwo kernel: [    0.708738] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Aug 14 20:55:35 skubuntwo kernel: [    0.708742] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Aug 14 20:55:35 skubuntwo kernel: [    0.708859] mice: PS/2 mouse device common for all mice
Aug 14 20:55:35 skubuntwo kernel: [    0.709063] rtc_cmos 00:03: RTC can wake from S4
Aug 14 20:55:35 skubuntwo kernel: [    0.709128] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Aug 14 20:55:35 skubuntwo kernel: [    0.709164] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Aug 14 20:55:35 skubuntwo kernel: [    0.709343] device-mapper: uevent: version 1.0.3
Aug 14 20:55:35 skubuntwo kernel: [    0.709525] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Aug 14 20:55:35 skubuntwo kernel: [    0.709647] device-mapper: multipath: version 1.1.0 loaded
Aug 14 20:55:35 skubuntwo kernel: [    0.709652] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 14 20:55:35 skubuntwo kernel: [    0.710007] cpuidle: using governor ladder
Aug 14 20:55:35 skubuntwo kernel: [    0.710167] cpuidle: using governor menu
Aug 14 20:55:35 skubuntwo kernel: [    0.710690] TCP cubic registered
Aug 14 20:55:35 skubuntwo kernel: [    0.710922] NET: Registered protocol family 10
Aug 14 20:55:35 skubuntwo kernel: [    0.712001] NET: Registered protocol family 17
Aug 14 20:55:35 skubuntwo kernel: [    0.712945] PM: Resume from disk failed.
Aug 14 20:55:35 skubuntwo kernel: [    0.712973] registered taskstats version 1
Aug 14 20:55:35 skubuntwo kernel: [    0.713531]   Magic number: 7:78:953
Aug 14 20:55:35 skubuntwo kernel: [    0.713665] rtc_cmos 00:03: setting system clock to 2011-08-14 20:55:11 UTC (1313355311)
Aug 14 20:55:35 skubuntwo kernel: [    0.713669] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 14 20:55:35 skubuntwo kernel: [    0.713672] EDD information not available.
Aug 14 20:55:35 skubuntwo kernel: [    0.713787] Freeing unused kernel memory: 888k freed
Aug 14 20:55:35 skubuntwo kernel: [    0.714170] Write protecting the kernel read-only data: 7688k
Aug 14 20:55:35 skubuntwo kernel: [    0.735617] udev: starting version 151
Aug 14 20:55:35 skubuntwo kernel: [    0.746601] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Aug 14 20:55:35 skubuntwo kernel: [    0.878940] ahci 0000:00:1f.2: version 3.0
Aug 14 20:55:35 skubuntwo kernel: [    0.878966] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 14 20:55:35 skubuntwo kernel: [    0.879091]   alloc irq_desc for 26 on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.879095]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [    0.879110] ahci 0000:00:1f.2: irq 26 for MSI/MSI-X
Aug 14 20:55:35 skubuntwo kernel: [    0.879180] ahci: SSS flag set, parallel bus scan disabled
Aug 14 20:55:35 skubuntwo kernel: [    0.879227] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
Aug 14 20:55:35 skubuntwo kernel: [    0.879233] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ccc ems 
Aug 14 20:55:35 skubuntwo kernel: [    0.879241] ahci 0000:00:1f.2: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [    0.931437] scsi0 : ahci
Aug 14 20:55:35 skubuntwo kernel: [    0.931603] scsi1 : ahci
Aug 14 20:55:35 skubuntwo kernel: [    0.931695] scsi2 : ahci
Aug 14 20:55:35 skubuntwo kernel: [    0.931799] scsi3 : ahci
Aug 14 20:55:35 skubuntwo kernel: [    0.931883] scsi4 : ahci
Aug 14 20:55:35 skubuntwo kernel: [    0.931969] scsi5 : ahci
Aug 14 20:55:35 skubuntwo kernel: [    0.932648] ata1: SATA max UDMA/133 abar m2048@0xe4505000 port 0xe4505100 irq 26
Aug 14 20:55:35 skubuntwo kernel: [    0.932653] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 26
Aug 14 20:55:35 skubuntwo kernel: [    0.932656] ata3: DUMMY
Aug 14 20:55:35 skubuntwo kernel: [    0.932658] ata4: DUMMY
Aug 14 20:55:35 skubuntwo kernel: [    0.932662] ata5: SATA max UDMA/133 abar m2048@0xe4505000 port 0xe4505300 irq 26
Aug 14 20:55:35 skubuntwo kernel: [    0.932667] ata6: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 26
Aug 14 20:55:35 skubuntwo kernel: [    0.990098] usb 1-2: new high speed USB device using ehci_hcd and address 2
Aug 14 20:55:35 skubuntwo kernel: [    1.219928] usb 1-2: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    1.281324] ata1: SATA link down (SStatus 0 SControl 300)
Aug 14 20:55:35 skubuntwo kernel: [    2.230108] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 14 20:55:35 skubuntwo kernel: [    2.231579] ata2.00: ACPI _SDD failed (AE 0x5)
Aug 14 20:55:35 skubuntwo kernel: [    7.760109] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 14 20:55:35 skubuntwo kernel: [    7.761573] ata2.00: ACPI _SDD failed (AE 0x5)
Aug 14 20:55:35 skubuntwo kernel: [    7.761577] ata2.00: ACPI: failed the second time, disabled
Aug 14 20:55:35 skubuntwo kernel: [    7.806560] ata2.00: ATA-8: WDC WD3200BEVT-22ZCT0, 11.01A11, max UDMA/133
Aug 14 20:55:35 skubuntwo kernel: [    7.806564] ata2.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Aug 14 20:55:35 skubuntwo kernel: [    7.809384] ata2.00: configured for UDMA/133
Aug 14 20:55:35 skubuntwo kernel: [    7.820350] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-2 11.0 PQ: 0 ANSI: 5
Aug 14 20:55:35 skubuntwo kernel: [    7.820571] sd 1:0:0:0: Attached scsi generic sg0 type 0
Aug 14 20:55:35 skubuntwo kernel: [    7.820677] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Aug 14 20:55:35 skubuntwo kernel: [    7.820758] sd 1:0:0:0: [sda] Write Protect is off
Aug 14 20:55:35 skubuntwo kernel: [    7.820762] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 14 20:55:35 skubuntwo kernel: [    7.820798] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 14 20:55:35 skubuntwo kernel: [    7.820992]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
Aug 14 20:55:35 skubuntwo kernel: [    7.862345] sd 1:0:0:0: [sda] Attached SCSI disk
Aug 14 20:55:35 skubuntwo kernel: [    8.170109] ata5: SATA link down (SStatus 0 SControl 300)
Aug 14 20:55:35 skubuntwo kernel: [    9.130160] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 14 20:55:35 skubuntwo kernel: [    9.134309] ata6.00: ACPI _SDD failed (AE 0x5)
Aug 14 20:55:35 skubuntwo kernel: [   14.660104] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 14 20:55:35 skubuntwo kernel: [   14.664249] ata6.00: ACPI _SDD failed (AE 0x5)
Aug 14 20:55:35 skubuntwo kernel: [   14.664253] ata6.00: ACPI: failed the second time, disabled
Aug 14 20:55:35 skubuntwo kernel: [   14.664259] ata6.00: ATAPI: HL-DT-ST DVDRAM GU10N, AP04, max UDMA/133
Aug 14 20:55:35 skubuntwo kernel: [   14.669153] ata6.00: configured for UDMA/133
Aug 14 20:55:35 skubuntwo kernel: [   14.693371] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GU10N     AP04 PQ: 0 ANSI: 5
Aug 14 20:55:35 skubuntwo kernel: [   14.704633] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 14 20:55:35 skubuntwo kernel: [   14.704637] Uniform CD-ROM driver Revision: 3.20
Aug 14 20:55:35 skubuntwo kernel: [   14.704762] sr 5:0:0:0: Attached scsi CD-ROM sr0
Aug 14 20:55:35 skubuntwo kernel: [   14.704836] sr 5:0:0:0: Attached scsi generic sg1 type 5
Aug 14 20:55:35 skubuntwo kernel: [   15.265372] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Aug 14 20:55:35 skubuntwo kernel: [   15.265379] EXT4-fs (sda5): write access will be enabled during recovery
Aug 14 20:55:35 skubuntwo kernel: [   15.467907] EXT4-fs (sda5): recovery complete
Aug 14 20:55:35 skubuntwo kernel: [   15.468497] EXT4-fs (sda5): mounted filesystem with ordered data mode
Aug 14 20:55:35 skubuntwo kernel: [   24.062127] udev: starting version 151
Aug 14 20:55:35 skubuntwo kernel: [   24.099380] lp: driver loaded but no devices found
Aug 14 20:55:35 skubuntwo kernel: [   24.142773] Adding 5707768k swap on /dev/sda6.  Priority:-1 extents:1 across:5707768k 
Aug 14 20:55:35 skubuntwo kernel: [   24.192364] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
Aug 14 20:55:35 skubuntwo kernel: [   24.193865] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
Aug 14 20:55:35 skubuntwo kernel: [   24.456302] [drm] Initialized drm 1.1.0 20060810
Aug 14 20:55:35 skubuntwo kernel: [   24.464364] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Aug 14 20:55:35 skubuntwo kernel: [   24.499300] atl1c 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 14 20:55:35 skubuntwo kernel: [   24.499316] atl1c 0000:02:00.0: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [   24.505366] Linux video capture interface: v2.00
Aug 14 20:55:35 skubuntwo kernel: [   24.522522] cfg80211: Calling CRDA to update world regulatory domain
Aug 14 20:55:35 skubuntwo kernel: [   24.522796] uvcvideo: Found UVC 1.00 device HD Video WebCam (064e:a133)
Aug 14 20:55:35 skubuntwo kernel: [   24.537593] type=1505 audit(1313380535.316:2):  operation="profile_load" pid=678 name="/sbin/dhclient3"
Aug 14 20:55:35 skubuntwo kernel: [   24.539613] type=1505 audit(1313380535.316:3):  operation="profile_load" pid=678 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 14 20:55:35 skubuntwo kernel: [   24.540313] type=1505 audit(1313380535.326:4):  operation="profile_load" pid=678 name="/usr/lib/connman/scripts/dhclient-script"
Aug 14 20:55:35 skubuntwo kernel: [   24.547817] input: HD Video WebCam as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input6
Aug 14 20:55:35 skubuntwo kernel: [   24.547898] usbcore: registered new interface driver uvcvideo
Aug 14 20:55:35 skubuntwo kernel: [   24.547902] USB Video Class driver (v0.1.0)
Aug 14 20:55:35 skubuntwo kernel: [   24.565062] cfg80211: World regulatory domain updated:
Aug 14 20:55:35 skubuntwo kernel: [   24.565067] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 14 20:55:35 skubuntwo kernel: [   24.565071] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 14 20:55:35 skubuntwo kernel: [   24.565076] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 14 20:55:35 skubuntwo kernel: [   24.565079] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 14 20:55:35 skubuntwo kernel: [   24.565083] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 14 20:55:35 skubuntwo kernel: [   24.565087] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 14 20:55:35 skubuntwo kernel: [   24.566483] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 14 20:55:35 skubuntwo kernel: [   24.566491] i915 0000:00:02.0: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [   24.625534] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 14 20:55:35 skubuntwo kernel: [   24.640028]   alloc irq_desc for 27 on node -1
Aug 14 20:55:35 skubuntwo kernel: [   24.640033]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [   24.640046] i915 0000:00:02.0: irq 27 for MSI/MSI-X
Aug 14 20:55:35 skubuntwo kernel: [   24.640065] [drm] set up 63M of stolen space
Aug 14 20:55:35 skubuntwo kernel: [   24.642333] atl1c 0000:02:00.0: version 1.0.0.1-NAPI
Aug 14 20:55:35 skubuntwo kernel: [   24.718119] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Aug 14 20:55:35 skubuntwo kernel: [   24.718123] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Aug 14 20:55:35 skubuntwo kernel: [   24.718211] iwlagn 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 14 20:55:35 skubuntwo kernel: [   24.718222] iwlagn 0000:01:00.0: setting latency timer to 64
Aug 14 20:55:35 skubuntwo kernel: [   24.718271] iwlagn 0000:01:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Aug 14 20:55:35 skubuntwo kernel: [   24.799201] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Aug 14 20:55:35 skubuntwo kernel: [   24.799545] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Aug 14 20:55:35 skubuntwo kernel: [   24.799549] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Aug 14 20:55:35 skubuntwo kernel: [   24.799552] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Aug 14 20:55:35 skubuntwo kernel: [   24.810294] iwlagn 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Aug 14 20:55:35 skubuntwo kernel: [   24.810367]   alloc irq_desc for 28 on node -1
Aug 14 20:55:35 skubuntwo kernel: [   24.810371]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [   24.810394] iwlagn 0000:01:00.0: irq 28 for MSI/MSI-X
Aug 14 20:55:35 skubuntwo kernel: [   24.929084] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 14 20:55:35 skubuntwo kernel: [   25.096252]   alloc irq_desc for 29 on node -1
Aug 14 20:55:35 skubuntwo kernel: [   25.096257]   alloc kstat_irqs on node -1
Aug 14 20:55:35 skubuntwo kernel: [   25.096278] atl1c 0000:02:00.0: irq 29 for MSI/MSI-X
Aug 14 20:55:35 skubuntwo kernel: [   25.097268] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 14 20:55:35 skubuntwo kernel: [   25.121111] phy0: Selected rate control algorithm 'iwl-agn-rs'
Aug 14 20:55:35 skubuntwo NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Aug 14 20:55:35 skubuntwo NetworkManager:    SCPluginIfupdown: locking wireless connection setting
Aug 14 20:55:35 skubuntwo NetworkManager:    Ifupdown: get unmanaged devices count: 2
Aug 14 20:55:35 skubuntwo NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Aug 14 20:55:35 skubuntwo NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
Aug 14 20:55:35 skubuntwo NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 14 20:55:35 skubuntwo dhclient: Listening on LPF/eth0/00:1e:33:26:94:a0
Aug 14 20:55:35 skubuntwo dhclient: Sending on   LPF/eth0/00:1e:33:26:94:a0
Aug 14 20:55:35 skubuntwo dhclient: Sending on   Socket/fallback
Aug 14 20:55:35 skubuntwo kernel: [   25.158455] iwlagn 0000:01:00.0: firmware: requesting iwlwifi-5000-2.ucode
Aug 14 20:55:36 skubuntwo kernel: [   25.243647] iwlagn 0000:01:00.0: loaded firmware version 8.24.2.12
Aug 14 20:55:36 skubuntwo kernel: [   25.400374] Registered led device: iwl-phy0::radio
Aug 14 20:55:36 skubuntwo kernel: [   25.400402] Registered led device: iwl-phy0::assoc
Aug 14 20:55:36 skubuntwo kernel: [   25.400426] Registered led device: iwl-phy0::RX
Aug 14 20:55:36 skubuntwo kernel: [   25.400454] Registered led device: iwl-phy0::TX
Aug 14 20:55:36 skubuntwo kernel: [   25.414839] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000/0xa0000
Aug 14 20:55:36 skubuntwo kernel: [   25.431109] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 14 20:55:36 skubuntwo kernel: [   25.447714] fb0: inteldrmfb frame buffer device
Aug 14 20:55:36 skubuntwo kernel: [   25.447718] registered panic notifier
Aug 14 20:55:36 skubuntwo kernel: [   25.453384] acpi device:02: registered as cooling_device2
Aug 14 20:55:36 skubuntwo kernel: [   25.453884] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
Aug 14 20:55:36 skubuntwo kernel: [   25.453966] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
Aug 14 20:55:36 skubuntwo kernel: [   25.454065] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Aug 14 20:55:36 skubuntwo kernel: [   25.454124]   alloc irq_desc for 22 on node -1
Aug 14 20:55:36 skubuntwo kernel: [   25.454127]   alloc kstat_irqs on node -1
Aug 14 20:55:36 skubuntwo kernel: [   25.454137] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 14 20:55:36 skubuntwo kernel: [   25.454188] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 14 20:55:36 skubuntwo kernel: [   25.457902] vga16fb: initializing
Aug 14 20:55:36 skubuntwo kernel: [   25.457907] vga16fb: mapped to 0xffff8800000a0000
Aug 14 20:55:36 skubuntwo kernel: [   25.457913] vga16fb: not registering due to another framebuffer present
Aug 14 20:55:36 skubuntwo kernel: [   25.460987] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Aug 14 20:55:36 skubuntwo gdm-binary[992]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 14 20:55:36 skubuntwo auditd: /sbin/audispd permissions should be 0750
Aug 14 20:55:36 skubuntwo auditd[1034]: Started dispatcher: /sbin/audispd pid: 1036
Aug 14 20:55:36 skubuntwo audispd: priority_boost_parser called with: 4
Aug 14 20:55:36 skubuntwo audispd: max_restarts_parser called with: 10
Aug 14 20:55:36 skubuntwo audispd: af_unix plugin initialized
Aug 14 20:55:36 skubuntwo audispd: audispd initialized with q_depth=80 and 1 active plugins
Aug 14 20:55:36 skubuntwo kernel: [   25.540446] type=1505 audit(1313380536.326:5):  operation="profile_load" pid=1021 name="/usr/share/gdm/guest-session/Xsession"
Aug 14 20:55:36 skubuntwo kernel: [   25.540686] type=1505 audit(1313380536.326:6):  operation="profile_replace" pid=1022 name="/sbin/dhclient3"
Aug 14 20:55:36 skubuntwo kernel: [   25.541838] type=1505 audit(1313380536.326:7):  operation="profile_replace" pid=1022 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 14 20:55:36 skubuntwo kernel: [   25.542442] type=1505 audit(1313380536.326:8):  operation="profile_replace" pid=1022 name="/usr/lib/connman/scripts/dhclient-script"
Aug 14 20:55:36 skubuntwo kernel: [   25.548362] type=1505 audit(1313380536.326:9):  operation="profile_load" pid=1025 name="/usr/lib/cups/backend/cups-pdf"
Aug 14 20:55:36 skubuntwo kernel: [   25.549674] type=1505 audit(1313380536.326:10):  operation="profile_load" pid=1025 name="/usr/sbin/cupsd"
Aug 14 20:55:36 skubuntwo kernel: [   25.552163] type=1505 audit(1313380536.336:11):  operation="profile_load" pid=1023 name="/usr/bin/evince"
Aug 14 20:55:36 skubuntwo kernel: [   25.643646] hda_codec: ALC269: BIOS auto-probing.
Aug 14 20:55:36 skubuntwo kernel: [   25.644252] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
Aug 14 20:55:36 skubuntwo kernel: [   25.676050] Console: switching to colour frame buffer device 170x48
Aug 14 20:55:36 skubuntwo gdm-simple-slave[1118]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 14 20:55:36 skubuntwo auditd[1034]: Init complete, auditd 1.7.13 listening for events (startup state enable)
Aug 14 20:55:36 skubuntwo gdm-binary[992]: WARNING: Unable to find users: no seat-id found
Aug 14 20:55:36 skubuntwo init: apport pre-start process (1168) terminated with status 1
Aug 14 20:55:36 skubuntwo cron[1174]: (CRON) INFO (pidfile fd = 3)
Aug 14 20:55:36 skubuntwo acpid: starting up with proc fs
Aug 14 20:55:36 skubuntwo acpid: 36 rules loaded
Aug 14 20:55:36 skubuntwo anacron[1185]: Anacron 2.3 started on 2011-08-14
Aug 14 20:55:36 skubuntwo acpid: waiting for events: event logging is off
Aug 14 20:55:36 skubuntwo cron[1190]: (CRON) STARTUP (fork ok)
Aug 14 20:55:36 skubuntwo init: apport post-stop process (1182) terminated with status 1
Aug 14 20:55:36 skubuntwo cron[1190]: (CRON) INFO (Running @reboot jobs)
Aug 14 20:55:36 skubuntwo kernel: [   26.048502] ppdev: user-space parallel port driver
Aug 14 20:55:36 skubuntwo anacron[1185]: Normal exit (0 jobs run)
Aug 14 20:55:37 skubuntwo dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 14 20:55:37 skubuntwo dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 14 20:55:37 skubuntwo dhclient: All rights reserved.
Aug 14 20:55:37 skubuntwo dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 14 20:55:37 skubuntwo dhclient: 
Aug 14 20:55:37 skubuntwo dhclient: Listening on LPF/wlan0/00:22:fb:3d:ad:9c
Aug 14 20:55:37 skubuntwo dhclient: Sending on   LPF/wlan0/00:22:fb:3d:ad:9c
Aug 14 20:55:37 skubuntwo dhclient: Sending on   Socket/fallback
Aug 14 20:55:37 skubuntwo anacron[1355]: Anacron 2.3 started on 2011-08-14
Aug 14 20:55:37 skubuntwo anacron[1355]: Normal exit (0 jobs run)
Aug 14 20:55:37 skubuntwo kernel: [   26.610317] CPU0 attaching NULL sched-domain.
Aug 14 20:55:37 skubuntwo kernel: [   26.610325] CPU1 attaching NULL sched-domain.
Aug 14 20:55:37 skubuntwo acpid: client connected from 1331[0:0]
Aug 14 20:55:37 skubuntwo acpid: 1 client rule loaded
Aug 14 20:55:37 skubuntwo kernel: [   26.680216] CPU0 attaching sched-domain:
Aug 14 20:55:37 skubuntwo kernel: [   26.680221]  domain 0: span 0-1 level MC
Aug 14 20:55:37 skubuntwo kernel: [   26.680225]   groups: 0 1
Aug 14 20:55:37 skubuntwo kernel: [   26.680234] CPU1 attaching sched-domain:
Aug 14 20:55:37 skubuntwo kernel: [   26.680237]  domain 0: span 0-1 level MC
Aug 14 20:55:37 skubuntwo kernel: [   26.680240]   groups: 1 0
Aug 14 20:55:37 skubuntwo init: plymouth-stop pre-start process (1381) terminated with status 1
Aug 14 20:55:40 skubuntwo wpa_supplicant[1307]: WPS-AP-AVAILABLE 
Aug 14 20:55:41 skubuntwo gdm-session-worker[1420]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 14 20:55:42 skubuntwo polkitd[1429]: started daemon version 0.96 using authority implementation `local' version `0.96'
Aug 14 20:55:42 skubuntwo anacron[1474]: Anacron 2.3 started on 2011-08-14
Aug 14 20:55:42 skubuntwo anacron[1474]: Normal exit (0 jobs run)
Aug 14 20:55:42 skubuntwo kernel: [   32.002037] CPU0 attaching NULL sched-domain.
Aug 14 20:55:42 skubuntwo kernel: [   32.002046] CPU1 attaching NULL sched-domain.
Aug 14 20:55:42 skubuntwo gdm-simple-greeter[1417]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Aug 14 20:55:42 skubuntwo kernel: [   32.051449] CPU0 attaching sched-domain:
Aug 14 20:55:42 skubuntwo kernel: [   32.051455]  domain 0: span 0-1 level MC
Aug 14 20:55:42 skubuntwo kernel: [   32.051459]   groups: 0 1
Aug 14 20:55:42 skubuntwo kernel: [   32.051468] CPU1 attaching sched-domain:
Aug 14 20:55:42 skubuntwo kernel: [   32.051471]  domain 0: span 0-1 level MC
Aug 14 20:55:42 skubuntwo kernel: [   32.051474]   groups: 1 0

```

And here's the pm-suspend.log for this run:
```

Initial commandline parameters: 
Sun Aug 14 20:54:04 PDT 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux skubuntwo 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7960  1 
snd_hda_codec_intelhdmi    13090  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279008  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11104  0 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
snd_hda_intel          25805  0 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1473  2 
snd_seq_dummy           1782  0 
ip6table_filter         1712  1 
snd_seq_oss            31191  0 
ip6_tables             19428  1 ip6table_filter
snd_seq_midi            5829  0 
nf_nat_irc              1577  0 
snd_rawmidi            23420  1 snd_seq_midi
nf_conntrack_irc        4429  1 nf_nat_irc
nf_nat_ftp              2513  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack_ipv4      12742  9 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
nf_conntrack_ftp        7126  1 nf_nat_ftp
iwlagn                123060  0 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iwlcore               125250  1 iwlagn
iptable_filter          1841  1 
mac80211              238896  2 iwlagn,iwlcore
led_class               3764  1 iwlcore
snd                    71283  13 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  324711  2 
uvcvideo               62851  0 
ip_tables              18201  1 iptable_filter
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
cfg80211              148341  3 iwlagn,iwlcore,mac80211
atl1c                  32975  0 
drm_kms_helper         30742  1 i915
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
psmouse                65040  0 
drm                   198886  3 i915,drm_kms_helper
serio_raw               4918  0 
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
intel_agp              29319  2 i915
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
             total       used       free     shared    buffers     cached
Mem:       3961156     385684    3575472          0      44728     137532
-/+ buffers/cache:     203424    3757732
Swap:      5707768          0    5707768
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Sun Aug 14 20:54:04 PDT 2011: performing suspend

```

As for when the problem started, I bought the laptop a few weeks ago. Out of the box, suspend worked, resumed failed (in the same way that it does now). As I was tinkering with it a bit, resume began working on Aug 1, and continued to work until the next time I restarted the machine. Thereafter, it has never worked again.

I've tried everything I could, to figure out what changed in the machine to make it begin to work. Turns out, none of the things I had tried on purpose actually had any effect. (I tried them again.)

I went as far as using 'find' to list every file in the entire file system that was modified from the time of the last failed resume, up to the time of the first succesful resume. I found weird and interesting stuff, but could not make sense of any of it.

By the way, I still have syslogs and pm-suspend.log's from the times when the resume was actually working properly. Could these be helpful?

re: lid
No, opening the lid never caused the machine to resume, even when resume was working. The power button would do it, and so would any key on the keyboard.

re: kernel parameters you suggested
I tried both together, as well as each one by itself. None of these configurations caused resume to work.

---

### Post by Toz on 2011-08-15
There really isn't much in the log files. I noticed:
> Aug 14 20:55:35 skubuntwo kernel: [    0.700582] usb usb3: configuration #1 chosen from 1 choice
Aug 14 20:55:35 skubuntwo kernel: [    0.700624] hub 3-0:1.0: USB hub found
Aug 14 20:55:35 skubuntwo kernel: [    0.700633] hub 3-0:1.0: 2 ports detected
...that you have usb 3 ports. I've run into a situation a couple of times before where usb 3 has interfered with resume/suspend. Lets try unbinding these devices before suspend and rebinding afterwards to see if that might be the problem. Here is a link to the scripts you will need to create: [http://tak.atso-net.jp/blog/2011/05/problems-suspending-machines-with-usb3-in-ubuntu]("http://tak.atso-net.jp/blog/2011/05/problems-suspending-machines-with-usb3-in-ubuntu"). 

The important thing here is to specify the correct pci addresses. To get your current pci addresses, do this:
```
ls /sys/bus/pci/drivers/ehci_hcd/
```
They will be the ones in the format ```
xxxx:xx:xx:x
``` For each one of your pci devices, create an entry in both the "hibernate|suspend" and "resume|thaw" sections.

If you don't mind, can you post back the results of the ls command and the script file you created (don't forget to make the script file executable)?

---

### Post by skief on 2011-08-15
I created the scripts and tried another suspend/resume, but the behavior was the same: suspend OK, resume fail.

Here are my pci addresses:
```

> ll /sys/bus/pci/drivers/ehci_hcd/
total 0
drwxr-xr-x  2 root root    0 2011-08-15 08:51 ./
drwxr-xr-x 21 root root    0 2011-08-15 08:40 ../
lrwxrwxrwx  1 root root    0 2011-08-15 08:51 0000:00:1a.7 -> ../../../../devices/pci0000:00/0000:00:1a.7/
lrwxrwxrwx  1 root root    0 2011-08-15 08:51 0000:00:1d.7 -> ../../../../devices/pci0000:00/0000:00:1d.7/
--w-------  1 root root 4096 2011-08-15 08:51 bind
lrwxrwxrwx  1 root root    0 2011-08-15 08:51 module -> ../../../../module/ehci_hcd/
--w-------  1 root root 4096 2011-08-15 08:51 new_id
--w-------  1 root root 4096 2011-08-15 08:51 remove_id
--w-------  1 root root 4096 2011-08-15 08:51 uevent
--w-------  1 root root 4096 2011-08-15 08:51 unbind

```
And here are the files I created, along with demonstration that they are executable:
```

> cd /etc/pm/sleep.d/

> ll 20_custom-ehci_hcd
-rwxr-xr-x 1 root root 472 2011-08-15 08:34 20_custom-ehci_hcd*

> cat 20_custom-ehci_hcd
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
               echo -n "0000:00:1a.7" | tee # /sys/bus/pci/drivers/ehci_hcd/unbind
               echo -n "0000:00:1d.7" | tee # /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              echo -n "0000:00:1a.7" | tee # /sys/bus/pci/drivers/ehci_hcd/bind
              echo -n "0000:00:1d.7" | tee # /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac

```
and
```

> cd /etc/pm/config.d/

> ll usb3-suspend-workaround 
-rwxr-xr-x 1 root root 74 2011-08-15 08:35 usb3-suspend-workaround*

> cat usb3-suspend-workaround 
#File: "/etc/pm/config.d/usb3-suspend-workaround".
SUSPEND_MODULES="xhci"

```
(don't know if I needed to make the second one executable, but I did anyway). And here is the pm-suspend.log showing that this new hook number 20 was actually called:
```

Initial commandline parameters: 
Mon Aug 15 08:39:22 PDT 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux skubuntwo 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   279008  1 
fbcon                  39270  72 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11104  0 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
ip6table_filter         1712  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
ip6_tables             19428  1 ip6table_filter
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
nf_nat_irc              1577  0 
nf_conntrack_irc        4429  1 nf_nat_irc
snd_seq_dummy           1782  0 
nf_nat_ftp              2513  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_seq_oss            31191  0 
nf_conntrack_ipv4      12742  9 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_seq_midi            5829  0 
nf_conntrack_ftp        7126  1 nf_nat_ftp
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_rawmidi            23420  1 snd_seq_midi
iptable_filter          1841  1 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
arc4                    1473  2 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              18201  1 iptable_filter
iwlagn                123060  0 
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               125250  1 iwlagn
i915                  324711  2 
mac80211              238896  2 iwlagn,iwlcore
led_class               3764  1 iwlcore
drm_kms_helper         30742  1 i915
snd                    71283  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
atl1c                  32975  0 
psmouse                65040  0 
serio_raw               4918  0 
cfg80211              148341  3 iwlagn,iwlcore,mac80211
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm                   198886  3 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
intel_agp              29319  2 i915
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
             total       used       free     shared    buffers     cached
Mem:       3961156     801108    3160048          0     113672     418968
-/+ buffers/cache:     268468    3692688
Swap:      5707768          0    5707768
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:xmodmap:  unable to open display ''
xmodmap:  unable to open display ''
success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:0000:00:1a.70000:00:1d.7success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Mon Aug 15 08:39:24 PDT 2011: performing suspend

```
Should I be trying this with either or both of the kernel parameters that you suggested before? (I did not use either of them.)

Meanwhile, I note that, back when resume was working, my backlight would switch on within a second or two of waking the computer; when it is not working, as now, the backlight never switches on before the machine shuts off.

---

### Post by Toz on 2011-08-15
Ok, a long shot here. Is there anything in your bios that you can set for sleep/resume functionality?

Also, have a look at the history.log* files in /var/log/apt to see if pm-utils or the kernel or any other major program was updated around August 1st. Might give us a clue.

A few more kernel parameters to try:
- acpi_osi=Linux
- acpi_osi="Linux"
- acpi_osi=\"Linux\"

Have you tried s2ram?
```
sudo apt-get uswsusp
```
...then
```
s2ram
```
...if you get an error message, try:
```
s2ram -f
```

And finally, can you boot into a previous kernel from your grub screen? Have you tried any of the newer mainline kernels?

---

### Post by skief on 2011-08-16
re: bios
I don't know. Do you mean something I would set by pressing F2 during startup? I looked around, and I did not see anything to do with suspend/resume in there. Or is there another way to access what you're talking about?

re: /var/log/apt/history.log
Below is everything from Aug 1 and Aug 2. Neither of the two things from Aug 1 made it start working -- these are just auditing tools I was trying to use to see what was going wrong during resume. And I know for sure it was about 4 hours later ( namely, at 21:58 ) that I had the first successful resume.

As for the Aug 2 stuff, I'll admit I don't know what some of those things are, but it all looks pretty innocuous at first glance. I keep a hand-written log as well, and the only admin tasks I carried out deliberately were these:

1. *Attempted* to install Adobe Flash Player from within Firefox -- it didn't work properly, and I gave up.

2. Installed Subversion, with sudo apt-get install subversion.

3. Downloaded JDK6 from oracle.com and installed it in /usr/local.

4. Installed Eclipse, with sudo apt-get install eclipse.

It is *possible* that Update Manager also popped up that day, and I did whatever it wanted to do, but I'm not sure.

I suppose I will google all the packages in there, and make sure there's nothing suspicious.

```

Start-Date: 2011-08-01  17:32:23
Install: acct (6.5.1-1ubuntu1)
End-Date: 2011-08-01  17:32:31

Start-Date: 2011-08-01  17:42:10
Install: auditd (1.7.13-1ubuntu2), libaudit0 (1.7.13-1ubuntu2)
End-Date: 2011-08-01  17:42:16

Start-Date: 2011-08-02  16:26:19
Upgrade: libsmbclient (3.4.7~dfsg-1ubuntu3.6, 3.4.7~dfsg-1ubuntu3.7), smbclient (3.4.7~dfsg-1ubuntu3.6, 3.4.7~dfsg-1ubuntu3.7), libwbclient0 (3.4.7~dfsg-1ubuntu3.6, 3.4.7~dfsg-1ubuntu3.7), samba-common (3.4.7~dfsg-1ubuntu3.6, 3.4.7~dfsg-1ubuntu3.7), samba-common-bin (3.4.7~dfsg-1ubuntu3.6, 3.4.7~dfsg-1ubuntu3.7)
End-Date: 2011-08-02  16:26:34

Start-Date: 2011-08-02  16:58:05
Install: libapr1 (1.3.8-1ubuntu0.3), subversion (1.6.6dfsg-2ubuntu1.3), libsvn1 (1.6.6dfsg-2ubuntu1.3), libaprutil1 (1.3.9+dfsg-3ubuntu0.10.04.1)
End-Date: 2011-08-02  16:58:12

Start-Date: 2011-08-02  17:45:30
Install: libjaxp1.3-java (1.3.04-5ubuntu3), libdb-je-java (3.3.62-3), libecj-java (3.5.1-1), realpath (1.15build1), libdb4.7-java (4.7.25-9), eclipse-platform-data (3.5.2-2ubuntu4.3), libxerces2-java (2.9.1-4ubuntu1), libjtidy-java (7+svn20070309-4), libicu4j-java (4.0.1.1-1), eclipse-rcp (3.5.2-2ubuntu4.3), libservlet2.4-java (5.0.30-10), libdb4.7-java-gcj (4.7.25-9), libcommons-beanutils-java (1.8.2-1), libcommons-logging-java (1.1.1-7), libcommons-compress-java (1.0-1), ant (1.7.1-4ubuntu1.1), libjsch-java (0.1.42-1ubuntu0.1), jarwrapper (0.28), ant-optional (1.7.1-4ubuntu1.1), sat4j (2.1.1-3), libcommons-el-java (1.0-5), libservlet2.5-java (6.0.24-2ubuntu1.7), libcommons-httpclient-java (3.1-9), libslf4j-java (1.5.10-1), libregexp-java (1.5-2), fastjar (0.98-1ubuntu0.10.04.1), libjasper-java (5.5.26-5), ant-optional-gcj (1.7.1-4ubuntu1.1), libcommons-codec-java (1.4-2), liblucene2-java (2.9.2+ds1-1), libequinox-osgi-java (3.5.2-2ubuntu4.3), libcommons-collections3-java (3.2.1-4), eclipse-platform (3.5.2-2ubuntu4.3), ant-gcj (1.7.1-4ubuntu1.1), libcommons-digester-java (1.8.1-2), libjetty-java (6.1.22-1ubuntu1), libjline-java (0.9.94-5)
End-Date: 2011-08-02  17:46:21

```


kernel parameters:
No luck, on any of the three.


s2ram:
I did have to go to the forced version s2ram -f. Resume still
failed. On restart, the message
```

resume: libgcrypt version 1.4.4

```
was displayed for several seconds. Googling the phrase, I see there's
quite a lot of discussion about it, out there. I guess I'd better
start reading.... (Unless you happen to already know something about it?)

At the grub screen I have only one kernel, Linux 2.6.32-33-generic.
I have not tried any other kernels. Perhaps that should be a next step.

Anyway, I am traveling for the next week, and probably won't have a chance to try these things until I get back.

Truly appreciate all your headscratching on this problem! :)

---

### Post by Toz on 2011-08-16
It really is a head scratcher. Anyways, happy travelings. When you return you might also want to have a look at: [https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend"). This is a low-level debugging exercise that may also help identify the problem.

---

### Post by skief on 2011-08-23
I tried the debugging procedure at
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend).
(By the way, storing the information in the real time clock: about the most bloody brilliant thing I've heard of in a long time. :cool: )
Unfortunately I'm not getting much in dmesg after the reboot.
First attempt:
```

[    0.703569]   Magic number: 7:131:129
[    0.703647] acpi device:04: hash matches

```
Second attempt:
```

[    0.713709]   Magic number: 7:675:152
[    0.713733] bdi 1:4: hash matches

```
Meanwhile, lspci shows no devices whose numbers seem to be anything like 04 or 1:4.
```

> lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)

```
So honestly, I don't know what to make of this.

---

### Post by Toz on 2011-08-23
Not much in the logs. Does **lsusb** or **lspcmcia** show a device 04 or 1:4?

(Disclaimer: I'm reaching here....)

Maybe the system is reacting to the power button as shutdown and not as a resume request??? ([https://bugzilla.kernel.org/show_bug.cgi?id=6612]("https://bugzilla.kernel.org/show_bug.cgi?id=6612") - old, I know). I don't have a 10.04 install available, but in 11.04 in the /etc/acpi/powerbtn.sh script, there is a check for acpisleep prior to initiating shutdown. Maybe there is something screwy there.

Maybe you can try this. **rtcwake** is a utility that suspends the system and resumes it at a specified time (no interaction required). Might be worth a test to see if it works. Here is a script I came across a while ago:
```
#!/bin/bash

# Auto suspend and wake-up script
#
# Puts the computer on standby and automatically wakes it up at specified time
#
# Written by Romke van der Meulen <redge.online@gmail.com>
#
# Takes a 24hour time HH:MM as its argument
# Example:
# suspend_until 9:30
# suspend_until 18:45
# suspend_until 0325
# suspend_until 515

# (just drag the scriptfile into terminal window and add time to the line)

# ------------------------------------------------------
# Argument check
if [ $# -lt 1 ]; then
	echo "Usage: suspend_until HH:MM"
fi

# Check whether specified time today or tomorrow
DESIRED=$((`date +%s -d "$1"`))
NOW=$((`date +%s`))
if [ $DESIRED -lt $NOW ]; then
	DESIRED=$((`date +%s -d "$1"` + 24*60*60))
fi


# Define hours/mins/sec to wake-up (for printing purposes only):
hours=$(((DESIRED-NOW)/3600))
minutes=$((  ((DESIRED-NOW)-(hours*3600))/60  ))
seconds=$(( ((DESIRED-NOW)-((hours*3600)+(minutes*60)))  ))

# Kill rtcwake if already running
sudo killall rtcwake

# Let user know what we're going to do
echo "Going to suspend for $hours h $minutes min"

echo "To cancel, press Ctrl+c within the next 10 seconds."
sleep 10

# Set RTC wakeup time
sudo rtcwake -l -m on -t $DESIRED &

# feedback
echo "Suspending..."

# give rtcwake some time to make its stuff
sleep 2

# then suspend
sudo pm-suspend
# -------------------------------------------------------------------------------------
# Any commands you want to launch after wakeup can be placed here
# Remember: sudo may have expired by now

# Unload rtcwake if it's running, otherwise next time computer won't wake up from sleep
SERVICE='rtcwake'
if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE running, killing process..."
    sudo killall rtcwake
else
    echo "$SERVICE is not running, no action taken."
fi
```

Another suggestion would be to boot off of the live cd and see if suspend/resume works from there (to rule out kernel/config issue).

Maybe also look at the available **acpi_sleep=** kernel parameters ([http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt"))

---

