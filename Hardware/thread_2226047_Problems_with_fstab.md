---
title: "Problems with fstab"
date: 2014-05-24
forum: Hardware
---

### Post by DBQ on 2014-05-24
Hi All,

I have a server with 4 drive bays. I am running ubuntu 12.04.

I would like all drives to be mounted on system bootup based on their UUID.

I modified my fstab file as shown below. When I run mount -a, everything is mounted as expected and works.  
However, when I reboot the system and cd into disk1, disk2, etc, I cannot see any files. When I run mount, the drives show up as mounted.

```

proc            /proc           proc    nodev,noexec,nosuid 0       0
#/dev/sda1 /disk2   ext4  rw,suid,dev,noexec,auto,user,async      0  0
# / was on /dev/sda1 during installation
UUID=3099a0df-c698-469d-bc87-f1021aca8774 /               ext4 defaults,errors=remount-ro 0       1
#UUID=6a023438-6e6c-49ec-9888-0c9760d1e4b8 /home/josh/disk1 ext4 defaults 0 0  
UUID=28ea4344-eef9-44d8-ba4c-60ff201413b6 /home/josh/disk3 ext4 defaults,errors=remount-ro 0       1 
UUID=30e337e3-dea7-4e62-842b-4597e6323796 /home/josh/disk2 ext4 defaults,errors=remount-ro 0       1

```

Here is the output of my blkid

```

$blkid
/dev/sda1: LABEL="drive3" UUID="30e337e3-dea7-4e62-842b-4597e6323796" TYPE="ext4" 
/dev/sdb1: LABEL="Disk2_2TB" UUID="28ea4344-eef9-44d8-ba4c-60ff201413b6" TYPE="ext4" 
/dev/sdc1: UUID="3099a0df-c698-469d-bc87-f1021aca8774" TYPE="ext4" 
/dev/sdd1: LABEL="drive4" UUID="6a023438-6e6c-49ec-9888-0c9760d1e4b8" TYPE="ext4"

```

Any ideas?

Thank You!

---

### Post by brantcgardner on 2014-05-27
What is the output of **mount**?

---

### Post by mcduck on 2014-05-27
I assume you have created the mount points already?

Anyway, if nothing else the last number on the fstab entries should be "2". (the number defines fsck order, 0 means no check, 1 should only be used for the root partition, and 2 or higher for everything else. I suppose in some cases it could cause troubles like mount point not being available)

---

### Post by vanadium on 2014-05-27
I don't know about your hardware, but might it be that the drives are not ready yet at the time /etc/fstab is being processed? In that case, you could add the option "noauto" to each of the partitions, and mount the drives later during the startup, i.e. in rc.local. The commands you issue in rc.local then simply can be like
```

mount /home/josh/disk3

```
The system retrieves the details and the options from fstab.

---

### Post by brantcgardner on 2014-05-27
Unless the user is mistaken about their original description, I think the issue is deeper than indicated here.  They said:

> When I run mount, the drives show up as mounted.

If the issue was that they weren't ready to mount or that the mount points didn't exist then they should be reported as **not** mounted after boot, yes?

I've asked to see what the output of mount is but I guess the user has not yet had a chance to come back and reply.

---

### Post by mcduck on 2014-05-28
> **brantcgardner said:**
> Unless the user is mistaken about their original description, I think the issue is deeper than indicated here.  They said:



If the issue was that they weren't ready to mount or that the mount points didn't exist then they should be reported as **not** mounted after boot, yes?

I've asked to see what the output of mount is but I guess the user has not yet had a chance to come back and reply.

They could end being automounted if the fstab entry didn't work... That would mean they'd still show up as mounted, just not with the desired mount point and options. So I agree that seeing the output of "mount" would be useful.

---

