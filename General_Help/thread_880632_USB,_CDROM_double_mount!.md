---
title: "USB, CDROM double mount!"
date: 2008-08-05
forum: General Help
---

### Post by tw1ggy.ramir3z on 2008-08-05
I've got an annoying problem with my Xubuntu Hardy 8.04. When I plug a pen-drive or I insert a CD/DVD, the system mount they twice. I formatted my pc and the bug was gone, but after few days the bug returned. Any suggestion?

P.S. Sorry for my bad English, I'm Italian.

---

### Post by lisati on 2008-08-05
I recall reading something in the forums a few days ago about a bug along these lines, but can't remember the details.....

Anyone else?

---

### Post by tw1ggy.ramir3z on 2008-08-05
Do you remember thread's title?

---

### Post by PGScooter on 2008-08-06
tw1ggy,

we are both using Xubuntu. That probably not a coincidence.

What packages did you install from the time when it was working well to when the bug occurred?

You and I must have done something! I didn't try to think at the time what it could have been, and now its too long ago for me to remember. I have just learned to live with the problem.

Also, I want to make sure that we do have the same problem.
"mount" actually refers to a filesystem being put into use through a folder (which you "mount" to). So when you say double mount, I think that means that your usb drive is showing up on /media/usb1 and /media/usb2 but I think you mean to say that when you mount (only once), two exact copies of windows show up. Is that correct?

---

### Post by Ape3000 on 2008-08-06
I'm having the same problem with Intrepid Alpha3..

EDIT:
When I try to unmount the first one, it will say:
> Unable to mount X
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found

When I try to remove the other one it will go as it should and the first is also unmounted..

---

### Post by geirha on 2008-08-06
The logfiles might contain some clues. Could you insert an USB storage device or a CD-rom, and the post a few lines from the end of /var/log/syslog? The log lines should be prepended with date and time, so post the lines which are written in the last minute or so.

---

### Post by tw1ggy.ramir3z on 2008-08-06
> **PGScooter said:**
> tw1ggy,

we are both using Xubuntu. That probably not a coincidence.

What packages did you install from the time when it was working well to when the bug occurred?

You and I must have done something! I didn't try to think at the time what it could have been, and now its too long ago for me to remember. I have just learned to live with the problem.

Also, I want to make sure that we do have the same problem.
"mount" actually refers to a filesystem being put into use through a folder (which you "mount" to). So when you say double mount, I think that means that your usb drive is showing up on /media/usb1 and /media/usb2 but I think you mean to say that when you mount (only once), two exact copies of windows show up. Is that correct?

Yes it is correct, the mount point is the same but I got two windows when I plug my pendrive. Unfortunately I cannot remember what I could do to make it happens...

---

### Post by tw1ggy.ramir3z on 2008-08-06
> **geirha said:**
> The logfiles might contain some clues. Could you insert an USB storage device or a CD-rom, and the post a few lines from the end of /var/log/syslog? The log lines should be prepended with date and time, so post the lines which are written in the last minute or so.

It's my syslog
```
Aug  6 23:49:41 the-pit kernel: [272869.600265] usb 3-5: new high speed USB device using ehci_hcd and address 9
Aug  6 23:49:41 the-pit kernel: [272869.926518] usb 3-5: configuration #1 chosen from 1 choice
Aug  6 23:49:41 the-pit kernel: [272869.927203] scsi7 : SCSI emulation for USB Mass Storage devices
Aug  6 23:49:41 the-pit kernel: [272869.927545] usb-storage: device found at 9
Aug  6 23:49:41 the-pit kernel: [272869.927549] usb-storage: waiting for device to settle before scanning
Aug  6 23:49:43 the-pit NetworkManager: <debug> [1218059383.146489] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_58f_6387_SQGZWLZM'). 
Aug  6 23:49:43 the-pit NetworkManager: <debug> [1218059383.279540] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_58f_6387_SQGZWLZM_if0'). 
Aug  6 23:49:46 the-pit kernel: [272874.920966] usb-storage: device scan complete
Aug  6 23:49:46 the-pit kernel: [272874.932767] scsi 7:0:0:0: Direct-Access     JetFlash TS1GJFV30        8.07 PQ: 0 ANSI: 2
Aug  6 23:49:46 the-pit kernel: [272874.945196] sd 7:0:0:0: [sdc] 1986560 512-byte hardware sectors (1017 MB)
Aug  6 23:49:46 the-pit kernel: [272874.946198] sd 7:0:0:0: [sdc] Write Protect is off
Aug  6 23:49:46 the-pit kernel: [272874.946208] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
Aug  6 23:49:46 the-pit kernel: [272874.946212] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Aug  6 23:49:46 the-pit kernel: [272874.949685] sd 7:0:0:0: [sdc] 1986560 512-byte hardware sectors (1017 MB)
Aug  6 23:49:46 the-pit kernel: [272874.950722] sd 7:0:0:0: [sdc] Write Protect is off
Aug  6 23:49:46 the-pit kernel: [272874.950732] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
Aug  6 23:49:46 the-pit kernel: [272874.950736] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Aug  6 23:49:46 the-pit kernel: [272874.950747]  sdc: sdc1
Aug  6 23:49:46 the-pit kernel: [272874.952075] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Aug  6 23:49:46 the-pit kernel: [272874.952146] sd 7:0:0:0: Attached scsi generic sg3 type 0
Aug  6 23:49:46 the-pit NetworkManager: <debug> [1218059386.634592] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_58f_6387_SQGZWLZM_if0_scsi_host'). 
Aug  6 23:49:46 the-pit NetworkManager: <debug> [1218059386.642520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_58f_6387_SQGZWLZM_if0_scsi_host_scsi_device_lun0'). 
Aug  6 23:49:46 the-pit NetworkManager: <debug> [1218059386.800639] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_58f_6387_SQGZWLZM_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug  6 23:49:47 the-pit NetworkManager: <debug> [1218059387.451983] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_JetFlash_TS1GJFV30_SQGZWLZM_0_0'). 
Aug  6 23:49:47 the-pit NetworkManager: <debug> [1218059387.672260] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4897_814E'). 
Aug  6 23:49:53 the-pit hald: mounted /dev/sdc1 on behalf of uid 1000
Aug  6 23:50:49 the-pit dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Aug  6 23:50:49 the-pit dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Aug  6 23:50:49 the-pit dhclient: bound to 192.168.1.2 -- renewal in 9025 seconds.
Aug  6 23:50:50 the-pit NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 

```

Can you understand anything?

---

### Post by chrisccoulson on 2008-08-06
> **Ape3000 said:**
> I'm having the same problem with Intrepid Alpha3..

EDIT:
When I try to unmount the first one, it will say:


When I try to remove the other one it will go as it should and the first is also unmounted..

This is [https://bugs.launchpad.net/gvfs/+bug/251991]("https://bugs.launchpad.net/gvfs/+bug/251991")

---

### Post by PGScooter on 2008-08-06
> **geirha said:**
> The logfiles might contain some clues. Could you insert an USB storage device or a CD-rom, and the post a few lines from the end of /var/log/syslog? The log lines should be prepended with date and time, so post the lines which are written in the last minute or so.

mine is as follows:

```

Aug  6 16:41:19 Yannick syslogd 1.5.0#1ubuntu1: restart.
Aug  6 16:41:19 Yannick anacron[5209]: Job `cron.daily' terminated
Aug  6 16:41:19 Yannick anacron[5209]: Normal exit (1 job run)
Aug  6 16:46:06 Yannick kernel: [  792.833666] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
Aug  6 16:46:06 Yannick hald: mounted /dev/sdb2 on behalf of uid 1000
Aug  6 16:48:21 Yannick hald: mounted /dev/sdb5 on behalf of uid 1000

```

---

### Post by tw1ggy.ramir3z on 2008-08-07
I can't believe that! Bug was gone! :confused: I don't know what I've done, I can only suppose last updates fix it all! :lolflag:

---

### Post by petr.simacek on 2008-09-17
Hi, 

I have all the official updates, and the problem persists. Is there a solution?

Thanks, Petr

---

### Post by PGScooter on 2008-09-18
I have not found a fix yet :(

---

### Post by petr.simacek on 2008-09-19
It is a very annoying, because it does not work burner, or DVD:rip and the like. Just everything, what works with cdrom. I don't want move to 8.10, while 8.04 is LTS. P.

---

### Post by MartijnNL on 2009-08-11
In case you're still having this problem (or for anyone else with this problem). It is probably the result of multiple active thunar processes. (I don't mean open thunar windows. Thunar is running even if you have no windows open.)

Try:

pgrep thunar

If you see more than one instance of thunar, kill all the extra ones using the system monitor or the 'kill' command. This should also work after a restart (did so for me anyway).

Regards,

Martijn

---

