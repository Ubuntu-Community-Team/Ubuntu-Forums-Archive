---
title: "usb drive not mounting"
date: 2009-05-10
forum: Hardware
---

### Post by rainy-day on 2009-05-10
Hi, I have a 500mb usb flash drive that mounted once but then stopped mounting. When I plug it in, it keeps flashing and doing tail -f /var/log/messages shows these continuously appending messages:

May 10 11:29:01 ak-desktop kernel: [69319.372521] usb 2-1: new high speed USB device using ehci_hcd and address 23
May 10 11:29:01 ak-desktop kernel: [69320.048015] usb 2-1: new high speed USB device using ehci_hcd and address 26
May 10 11:29:02 ak-desktop kernel: [69320.348013] usb 2-1: new high speed USB device using ehci_hcd and address 27
May 10 11:29:03 ak-desktop kernel: [69321.400063] usb 2-1: new high speed USB device using ehci_hcd and address 32
May 10 11:29:04 ak-desktop kernel: [69322.640515] usb 2-1: new high speed USB device using ehci_hcd and address 38
May 10 11:29:04 ak-desktop kernel: [69323.316016] usb 2-1: new high speed USB device using ehci_hcd and address 41
May 10 11:29:05 ak-desktop kernel: [69323.616515] usb 2-1: new high speed USB device using ehci_hcd and address 42

They keep scrolling down at a rate about 3-4 lines a second.

Please help. I searched the forums and tried the solutions that worked for others but did not help me. I'm using ubuntu 9.04.

thanks!

---

### Post by rainy-day on 2009-05-10
Update: it did mount but only after 4-5 minutes!

Here's what it says in log/messages: (note that it's actually 128mb drive not 500mb as I said before):

May 10 11:37:10 ak-desktop kernel: [69808.785680] scsi8 : SCSI emulation for USB Mass Storage devices
May 10 11:37:15 ak-desktop kernel: [69813.788941] scsi 8:0:0:0: Direct-Access     ITE TECH  PEN DRIVE Flash 2.20 PQ: 0 ANSI: 2
May 10 11:37:15 ak-desktop kernel: [69813.806934] sd 8:0:0:0: [sdc] 255488 512-byte hardware sectors: (130 MB/124 MiB)
May 10 11:37:15 ak-desktop kernel: [69813.814393] sd 8:0:0:0: [sdc] Write Protect is off
May 10 11:37:15 ak-desktop kernel: [69813.825928] sd 8:0:0:0: [sdc] 255488 512-byte hardware sectors: (130 MB/124 MiB)
May 10 11:37:15 ak-desktop kernel: [69813.828945] sd 8:0:0:0: [sdc] Write Protect is off
May 10 11:37:15 ak-desktop kernel: [69813.828955]  sdc:
May 10 11:37:15 ak-desktop kernel: [69813.835030] sd 8:0:0:0: [sdc] Attached SCSI removable disk
May 10 11:37:15 ak-desktop kernel: [69813.835098] sd 8:0:0:0: Attached scsi generic sg3 type 0

---

### Post by ptsubin on 2009-05-10
Try making an entry in /etc/fstab for /dev/sdb or whatever the fdisk -l given name is. And after plugging,if it is not getting mounted automatically, try manually. USB storage devices may take longer to mount from my experience..

---

### Post by rainy-day on 2009-05-10
When I do fdisk -l, I get this:

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     3112544     7678583   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(3112543, 3, 9)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(7678582, 0, 39)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      674759     8418872   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(674758, 0, 23)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(8418871, 0, 12)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?     7479526    15223639   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(7479525, 4, 16)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(15223638, 3, 7)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?    11542725    11542947       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(11542724, 3, 3)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(11542946, 3, 1)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


This seems to be completely wrong, I just reformatted the drive from a winXP system and it should only have one partition marked vfat32.

---

### Post by rainy-day on 2009-05-10
Ok, I fixed this and if anyone else runs into this, here's what I did:

using fdisk -l I found that it normally mounts to /dev/sdc1 through 5

I created this entry in /etc/fstab:

/dev/sdc /media/disk vfat defaults,user,noauto,exec 0 0

I actually did not realize before that you can just point to /dev/sdc !

I also created /media/disk directory.

Now I can mount and unmount manually. On top of that, it now automounts successfully in about 5 seconds vs. ~5+ minutes previously!

Should I submit a bug report for this?

---

