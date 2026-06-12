---
title: "Mounting a firewire dvd writer"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by boeman on 2006-07-14
Hi,

When trying to mount a firewire dvd writer, I get this in the syslog:

Jul 14 09:38:33 localhost kernel: [17179739.520000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00d04b00052440d3]
Jul 14 09:38:33 localhost kernel: [17179739.520000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Jul 14 09:38:33 localhost kernel: [17179739.520000] scsi4 : SCSI emulation for IEEE-1394 SBP-2 Devices
Jul 14 09:38:34 localhost kernel: [17179740.628000] ieee1394: sbp2: Logged into SBP-2 device
Jul 14 09:38:34 localhost kernel: [17179740.628000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Jul 14 09:38:34 localhost kernel: [17179740.628000] ieee1394: sbp2: scsi_add_device failed (-19)
Jul 14 09:38:34 localhost kernel: [17179740.628000] scsi5 : SCSI emulation for IEEE-1394 SBP-2 Devices
Jul 14 09:38:35 localhost kernel: [17179741.736000] ieee1394: sbp2: Logged into SBP-2 device
Jul 14 09:38:35 localhost kernel: [17179741.736000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Jul 14 09:38:35 localhost kernel: [17179741.740000] ieee1394: sbp2: scsi_add_device failed (-19)


Mounting a harddrive in that same case works without a problem. 
The writer is a plextor px-712a.

---

### Post by dangermouse28 on 2006-07-14
The obvious difference is that there isn't a disk there until you pop one in. What happens when you put a dvd in (not a blank one!)?

---

### Post by boeman on 2006-07-14
I get this when mounting it with a non-empty disc inserted:
Jul 14 16:10:50 localhost kernel: [17203274.776000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00d04b00052440d3]Jul 14 16:10:50 localhost kernel: [17203274.776000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Jul 14 16:10:50 localhost kernel: [17203274.776000] scsi6 : SCSI emulation for IEEE-1394 SBP-2 Devices
Jul 14 16:10:51 localhost kernel: [17203275.884000] ieee1394: sbp2: Logged into SBP-2 device
Jul 14 16:10:51 localhost kernel: [17203275.884000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Jul 14 16:10:51 localhost kernel: [17203275.888000] ieee1394: sbp2: scsi_add_device failed (-19)

So basicly the same... Mounting it with a non-empty disc doesn't make sense anyway, what if I want to write to an empty dvd?

---

### Post by boeman on 2006-07-14
I tried to mount a hard drive again, but this time, it also failed, with the same message in syslog as for the writer.
The writer is detected fine when it is hooked onto a USB external casing.

---

### Post by wall0159 on 2006-07-17
I have a similar problem. My firewire port works fine for my iPod, in fact I can daisy-chain my ipod through my non-functioning FW DVD-RW without problems (weird).

This drive has been functional in the past (both for reading and writing) although I have a feeling it needed to be switched on at boot time - I'm not quite sure when it stopped working. It *might* have been the upgrade to Dapper Drake.

My dmesg:
command: Test Unit Ready: 00 00 00 00 00 00
[17180300.328000] ieee1394: sbp2: reset requested
[17180300.328000] ieee1394: sbp2: Generating sbp2 fetch agent reset
[17180320.332000] ieee1394: sbp2: aborting sbp2 command
[17180320.332000]  2:0:0:0:
[17180320.332000]         command: Test Unit Ready: 00 00 00 00 00 00
[17180320.332000]  2:0:0:0: scsi: Device offlined - not ready after error recovery
[17180320.332000] ieee1394: sbp2: scsi_add_device failed (-19)

This drive works on my iBook, too.

It's possible I'll forget to check back here - if you need more info, write to me at domain: "flinders [dot] edu.au" username: "angus [dot] wallace"

Cheers
-Gus

---

### Post by wall0159 on 2006-07-18
For what it's worth, I upgraded the kernel today, and it seems to be closer to working, but it still doesn't..

$ uname -a
Linux Desktop 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux

$ dmesg
[17180339.196000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0050770500005005]
[17180339.196000] scsi4 : SCSI emulation for IEEE-1394 SBP-2 Devices
[17180340.304000] ieee1394: sbp2: Logged into SBP-2 device
[17180340.304000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[17180345.804000] ieee1394: sbp2: aborting sbp2 command
[17180345.804000]  4:0:0:0:
[17180345.804000]         command: Inquiry: 12 00 00 00 24 00
[17180355.804000] ieee1394: sbp2: aborting sbp2 command
[17180355.804000]  4:0:0:0:
[17180355.804000]         command: Test Unit Ready: 00 00 00 00 00 00
[17180355.804000] ieee1394: sbp2: reset requested
[17180355.804000] ieee1394: sbp2: Generating sbp2 fetch agent reset
[17180365.804000] ieee1394: sbp2: aborting sbp2 command
[17180365.804000]  4:0:0:0:
[17180365.804000]         command: Test Unit Ready: 00 00 00 00 00 00
[17180365.804000] ieee1394: sbp2: reset requested
[17180365.804000] ieee1394: sbp2: Generating sbp2 fetch agent reset
[17180385.808000] ieee1394: sbp2: aborting sbp2 command
[17180385.808000]  4:0:0:0:
[17180385.808000]         command: Test Unit Ready: 00 00 00 00 00 00
[17180385.808000] ieee1394: sbp2: reset requested
[17180385.808000] ieee1394: sbp2: Generating sbp2 fetch agent reset
[17180405.812000] ieee1394: sbp2: aborting sbp2 command
[17180405.812000]  4:0:0:0:
[17180405.812000]         command: Test Unit Ready: 00 00 00 00 00 00
[17180405.812000]  4:0:0:0: scsi: Device offlined - not ready after error recovery
[17180405.812000] ieee1394: sbp2: scsi_add_device failed (-19)

during this, the DVD spins up and down, as if it's 'trying' to mount...

---

### Post by AnthoMacP on 2006-07-19
I'm also having the same issue with my firewire external, and it's quite annoying because it has all my media and work data on it and I get relatively the same error message with it finally failing (-19) at the end as well.

---

