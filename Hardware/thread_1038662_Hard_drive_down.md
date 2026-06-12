---
title: "Hard drive down?"
date: 2009-01-13
forum: Hardware
---

### Post by Seth Kriticos on 2009-01-13
Hello there,

I have an Ubuntu Intrepid setup with 2 HDD's (SATA) bound in software RAID1. Now I get a bunch of error messages and I'm not sure what they are about:

```

sudo cat /var/log/messages

(...)

Jan 13 20:28:41 styx kernel: [15912.492043] ata8: hard resetting link
Jan 13 20:28:41 styx kernel: [15912.968031] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 13 20:28:41 styx kernel: [15913.072131] ata8.00: configured for UDMA/25
Jan 13 20:28:41 styx kernel: [15913.072144] ata8: EH complete
Jan 13 20:29:22 styx kernel: [15953.496024] ata8.00: limiting speed to PIO4
Jan 13 20:29:22 styx kernel: [15953.496044] ata8: hard resetting link
Jan 13 20:29:22 styx kernel: [15953.972031] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 13 20:29:22 styx kernel: [15954.060132] ata8.00: configured for PIO4
Jan 13 20:29:22 styx kernel: [15954.060146] ata8: EH complete
Jan 13 20:29:48 styx kernel: [15979.496037] ata8: hard resetting link
Jan 13 20:29:48 styx kernel: [15979.972029] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 13 20:29:48 styx kernel: [15980.076130] ata8.00: configured for PIO4
Jan 13 20:29:48 styx kernel: [15980.076144] ata8: EH complete
Jan 13 20:30:05 styx kernel: [15996.500023] ata8.00: limiting speed to PIO3
Jan 13 20:30:05 styx kernel: [15996.500042] ata8: hard resetting link
Jan 13 20:30:05 styx kernel: [15996.976029] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 13 20:30:05 styx kernel: [15997.080141] ata8.00: configured for PIO3
Jan 13 20:30:05 styx kernel: [15997.080154] ata8: EH complete
Jan 13 20:31:56 styx kernel: [16107.500274] sr 7:0:0:0: ioctl_internal_command return code = 8000002
Jan 13 20:31:56 styx kernel: [16107.500277]    : Sense Key : Hardware Error [current] 
Jan 13 20:31:56 styx kernel: [16107.500280]    : Add. Sense: Unreachable copy target
Jan 13 20:31:58 styx kernel: [16109.499626] sr 7:0:0:0: ioctl_internal_command return code = 8000002
Jan 13 20:31:58 styx kernel: [16109.499629]    : Sense Key : Hardware Error [current] 
Jan 13 20:31:58 styx kernel: [16109.499632]    : Add. Sense: Unreachable copy target
Jan 13 20:32:02 styx kernel: [16113.500739] sr 7:0:0:0: ioctl_internal_command return code = 8000002
Jan 13 20:32:02 styx kernel: [16113.500742]    : Sense Key : Hardware Error [current] 
Jan 13 20:32:02 styx kernel: [16113.500744]    : Add. Sense: Unreachable copy target
Jan 13 20:32:38 styx kernel: [16149.502766] sr 7:0:0:0: ioctl_internal_command return code = 8000002
Jan 13 20:32:38 styx kernel: [16149.502769]    : Sense Key : Hardware Error [current] 
Jan 13 20:32:38 styx kernel: [16149.502772]    : Add. Sense: Unreachable copy target
```

I find it strange, because the /proc/mdstat file says both my drives are up and running:

```

% cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0] sdb1[1]
      488383936 blocks [2/2] [UU]
      
unused devices: <none>
```

Any ideas?

---

### Post by Seth Kriticos on 2009-01-14
2/3

This seriously bugs me. Any ideas anyone. Come on!

---

### Post by Seth Kriticos on 2009-01-14
Here is some additional output for the RAID array, also says that it is ok:

> % sudo mdadm --detail /dev/md0 
[sudo] password for seth: 
/dev/md0:
        Version : 00.90
  Creation Time : Sun Nov 16 16:07:01 2008
     Raid Level : raid1
     Array Size : 488383936 (465.76 GiB 500.11 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jan 14 20:01:54 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 87527d8a:2578de8a:7bbac5c6:54b08526
         Events : 0.25

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

---

### Post by Seth Kriticos on 2009-01-14
Hm, the dmesg errors are a bit more descriptive:

> [27750.473983] ata8.00: exception Emask 0x0 SAct 0x0 SErr 0x1c00000 action 0x0
[27750.473987] ata8: SError: { Handshk LinkSeq TrStaTrns }
[27750.473991] ata8.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[27750.473992]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[27750.473992]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[27750.473994] ata8.00: status: { DRDY ERR }

Now [http://ata.wiki.kernel.org/index.php/Libata_error_messages#ATA_status_expansion]("http://ata.wiki.kernel.org/index.php/Libata_error_messages#ATA_status_expansion") is telling me, that the SError bits mean:

* Handshk	R_ERR handshake response received in response to frame transmission 
* LinkSeq	Link state machine error occurred 
* TrStaTrns	Transport layer state transition error occurred 

Now I'm not *that* good, that I could understand this. Can anybody translate what this exactly means and if it should worry me? Please!

---

### Post by Seth Kriticos on 2009-01-14
Ok, I'm impatient, so I answer my own question. I did Google for a while and came up with this explanation:

Either my SATA cables have problems (one may be broken) or my power supply is not adequate / deffective. Both may be possible, since I just about a month ago have built this system.

Anyway, I also found the explanation for the error bits of the sata system. Here it comes:
> 
> 0x400000 = "Handshake error: When set to one, this bit indicates that one or
> more R_ERR handshake response was received in response to frame transmission.
> Such errors may be the result of a CRC error detected by the recipient, a
> disparity or 10b/8b decoding error, or other error condition leading to a
> negative handshake on a transmitted frame."
>
> 0x1800000 = "Link Sequence Error: When set to one, this bit indicates that one
> or more Link state machine error conditions was encountered since the last
> time this bit was cleared. The Link Layer state machine defines the conditions
> under which the link layer detects an erroneous transition."
>
> and
>
> "Transport state transition error: When set to one, this bit indicates that an
> error has occurred in the transition from one state to another within the
> Transport layer since the last time this bit was cleared."

Thanks for nice conversation.

---

