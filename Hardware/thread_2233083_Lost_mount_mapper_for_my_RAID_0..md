---
title: "Lost mount mapper for my RAID 0."
date: 2014-07-06
forum: Hardware
---

### Post by arash5 on 2014-07-06
Hi,

I have an ubuntu machine on a SSD and two HDDs on a RAID-0 for storage. For some reason my RAID-0 does not mount after a premature restart and I can not access my data. Here is the error that I get:

Error mounting /dev/dm-2 at /media/valuedc/lin: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-2" "/media/valuedc/lin"' exited with non-zero exit status 32: mount: special device /dev/mapper/ddf1_4c53492020202020100000791000928247114711f8b848e4p2 does not exist (udisks-error-quark, 0)

Please let me know if there is any way to access my data. Thanks!

---

### Post by steeldriver on 2014-07-07
Can you open a terminal and provide the output of the following command please

```

sudo blkid -c /dev/null

```

---

### Post by arash5 on 2014-07-07
Here is the output of the above command:

/dev/sda1: UUID="891fb210-53b3-4424-a811-9303f25bb3a9" TYPE="ext4" 
/dev/sda5: UUID="222feadf-1dd6-4344-927f-25c25b1d4d6a" TYPE="swap"

---

### Post by steeldriver on 2014-07-07
OK so it looks like it is not even seeing the HDDs - nevermind the array. If you have parted on your system, then see if

```

sudo parted -l

```
shows anything in addition to /dev/sda1 and /dev/sda5 - if you don't have parted, then try fdisk
```

sudo fdisk -l

```

---

### Post by arash5 on 2014-07-07
Here is the output of parted:

Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  181GB  181GB   primary   ext4            boot
 2      181GB   250GB  68.7GB  extended
 5      181GB   250GB  68.7GB  logical   linux-swap(v1)




Error: /dev/sdh: unrecognised disk label

---

### Post by arash5 on 2014-07-07
And fdisk has a similar output:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d5851


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   354303999   177150976   83  Linux
/dev/sda2       354306046   488396799    67045377    5  Extended
/dev/sda5       354306048   488396799    67045376   82  Linux swap / Solaris


Disk /dev/sdh: 4000.6 GB, 4000627818496 bytes
255 heads, 63 sectors/track, 486381 cylinders, total 7813726208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdh doesn't contain a valid partition table

---

### Post by steeldriver on 2014-07-07
What kind of array was it? md (softraid) or dmraid (fakeraid)? is the mdadm package currently installed?

---

### Post by arash5 on 2014-07-07
I do not know the difference between these two RAIDs. 
I have a RAID card and it has a setup that shows up whenever I boot the system (BIOS type setup page). I do not get any errors on that page and it confirms that the RAID is configured. I do know if this description helps you find out what type of RAID I am suing.
mdadm is installed. Please let me know if you need me to check something and thank you very much for your quick respond.

---

### Post by steeldriver on 2014-07-07
If it's managed at the BIOS level then it sounds like either true (hardware) RAID or fakeraid - and based on the fact that it was previously managed by the device mapper I would assume that means fakeraid - so is the **dmraid **package installed?

I only have experience with mdadm softraid unfortunately but there are a couple of VERY knowledgeable RAID gurus we may be able to summon

---

### Post by arash5 on 2014-07-07
Yes. Your description is accurate.
-----
about the dmraid: Yes it is installed;
dmraid version:		1.0.0.rc16 (2009.09.16) shared 
dmraid library version:	1.0.0.rc16 (2009.09.16)
device-mapper version:	unknown
-----
I really appreciate your help. Is there anyway we could invite those RAID specialists to this conversation? May be ping them :)
In the meantime is there anything you want me to check?

---

### Post by steeldriver on 2014-07-07
Bat signal sent! in the meantime, it might be worth checking dmesg and/or /var/log/syslog for error messages concerning the device (/dev/sdh?)

---

### Post by rubylaser on 2014-07-07
Hello, Steeldriver invited me here.  I'm very comfortable with almost all hardware and software RAID systems, but I would not consider myself a fakeraid expert (or guru). With that being said, I would suggest that you first see if dmraid can even see your devices.
```

sudo -i
dmraid -r

```

Please run that and report back.

---

### Post by arash5 on 2014-07-07
It does not find any RAIDs. Here is the output:

no raid disks

---

### Post by arash5 on 2014-07-07
@SteelDriver
here are the errors from dmesg:
[    5.828761] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    0.747195] ioapic: probe of 0000:00:05.4 failed with error -22

---

### Post by rubylaser on 2014-07-07
Okay, next let's try
```

dmraid -ay -vvv -d

```
If errors show up here, that probably indicates that other problems outside of dmraid exist with your disks.
If there are no errors, let's see if it can find the block devices.
```

dmraid -b

```

---

### Post by arash5 on 2014-07-07
Looks like while it is not detecting any RAIDs it is not reporting any errors. here is the output from the first command:
----------------------------------------
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sdc
NOTICE: skipping removable device /dev/sdd
NOTICE: skipping removable device /dev/sde
NOTICE: skipping removable device /dev/sdf
NOTICE: skipping removable device /dev/sdg
NOTICE: /dev/sdh: asr     discovering
NOTICE: /dev/sdh: ddf1    discovering
NOTICE: /dev/sdh: hpt37x  discovering
NOTICE: /dev/sdh: hpt45x  discovering
NOTICE: /dev/sdh: isw     discovering
DEBUG: not isw at 4000627817472
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 4000626735616
NOTICE: /dev/sdh: jmicron discovering
NOTICE: /dev/sdh: lsi     discovering
NOTICE: /dev/sdh: nvidia  discovering
NOTICE: /dev/sdh: pdc     discovering
NOTICE: /dev/sdh: sil     discovering
NOTICE: /dev/sdh: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
DEBUG: not isw at 250059348992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 250058267136
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
no raid disks
WARN: unlocking /var/lock/dmraid/.lock
----------------------------------------
The output of the second command:
/dev/sdh:   7813726208 total, ""
/dev/sda:    488397168 total, "S1DBNEAD853421L"

---

### Post by arash5 on 2014-07-07
BTW I found these errors in the syslog:
Jul  7 09:08:28 AVA-408440-2 kernel: [    1.024181] ioapic: probe of 0000:00:05.4 failed with error -22
Jul  7 09:08:28 AVA-408440-2 kernel: [    8.113167] sas: ata11: end_device-0:0: dev error handler
Jul  7 09:08:28 AVA-408440-2 kernel: [    8.284817] sas: ata11: end_device-0:0: dev error handler
Jul  7 09:08:28 AVA-408440-2 kernel: [    8.284819] sas: ata12: end_device-0:1: dev error handler
Jul  7 09:08:28 AVA-408440-2 kernel: [   11.059338] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

Jul  7 09:08:28 AVA-408440-2 kernel: [   11.876316] sas: ata12: end_device-0:1: cmd error handler
Jul  7 09:08:28 AVA-408440-2 kernel: [   11.876318] sas: ata11: end_device-0:0: cmd error handler
Jul  7 09:08:28 AVA-408440-2 kernel: [   11.876335] sas: ata11: end_device-0:0: dev error handler
Jul  7 09:08:28 AVA-408440-2 kernel: [   11.876348] sas: ata12: end_device-0:1: dev error handler

Jul  7 09:08:28 AVA-408440-2 kernel: [   11.876892] sas: ata12: end_device-0:1: cmd error handler
Jul  7 09:08:28 AVA-408440-2 kernel: [   11.876894] sas: ata11: end_device-0:0: cmd error handler
Jul  7 09:08:28 AVA-408440-2 kernel: [   11.876902] sas: ata11: end_device-0:0: dev error handler
Jul  7 09:08:28 AVA-408440-2 kernel: [   11.876903] sas: ata12: end_device-0:1: dev error handler
[B]
Jul  7 09:08:28 AVA-408440-2 dmraid-activate: ERROR: Cannot retrieve RAID set information for ddf1_4c53492020202020100000791000928247114711f8b848e4

Jul  7 09:08:28 AVA-408440-2 dmraid-activate: ERROR: Cannot retrieve RAID set information for ddf1_4c53492020202020100000791000928247114711f8b848e4
[/B]
Jul  7 09:08:34 AVA-408440-2 NetworkManager[1471]: <error> [1404738514.790970] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no 
such nameJul  7 09:43:29 AVA-408440-2 kernel: [    0.751231] ioapic: probe of 0000:00:05.4 failed with error -22

Jul  7 09:43:29 AVA-408440-2 kernel: [    6.018871] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

---

### Post by rubylaser on 2014-07-07
Run the command "dmraid -rD". It should create three output files: ( .dat, .offset, .size ). Hopefully it will create those files for you.  If so, you will want to attach them here for dmraid experts to review (unfortunately, not me).

---

### Post by arash5 on 2014-07-07
Unfortunately it does not create any of the files (.dat,.offset,.size). The output says "no raid disks".

---

### Post by rubylaser on 2014-07-08
Well, I have just exhausted my very limited FakeRAID skills :)

---

### Post by steeldriver on 2014-07-08
Thanks for stepping up @rubylaser - you got us WAAAY further than I would have been able to

It sounds to me like either the BIOS/MB isn't correctly assembling/presenting the array to the OS (perhaps because of metadata corruption?), or some regression in dmraid that has caused it to lose support for the particular subsystem

---

