---
title: "CDROM Drive Not Working"
date: 2011-04-07
forum: Hardware
---

### Post by thecarter on 2011-04-07
I've had a look at some of the threads about this but I haven't found a solution yet. Having errors reading ANYTHING from my cd/dvd drive. It used to work so I think the update to the kernel must've changed a setting?

According to Disk Utility - my cd rom device is located on /dev/sr0.

I try to mount /dev/sr0 and it says 'unknown device'.

I ran dmesg - hopefully this makes sense to someone:
> [    1.588595] ata1.01: ATAPI: MATSHITADVD-RAM UJ-860S, 1.00, max UDMA/33
[    1.604567] ata1.01: configured for UDMA/33
[    1.607195] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-860S  1.00 PQ: 0 ANSI: 5
[    1.612202] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.612206] Uniform CD-ROM driver Revision: 3.20
[    1.612608] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.612764] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    1.768065] ata6: SATA link down (SStatus 0 SControl 300)
[    1.768104] ata4: SATA link down (SStatus 0 SControl 300)
[    1.768165] ata5: SATA link down (SStatus 0 SControl 300)
[    1.940045] ata3: softreset failed (device not ready)
[    1.940049] ata3: applying SB600 PMP SRST workaround and retrying
[    2.112055] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.112919] ata3.00: ATA-7: ST9120822AS, 3.ALC, max UDMA/133
[    2.112922] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.112948] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.114026] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.114028] ata3.00: configured for UDMA/133
[    2.114136] scsi 2:0:0:0: Direct-Access     ATA      ST9120822AS      3.AL PQ: 0 ANSI: 5
[    2.114289] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.114542] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.114601] sd 2:0:0:0: [sda] Write Protect is off
[    2.114604] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.114628] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.115090]  sda: sda1 sda2 < sda5 >


Any help would be appreciated.

---

### Post by g_marotta on 2011-04-07
Hi,
unfortunately I have a similar problem. Ubunto does not recognize my DVD/CD-RW as such, but just as a simple CD-R.
I cannot find any driver MATSHITA for Linux: how is it possible?
I fired off a few commands to provide more information:

gc@gc-Satellite-A30:~$ mount
[I]/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gc)[/I]

gc@gc-Satellite-A30:~$ dmesg | grep -i cd | grep -i rom
[I][    1.004783] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA750 DVD/CDRW 1.50 PQ: 0 ANSI: 5
[    1.010421] Uniform CD-ROM driver Revision: 3.20
[    1.010551] sr 1:0:0:0: Attached scsi CD-ROM sr0[/I]

gc@gc-Satellite-A30:~$ cat /etc/fstab
[I]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=573ca194-22a5-4cba-8b69-134972226cd3 none            swap    sw              0       0[/I]

Do not tell me that there is no solution: I was so happy to remove that Microsoft crap from my laptop after a few years...

Thanks and regards
GC

---

