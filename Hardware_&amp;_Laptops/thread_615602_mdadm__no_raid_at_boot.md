---
title: "mdadm | no raid at boot"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by Bultot on 2007-11-17
i've a raid1 array /dev/md0 (which consists of /dev/sda8 & /dev/ sdb7). The raid is used for my "/home". I's working properly. But a problem occurs at boot.
Something about superblock not found. (Ctrl-D to continue)

When I continue, I have to assemble the raid manual (sudo mdadm --assemble /dev/md0 /dev/sda8 /dev/sdb6) Then remount the partition. (sudo mount -a) and everything is fine.

It looks like the raid is not detected at boot. What could the problem be? Better, how to fix it?

Thanks in advance

-----------boot_output-----------
Checking file systems...fsck
fsck.ext3: No such file or directory while trying to open /dev/md0
/dev/md0:
The superblock could nog be read or does not describe a correct ext2 filesystem . If the device is valid and it really contains an ext2 filesystem (and not swap of ufs or something else), then the superblock is corrupt and you might try running e2fsck with an alternative superblock:
  e2fsck -b 8193 <device>

---

### Post by Bultot on 2007-11-24
*bump

---

### Post by dutch_gecko on 2007-11-24
I'm a bit of an mdadm newbie, but it looks like something might have gone wrong in mdadm's configuration. I found [this tutorial](http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html?page=1) to be a great help in figuring out how the configuration file is meant to work. Try editing the file manually to fix up any errors it might have.

as an aside, the superblock error you're receiving is because fsck is trying to find some partition information, on a partition that isn't mounted yet. Confusingly, mdadm itself uses a different kind of superblock to find the drives it should be managing.

---

### Post by Bultot on 2007-11-24
Thanks for replying..  Just found the problem. In every howto they talk about /etc/mdadm.conf. Just found out I have to write /etc/mdadm/mdadm.conf :oops: and not /etc/mdadm.conf

---

### Post by mattschulte on 2007-11-26
You need:
```
sudo -i
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
exit

```

---

