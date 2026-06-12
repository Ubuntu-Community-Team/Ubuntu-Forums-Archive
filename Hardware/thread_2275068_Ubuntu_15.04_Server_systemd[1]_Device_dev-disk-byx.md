---
title: "Ubuntu 15.04 Server systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device"
date: 2015-04-24
forum: Hardware
---

### Post by kymmitsu on 2015-04-24
Hi 

I'm Getting in Syslog after a fresh install of the new Ubuntu 15.04 Server on my test server -  Any ideas - I have done another reinstall just incase - and google doesn't seem to have many hits. 

> Apr 24 16:26:20 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sdb/sdb1
Apr 24 16:26:20 HPPPENAS systemd[1]: message repeated 2 times: [ Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sdb/sdb1]
Apr 24 16:26:20 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata3/host2/target2:0:0/2:0:0:0/block/sdd/sdd1
Apr 24 16:26:20 HPPPENAS systemd[1]: message repeated 2 times: [ Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata3/host2/target2:0:0/2:0:0:0/block/sdd/sdd1]
Apr 24 16:26:20 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
Apr 24 16:26:20 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
Apr 24 16:31:23 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sdb/sdb1
Apr 24 16:31:23 HPPPENAS systemd[1]: message repeated 2 times: [ Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sdb/sdb1]
Apr 24 16:31:23 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata3/host2/target2:0:0/2:0:0:0/block/sdd/sdd1
Apr 24 16:31:23 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sdb/sdb1
Apr 24 16:31:23 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
Apr 24 16:31:23 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata3/host2/target2:0:0/2:0:0:0/block/sdd/sdd1
Apr 24 16:31:23 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
Apr 24 16:33:58 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sdb/sdb1
Apr 24 16:33:58 HPPPENAS systemd[1]: message repeated 2 times: [ Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sdb/sdb1]
Apr 24 16:33:58 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata3/host2/target2:0:0/2:0:0:0/block/sdd/sdd1
Apr 24 16:33:58 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sdb/sdb1
Apr 24 16:33:58 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1
Apr 24 16:33:58 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata3/host2/target2:0:0/2:0:0:0/block/sdd/sdd1
Apr 24 16:33:58 HPPPENAS systemd[1]: Device dev-disk-by\x2dpartlabel-primary.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:11.0/ata4/host4/target4:0:0/4:0:0:0/block/sde/sde1 and /sys/devices/pci0000:00/0000:00:11.0/ata2/host1/target1:0:0/1:0:0:0/block/sdc/sdc1


> kymbo@HPPENAS:~$ sudo blkid
/dev/sdb1: UUID="a9336e51-e706-2f73-5b1d-5ce2d13a9909" UUID_SUB="95915ad7-7c53-611e-db2e-f4f75fa39607" LABEL="HPPENAS:0" TYPE="linux_raid_member" PARTLABEL="primary" PARTUUID="e9aed1e1-3425-4af9-a71c-47834b956e63"
/dev/sde1: UUID="72d2186d-6720-46d4-9b32-1c43530e3b0d" TYPE="ext4" PARTLABEL="primary" PARTUUID="0b7f81d5-af98-4840-8461-2678ad39d578"
/dev/sdd1: UUID="a9336e51-e706-2f73-5b1d-5ce2d13a9909" UUID_SUB="9fcd4435-7b55-5717-d620-d8dac986e52c" LABEL="HPPENAS:0" TYPE="linux_raid_member" PARTLABEL="primary" PARTUUID="452bf68f-acd6-456e-9bfa-f28500d558fb"
/dev/sdc1: UUID="a9336e51-e706-2f73-5b1d-5ce2d13a9909" UUID_SUB="d8fabff0-9808-beb8-c729-18748cab1ea8" LABEL="HPPENAS:0" TYPE="linux_raid_member" PARTLABEL="primary" PARTUUID="6cdb505d-6cb2-4852-b60d-3e72b406f79a"
/dev/sda1: UUID="049cbf7e-1f57-4c56-afd1-0aade8473790" TYPE="ext4" PARTLABEL="Primary" PARTUUID="0557fadf-4774-47db-b400-f0590929b40f"
/dev/sdf1: UUID="2a916d8f-11dd-4200-a6c0-74145e11d7d3" TYPE="ext4" PARTUUID="d31d0613-01"
/dev/sdf5: UUID="10f3765d-b616-481c-b06b-a4ba4b6855d0" TYPE="swap" PARTUUID="d31d0613-05"
/dev/md0: LABEL="Storage" UUID="84845d78-09d2-46d3-81ce-f6b5da300f8b" TYPE="ext4"


FSTAB

> UUID=2a916d8f-11dd-4200-a6c0-74145e11d7d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=10f3765d-b616-481c-b06b-a4ba4b6855d0 none            swap    sw              0       0
UUID=84845d78-09d2-46d3-81ce-f6b5da300f8b /Storage        ext4    defaults        0       0
UUID=72d2186d-6720-46d4-9b32-1c43530e3b0d /RADBackup      ext4    defaults        0       0
UUID=049cbf7e-1f57-4c56-afd1-0aade8473790 /EXTBackup      ext4    defaults        0       0


Thanks

---

### Post by dino99 on 2015-04-24
check your raid installation
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)

---

### Post by kymmitsu on 2015-04-24
Thanks I can see why you would think its the RAID however Its coming back as clean

I don't recreate the RAID so after installing mdadm I simply copy across mdadm.conf run "update-initramfs -u" and reconnect the drives.

This is unique to 15.04 - because in between a second reinstall I went back to 14.04.2LTS and I don't get any errors.

---

### Post by Bashing-om on 2015-04-24
kymmitsu; Hello:

I do not know the why or the whereof; but the log is telling the truth.
What I do see:
> 
[color=red]/dev/sdd1:[/color] UUID="a9336e51-e706-2f73-5b1d-5ce2d13a9909" UUID_SUB="9fcd4435-7b55-5717-d620-d8dac986e52c" LABEL="HPPENAS:0" 
[color=red]/dev/sdc1:[/color] UUID="a9336e51-e706-2f73-5b1d-5ce2d13a9909" UUID_SUB="d8fabff0-9808-beb8-c729-18748cab1ea8" LABEL="HPPENAS:0" 

where the same UUID is assigned to different devices . No can do that !

Maybe terminal command:
```

ls /dev/disk/by-uuid -alh

```
will point in a direction of where to start looking ?

[INDENT][INDENT]2 sets of eyes are better than one
[/INDENT][/INDENT]

---

### Post by kymmitsu on 2015-04-24
Cool thanks for the reply

From what I have read / googled RAID member disks have the same UUID - so there should be nothing wrong with the my RAID as per blkid output.

The "Device dev-disk-by\x2dpartlabel-primary.device" in syslog is really just white noise (or a non important bug) as there at this stage seems no effect from it even though frequent and it fills the log.

---

### Post by Demoman on 2015-05-28
I'll throw my hat into this ring as well, however mine is with a 4 drive ZFS Raid Z array

```
May 28 15:20:30 mike systemd[62829]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdd/sdd1 and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdb/sdb1
May 28 15:20:30 mike systemd[62829]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdd/sdd1 and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1
May 28 15:20:30 mike systemd[62829]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdd/sdd1 and /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdb/sdb1
May 28 15:20:30 mike systemd[62829]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdd/sdd1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sdc/sdc1
```

Output from systemctl

```
&#9679; dev-disk-by\x2dpartlabel-zfs.device - WDC_WD30EFRX-68EUZN0 dump                                                                                                   
   Follow: unit currently follows state of sys-devices-pci0000:00-0000:00:1f.2-ata2-host1-target1:0:0-1:0:0:0-block-sdb-sdb1.device                                 
   Loaded: loaded                                                                                                                                                   
   Active: active (plugged) since Wed 2015-05-27 18:58:39 AEST; 20h ago                                                                                             
   Device: /sys/devices/pci0000:00/0000:00:1f.2/ata2/host1/target1:0:0/1:0:0:0/block/sdb/sdb1                                                                       
                                                                                                                                                                    
May 28 15:30:51 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdd/sdd1                                         
May 28 15:30:51 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sdc/sdc1                                         
May 28 15:30:51 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdd/sdd1                                         
May 28 15:30:51 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdd/sdd1                                         
May 28 15:35:55 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1                                         
May 28 15:35:55 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1                                         
May 28 15:35:56 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sdc/sdc1                                         
May 28 15:35:56 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sdc/sdc1                                         
May 28 15:35:56 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdd/sdd1                                         
May 28 15:35:56 mike systemd[1]: Device dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:1f.2/ata2/host
1/target1:0:0/1:0:0:0/block/sdb/sdb1 and /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdd/sdd1
```

It seems strange that systemctl has only "detected" sdb1 as this "device" but no the others.

No idea what is going on. Everything is working fine, but syslogs full of the above errors (every 5 minutes or so)

---

### Post by kymmitsu on 2015-05-30
Only just finished playing with this and though I would post a follow-up. Also appears in google so it may help.

I think I have fixed it. But I needed to destroy the RAID array and then recreate.

If you refer to my blkid output - all of my disks partitions sd[abcd] are  PARTLABEL="primary". All I have done is to change them to a different unique name using parted. This was my only change. "mkpart <unique name>"

I don't know if you can change the name of a partition and leave the files intact - I didn't. 

I don't know why my test servers of Centos 7 and Ubuntu 14.04.02 - didn't report the error - but the new Fedora 22 and Ubuntu 15.04 did. Possibly new Kernel or systemctl!

---

