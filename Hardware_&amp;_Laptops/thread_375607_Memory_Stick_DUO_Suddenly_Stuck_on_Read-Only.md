---
title: "Memory Stick DUO Suddenly Stuck on Read-Only"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by ImmortalGrey on 2007-03-03
I've looked around already for help on this, but this just isn't making sense, and it's got me really frustrated...

I have a Sony Memory Stick Pro DUO, and I was copying files to it earlier and stuff, no problems at all..  Things worked great.

And then I was in the process of converting a file to be compatible with the PlayStation Portable, and when it finally completed, I popped in my memory stick to copy the file over... And I get a pop-up saying that I do not have permission to write to the folder.

... Alright, no worries, I tried chmod 777 and sudo chmod 700, neither did anything to change permissions, just kept coming back saying the memory stick was "read-only", which I don't know how it suddenly happened.

I've tried restarting, shutting down, then re-booting, nothing will give me access back.

I read one thread that said something about modifying my /etc/fstab file, but nothing they were doing seemed to work for me...

How do I get access back?

---

### Post by Repo on 2007-03-13
I have the same problem, started from last week. My other usb memory stick works now for read-only. My second memory stick(different model) works fine.

Here is part of mtab:

[COLOR="RoyalBlue"]/dev/sdb /media/usbdisk vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0[/COLOR]

and here is part of /var/log/messages:

[COLOR="RoyalBlue"]Mar 13 21:51:34 localhost kernel: [4296476.210000] usb 5-7: new high speed USB device using ehci_hcd and address 4
Mar 13 21:51:34 localhost kernel: [4296476.325000] scsi4 : SCSI emulation for USB Mass Storage devices
Mar 13 21:51:39 localhost kernel: [4296481.325000]   Vendor: USB 2.0   Model: Flash Disk        Rev: 2.00
Mar 13 21:51:39 localhost kernel: [4296481.325000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Mar 13 21:51:39 localhost kernel: [4296481.326000] SCSI device sdb: 1026559 512-byte hdwr sectors (526 MB)
Mar 13 21:51:39 localhost kernel: [4296481.327000] sdb: Write Protect is off
Mar 13 21:51:39 localhost kernel: [4296481.330000] SCSI device sdb: 1026559 512-byte hdwr sectors (526 MB)
Mar 13 21:51:39 localhost kernel: [4296481.331000] sdb: Write Protect is off
Mar 13 21:51:39 localhost kernel: [4296481.331000]  sdb: unknown partition table
Mar 13 21:51:39 localhost kernel: [4296481.334000] sd 4:0:0:0: Attached scsi removable disk sdb
Mar 13 21:51:39 localhost kernel: [4296481.334000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[/COLOR]

 Is the "Unknown partition table" the reason? maybe a update is behind this ?
The working model has no errors on mounting.

Everything has been working fine about 2 years :confused:

---

### Post by eidam655 on 2008-03-28
i have similar problem :(

when the card is mounted, the persmissions are fine. when i copy something over the command line with 'sudo cp /from/here/file /to/the/card/file' everything is just ok. when i accessany folder on the card with doubleclick and press Back, a Locked symbol is added to the icons, i can read files only and the cmd line copying isn't working anymore.

any suggestions?

thx in advance

EDIT: this is what dmesg says:

> [ 2157.832000] sd 4:0:0:0: [sdb] 960512 512-byte hardware sectors (492 MB)
[ 2157.832000] sd 4:0:0:0: [sdb] Write Protect is off
[ 2157.832000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2157.832000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2157.836000] sd 4:0:0:0: [sdb] 960512 512-byte hardware sectors (492 MB)
[ 2157.840000] sd 4:0:0:0: [sdb] Write Protect is off
[ 2157.840000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2157.840000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2157.840000]  sdb: sdb1
[ 2157.840000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 2157.840000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2276.700000] FAT: Filesystem panic (dev sdb1)
[ 2276.700000]     invalid access to FAT (entry 0x0000ff00)
[ 2276.700000]     File system has been set read-only
[ 2276.700000] attempt to access beyond end of device
[ 2276.700000] sdb1: rw=0, want=4178005, limit=958999
[ 2276.700000] FAT: Filesystem panic (dev sdb1)
[ 2276.700000]     invalid access to FAT (entry 0x0000ff00)
[ 2276.700000] FAT: Filesystem panic (dev sdb1)
[ 2276.700000]     invalid access to FAT (entry 0x0000ff00)
[ 2276.700000] FAT: Filesystem panic (dev sdb1)


---

