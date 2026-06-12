---
title: "HDD mounting Issue during start up."
date: 2016-05-06
forum: Hardware
---

### Post by u-cam on 2016-05-06
Hi, 

I had managed to set up a home server utilising

Ubuntu 14.04 - 2of 1TB HDD (Was originally sda & sdb) as a Raid 1 and 
   as a backup a Hot swap-able HDD bay with another 1TB HDD (Was originally sbc) (not done any swapping yet)
System shuts down at night via crontab and reboots in the morning via Bios

However things are going the way of my backside .... pear shaped (dont hold that thought)

During startup I get "Serious errors where found checking /media/backupdrive" - to which I have to press S to skip

Somehow sdb become sdc and sdc has.... who knows - a lie they have change again, see below! A clue perhaps?

[SIZE=6]BUT![/SIZE]
Since starting writing this question - things have started working ... but i believe this is only a temporary reprieval

I'm assuming  my problems are related to the swapping of "logical names"

Any direction greatly appreciated - bearing in mine Im a novice with very big wings :)

Many thanks.



sudo lshw -C disk
> 
  *-disk
       description: SCSI Disk
       product: Stylus Storage
       vendor: EPSON
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1.00
       capabilities: removable
       configuration: ansiversion=2 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sda
  *-disk
       description: ATA Disk
       product: ST1000LM024 HN-M
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 0004
       serial: S2WZJ90D702255
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=b10c5708
  *-disk
       description: ATA Disk
       product: ST1000LM024 HN-M
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 0004
       serial: S2WZJ90D723103
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=59a9799d
  *-disk
       description: ATA Disk
       product: SAMSUNG HD103SI
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdd
       version: 1113
       serial: S1VSJ1KS202440
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=00059fba


[COLOR=#000000][FONT=Ubuntu Mono]sudo blkid[/FONT][/COLOR]
> 
/dev/sdb1: UUID="780d0d08-4dff-d6fb-96e7-6e704ecc0bb0" UUID_SUB="d575d1f1-c761-8e15-20ba-1ae74cd28dea" LABEL="SERVER:0" TYPE="linux_raid_member"
/dev/sdb2: UUID="05273ead-63d8-9c40-40b8-fa8fd94d896c" UUID_SUB="03fb85d4-393b-803f-f162-fdee69302336" LABEL="SERVER:1" TYPE="linux_raid_member"
/dev/sdc1: UUID="780d0d08-4dff-d6fb-96e7-6e704ecc0bb0" UUID_SUB="664f4ad7-7432-586e-5132-61176014252e" LABEL="SERVER:0" TYPE="linux_raid_member"
/dev/sdc2: UUID="05273ead-63d8-9c40-40b8-fa8fd94d896c" UUID_SUB="f11c4a81-7f66-790e-66a8-ea759cde3fc6" LABEL="SERVER:1" TYPE="linux_raid_member"
/dev/sdd1: UUID="1da54696-21af-49b3-8681-c829ee7fd021" TYPE="ext4"
/dev/md1: UUID="7d5bb3ae-f510-46bf-9008-8dc0433b57a2" TYPE="ext4"
/dev/md0: UUID="f050436b-8a02-4e39-a597-a46615e65420" TYPE="swap"


sudo cat /etc/fstab
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/md1 during installation
UUID=7d5bb3ae-f510-46bf-9008-8dc0433b57a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/md0 during installation
UUID=f050436b-8a02-4e39-a597-a46615e65420 none            swap    sw              0       0
/dev/sdd1    /media/backupdrive   ext4    defaults     0        2


---

### Post by u-cam on 2016-08-20
Solved this problem by using UUID in fstab :)

---

