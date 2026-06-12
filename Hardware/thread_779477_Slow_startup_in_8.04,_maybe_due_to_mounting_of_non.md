---
title: "Slow startup in 8.04, maybe due to mounting of non-existent drive"
date: 2008-05-02
forum: Hardware
---

### Post by Tetyl on 2008-05-02
Since upgrading to 8.04 I've had much slower startups. It takes nearly a minute on the splash screen compared to less than 10 seconds before the upgrade.

By turning off the splash screen and inspecting what part of the the boot is taking so long, and then crawling through the syslog it appears that the problem is that Ubuntu creates a device /dev/sdc and tries to mount it. I only have 2 HDDs, sda and sdb, so there shouldn't be any sdc at all. Sure enough though, when I do lshw, I get this mysterious entry:

```

*-disk:2
    description: SCSI Disk
    physical id: 1
    bus info: scsi@5:0.0.0
    logical name: /dev/sdc
    size: 320KiB (327KB)
```

The relevant syslog entries include (the last 3 entries repeat for a while):

```
May  2 17:06:26 Jon-Ubuntu kernel: [   51.253156] sd 5:0:0:0: [sdc] 640 512-byte hardware sectors (0 MB)
May  2 17:06:26 Jon-Ubuntu kernel: [   51.253163] sd 5:0:0:0: [sdc] Write Protect is off
May  2 17:06:26 Jon-Ubuntu kernel: [   51.253165] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May  2 17:06:26 Jon-Ubuntu kernel: [   51.253176] sd 5:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
May  2 17:06:26 Jon-Ubuntu kernel: [   51.253202] sd 5:0:0:0: [sdc] 640 512-byte hardware sectors (0 MB)
May  2 17:06:26 Jon-Ubuntu kernel: [   51.253213] sd 5:0:0:0: [sdc] Write Protect is off
May  2 17:06:26 Jon-Ubuntu kernel: [   51.253215] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May  2 17:06:26 Jon-Ubuntu kernel: [   51.253226] sd 5:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
May  2 17:06:26 Jon-Ubuntu kernel: [   51.253228]  sdc:<3>ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
May  2 17:06:26 Jon-Ubuntu kernel: [   81.183284] ata6.00: cmd c4/00:08:00:00:00/00:00:00:00:00/e0 tag 0 pio 4096 in
May  2 17:06:26 Jon-Ubuntu kernel: [   81.183286]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
May  2 17:06:26 Jon-Ubuntu kernel: [   81.183289] ata6.00: status: { DRDY }
May  2 17:06:26 Jon-Ubuntu kernel: [   81.183298] ata6: soft resetting link
May  2 17:06:26 Jon-Ubuntu kernel: [   86.367712] ata6: port is slow to respond, please be patient (Status 0xd0)
May  2 17:06:26 Jon-Ubuntu kernel: [   91.173000] ata6: SRST failed (errno=-16)
May  2 17:06:26 Jon-Ubuntu kernel: [   91.173003] ata6: soft resetting link
May  2 17:06:26 Jon-Ubuntu kernel: [   96.358440] ata6: port is slow to respond, please be patient (Status 0xd0)
May  2 17:06:26 Jon-Ubuntu kernel: [  101.163729] ata6: SRST failed (errno=-16)
May  2 17:06:26 Jon-Ubuntu kernel: [  101.163732] ata6: soft resetting link
May  2 17:06:26 Jon-Ubuntu kernel: [  106.347174] ata6: port is slow to respond, please be patient (Status 0xd0)
May  2 17:06:26 Jon-Ubuntu kernel: [  136.128789] ata6: SRST failed (errno=-16)
May  2 17:06:26 Jon-Ubuntu kernel: [  136.128794] ata6: soft resetting link
May  2 17:06:26 Jon-Ubuntu kernel: [  141.145606] ata6: SRST failed (errno=-16)
May  2 17:06:26 Jon-Ubuntu kernel: [  141.145608] ata6: reset failed, giving up
May  2 17:06:26 Jon-Ubuntu kernel: [  141.145611] ata6.00: disabled
May  2 17:06:26 Jon-Ubuntu kernel: [  141.145622] ata6: EH complete
May  2 17:06:26 Jon-Ubuntu kernel: [  141.145634] sd 5:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
May  2 17:06:26 Jon-Ubuntu kernel: [  141.145638] end_request: I/O error, dev sdc, sector 0
May  2 17:06:26 Jon-Ubuntu kernel: [  141.145640] Buffer I/O error on device sdc, logical block 0
```

Any one have any ideas about how to get this behavior to stop? Maybe some way for Ubuntu just to ignore the device, or anything else that will help.

Thanks.

---

### Post by ajmorris on 2008-05-03
hi there,
this could be because linux thinks a flash disk or external device is still plugged in, or plugged in when you boot up? it could be because of a hotplug malfunction, or a few other reasons.
Just to start with, could you please post your /etc/fstab file

AJ

---

### Post by Tetyl on 2008-05-06
Thanks for your reply. Sorry I took so long to get this posted for you. Nothing in here looks suspicious to me.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=224cfdf0-c16c-414e-992e-cb142ae99160 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7460E99C60E964F8 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=46D2-4F03  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=4dc80cd6-a705-4e8a-bdd0-7b4eda9092ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by lvanderree on 2008-06-12
I've got the same issue,

I've got a Asus P5W (DH) motherboard and I suspect it has something to do with drives which are found but not plugged in too.

I tried it on another Asus P5W as well, and the live CD also has problems with it. Sometimes getting busybox and always the same errors as you described.

I guess it might have someting to do with the SATA-controller (you can have it in compatibility mode or enhanced mode and some other mode I can't recall.

---

### Post by EzeQL on 2008-07-26
> **lvanderree said:**
> I've got the same issue,

I've got a Asus P5W (DH) motherboard and I suspect it has something to do with drives which are found but not plugged in too.

I tried it on another Asus P5W as well, and the live CD also has problems with it. Sometimes getting busybox and always the same errors as you described.

I guess it might have someting to do with the SATA-controller (you can have it in compatibility mode or enhanced mode and some other mode I can't recall.

hi. I have the same motherboard and having the same problem.
i have one HD Sata , one HD IDE and One DVDRW SATA.
i cant install ubuntu on the IDE Drive . it throws this "ata srst error nr 16"

---

### Post by lvanderree on 2008-07-27
I've done a clean-install of Ubuntu 8.04 (32bit) and now boot times are back to normal. There clearly was something wrong after the upgrade, but I couldn't resolve what.

---

