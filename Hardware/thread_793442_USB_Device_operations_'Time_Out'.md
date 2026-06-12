---
title: "USB Device operations 'Time Out'"
date: 2008-05-13
forum: Hardware
---

### Post by TheForkOfJustice on 2008-05-13
I recently ran into a filesystem crash on my USB drive.  I am currently trying to recover some important files that were on there using instructions I found here: [http://www.linuxjournal.com/article/8366](http://www.linuxjournal.com/article/8366)

However, I have a problem.

I found that when I run 

```
dd if=/dev/sda of=/tmp/r1 bs=512
```

as the instructions say, I only get 14.3 GB copied before it all stops.  Earlier I tried using fsck and it also stopped running after a period of time and would not continue until I rebooted.

I believe there is some kind of time-out setting that is interrupting halting my commands and therefore, recovery.

I am using a Maxtor OneTouch External USB.  If it is any help, I entered the command

```
tail -f /var/log/messages
```

and turned the device on and got this output:

```

usb 5-6: new high speed USB device using ehci_hcd and address 5
usb 5-6: configuration #1 chosen from 1 choice
scsi3 : SCSI emulation for USB Mass Storage devices
scsi 3:0:0:0: Direct-Access     Maxtor   OneTouch         0201 PQ: 0 ANSI: 0 CCS
sd 3:0:0:0: [sde] 160084992 512-byte hardware sectors (81964 MB)
sd 3:0:0:0: [sde] Write Protect is off
sd 3:0:0:0: [sde] 160084992 512-byte hardware sectors (81964 MB)
sd 3:0:0:0: [sde] Write Protect is off
 sde: sde1 sde2
sd 3:0:0:0: [sde] Attached SCSI disk
sd 3:0:0:0: Attached scsi generic sg4 type 0
sd 3:0:0:0: [sde] Sense Key : No Sense [current] 
sd 3:0:0:0: [sde] Add. Sense: No additional sense information
sd 3:0:0:0: [sde] Sense Key : No Sense [current] 
sd 3:0:0:0: [sde] Add. Sense: No additional sense information
sd 3:0:0:0: [sde] Sense Key : No Sense [current] 
sd 3:0:0:0: [sde] Add. Sense: No additional sense information
sd 3:0:0:0: [sde] Sense Key : No Sense [current] 
sd 3:0:0:0: [sde] Add. Sense: No additional sense information
sd 3:0:0:0: [sde] Sense Key : No Sense [current] 
sd 3:0:0:0: [sde] Add. Sense: No additional sense information
sd 3:0:0:0: [sde] Sense Key : No Sense [current] 
sd 3:0:0:0: [sde] Add. Sense: No additional sense information

```


Can anyone provide some insight?

---

