---
title: "Ubuntu 7.10 hanging with Gigabyte ga-p35-ds2 and intel quad core q6600"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by SylvestreMergulhao on 2008-04-02
Some weeks ago I buyed a new machine with these config:

Motherboard Gigabyte Ga-p35-ds2 v2.0
Intel Core2 quad q6600
Video GeForce 7300 SE
2x Kingston 1gb DDR2 800
Seagate Sata 160gb

My Ubuntu have been hanging some times a day (some days not hangs too). My /var/log/messages show messages like below when system hangs:

============================

Apr  2 20:00:47 homelinux kernel: [  972.217270]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Apr  2 20:00:47 homelinux kernel: [  972.217278]  [note_interrupt+610/672] note_interrupt+0x262/0x2a0
Apr  2 20:00:47 homelinux kernel: [  972.217285]  [handle_level_irq+219/272] handle_level_irq+0xdb/0x110
Apr  2 20:00:47 homelinux kernel: [  972.217290]  [do_IRQ+59/112] do_IRQ+0x3b/0x70
Apr  2 20:00:47 homelinux kernel: [  972.217294]  [smp_apic_timer_interrupt+85/128] smp_apic_timer_interrupt+0x55/0x80
Apr  2 20:00:47 homelinux kernel: [  972.217300]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Apr  2 20:00:47 homelinux kernel: [  972.217305]  [__do_softirq+91/272] __do_softirq+0x5b/0x110
Apr  2 20:00:47 homelinux kernel: [  972.217310]  [do_softirq+85/96] do_softirq+0x55/0x60
Apr  2 20:00:47 homelinux kernel: [  972.217313]  [irq_exit+109/128] irq_exit+0x6d/0x80
Apr  2 20:00:47 homelinux kernel: [  972.217315]  [do_IRQ+64/112] do_IRQ+0x40/0x70
Apr  2 20:00:47 homelinux kernel: [  972.217318]  [getnstimeofday+54/208] getnstimeofday+0x36/0xd0
Apr  2 20:00:47 homelinux kernel: [  972.217323]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Apr  2 20:00:47 homelinux kernel: [  972.217328]  [mwait_idle_with_hints+70/96] mwait_idle_with_hints+0x46/0x60
Apr  2 20:00:47 homelinux kernel: [  972.217332]  [mwait_idle+0/32] mwait_idle+0x0/0x20
Apr  2 20:00:47 homelinux kernel: [  972.217335]  [cpu_idle+83/224] cpu_idle+0x53/0xe0
Apr  2 20:00:47 homelinux kernel: [  972.217338]  [start_kernel+805/944] start_kernel+0x325/0x3b0
Apr  2 20:00:47 homelinux kernel: [  972.217343]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Apr  2 20:00:47 homelinux kernel: [  972.217348]  =======================
Apr  2 20:01:17 homelinux kernel: [ 1002.172469]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:01:17 homelinux kernel: [ 1002.172483] ata3: soft resetting port
Apr  2 20:01:48 homelinux kernel: [ 1032.452477] ata3.00: qc timeout (cmd 0x27)
Apr  2 20:01:48 homelinux kernel: [ 1032.452487] ata3.00: ata_hpa_resize 1: hpa sectors (0) is smaller than sectors (156301488)
Apr  2 20:01:48 homelinux kernel: [ 1032.452499] ata3: failed to recover some devices, retrying in 5 secs
Apr  2 20:01:53 homelinux kernel: [ 1037.448537] ata3: soft resetting port
Apr  2 20:02:23 homelinux kernel: [ 1067.728566] ata3.00: qc timeout (cmd 0x27)
Apr  2 20:02:23 homelinux kernel: [ 1067.728575] ata3.00: ata_hpa_resize 1: hpa sectors (0) is smaller than sectors (156301488)
Apr  2 20:02:23 homelinux kernel: [ 1067.728588] ata3.00: limiting speed to UDMA/100:PIO3
Apr  2 20:02:23 homelinux kernel: [ 1067.728591] ata3: failed to recover some devices, retrying in 5 secs
Apr  2 20:02:28 homelinux kernel: [ 1072.724627] ata3: soft resetting port
Apr  2 20:02:58 homelinux kernel: [ 1103.004656] ata3.00: qc timeout (cmd 0x27)
Apr  2 20:02:58 homelinux kernel: [ 1103.004665] ata3.00: ata_hpa_resize 1: hpa sectors (0) is smaller than sectors (156301488)
Apr  2 20:02:58 homelinux kernel: [ 1103.004677] ata3.00: disabled
Apr  2 20:02:58 homelinux kernel: [ 1103.004680] ata3: failed to recover some devices, retrying in 5 secs
Apr  2 20:02:59 homelinux kernel: [ 1103.763415] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:03:03 homelinux kernel: [ 1108.000711] ata3: failed to recover some devices, retrying in 5 secs
Apr  2 20:03:08 homelinux kernel: [ 1112.996799] ata3: soft resetting port
Apr  2 20:03:09 homelinux kernel: [ 1113.488601] ata3.01: configured for UDMA/33
Apr  2 20:03:09 homelinux kernel: [ 1113.488609] ata3: EH complete
Apr  2 20:03:39 homelinux kernel: [ 1143.440562]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:03:39 homelinux kernel: [ 1143.440576] ata3: soft resetting port
Apr  2 20:03:39 homelinux kernel: [ 1143.932331] ata3.01: configured for UDMA/33
Apr  2 20:03:39 homelinux kernel: [ 1143.932339] ata3: EH complete
Apr  2 20:04:09 homelinux kernel: [ 1173.884309]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:04:09 homelinux kernel: [ 1173.884324] ata3: soft resetting port
Apr  2 20:04:10 homelinux kernel: [ 1174.376079] ata3.01: configured for UDMA/33
Apr  2 20:04:10 homelinux kernel: [ 1174.376087] ata3: EH complete
Apr  2 20:04:17 homelinux kernel: [ 1181.639984] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:04:40 homelinux kernel: [ 1204.328047] ata3.01: limiting speed to UDMA/25:PIO4
Apr  2 20:04:40 homelinux kernel: [ 1204.328059]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:04:40 homelinux kernel: [ 1204.328073] ata3: soft resetting port
Apr  2 20:04:40 homelinux kernel: [ 1204.819873] ata3.01: configured for UDMA/25
Apr  2 20:04:40 homelinux kernel: [ 1204.819885] ata3: EH complete
Apr  2 20:04:40 homelinux kernel: [ 1204.819931] sd 2:0:0:0: [sda] READ CAPACITY failed
Apr  2 20:04:40 homelinux kernel: [ 1204.819934] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Apr  2 20:04:40 homelinux kernel: [ 1204.819939] sd 2:0:0:0: [sda] Sense not available.
Apr  2 20:04:47 homelinux kernel: [ 1211.592514] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:05:10 homelinux kernel: [ 1234.771804]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:05:10 homelinux kernel: [ 1234.771818] ata3: soft resetting port
Apr  2 20:05:11 homelinux kernel: [ 1235.263574] ata3.01: configured for UDMA/25
Apr  2 20:05:11 homelinux kernel: [ 1235.263582] ata3: EH complete
Apr  2 20:05:11 homelinux kernel: [ 1235.263692] sd 2:0:0:0: [sda] Write Protect is off
Apr  2 20:05:11 homelinux kernel: [ 1235.554533] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:05:41 homelinux kernel: [ 1265.215551]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:05:41 homelinux kernel: [ 1265.215566] ata3: soft resetting port
Apr  2 20:05:41 homelinux kernel: [ 1265.507058] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:05:41 homelinux kernel: [ 1265.707323] ata3.01: configured for UDMA/25
Apr  2 20:05:41 homelinux kernel: [ 1265.707331] ata3: EH complete
Apr  2 20:05:53 homelinux kernel: [ 1277.488067] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:06:11 homelinux kernel: [ 1295.659299]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:06:11 homelinux kernel: [ 1295.659313] ata3: soft resetting port
Apr  2 20:06:12 homelinux kernel: [ 1296.151068] ata3.01: configured for UDMA/25
Apr  2 20:06:12 homelinux kernel: [ 1296.151078] ata3: EH complete
Apr  2 20:06:35 homelinux kernel: [ 1319.421605] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:06:42 homelinux kernel: [ 1326.103047]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:06:42 homelinux kernel: [ 1326.103061] ata3: soft resetting port
Apr  2 20:06:42 homelinux kernel: [ 1326.594816] ata3.01: configured for UDMA/25
Apr  2 20:06:42 homelinux kernel: [ 1326.594827] ata3: EH complete
Apr  2 20:06:42 homelinux kernel: [ 1326.594847] sr: Sense Key : Aborted Command [current] [descriptor]
Apr  2 20:06:42 homelinux kernel: [ 1326.594856] sr: Add. Sense: No additional sense information
Apr  2 20:06:52 homelinux kernel: [ 1336.578443]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:06:52 homelinux kernel: [ 1336.578457] ata3: soft resetting port
Apr  2 20:06:53 homelinux kernel: [ 1337.070213] ata3.01: configured for UDMA/25
Apr  2 20:06:53 homelinux kernel: [ 1337.070222] ata3: EH complete
Apr  2 20:06:59 homelinux kernel: [ 1343.383627] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:07:03 homelinux kernel: [ 1347.053841]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:07:03 homelinux kernel: [ 1347.053855] ata3: soft resetting port
Apr  2 20:07:03 homelinux kernel: [ 1347.545612] ata3.01: configured for UDMA/25
Apr  2 20:07:03 homelinux kernel: [ 1347.545621] ata3: EH complete
Apr  2 20:07:13 homelinux kernel: [ 1357.529238]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:07:13 homelinux kernel: [ 1357.529253] ata3: soft resetting port
Apr  2 20:07:14 homelinux kernel: [ 1358.021007] ata3.01: configured for UDMA/25
Apr  2 20:07:14 homelinux kernel: [ 1358.021017] ata3: EH complete
Apr  2 20:07:17 homelinux kernel: [ 1361.355142] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:07:24 homelinux kernel: [ 1368.004635]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:07:24 homelinux kernel: [ 1368.004649] ata3: soft resetting port
Apr  2 20:07:24 homelinux kernel: [ 1368.496404] ata3.01: configured for UDMA/25
Apr  2 20:07:24 homelinux kernel: [ 1368.496413] ata3: EH complete
Apr  2 20:07:34 homelinux kernel: [ 1378.480031]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:07:34 homelinux kernel: [ 1378.480045] ata3: soft resetting port
Apr  2 20:07:35 homelinux kernel: [ 1378.971802] ata3.01: configured for UDMA/25
Apr  2 20:07:35 homelinux kernel: [ 1378.971810] ata3: EH complete
Apr  2 20:07:45 homelinux kernel: [ 1388.955428]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:07:45 homelinux kernel: [ 1388.955443] ata3: soft resetting port
Apr  2 20:07:45 homelinux kernel: [ 1389.447197] ata3.01: configured for UDMA/25
Apr  2 20:07:45 homelinux kernel: [ 1389.447208] ata3: EH complete
Apr  2 20:07:45 homelinux kernel: [ 1389.447217] sr 2:0:1:0: ioctl_internal_command return code = 8000002
Apr  2 20:07:45 homelinux kernel: [ 1389.447220]    : Sense Key : Aborted Command [current] [descriptor]
Apr  2 20:07:45 homelinux kernel: [ 1389.447226]    : Add. Sense: No additional sense information
Apr  2 20:07:53 homelinux kernel: [ 1397.298173] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:08:15 homelinux kernel: [ 1419.399167] ata3.01: limiting speed to PIO4
Apr  2 20:08:15 homelinux kernel: [ 1419.399180]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:08:15 homelinux kernel: [ 1419.399194] ata3: soft resetting port
Apr  2 20:08:16 homelinux kernel: [ 1419.890878] ata3.01: configured for PIO4
Apr  2 20:08:16 homelinux kernel: [ 1419.890887] ata3: EH complete
Apr  2 20:08:29 homelinux kernel: [ 1433.241205] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:08:41 homelinux kernel: [ 1445.222216] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:08:46 homelinux kernel: [ 1449.842924]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:08:46 homelinux kernel: [ 1449.842938] ata3: soft resetting port
Apr  2 20:08:46 homelinux kernel: [ 1450.334626] ata3.01: configured for PIO4
Apr  2 20:08:46 homelinux kernel: [ 1450.334635] ata3: EH complete
Apr  2 20:09:16 homelinux kernel: [ 1480.286670]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
Apr  2 20:09:16 homelinux kernel: [ 1480.286686] ata3: soft resetting port
Apr  2 20:09:17 homelinux kernel: [ 1480.778387] ata3.01: configured for PIO4
Apr  2 20:09:17 homelinux kernel: [ 1480.778396] ata3: EH complete
Apr  2 20:09:17 homelinux kernel: [ 1481.165249] NETDEV WATCHDOG: eth0: transmit timed out
Apr  2 20:10:27 homelinux syslogd 1.4.1#21ubuntu3: restart.

============================

Mar 17 23:49:55 homelinux kernel: [13595.719602]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Mar 17 23:49:55 homelinux kernel: [13595.719613]  [note_interrupt+610/672] note_interrupt+0x262/0x2a0
Mar 17 23:49:55 homelinux kernel: [13595.719624]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Mar 17 23:49:55 homelinux kernel: [13595.719631]  [handle_fasteoi_irq+187/240] handle_fasteoi_irq+0xbb/0xf0
Mar 17 23:49:55 homelinux kernel: [13595.719639]  [do_IRQ+59/112] do_IRQ+0x3b/0x70
Mar 17 23:49:55 homelinux kernel: [13595.719644]  [getnstimeofday+54/208] getnstimeofday+0x36/0xd0
Mar 17 23:49:55 homelinux kernel: [13595.719652]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Mar 17 23:49:55 homelinux kernel: [13595.719666]  [mwait_idle_with_hints+70/96] mwait_idle_with_hints+0x46/0x60
Mar 17 23:49:55 homelinux kernel: [13595.719671]  [mwait_idle+0/32] mwait_idle+0x0/0x20
Mar 17 23:49:55 homelinux kernel: [13595.719676]  [cpu_idle+83/224] cpu_idle+0x53/0xe0
Mar 17 23:49:55 homelinux kernel: [13595.719699]  =======================

============================


I've tried many things in kernel boot options like: noapic, nolapic, noacpi, irqpoll, irq=nopoll

But nothing seens to take effect. Someone known whats happening?

Thanks!

---

### Post by labralabra on 2008-04-04
I have almost the same hardware and exactly the same problem:

-------- /var/log/messages:
[__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
[note_interrupt+610/672] note_interrupt+0x262/0x2a0
[handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
[handle_fasteoi_irq+187/240] handle_fasteoi_irq+0xbb/0xf0
[do_IRQ+59/112] do_IRQ+0x3b/0x70
[common_interrupt+35/48] common_interrupt+0x23/0x30
[mwait_idle_with_hints+70/96] mwait_idle_with_hints+0x46/0x60
[mwait_idle+0/32] mwait_idle+0x0/0x20
[cpu_idle+83/224] cpu_idle+0x53/0xe0
=======================
          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4
--------


The hangups began today (I've run Ubuntu now for few months) after I made some upgrades to packages:

---------

Log started: 2008-04-03  17:52:33
(Reading database ... 142988 files and directories currently installed.)
Preparing to replace language-pack-en 1:7.10+20080205 (using .../language-pack-en_1%3a7.10+20080229_all.deb) ...
Unpacking replacement language-pack-en ...
Replacing files in old package language-pack-en-base ...
Preparing to replace language-pack-gnome-en 1:7.10+20080205 (using .../language-pack-gnome-en_1%3a7.10+20080229_all.deb) ...
Unpacking replacement language-pack-gnome-en ...
Replacing files in old package language-pack-gnome-en-base ...
Preparing to replace python2.5-dev 2.5.1-5ubuntu5 (using .../python2.5-dev_2.5.1-5ubuntu5.1_i386.deb) ...
Unpacking replacement python2.5-dev ...
Preparing to replace bzip2 1.0.4-0ubuntu2 (using .../bzip2_1.0.4-0ubuntu2.1_i386.deb) ...
Unpacking replacement bzip2 ...
Preparing to replace libbz2-1.0 1.0.4-0ubuntu2 (using .../libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb) ...
Unpacking replacement libbz2-1.0 ...
Preparing to replace python2.5 2.5.1-5ubuntu5 (using .../python2.5_2.5.1-5ubuntu5.1_i386.deb) ...
Unpacking replacement python2.5 ...
Preparing to replace python2.5-minimal 2.5.1-5ubuntu5 (using .../python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb) ...
Unpacking replacement python2.5-minimal ...
Setting up python2.5-minimal (2.5.1-5ubuntu5.1) ...

(Reading database ... 142988 files and directories currently installed.)
Preparing to replace tzdata 2007k-0ubuntu0.7.10 (using .../tzdata_2008a-0ubuntu0.7.10_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2008a-0ubuntu0.7.10) ...

Current default timezone: 'Europe/Helsinki'
Local time is now:      Thu Apr  3 17:52:47 EEST 2008.
Universal Time is now:  Thu Apr  3 14:52:47 UTC 2008.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Reading database ... 142988 files and directories currently installed.)
Preparing to replace libkrb5-dev 1.6.dfsg.1-7build1 (using .../libkrb5-dev_1.6.dfsg.1-7ubuntu0.1_i386.deb) ...
Unpacking replacement libkrb5-dev ...
Preparing to replace libkadm55 1.6.dfsg.1-7build1 (using .../libkadm55_1.6.dfsg.1-7ubuntu0.1_i386.deb) ...
Unpacking replacement libkadm55 ...
Preparing to replace libkrb53 1.6.dfsg.1-7build1 (using .../libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb) ...
Unpacking replacement libkrb53 ...
Preparing to replace openssh-server 1:4.6p1-5ubuntu0.1 (using .../openssh-server_1%3a4.6p1-5ubuntu0.2_i386.deb) ...
Unpacking replacement openssh-server ...
Preparing to replace openssh-client 1:4.6p1-5ubuntu0.1 (using .../openssh-client_1%3a4.6p1-5ubuntu0.2_i386.deb) ...
Unpacking replacement openssh-client ...
Preparing to replace libcupsys2 1.3.2-1ubuntu7.5 (using .../libcupsys2_1.3.2-1ubuntu7.6_i386.deb) ...
Unpacking replacement libcupsys2 ...
Preparing to replace libcupsimage2 1.3.2-1ubuntu7.5 (using .../libcupsimage2_1.3.2-1ubuntu7.6_i386.deb) ...
Unpacking replacement libcupsimage2 ...
Preparing to replace cupsys-common 1.3.2-1ubuntu7.5 (using .../cupsys-common_1.3.2-1ubuntu7.6_all.deb) ...
Unpacking replacement cupsys-common ...
Preparing to replace cupsys 1.3.2-1ubuntu7.5 (using .../cupsys_1.3.2-1ubuntu7.6_i386.deb) ...
 * Stopping Common Unix Printing System: cupsd
   ...done.
Unpacking replacement cupsys ...
Preparing to replace cupsys-bsd 1.3.2-1ubuntu7.5 (using .../cupsys-bsd_1.3.2-1ubuntu7.6_i386.deb) ...
Unpacking replacement cupsys-bsd ...
Preparing to replace cupsys-client 1.3.2-1ubuntu7.5 (using .../cupsys-client_1.3.2-1ubuntu7.6_i386.deb) ...
Unpacking replacement cupsys-client ...
Preparing to replace evolution 2.12.1-0ubuntu1 (using .../evolution_2.12.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement evolution ...
Preparing to replace evolution-common 2.12.1-0ubuntu1 (using .../evolution-common_2.12.1-0ubuntu1.1_all.deb) ...
Unpacking replacement evolution-common ...
Preparing to replace evolution-plugins 2.12.1-0ubuntu1 (using .../evolution-plugins_2.12.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement evolution-plugins ...
Preparing to replace firefox-gnome-support 2.0.0.12+2nobinonly+2-0ubuntu0.7.10 (using .../firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox 2.0.0.12+2nobinonly+2-0ubuntu0.7.10 (using .../firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace gthumb 3:2.10.6-0ubuntu1 (using .../gthumb_3%3a2.10.6-0ubuntu1.1_i386.deb) ...
Unpacking replacement gthumb ...
Preparing to replace libicu36 3.6-3 (using .../libicu36_3.6-3ubuntu0.1_i386.deb) ...
Unpacking replacement libicu36 ...
Preparing to replace mysql-common 5.0.45-1ubuntu3.1 (using .../mysql-common_5.0.45-1ubuntu3.3_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient15off 5.0.45-1ubuntu3.1 (using .../libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb) ...
Unpacking replacement libmysqlclient15off ...
Preparing to replace libruby1.8 1.8.6.36-1ubuntu3 (using .../libruby1.8_1.8.6.36-1ubuntu3.1_i386.deb) ...
Unpacking replacement libruby1.8 ...
Preparing to replace libsdl-image1.2 1.2.5-3 (using .../libsdl-image1.2_1.2.5-3ubuntu0.1_i386.deb) ...
Unpacking replacement libsdl-image1.2 ...
Preparing to replace libxine1-doc 1.1.7-1ubuntu1 (using .../libxine1-doc_1.1.10-1~gutsy1_all.deb) ...
Unpacking replacement libxine1-doc ...
Preparing to replace ruby1.8 1.8.6.36-1ubuntu3 (using .../ruby1.8_1.8.6.36-1ubuntu3.1_i386.deb) ...
Unpacking replacement ruby1.8 ...
Preparing to replace ssh-askpass-gnome 1:4.6p1-5ubuntu0.1 (using .../ssh-askpass-gnome_1%3a4.6p1-5ubuntu0.2_i386.deb) ...
Unpacking replacement ssh-askpass-gnome ...
Preparing to replace skype 2.0.0.63-0medibuntu0.7.10.1 (using .../skype_2.0.0.68-0medibuntu0.7.10.1_i386.deb) ...
Unpacking replacement skype ...
Preparing to replace skype-common 2.0.0.63-0medibuntu0.7.10.1 (using .../skype-common_2.0.0.68-0medibuntu0.7.10.1_all.deb) ...
Unpacking replacement skype-common ...
Setting up language-pack-en (1:7.10+20080229) ...
Setting up language-pack-gnome-en (1:7.10+20080229) ...
Setting up libbz2-1.0 (1.0.4-0ubuntu2.1) ...

Setting up python2.5 (2.5.1-5ubuntu5.1) ...

Setting up python2.5-dev (2.5.1-5ubuntu5.1) ...
Setting up bzip2 (1.0.4-0ubuntu2.1) ...

Setting up libkrb53 (1.6.dfsg.1-7ubuntu0.1) ...

Setting up libkadm55 (1.6.dfsg.1-7ubuntu0.1) ...

Setting up libkrb5-dev (1.6.dfsg.1-7ubuntu0.1) ...
Setting up openssh-client (1:4.6p1-5ubuntu0.2) ...

Setting up openssh-server (1:4.6p1-5ubuntu0.2) ...
 * Restarting OpenBSD Secure Shell server sshd
   ...done.

Setting up libcupsys2 (1.3.2-1ubuntu7.6) ...

Setting up libcupsimage2 (1.3.2-1ubuntu7.6) ...

Setting up cupsys-common (1.3.2-1ubuntu7.6) ...
Setting up cupsys (1.3.2-1ubuntu7.6) ...
Reloading AppArmor profiles : done.
 * Starting Common Unix Printing System: cupsd
   ...done.

Setting up cupsys-client (1.3.2-1ubuntu7.6) ...

Setting up cupsys-bsd (1.3.2-1ubuntu7.6) ...

Setting up evolution-common (2.12.1-0ubuntu1.1) ...

Setting up evolution (2.12.1-0ubuntu1.1) ...

Setting up evolution-plugins (2.12.1-0ubuntu1.1) ...
Setting up firefox (2.0.0.13+1nobinonly-0ubuntu0.7.10) ...
Please restart any running Firefoxes, or you will experience problems.

Setting up firefox-gnome-support (2.0.0.13+1nobinonly-0ubuntu0.7.10) ...

Setting up gthumb (3:2.10.6-0ubuntu1.1) ...

Setting up libicu36 (3.6-3ubuntu0.1) ...

Setting up mysql-common (5.0.45-1ubuntu3.3) ...
Setting up libmysqlclient15off (5.0.45-1ubuntu3.3) ...

Setting up libruby1.8 (1.8.6.36-1ubuntu3.1) ...

Setting up libsdl-image1.2 (1.2.5-3ubuntu0.1) ...

Setting up libxine1-doc (1.1.10-1~gutsy1) ...
Setting up ruby1.8 (1.8.6.36-1ubuntu3.1) ...
Setting up ssh-askpass-gnome (1:4.6p1-5ubuntu0.2) ...

Setting up skype-common (2.0.0.68-0medibuntu0.7.10.1) ...
Setting up skype (2.0.0.68-0medibuntu0.7.10.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2008-04-03  17:53:34

--------------

Which of these updates may have caused the hangups?

---

### Post by SylvestreMergulhao on 2008-04-08
No one knows whats going wrong?

---

### Post by SylvestreMergulhao on 2008-04-12
Have you tried to disable the old ata on bios? I'm guessing maybe it. I disabled it to test. The problem is that I have 1 hd and my dvd-rw in the old ata channel.

Since I disabled it - yesterday - my systems do not hangs.

---

### Post by labralabra on 2008-04-19
> **SylvestreMergulhao said:**
> Have you tried to disable the old ata on bios? I'm guessing maybe it. I disabled it to test. The problem is that I have 1 hd and my dvd-rw in the old ata channel.

Since I disabled it - yesterday - my systems do not hangs.

Has that really helped you? No more crashes? (I have the same situation - still old IDE hardrive + rewritable dvd to use, so I would not like to just try).

Just had another hangup yesterday and today :(

---

