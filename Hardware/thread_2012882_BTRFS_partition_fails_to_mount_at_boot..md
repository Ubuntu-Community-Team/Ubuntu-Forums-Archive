---
title: "BTRFS partition fails to mount at boot."
date: 2012-06-29
forum: Hardware
---

### Post by jtappin on 2012-06-29
I have an eSATA external drive as a backup system. I recently updgraded from a 1Tb drive with a normal MBR and an Ext4 filesystem to a 3Tb drive with a GPT partition table and btrfs filesystem.

Since then, on boot the system hangs during the boot process (no error messages or "press S to skip mount .." message). The only way I was able to boot was to power off the drive and the reboot.

However if I comment out the line in /etc/fstab, the system boots, and then after I restore the relevant line in fstab and enter "mount -a" the drive mounts successfully, but every half-hour or so the following message appears in /var/log/syslog:
```

Jun 29 21:11:13 xena kernel: [ 9036.800093] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jun 29 21:11:13 xena kernel: [ 9036.800106] ata3.00: failed command: IDENTIFY DEVICE
Jun 29 21:11:13 xena kernel: [ 9036.800121] ata3.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
Jun 29 21:11:13 xena kernel: [ 9036.800125]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Jun 29 21:11:13 xena kernel: [ 9036.800133] ata3.00: status: { DRDY }
Jun 29 21:11:13 xena kernel: [ 9036.800142] ata3: hard resetting link
Jun 29 21:11:14 xena kernel: [ 9037.292142] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 29 21:11:14 xena kernel: [ 9037.302567] ata3.00: configured for UDMA/133

```

I'm guessing that the boot issue moght be a module missing in the initrd, but I don't know which. The syslog message as far as I can track looks to be SMART-related but I don't see any recent fixes.

The system is a fully up-to-date Precise Kubuntu install.

Any ideas?

Thanks
 James

---

