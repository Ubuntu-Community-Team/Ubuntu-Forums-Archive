---
title: "Adding new HDD nightmare"
date: 2013-04-24
forum: Hardware
---

### Post by SteffJay on 2013-04-24
Hello all. I am having a hell of a time trying to get the new HDD to auto-start on boot. It is formatted EXT4 and the label is called "Store". I am using Ubuntu 12.04 LTS.

Here is the list of my mtab and fstab:

**mtab**

/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sdb1 /media/Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0
gvfs-fuse-daemon /home/steff/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=steff 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
/dev/sdc1 /media/Store_ ext4 rw,nosuid,nodev,uhelper=udisks 0 0

**fstab**

/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sdb1 /media/Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0
gvfs-fuse-daemon /home/steff/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=steff 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
/dev/sdc1 /media/Store_ ext4 rw,nosuid,nodev,uhelper=udisks 0 0

I can only mount it using **root**.

The second request is; i have a USB section on-board and i would like it to be non accessible on boot.

The syntax for achieving both of the problems would be most appreciative as well.

Thanks in advance.

---

### Post by ajgreeny on 2013-04-24
Are you certain those two are your fstab and mtab files?

What do you mean by "trying to get the HDD to autostart at boot"; I presume you just want it to automount with read/write permissions?

I have never seen anything like that before as /etc/fstab; yours looks exactly the same as mtasb or more like the output of the command **mount**, so let's really see what your fstab is by showing us the output of ```
cat /etc/fstab
```and also ```
sudo blkid -c /dev/null
``` We can then help you with the problem.

---

### Post by SteffJay on 2013-04-25
Thanks for your reply **ajgreeny**. Here is the result of your first request:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ea2cd6cf-1557-4480-a226-2798bd274c8c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5d7b8fa-bf56-4f83-b6d2-3b1f369d6bc3 none            swap    sw              0       0
/dev/sdb1 /media/Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0

Here is the reuult of your second request:

/dev/sda1: UUID="ea2cd6cf-1557-4480-a226-2798bd274c8c" TYPE="ext4" 
/dev/sda5: UUID="c5d7b8fa-bf56-4f83-b6d2-3b1f369d6bc3" TYPE="swap" 
/dev/sdb1: LABEL="Store" UUID="c8b592b0-7ec8-466c-b750-fda9ba74797e" TYPE="ext4" 
/dev/sdc1: LABEL="USB SMI" UUID="c8a822bb-c4df-4386-b71a-8724056e2232" TYPE="ext3"

I hope this helps. Thanks in advance.

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by SteffJay on 2013-04-25
hello **ahallubuntu**. Thank you for your reply. I opted for this configuration: **UUID=c8b592b0-7ec8-466c-b750-fda9ba74797e /Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0** and ran **sudo mount -a** and had no errors in the **fstap**. However, i still need to mount it with **root**. Also, it still does not autoboot with the operating system. Please advise. Thanks in advance.

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by SteffJay on 2013-04-25
Here you go:
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sdb1       74891424 4520808  66566304   7% /
udev             1007020       4   1007016   1% /dev
tmpfs             405816     764    405052   1% /run
none                5120       0      5120   0% /run/lock
none             1014532      84   1014448   1% /run/shm
/dev/sdb1       74891424 4520808  66566304   7% /media/Store
/dev/sda1         244416  137501     94295  60% /media/USB SMI
/dev/sdc1      480719568  202688 456097656   1% /media/Store_

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by SteffJay on 2013-04-25
Ok. After reboot the "df" is as follows:

Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sdb1       74891424 4520916  66566196   7% /
udev             1007020       4   1007016   1% /dev
tmpfs             405816     764    405052   1% /run
none                5120       0      5120   0% /run/lock
none             1014532      80   1014452   1% /run/shm
/dev/sdb1       74891424 4520916  66566196   7% /media/Store
/dev/sda1         244416  137501     94295  60% /media/USB SMI

The /etc/mtab is as follows:

/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sdb1 /media/Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0
gvfs-fuse-daemon /home/steff/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=steff 0 0
/dev/sda1 /media/USB\040SMI ext3 rw,nosuid,nodev,uhelper=udisks 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0

I hope this helps. Thanks in advance.

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by SteffJay on 2013-04-25
Here you go:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ea2cd6cf-1557-4480-a226-2798bd274c8c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5d7b8fa-bf56-4f83-b6d2-3b1f369d6bc3 none            swap    sw              0       0
/dev/sdb1 /media/Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by SteffJay on 2013-04-25
Sorry, i have just added it and now rebooting.

---

### Post by SteffJay on 2013-04-25
The /etc/fstab is now this after booting:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ea2cd6cf-1557-4480-a226-2798bd274c8c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5d7b8fa-bf56-4f83-b6d2-3b1f369d6bc3 none            swap    sw              0       0
/dev/sdb1 /media/Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0
UUID=c8b592b0-7ec8-466c-b750-fda9ba74797e /Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0

The Store drive is still not mounting after rebooting.

---

### Post by oldfred on 2013-04-25
It looks like your system is one that has to use UUIDs. You keep getting different drives as sda, sdb & sdc. Some BIOS do promote flash drives to sda which then reorders drives.

From your first post:
 [COLOR=#ff0000]/dev/sdb1[/COLOR] / ext4 rw,errors=remount-ro 0 0
[COLOR=#ff0000]/dev/sdb1[/COLOR] /media/Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0

You cannot have the same partition mounted twice.

And then in post #14 your have this:
[COLOR=#ff0000]/dev/sdb1[/COLOR] /media/Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0
UUID=[COLOR=#ff0000]c8b592b0-7ec8-466c-b750-fda9ba74797e[/COLOR] /Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0

But at least some of your reports show that as the same partition which cannot be. You need to be consistent with UUIDs not devices.

Then the Store and Store_ is offen an artifact of Nautilus mounting a mount in /media a second time. The second never works.
      
 Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

 Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

### Post by SteffJay on 2013-04-25
Hello **oldfred**. Thanks for your reply. I am totaly lost with this issue now. Is there a chance you could give me the propper syntax (looking at the fstab) i submitted to resolve this issue please?

Thanks in advance.

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by SteffJay on 2013-04-25
Hello **oldfred**. Thanks for your reply. Here is the fstab after removing the line from it as directed:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ea2cd6cf-1557-4480-a226-2798bd274c8c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5d7b8fa-bf56-4f83-b6d2-3b1f369d6bc3 none            swap    sw              0       0
UUID=c8b592b0-7ec8-466c-b750-fda9ba74797e /Store ext4 rw,nosuid,nodev,uhelper=udisks 0 0

The "Store" is in the file system. However, i cannot make a bookmark to the left panel as there is no availability anywhere to do so.

This is the "df" list:

df: `/root/.gvfs': Permission denied
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sdb1       74891424 4501064  66586048   7% /
udev             1007020       4   1007016   1% /dev
tmpfs             405816     764    405052   1% /run
none                5120       0      5120   0% /run/lock
none             1014532      84   1014448   1% /run/shm
/dev/sdc1      480719568  202688 456097656   1% /Store
/dev/sda1         244416  137501     94295  60% /media/USB SMI

Thanks in advance.

---

### Post by SteffJay on 2013-04-25
OK, this is now working thank you :P The only thing i would like to do now is, remove the SMI USB from auto-booting (IE making it unavailable). Do i just remove the line from fstab ?

---

### Post by ahallubuntu on 2013-04-25
~

---

