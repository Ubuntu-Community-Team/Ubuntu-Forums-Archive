---
title: "Bo automount of CD-rom on 12.04"
date: 2012-10-20
forum: Hardware
---

### Post by stephen67 on 2012-10-20
This is the first time I have tried to rip a CD on 12.04. I am using clasic gnome.

The CD-rom (music) never appears on my desktop and applications do not see it.

Searches here and on Google suggest things that my system does not have. Like a setting in Nautilus for autorun. My preferences dialog does not show that.

So I am back at the beginning.

fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fdc65bec-ed4b-407b-beef-b7c630f96acf /               ext4    errors=remount-ro 0       1
# /more was on /dev/sda6 during installation
UUID=976259d9-7cdf-4faf-94ea-b636e0b910c5 /more           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=0cd6ede7-e59b-4577-9a73-a85a3c37aa85 none            swap    sw              0       0

UUID=75503554-d27d-4227-898b-f9ad783c939e /big0     ext4    errors=remount-ro 0       1

UUID=30d6b7e9-b6a2-4227-ad0a-e180ab2340ba /home     ext4    errors=remount-ro 0       1

/dev/sr0  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0


Both /dev/sr0 and /media/cdrom0 exist.

Where do I go from here?

Any and all suggestions appreciated!

---

