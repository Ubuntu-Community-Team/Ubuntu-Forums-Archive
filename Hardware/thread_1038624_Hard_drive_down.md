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

