---
title: "I cant burn CD/DVD in Debian(I tried SW like Brasero...)"
date: 2009-08-22
forum: Hardware
---

### Post by polo23 on 2009-08-22
I cant burn CD/DVD in Debian(I tried SW like Brasero...)


Hello,
I cant burn CD/DVD in Debian Lenny. I tried SW like Brasero, Gnomebaker, K3b. After burning disappear from Desktop Media disc(DVD) icon. When I click on "mechnics cd/dvd" in "computer" icon so I get message "there is probably no media in drive". But DVD disc in still in mechanics. According to me is it system problem. Burning programs works correct. Here are log from log files.

kernel: linux-image-2.6.30-bpo

**/var/log/kern.log**

Aug 22 13:20:59 debian kernel: [ 7380.850133] cdrom: This disc doesn't have any tracks I recognize!
Aug 22 13:22:51 debian kernel: [ 7493.525952] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Aug 22 13:22:51 debian kernel: [ 7493.525963] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Aug 22 13:22:51 debian kernel: [ 7493.525965] cdb 35 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aug 22 13:22:51 debian kernel: [ 7493.525966] res 40/00:03:00:00:80/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 22 13:22:51 debian kernel: [ 7493.525969] ata2.00: status: { DRDY }
Aug 22 13:22:51 debian kernel: [ 7493.525977] ata2: hard resetting link
Aug 22 13:22:56 debian kernel: [ 7498.902850] ata2: link is slow to respond, please be patient (ready=0)
Aug 22 13:23:01 debian kernel: [ 7503.548270] ata2: COMRESET failed (errno=-16)
Aug 22 13:23:01 debian kernel: [ 7503.548288] ata2: hard resetting link
Aug 22 13:23:06 debian kernel: [ 7508.914783] ata2: link is slow to respond, please be patient (ready=0)
Aug 22 13:23:11 debian kernel: [ 7513.565638] ata2: COMRESET failed (errno=-16)
Aug 22 13:23:11 debian kernel: [ 7513.565656] ata2: hard resetting link
Aug 22 13:23:16 debian kernel: [ 7518.934961] ata2: link is slow to respond, please be patient (ready=0)
Aug 22 13:23:46 debian kernel: [ 7548.653673] ata2: COMRESET failed (errno=-16)
Aug 22 13:23:46 debian kernel: [ 7548.653692] ata2: limiting SATA link speed to 1.5 Gbps
Aug 22 13:23:46 debian kernel: [ 7548.653697] ata2: hard resetting link
Aug 22 13:23:51 debian kernel: [ 7553.683672] ata2: COMRESET failed (errno=-16)
Aug 22 13:23:51 debian kernel: [ 7553.683690] ata2: reset failed, giving up
Aug 22 13:23:51 debian kernel: [ 7553.683695] ata2.00: disabled
Aug 22 13:23:51 debian kernel: [ 7553.683726] ata2: EH complete
Aug 22 13:23:57 debian kernel: [ 7559.270509] brasero[4740]: segfault at 14 ip 080bb4ce sp bf8fcf00 error 6 in brasero[8048000+c9000]

**/var/log/messages**
Aug 22 13:20:59 debian kernel: [ 7380.850133] cdrom: This disc doesn't have any tracks I recognize!
Aug 22 13:22:51 debian kernel: [ 7493.525965] cdb 35 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aug 22 13:22:51 debian kernel: [ 7493.525966] res 40/00:03:00:00:80/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 22 13:22:51 debian kernel: [ 7493.525977] ata2: hard resetting link
Aug 22 13:22:56 debian kernel: [ 7498.902850] ata2: link is slow to respond, please be patient (ready=0)
Aug 22 13:23:01 debian kernel: [ 7503.548288] ata2: hard resetting link
Aug 22 13:23:06 debian kernel: [ 7508.914783] ata2: link is slow to respond, please be patient (ready=0)
Aug 22 13:23:11 debian kernel: [ 7513.565656] ata2: hard resetting link
Aug 22 13:23:16 debian kernel: [ 7518.934961] ata2: link is slow to respond, please be patient (ready=0)
Aug 22 13:23:46 debian kernel: [ 7548.653692] ata2: limiting SATA link speed to 1.5 Gbps
Aug 22 13:23:46 debian kernel: [ 7548.653697] ata2: hard resetting link
Aug 22 13:23:51 debian kernel: [ 7553.683695] ata2.00: disabled
Aug 22 13:23:51 debian kernel: [ 7553.683726] ata2: EH complete
Aug 22 13:23:57 debian kernel: [ 7559.270509] brasero[4740]: segfault at 14 ip 080bb4ce sp bf8fcf00 error 6 in brasero[8048000+c9000]

**/var/log/syslog**

Aug 22 13:20:59 debian kernel: [ 7380.850133] cdrom: This disc doesn't have any tracks I recognize!
Aug 22 13:20:59 debian NetworkManager: <debug> [1250940059.081055] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_$
Aug 22 13:22:51 debian kernel: [ 7493.525952] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Aug 22 13:22:51 debian kernel: [ 7493.525963] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Aug 22 13:22:51 debian kernel: [ 7493.525965] cdb 35 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Aug 22 13:22:51 debian kernel: [ 7493.525966] res 40/00:03:00:00:80/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 22 13:22:51 debian kernel: [ 7493.525969] ata2.00: status: { DRDY }
Aug 22 13:22:51 debian kernel: [ 7493.525977] ata2: hard resetting link
Aug 22 13:22:56 debian kernel: [ 7498.902850] ata2: link is slow to respond, please be patient (ready=0)
Aug 22 13:23:01 debian kernel: [ 7503.548270] ata2: COMRESET failed (errno=-16)
Aug 22 13:23:01 debian kernel: [ 7503.548288] ata2: hard resetting link
Aug 22 13:23:06 debian kernel: [ 7508.914783] ata2: link is slow to respond, please be patient (ready=0)
Aug 22 13:23:11 debian kernel: [ 7513.565638] ata2: COMRESET failed (errno=-16)
Aug 22 13:23:11 debian kernel: [ 7513.565656] ata2: hard resetting link
Aug 22 13:23:16 debian kernel: [ 7518.934961] ata2: link is slow to respond, please be patient (ready=0)
Aug 22 13:23:46 debian kernel: [ 7548.653673] ata2: COMRESET failed (errno=-16)
Aug 22 13:23:46 debian kernel: [ 7548.653692] ata2: limiting SATA link speed to 1.5 Gbps
Aug 22 13:23:46 debian kernel: [ 7548.653697] ata2: hard resetting link
Aug 22 13:23:51 debian kernel: [ 7553.683672] ata2: COMRESET failed (errno=-16)
Aug 22 13:23:51 debian kernel: [ 7553.683690] ata2: reset failed, giving up
Aug 22 13:23:51 debian kernel: [ 7553.683695] ata2.00: disabled
Aug 22 13:23:51 debian kernel: [ 7553.683726] ata2: EH complete
Aug 22 13:23:54 debian NetworkManager: <debug> [1250940234.017282] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_$
Aug 22 13:23:57 debian kernel: [ 7559.270509] brasero[4740]: segfault at 14 ip 080bb4ce sp bf8fcf00 error 6 in brasero[8048000+c9000]

I appreciate every advise for solution of this problem.
Thanks

---

### Post by charlesedwardkelley on 2009-08-22
Have you tried other software like K3B or GnomeBaker? I had problems with Brasero as well, but K3B works great!

---

### Post by polo23 on 2009-08-23
Yes I tried Gnomebaker and K3b but result was the same.(The same messages in log files).

---

