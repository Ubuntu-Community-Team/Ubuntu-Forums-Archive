---
title: "USB SATA HP-UNIX HD --&gt;&gt; lsusb SEES it. fdisk -l DOES NOT (?)"
date: 2013-08-29
forum: Hardware
---

### Post by tabcom on 2013-08-29
I'm trying to dd a SATA HP-UNIX HD. 
lsusb sees the drive info. However, fdisk -l does not.

Here is the command captures:

[SIZE=3]ubuntu@ubuntu:~$ **lsusb**
Bus 003  Device 002: ID 152d:2338 JMicron Technology Corp. / JMicron USA  Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 005 Device 002: ID 04ca:0022 Lite-On Technology Corp. 
Bus 005 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ 

[SIZE=3]ubuntu@ubuntu:~$ **sudo fdisk -l**

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x788e6628

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   125042687    62417920    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ [/SIZE][/SIZE]

---

### Post by squakie on 2013-08-29
post back the output of:

df -h

---

### Post by VMC on 2013-08-30
Also what version of Ubuntu, and output "*uname -r*"

---

### Post by tabcom on 2013-08-30
> **squakie said:**
> post back the output of:

df -h

ubuntu@ubuntu:~$ **df -h **
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.9G  115M  1.8G   6% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           385M  1.1M  384M   1% /run
/dev/sr0        785M  785M     0 100% /cdrom
/dev/loop0      738M  738M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           1.9G  940K  1.9G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            1.9G  148K  1.9G   1% /run/shm
none            100M   28K  100M   1% /run/user
ubuntu@ubuntu:~$

---

### Post by tabcom on 2013-08-30
> **VMC said:**
> Also what version of Ubuntu, and output "*uname -r*"

13.04 running off of boot disk.

ubuntu@ubuntu:~$ **uname -r**
3.8.0-19-generic

---

### Post by VMC on 2013-08-30
There's been issues with usb devices, both usb2 and usb3. Separate issues. Looks like you have usb2.

Here's something to try. unplug the usb device then, do this: ```
tail -f /var/log/syslog
``` from a terminal,  and note the outputs. If the device doesn't get mounted paste the results back here.

edit: after you start monitoring *syslog*, then plug the device back into a usb port.

---

### Post by tabcom on 2013-08-30
> **VMC said:**
> There's been issues with usb devices, both usb2 and usb3. Separate issues. Looks like you have usb2.

Here's something to try. unplug the usb device then, do this: ```
tail -f /var/log/syslog
``` from a terminal,  and note the outputs. If the device doesn't get mounted paste the results back here.

edit: after you start monitoring *syslog*, then plug the device back into a usb port.

ubuntu@ubuntu:~$ **tail -f /var/log/syslog**
Aug 30 13:04:33 ubuntu ntfs-3g[6685]: Cmdline options: rw,nosuid,nodev,uhelper=udisks2,uid=999,gid=999,dmask=0077,fmask=0177
Aug 30 13:04:33 ubuntu ntfs-3g[6685]: Mount options: rw,nosuid,nodev,uhelper=udisks2,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdc1,blkdev,blksize=4096
Aug 30 13:04:33 ubuntu ntfs-3g[6685]: Global ownership and permissions enforced, configuration type 7
Aug 30 13:04:34 ubuntu kernel: [59807.459069] usb 1-5: USB disconnect, device number 3
Aug 30 13:04:34 ubuntu udisksd[5403]: Cleaning up mount point /media/ubuntu/&#26032;&#21152;&#21367; (device 8:33 no longer exist)
Aug 30 13:04:34 ubuntu ntfs-3g[6685]: Unmounting /dev/sdc1 (&#26032;&#21152;&#21367;)
Aug 30 13:17:01 ubuntu CRON[6714]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 14:17:01 ubuntu CRON[6742]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 15:17:01 ubuntu CRON[6767]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 30 15:30:15 ubuntu kernel: [68537.244361] usb 3-2: USB disconnect, device number 2

---

### Post by VMC on 2013-08-30
I'm unsure what's happening, but I see disconnect instead of connect. Did you keep it unplugged before you monitored, then plug it in?

Here's what it should resemble : ```
Aug 30 09:10:43 0823 kernel: [ 7306.200292] usb 1-3: new high-speed USB device number 5 using ehci-pciAug 30 09:10:43 0823 kernel: [ 7306.347169] usb 1-3: New USB device found, idVendor=0bc2, idProduct=2100
Aug 30 09:10:43 0823 kernel: [ 7306.347181] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug 30 09:10:43 0823 kernel: [ 7306.347189] usb 1-3: Product: FreeAgent Go
Aug 30 09:10:43 0823 kernel: [ 7306.347195] usb 1-3: Manufacturer: Seagate
Aug 30 09:10:43 0823 kernel: [ 7306.347200] usb 1-3: SerialNumber: 2GE50F5O
Aug 30 09:10:43 0823 kernel: [ 7306.352548] usb-storage 1-3:1.0: USB Mass Storage device detected
Aug 30 09:10:43 0823 kernel: [ 7306.352830] scsi6 : usb-storage 1-3:1.0
Aug 30 09:10:43 0823 mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3"
Aug 30 09:10:43 0823 mtp-probe: bus: 1, device: 5 was not an MTP device
Aug 30 09:10:44 0823 kernel: [ 7307.356147] scsi 6:0:0:0: Direct-Access     Seagate  FreeAgent Go     102C PQ: 0 ANSI: 4
Aug 30 09:10:44 0823 kernel: [ 7307.356820] sd 6:0:0:0: Attached scsi generic sg3 type 0
Aug 30 09:10:44 0823 kernel: [ 7307.363304] sd 6:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Aug 30 09:10:44 0823 kernel: [ 7307.364585] sd 6:0:0:0: [sdd] Write Protect is off
Aug 30 09:10:44 0823 kernel: [ 7307.364600] sd 6:0:0:0: [sdd] Mode Sense: 1c 00 00 00
Aug 30 09:10:44 0823 kernel: [ 7307.365963] sd 6:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 30 09:10:44 0823 kernel: [ 7307.400881]  sdd: sdd1
Aug 30 09:10:44 0823 kernel: [ 7307.407035] sd 6:0:0:0: [sdd] Attached SCSI disk
Aug 30 09:10:45 0823 ntfs-3g[3704]: Version 2012.1.15AR.1 external FUSE 28
Aug 30 09:10:45 0823 ntfs-3g[3704]: Mounted /dev/sdd1 (Read-Write, label "usbNTFS", NTFS 3.1)
Aug 30 09:10:45 0823 ntfs-3g[3704]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Aug 30 09:10:45 0823 ntfs-3g[3704]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdd1,blkdev,blksize=4096
Aug 30 09:10:45 0823 ntfs-3g[3704]: Global ownership and permissions enforced, configuration type 7
```

---

### Post by tabcom on 2013-08-30
Disregard the previous post. I'll retry now.

---

### Post by tabcom on 2013-08-30
I rebooted. Ran the command:

ubuntu@ubuntu:~$ tail -f /var/log/syslog
Aug 30 17:46:54 ubuntu rtkit-daemon[3402]: Successfully made thread 5341 of process 5339 (n/a) owned by '999' RT at priority 5.
Aug 30 17:46:54 ubuntu rtkit-daemon[3402]: Supervising 5 threads of 2 processes of 1 users.
Aug 30 17:46:54 ubuntu rtkit-daemon[3402]: Successfully made thread 5342 of process 5339 (n/a) owned by '999' RT at priority 5.
Aug 30 17:46:54 ubuntu rtkit-daemon[3402]: Supervising 6 threads of 2 processes of 1 users.
Aug 30 17:46:54 ubuntu colord: Device added: xrandr-Sony-SDM-HS75P-6301445
Aug 30 17:46:55 ubuntu colord: Profile added: icc-6e21d1e491410c8cbd744769673bff25
Aug 30 17:46:56 ubuntu dbus[1288]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Aug 30 17:46:56 ubuntu udisksd[5376]: udisks daemon version 2.1.0 starting
Aug 30 17:46:57 ubuntu dbus[1288]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Aug 30 17:46:57 ubuntu udisksd[5376]: Acquired the name org.freedesktop.UDisks2 on the system message bus

---

### Post by tabcom on 2013-08-30
I turned on the usb drive, ran the command again.

ubuntu@ubuntu:~$ tail -f /var/log/syslog
Aug 30 17:54:00 ubuntu kernel: [  596.591235] Read(10): 28 00 00 00 00 00 00 00 08 00
Aug 30 17:54:00 ubuntu kernel: [  596.593589] sd 6:0:0:0: [sdb] Unhandled sense code
Aug 30 17:54:00 ubuntu kernel: [  596.593597] sd 6:0:0:0: [sdb]  
Aug 30 17:54:00 ubuntu kernel: [  596.593601] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 30 17:54:00 ubuntu kernel: [  596.593606] sd 6:0:0:0: [sdb]  
Aug 30 17:54:00 ubuntu kernel: [  596.593610] Sense Key : Medium Error [current] 
Aug 30 17:54:00 ubuntu kernel: [  596.593617] sd 6:0:0:0: [sdb]  
Aug 30 17:54:00 ubuntu kernel: [  596.593621] Add. Sense: Unrecovered read error
Aug 30 17:54:00 ubuntu kernel: [  596.593626] sd 6:0:0:0: [sdb] CDB: 
Aug 30 17:54:00 ubuntu kernel: [  596.593629] Read(10): 28 00 00 00 00 00 00 00 08 00

---

### Post by tabcom on 2013-08-30
When I plug in a IDE USB Drive and run the command, I get this:

ubuntu@ubuntu:~$  tail -f /var/log/syslog
Aug 30 17:59:51 ubuntu kernel: [  946.473216]  sdb: sdb4
Aug 30 17:59:51 ubuntu kernel: [  946.473229] sdb: p4 size 273219584 extends beyond EOD, truncated
Aug 30 17:59:51 ubuntu kernel: [  946.477262] sd 7:0:0:0: [sdb] No Caching mode page present
Aug 30 17:59:51 ubuntu kernel: [  946.477273] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Aug 30 17:59:51 ubuntu kernel: [  946.477280] sd 7:0:0:0: [sdb] Attached SCSI disk
Aug 30 17:59:51 ubuntu kernel: [  946.602345] usb 1-5: reset high-speed USB device number 2 using ehci-pci
Aug 30 17:59:51 ubuntu ata_id[6092]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Aug 30 17:59:53 ubuntu udisksd[5376]: Mounted /dev/sdb4 at /media/ubuntu/103F-0000 on behalf of uid 999
Aug 30 17:59:57 ubuntu dbus[1288]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Aug 30 17:59:57 ubuntu dbus[1288]: [system] Successfully activated service 'org.freedesktop.hostname1'

---

### Post by tabcom on 2013-08-30
Do you think the older version of 3.8.0-19-generic is the issue?

---

### Post by VMC on 2013-08-30
Maybe, not sure on your issue. Saucy has an updated kernel that works, or you can install a newer kernel to see if that works. I have no issues on using any of the Saucy ISOs, and on Ubuntu 12.04 I installed kernel 3.11.0-999-generic.

---

### Post by tabcom on 2013-08-30
tabcom@tabcom-LINUX:~$ uname -r
3.10.9-031009-generic


fdisk -l still does not recognize the HP-UNIX SATA external USB drive. :confused:

---

### Post by VMC on 2013-08-30
I'm not sure about  [COLOR=#000000]3.10.9-031009-generic[/COLOR] I tried several unit I found [COLOR=#000000]3.11.0-999-generic[/COLOR]. By the way, the fix I'm referring to is fixed on stable 3.10.7 kernel. These are intermediates , and some have the fix, others don't. [COLOR=#000000][/COLOR]

---

### Post by tabcom on 2013-09-01
Loaded the 3.10.7 kernel. Regretfully, same results. :mad:

---

### Post by tabcom on 2013-09-01
When I try booting from the HP-UNIX disk, message reads, "Hard Disk is protected by a password. Enter the password or press <ESC> to exit. (Disk remains locked if <ESC> is used)."

---

### Post by tabcom on 2013-09-23
~~bump~~

---

### Post by VMC on 2013-09-23
> **tabcom said:**
> When I try booting from the HP-UNIX disk, message reads, "Hard Disk is protected by a password. Enter the password or press <ESC> to exit. (Disk remains locked if <ESC> is used)."
It looks like the disk is encrypted. What is a history of that usb  SATA HP disk?  Is it one that you found or someone gave you. Your going to need that password to unencrypt it.

---

### Post by tabcom on 2013-09-23
The disk is a designjet printer disk. The printer uses the HP-UNIX OS to manage print jobs.

---

