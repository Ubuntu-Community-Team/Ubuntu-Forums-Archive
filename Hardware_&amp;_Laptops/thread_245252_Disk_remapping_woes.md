---
title: "Disk remapping woes"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by Guy2 on 2006-08-27
I have three Windows partitions, hda1,2 and 3.
I want to mount them as /home/windows/system, /home/windows/apps and /home/windows/stuff.

Trouble is, when I installed Ubuntu (dual-boot) I used gparted to set up hda1 as /home/windows. (Lazily I left hda2 and 3 unmounted).

Tried the Admin > Disks tool but it's not hot on deleting (unmounting) things. So I opened a shell and did sudo umount /dev/hda1 followed by various mkdir and mount stuff which set it up nicely.

<shut down. sleep. breakfast>

Next day, I fire Dapper up again and it goes "root's been messin' with stuff. we can't have that!" and sets it back the broken way.

How can I get dapper to wake up and smell the coffee?

---

### Post by spin2cool on 2006-08-27
I think what you'll want to do is edit your /etc/fstab file to mount the partitions correctly on boot.

See: [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by Guy2 on 2006-08-28
> **spin2cool said:**
> I think what you'll want to do is edit your /etc/fstab file to mount the partitions correctly on boot.

See: [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

Yes, thanks. That fixed it a treat.

---

