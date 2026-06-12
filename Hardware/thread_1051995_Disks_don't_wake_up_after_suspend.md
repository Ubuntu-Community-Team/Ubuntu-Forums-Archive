---
title: "Disks don't wake up after suspend?"
date: 2009-01-27
forum: Hardware
---

### Post by _AndY on 2009-01-27
Hi there,
Having tried the default suspend function in Intrepid, I only got a black screen when resuming from the suspend to RAM.

I installed the hibernate package and now whenever I run hibernate-ram, all appears to work well. All fans and disks turn off, and afterwards I can resume and get back to my desktop very quickly.

However, after resuming, I get input/output errors when attempting to access my hard disk which I find strange because even if I suspend with firefox left open, I can still browse the Web after resuming.

It is almost as if the disks power down and then fail to power back up.

NOTE:
I am running Ubuntu Intrepid (amd64) installed on an mdadm raid device. This is just a RAID0 stripe over two identical SATA disks.

Thanks,
Andy

---

### Post by _AndY on 2009-01-29
Bump?

I've managed to log dmesg to a network share.

```
[  235.513068] sd 2:0:0:0: [sda] Starting disk
[  239.398648] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[  239.398649] ata4.00: revalidation failed (errno=-5)
[  239.466636] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[  239.466637] ata3.00: revalidation failed (errno=-5)
[  244.562643] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[  244.562645] ata4.00: revalidation failed (errno=-5)
[  244.562646] ata4.00: disabled
[  244.562656] ata4: soft resetting link
[  244.630636] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x3)
[  244.630637] ata3.00: revalidation failed (errno=-5)
[  244.630638] ata3.00: disabled
[  244.630644] ata3: soft resetting link
[  244.726443] ata4: EH complete
[  244.794445] ata3: EH complete
[  244.794464] sd 2:0:0:0: [sda] START_STOP FAILED
[  244.794465] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  244.794470] PM: Device 2:0:0:0 failed to resume: error 262144
[  244.794473] sd 3:0:0:0: [sdb] Starting disk
[  244.794485] sd 3:0:0:0: [sdb] START_STOP FAILED
[  244.794486] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  244.794488] PM: Device 3:0:0:0 failed to resume: error 262144
[  244.794928] PM: resume devices took 10.828 seconds
```

Might this be a driver problem?

Andy

---

### Post by alexei.colin on 2009-02-10
I have exactly the same problem in Intrepid 2.6.27-11-generic on Thinkpad T60. The error message printed repeatedly to the console is along the lines of:
end_request: i/o error on sda, sector 1123123
Only cycling power gets the system back into a working state. SMART (smartctl) finds no errors with the hard drive on either short or long tests.

I cannot reproduce the problem reliably, however. It at least once a day with frequent use, but did not happen when I did a sequence of about ~10 suspend/resumes in a row. 

Any help on this issue is appreciated!

---

### Post by DjNDB on 2009-02-12
> **alexei.colin said:**
> I cannot reproduce the problem reliably, however. It at least once a day with frequent use, but did not happen when I did a sequence of about ~10 suspend/resumes in a row.

Same here. The Error Message in /var/log messages is:
Feb 12 19:41:24 localhost kernel: [18943.540321] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK

However, I found out I can also fix it without rebooting by removing the S-ATA cable and reconnecting it (thanks to S-ATA Hotplug), which obviously is not a practicable solution.

Since my system is encrypted i also have to do:

sudo umount /home/media2/
sudo cryptsetup luksClose sdb1_crypt
sudo cryptsetup luksOpen /dev/disk/by-uuid/[myUUID] sdb1_crypt
sudo mount /dev/mapper/sdb1_crypt /home/media2/

I also tried to reset it via hdparm instead of removing the cable and failed:

sudo hdparm -w /dev/sdb

/dev/sdb:
 resetting drive
 HDIO_DRIVE_RESET failed: Inappropriate ioctl for device

In most cases only that secondary device fails so my system can run and i can fix it that way. Every now and then i can not resume at all. I assume in those cases my system disk fails, but i have no means of checking that, especially because it rarely and randomly happens.

I just had that problem again and further found out, that i could suspend/resume normally after i just fixed it in the aforementioned way.

---

### Post by DjNDB on 2009-02-22
> **DjNDB said:**
> 
I also tried to reset it via hdparm instead of removing the cable and failed:

sudo hdparm -w /dev/sdb

/dev/sdb:
 resetting drive
 HDIO_DRIVE_RESET failed: Inappropriate ioctl for device


I found out how to reset the "scsi host" of my hanging Hard disk. I needed to install scsiadd from the ubuntu repositories and use it like this:
```
sudo scsiadd -r 1 0 0 0
sudo scsiadd -a 1 0 0 0
```

values will vary depending on your system. 
You can try to identify it via
```
scsiadd -p
```
Someone could possibly find a nice way to get the ID from the Hard disks UUID to make it save.

Instead of scsiadd you could also directly manipulate /proc or /sys but don't ask me about details. 
I found close to no documentation for that.

At least that way i don't have to open up my case and disconnect the S-ATA cable anymore.
If I find the time i can probably figure out a way to detect whether the Hard disk is broken on resume and needs this fix to automate it.

---

### Post by Magnesium on 2009-10-07
Hello all,

If anyone is still listening...you might try adding pci=nomsi to your kernel options in /boot/grub/menu.lst, as per this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354462](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354462)

Hope this helps,
Mg

---

