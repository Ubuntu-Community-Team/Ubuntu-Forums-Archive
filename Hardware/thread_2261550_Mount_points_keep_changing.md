---
title: "Mount points keep changing"
date: 2015-01-19
forum: Hardware
---

### Post by PartisanEntity on 2015-01-19
Ubuntu 14.04 LTS headless server:

Every time I update the kernel, my mount points for all my internal and external HDDs change.

Now it is happening each time I restart my headless server.

This essentially breaks my raid10 array with is unable to assemble the disks because the mount points in the config file no longer reflect the real mount points upon boot up. And I have to manually update my mdadm config file after each boot and manually stop and then re-assemble the raid array.

Any help appreciated as this issue is driving me insane and I never experienced something like this before.

I have 4 SATA, 1 SSD and 1 external UDB drives. Mount points for all are changing. /dev/sdc will become /dev/sda and so on.

---

### Post by vinnywright on 2015-01-19
try using the UUID's of the drives/partitions(you should be mounting a partition on a drive /sda1 ,, 2,,,3 not the drive /sda) instead of /dev/sdxy

the blkid command will show them ,,,,,,,,,like so

```
vinny@vinny-Bonobo-Extreme:~$ sudo blkid
[sudo] password for vinny: 
/dev/sda1: LABEL="Ubuntu" UUID="7690a2fc-f8f6-41e2-97bb-de4d6d830056" TYPE="ext4" 
/dev/sda2: UUID="aeb8718b-d4a7-4d21-9584-425071e6c6ba" TYPE="swap" 
/dev/sda3: UUID="f10fe189-1184-4546-bbb2-58a9f0edbf8d" TYPE="ext4" 
/dev/sda5: UUID="a04c683e-16bc-4e31-a360-8532389c964c" TYPE="ext4" 
/dev/sda6: UUID="b2920726-5190-452a-a2ab-1aba610d9654" TYPE="ext4" 
/dev/sdb1: LABEL="Extra Drive 1" UUID="7164ec1f-1a6b-4c58-a481-20416b565202" TYPE="ext4" 

```

VINNY

---

### Post by PartisanEntity on 2015-01-19
Just to avoid any misunderstandings:

1. I do mean that /dev/sdc1 becomes dev/sdb1 for example.

2. In case it is relevant, the 4 disks that are part of my raid10 array are not included in /etc/fstab

3. In /etc/fstab I only have a mount point set for my raid10 array as follows: /dev/md0   /mnt/raiddisk

---

### Post by weatherman2 on 2015-01-20
You can use UUIDs to assemble your RAID arrays, even if they aren't included directly in the fstab file.  Then you don't need to worry about whether a disk is sdc1 or sdb1.

[http://unix.stackexchange.com/questions/52321/using-uuids-with-mdadm](http://unix.stackexchange.com/questions/52321/using-uuids-with-mdadm)

---

### Post by PartisanEntity on 2015-01-20
Thanks to the both of you very much, that makes perfect sense.

I am using the UUIDs now and have tested this and it's working perfectly, I just restarted, and while the device mount point changed yet again, this time the raid array was assembled automatically without me having to do anything manually.

For anyone interested, here are my changes:

old mdadm.conf configuration:

```
DEVICE /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
ARRAY /dev/md0 level=raid10 devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
```

new mdadm.conf configuration:

```
DEVICE UUID=47c17420-8c4f-5bf8-d70c-843638187fe6 UUID=47c17420-8c4f-5bf8-d70c-843638187fe6 UUID=47c17420-8c4f-5bf8-d70c-843638187fe6 UUID=47c17420-8c4f-5bf8-d70c-843638187fe6
ARRAY /dev/md0 level=raid10 devices=UUID=47c17420-8c4f-5bf8-d70c-843638187fe6,UUID=47c17420-8c4f-5bf8-d70c-843638187fe6,UUID=47c17420-8c4f-5bf8-d70c-843638187fe6,UUID=47c17420-8c4f-5bf8-d70c-843638187fe6
```

As suggested I used blkid to get the UUIDs.

---

### Post by vinnywright on 2015-01-20
;)

vinny

---

