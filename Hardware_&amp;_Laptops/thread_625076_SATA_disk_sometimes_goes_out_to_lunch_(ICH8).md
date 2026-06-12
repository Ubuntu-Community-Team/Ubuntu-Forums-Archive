---
title: "SATA disk sometimes goes out to lunch (ICH8)"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by Peter Cordes on 2007-11-27
I have an occasional system glitch and I'm not sure if it's hardware or software.

 I sometimes see sda stop responding.  This is very infrequent, e.g. usually months go by where it works fine.  I think I once had it happen a couple times in a couple days, but I didn't notice any kind of correlation with anything I was doing.   It's happened maybe 4 times in the year since I built this machine.

 The kernel log shows this:
Nov 22 05:28:44 tesla kernel: [714786.172320] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x2 frozen
Nov 22 05:28:44 tesla kernel: [714786.172329] ata1.00: cmd 61/01:00:df:73:99/00:00:03:00:00/40 tag 0 cdb 0x0 data 512 out
Nov 22 05:28:44 tesla kernel: [714786.172331]          res 40/00:ff:00:fa:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Nov 22 05:28:44 tesla kernel: [714786.172337] ata1.00: cmd 60/28:08:1a:8d:95/00:00:26:00:00/40 tag 1 cdb 0x0 data 20480 in
Nov 22 05:28:44 tesla kernel: [714786.172339]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Nov 22 05:28:45 tesla kernel: [714786.484245] ata1: soft resetting port
Nov 22 05:28:50 tesla kernel: [714791.743090] ata1: port is slow to respond, please be patient (Status 0xc0)
Nov 22 05:28:55 tesla kernel: [714796.558036] ata1: softreset failed (device not ready)
Nov 22 05:28:55 tesla kernel: [714796.558042] ata1: hard resetting port
Nov 22 05:29:00 tesla kernel: [714802.072821] ata1: port is slow to respond, please be patient (Status 0x80)
Nov 22 05:29:05 tesla kernel: [714806.607826] ata1: COMRESET failed (errno=-16)
Nov 22 05:29:05 tesla kernel: [714806.607834] ata1: hard resetting port
Nov 22 05:29:10 tesla kernel: [714812.122615] ata1: port is slow to respond, please be patient (Status 0x80)
Nov 22 05:29:40 tesla kernel: [714841.676126] ata1: COMRESET failed (errno=-16)
Nov 22 05:29:40 tesla kernel: [714841.676135] ata1: limiting SATA link speed to 1.5 Gbps
Nov 22 05:29:40 tesla kernel: [714841.676138] ata1: hard resetting port
Nov 22 05:29:45 tesla kernel: [714846.687024] ata1: COMRESET failed (errno=-16)
Nov 22 05:29:45 tesla kernel: [714846.687032] ata1: reset failed, giving up
Nov 22 05:29:45 tesla kernel: [714846.687034] ata1.00: disabled
Nov 22 05:29:45 tesla kernel: [714846.687049] ata1: EH complete
Nov 22 05:29:45 tesla kernel: [714846.687431] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov 22 05:29:45 tesla kernel: [714846.687438] end_request: I/O error, dev sda, sector 647335194
Nov 22 05:29:45 tesla kernel: [714846.687456] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov 22 05:29:45 tesla kernel: [714846.687460] end_request: I/O error, dev sda, sector 60388319
Nov 22 05:29:45 tesla kernel: [714846.687464] md: super_written gets error=-5, uptodate=0
Nov 22 05:29:45 tesla kernel: [714846.687468] raid1: Disk failure on dm-5, disabling device. 
Nov 22 05:29:45 tesla kernel: [714846.687470] ^IOperation continuing on 1 devices
Nov 22 05:29:45 tesla kernel: [714846.687481] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov 22 05:29:45 tesla kernel: [714846.687485] end_request: I/O error, dev sda, sector 131135
Nov 22 05:29:45 tesla kernel: [714846.687490] raid1: dm-10: rescheduling sector 131072
Nov 22 05:29:45 tesla kernel: [714846.687498] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov 22 05:29:45 tesla kernel: [714846.687502] end_request: I/O error, dev sda, sector 728063
Nov 22 05:29:45 tesla kernel: [714846.687506] raid1: dm-10: rescheduling sector 728000
Nov 22 05:29:45 tesla kernel: [714846.687511] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov 22 05:29:45 tesla kernel: [714846.687515] end_request: I/O error, dev sda, sector 744831
Nov 22 05:29:45 tesla kernel: [714846.687518] raid1: dm-10: rescheduling sector 744768
Nov 22 05:29:45 tesla kernel: [714846.687523] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov 22 05:29:45 tesla kernel: [714846.687527] end_request: I/O error, dev sda, sector 29322895
Nov 22 05:29:45 tesla kernel: [714846.687531] raid1: dm-5: rescheduling sector 26254480
Nov 22 05:29:45 tesla kernel: [714846.687663] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov 22 05:29:45 tesla kernel: [714846.687668] end_request: I/O error, dev sda, sector 131135
Nov 22 05:29:45 tesla kernel: [714846.687687] RAID1 conf printout:
Nov 22 05:29:45 tesla kernel: [714846.687689]  --- wd:1 rd:2
Nov 22 05:29:45 tesla kernel: [714846.687692]  disk 0, wo:1, o:0, dev:dm-5
Nov 22 05:29:45 tesla kernel: [714846.687694]  disk 1, wo:0, o:1, dev:dm-4
Nov 22 05:29:45 tesla kernel: [714846.689812] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Nov 22 05:29:45 tesla kernel: [714846.689817] end_request: I/O error, dev sda, sector 647335194
...


I run AMD64 Gutsy on a Core 2 Duo system (4GB RAM, Intel DG965WH mobo: g965, ICH8R).  I have 3 SATA hard drives on the ICH8R ahci controller (set to AHCI mode in the BIOS) and an IDE DVD burner (on the pata_marvell controller).  I use a combination of RAID1 and evms (with lvm2) to keep /, /usr, and /home on RAID1, and /var/tmp, /data, etc. on non-RAID storage from a volume group of partitions on my first two drives..  The third drive just has one partition which is one evms volume, and I just keep movies on it, so it can spin down when I'm not using it.  So normally there is I/O to SATA ports 1 and 2.

 My hardware is usually reliable.  I have the system in an Antec P150 case, with a Zalman flower heatsink that gets some airflow over the chipset heatsink.  (although it does get rather warm).  The power supply is the Antec Neo HE 430W that came with the case.  My system only draws 90-130W depending on load.  (I use the onboard g965 graphics, because they have Free 3D drivers.)  My RAM is 4x1GB Kingston ValueRAM DDR2-800MHz which is rated to work at the 1.8V the Intel mobo is limited to.  I've run memtest86+ on it overnight a couple times (never with any errors.)  So anyway, I don't think this is a result of the usual kinds of flaky hardware (overclocking or bad memory).

 I put my kernel logs and other info on my web server:
[http://www.cordes.ca/~peter/bugs/sata-drop/](http://www.cordes.ca/~peter/bugs/sata-drop/)
I trimmed the kernel logs a little bit, cutting repeating messages about attempts to access beyond the end of sr0 (my dvd)  kern.log.1 starts when I booted up days before the sata problem.  kern.log.0 has the actual problem.

 Also note that the virtualbox kernel module was loaded when this happened, but I've seen this problem happen before I ever installed virtualbox.

 After the disk locked up, I tried power-cycling the drive.  (SATA power connectors are hot-swap safe).  That had no effect.  (other than power-cycling sdb because of the momentary voltage drop.)  Unplugging sda from that motherboard sata port also had no effect.  It was detected normally when I plugged it in to a different sata port, but I obviously needed to reboot, so I didn't try to hot-add its partitions into the md devices.  EVMS doesn't need that kind of confusion, and it wouldn't have helped rescue the non-RAID1 filesystems that are on block devices that span part of sda.

 When I've seen these drop-outs in the past, it's always been the same hard drive, sda, the 500GB Western Digital RE2 hard drive on SATA port 1.

 So, has anyone else ever seen this?  Any ideas?  I want to have a _stable_ machine I can trust with being my mail server/firewall/whatever.

---

### Post by peteguhl on 2007-11-28
I've got the ICH7 chipset and have somewhat similiar issues...

Can you do me a favor and try adding this kernel option?

combined_mode=libata

To test it without making changes permanent, reboot and at the grub menu select the kernel you want to boot, then hit 'e' to edit the kernel (just temporary), and at the end just add:
combined_mode=libata
exit that menu and hit 'b' to boot the kernel.

Basically, 'combined_mode=libata' sets libata to control all IDE/SATA devices instead of letting it hash it out with generic ide support... seems to be an issue...

SATA devices instead of letting it hash it out with generic ide support... seems to be an issue...

If that does the trick, just add that argument to the 'kopt' line in your /boot/grub/menu.lst 
Here's an example of what it should look like (UUID will be different of course and keep the single '#'):

# kopt=root=UUID=496b19dd-c515-4ca4-9455-3d582e8bb79f ro combined_mode=libata

Then run 'sudo grub-update'.

---

### Post by Peter Cordes on 2007-11-28
> **peteguhl said:**
> I've got the ICH7 chipset and have somewhat similiar issues...

Can you do me a favor and try adding this kernel option?

combined_mode=libata

Basically, 'combined_mode=libata' sets libata to control all IDE/SATA devices instead of letting it hash it out with generic ide support... seems to be an issue...

SATA devices instead of letting it hash it out with generic ide support... seems to be an issue...


 Thanks for the reply.  I don't think my kernel log shows the ide subsystem grabbing any ports on the ahci controller.  It's set to AHCI mode in the bios, and I didn't think there were IDE drivers that could even talk to it.

 I looked at drivers/pci/quirks.c, and AFAICT the only effect should be controlling whether libata reserves the I/O resources for itself.  My /proc/ioports shows libata claiming io resources for the marvell pata controller on PCI bus #2.  /proc/iomem shows ahci claiming the io memory region for pci 00:1f.2.  I don't see anything at all suspicious, and certain no mention of ide or ata other than libata and ahci.  So I'm pretty sure libata got what it wanted, I doubt that combined_mode=libata can help.

 I don't think combined_mode=libata can hurt, so I did put it in my GRUB menu.lst.  (I know how to use grub interactively, and I've known how to use update-grub since maybe before Debian woody, whenever I switched from lilo, but thanks for the careful explanation :)

 I do tend to reboot more frequently than I've seen these sata dropouts, (esp. when I'm trying out new and exciting ways to crash X with the mesa g965 drivers...).  If I see another sata dropout, it will probably be with this enabled.  If I never see another one, then great.

 Anyway, thanks again.

---

### Post by Peter Cordes on 2008-01-31
This happened again.
> 
Jan 31 16:18:23 tesla kernel: [806100.226896] ata1.00: exception Emask 0x0 SAct 0x1ff SErr 0x0 action 0x2 frozen
Jan 31 16:18:23 tesla kernel: [806100.226906] ata1.00: cmd 61/08:00:9f:32:05/00:00:00:00:00/40 tag 0 cdb 0x0 data 4096 out
Jan 31 16:18:23 tesla kernel: [806100.226908]          res 40/00:ff:00:fa:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Jan 31 16:18:23 tesla kernel: [806100.226915] ata1.00: cmd 61/01:08:df:73:99/00:00:03:00:00/40 tag 1 cdb 0x0 data 512 out
Jan 31 16:18:23 tesla kernel: [806100.226917]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan 31 16:18:23 tesla kernel: [806100.226923] ata1.00: cmd 60/00:10:92:1e:7b/01:00:34:00:00/40 tag 2 cdb 0x0 data 131072 in
Jan 31 16:18:23 tesla kernel: [806100.226925]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan 31 16:18:23 tesla kernel: [806100.226931] ata1.00: cmd 60/e0:18:72:ea:bd/00:00:27:00:00/40 tag 3 cdb 0x0 data 114688 in
Jan 31 16:18:23 tesla kernel: [806100.226933]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan 31 16:18:23 tesla kernel: [806100.226939] ata1.00: cmd 60/08:20:6a:d2:5f/00:00:28:00:00/40 tag 4 cdb 0x0 data 4096 in
Jan 31 16:18:23 tesla kernel: [806100.226941]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan 31 16:18:23 tesla kernel: [806100.226947] ata1.00: cmd 60/68:28:a2:4c:df/00:00:16:00:00/40 tag 5 cdb 0x0 data 53248 in
Jan 31 16:18:23 tesla kernel: [806100.226949]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan 31 16:18:23 tesla kernel: [806100.226955] ata1.00: cmd 61/0a:30:90:16:5a/00:00:2b:00:00/40 tag 6 cdb 0x0 data 5120 out
Jan 31 16:18:23 tesla kernel: [806100.226957]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan 31 16:18:23 tesla kernel: [806100.226963] ata1.00: cmd 60/28:38:0a:76:89/00:00:2f:00:00/40 tag 7 cdb 0x0 data 20480 in
Jan 31 16:18:23 tesla kernel: [806100.226965]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan 31 16:18:23 tesla kernel: [806100.226971] ata1.00: cmd 60/08:40:f7:ea:8c/00:00:01:00:00/40 tag 8 cdb 0x0 data 4096 in
Jan 31 16:18:23 tesla kernel: [806100.226973]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jan 31 16:18:23 tesla kernel: [806100.538815] ata1: soft resetting port
Jan 31 16:18:28 tesla kernel: [806105.749671] ata1: port is slow to respond, please be patient (Status 0xc0)
Jan 31 16:18:33 tesla kernel: [806110.564622] ata1: softreset failed (device not ready)
Jan 31 16:18:33 tesla kernel: [806110.564629] ata1: hard resetting port
Jan 31 16:18:39 tesla kernel: [806116.079404] ata1: port is slow to respond, please be patient (Status 0x80)
Jan 31 16:18:43 tesla kernel: [806120.614409] ata1: COMRESET failed (errno=-16)
Jan 31 16:18:43 tesla kernel: [806120.614418] ata1: hard resetting port
Jan 31 16:18:49 tesla kernel: [806126.129195] ata1: port is slow to respond, please be patient (Status 0x80)
Jan 31 16:18:56 tesla kernel: [806133.700380] possible SYN flooding on port 4662. Sending cookies.
Jan 31 16:19:18 tesla kernel: [806155.618722] ata1: COMRESET failed (errno=-16)
Jan 31 16:19:18 tesla kernel: [806155.618730] ata1: limiting SATA link speed to 1.5 Gbps
Jan 31 16:19:18 tesla kernel: [806155.618733] ata1: hard resetting port
Jan 31 16:19:23 tesla kernel: [806160.629717] ata1: COMRESET failed (errno=-16)
Jan 31 16:19:23 tesla kernel: [806160.629724] ata1: reset failed, giving up
Jan 31 16:19:23 tesla kernel: [806160.629727] ata1.00: disabled
Jan 31 16:19:23 tesla kernel: [806160.629756] ata1: EH complete
Jan 31 16:19:23 tesla kernel: [806160.630291] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jan 31 16:19:23 tesla kernel: [806160.630297] end_request: I/O error, dev sda, sector 26012407
Jan 31 16:19:23 tesla kernel: [806160.630303] raid1: dm-5: rescheduling sector 22943992
Jan 31 16:19:23 tesla kernel: [806160.630314] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Jan 31 16:19:23 tesla kernel: [806160.630318] end_request: I/O error, dev sda, sector 797537802
...



 I think the initial lines correspond to queued requests submitted to the drive.  This time there were 8 requests queued when it screwed up.  Last time there were 2.  I don't think I have the logs from when it happened before that, though.

 It supports NCQ with a max depth of 31
peter@tesla:~$ cat /sys/block/sda/device/queue_depth 
31
peter@tesla:~$ cat /sys/block/sda/device/queue_type 
simple

 This is the same as what hdparm -I showed, IIRC.  I can't check now because the drive is currently not responding to commands, and I haven't rebooted yet...

 Now I'm suspicious about NCQ triggering the problem: neither of my other hard drives support a queue depth of more than 1.  sdb is a WDC WD3200YS-01PGB0 (WD 320GB RAID-edition (RE, not RE2)), which supports NCQ but with a max queue depth of 1.  sdc is a 200GB  WDC WD2000JD-00HBB0, which doesn't support NCQ at all.  Neither of them has ever had a problem, even though sdb gets heavy use.  (/var/tmp is on it, which I use to throw around big files...)

 I'll try to figure out how to disable NCQ support (any suggestions?), and then wait several months to see if the problem happens again...

---

### Post by Peter Cordes on 2008-02-01
This is probably partly the hardware/BIOS's fault.  A soft reboot (shutdown -r) did _not_ fix the problem.  The freshly booted kernel gets errors trying to access sda.  A power cycle got things back to normal, though.

 I disabled NCQ for that drive with
echo 1 > /sys/block/sda/device/queue_depth
(This might not technically disable NCQ, but like I said I've never had this problem on my NCQ-supporting drive which only supports a queue depth of 1).

---

### Post by Peter Cordes on 2008-04-06
> **Peter Cordes said:**
> This is probably partly the hardware/BIOS's fault.  A soft reboot (shutdown -r) did _not_ fix the problem.  The freshly booted kernel gets errors trying to access sda.  A power cycle got things back to normal, though.

 I disabled NCQ for that drive with
echo 1 > /sys/block/sda/device/queue_depth
(This might not technically disable NCQ, but like I said I've never had this problem on my NCQ-supporting drive which only supports a queue depth of 1).

 That didn't solve the problem.  I recently had another disappearance of /dev/sda. :(

---

### Post by zlisiecki on 2008-04-07
I seem to have the same problem for a longer time with Intels S875wp1 so called "entry server". It does not dissapear after i switched from ATA to SATA ! My os is opensuse, last kernel is 2.6.22.17-0.1 yet serveral updates took place since the problem arrised for the first time.

The server is running 24h and it switches to read only mode once a month without any reason. Obviously no error could be logged in read-only state ! Now I found:

sda hostbyte = DID_BAD_TARGET driverbyte = DRIVER_OK,SUGGEST_OK

in dmesg, which you already know. In such a state the system can well run as a router using RAM and no disks for many days without any trouble, so obviously the error regards a disk only. Simmilarily what has already been reported the warm restart in not enought - one efectively has to switch off the current.

Similarily I use an Antec PSU, so problems with power supply are highly improbable.

If you have any suggestions how to solve it I'll be very thankful.
regards,
Zbyszek

---

### Post by Peter Cordes on 2008-05-06
I meant to reply to this weeks ago.

> **zlisiecki said:**
> I seem to have the same problem for a longer time with Intels S875wp1 so called "entry server". It does not dissapear after i switched from ATA to SATA ! My os is opensuse, last kernel is 2.6.22.17-0.1 yet serveral updates took place since the problem arrised for the first time.


 My BIOS setting for the controller mode is AHCI.  I haven't tried other modes.

> 
The server is running 24h and it switches to read only mode once a month without any reason. Obviously no error could be logged in read-only state !



 If you had another drive, you could run RAID1 for the filesystem /var/log is on...  Or try syslog over network.  Might be useful for debugging.  But if you can log in and run dmesg, you're not gaining anything.

 It does sound like a very similar problem.  My system uses libata's ahci driver.  Maybe there's a bug in it, esp. if you also use that driver.

 If I ever figure this out, I'll post here.

---

### Post by Pullkick on 2008-05-16
Hi,
I own a Dell Vostro 1700 with a ICH8 and a Seagate HD.

Same problem here.

Detailed problem desrcibed here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196076/]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196076/")

But nobody seems to take care of the problem...

```
 [   22.733981]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
 [   22.733993]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
 [   22.734005]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
 [   22.734017]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
 [   22.734029]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
 [   22.734041]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
 [   22.734052]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x50 (ATA bus error)
 [   22.734066] ata1: hard resetting link
 [   22.813227] ata1: port is slow to respond, please be patient (Status 0x80)
 [   22.871492] ata1: hard resetting link
 [   22.878447] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
 [   22.881318] ata1.00: configured for UDMA/133
 [   22.881334] ata1: EH complete
 [   22.881435] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
 [   22.881473] sd 0:0:0:0: [sda] Write Protect is off
 [   22.881530] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 [   23.330869]          res 40/00:00:4f:32:80/00:00:01:00:00/40 Emask 0x10 (ATA bus error)
 [   23.637962] ata1: soft resetting link
 [   23.670244] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
 [   23.672334] ata1.00: configured for UDMA/133
 [   23.672341] ata1: EH complete
 [   23.672430] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
 [   23.672467] sd 0:0:0:0: [sda] Write Protect is off
 [   23.672522] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 [   53.827858]          res 40/00:00:4f:32:80/00:00:01:00:00/40 Emask 0x44 (timeout)
 [   53.827870]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x44 (timeout)
 [   53.827882]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x44 (timeout)
 [   53.827894]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x44 (timeout)
 [   53.827906]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x44 (timeout)
 [   53.827918]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x44 (timeout)
 [   53.827929]          res 40/00:30:97:81:8b/00:00:01:00:00/40 Emask 0x44 (timeout)
 [   53.827946]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.827953]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.827960]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.827967]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.827975]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.827982]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.827988]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.827995]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.828002]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.828009]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.828016]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
 [   53.828023]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)

```

Andre

---

### Post by rholt on 2008-05-17
> **peteguhl said:**
> # kopt=root=UUID=496b19dd-c515-4ca4-9455-3d582e8bb79f ro combined_mode=libata

Then run 'sudo grub-update'.

Typo:  $ sudo update-grub

---

### Post by oldmanuk on 2008-05-21
still seeing these issues even with Interpid's 2.6.25-1-generic kernel

---

### Post by yongjunj on 2008-06-17
Hi,

I'm having the exact same problem with my NAS server ([here is my original post]("http://ubuntuforums.org/showthread.php?p=5205345")).

I'm using parts from my old machine to run this server - SOYO KT880 Dragon and Athlon XP 3200+. The mobo has 2 different SATA controllers - VIA VT8237 and ALi M5281.

I was beginning to think that it's faulty mobo, but has anyone found an answer to this problem?

Thx,
Jun

---

### Post by oldmanuk on 2008-06-17
in the end it turned out to be a dying hard disk for me

one replacement later and the problem has gone away

---

### Post by yongjunj on 2008-06-17
Thanks for your input, oldmanuk.

I just bought my 4 HDDs two weeks ago, and I'm still sort of reluctant to take them back for RMA just yet.. until I've fully convinced myself.

How about everyone else? Did it turn out to be dying hdd for you guys as well? Anyone had mobo issues?

---

### Post by yongjunj on 2008-06-24
I tried pci=nomsi boot flag, and I just lost my array again.
I'm gonna see if I can get this HDD replaced.

---

