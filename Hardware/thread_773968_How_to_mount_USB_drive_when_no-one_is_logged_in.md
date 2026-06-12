---
title: "How to mount USB drive when no-one is logged in?"
date: 2008-04-29
forum: Hardware
---

### Post by johsch on 2008-04-29
My question is slightly different to the other "USB drive does not mount" questions which swamps my googling and searching of this forum.  I did find a similar question at [http://ubuntuforums.org/showthread.php?t=42003](http://ubuntuforums.org/showthread.php?t=42003) but there was no response to it.  Sincere apologies if I have missed a thread: in that case please just point me to it.  Thanks!

When I log into the desktop, there is an icon showing that my external USB drive is connected and mounted.  No problem with that.  However...

cron runs a nightly back-up script for me at 3 am when no-one should be logged in, but after migrating from Fedora to kubuntu Feisty, it fails at the point where I try to mount the external USB drive:

    MOUNT_OK=no
    for DISK in $DISK_LABELS
      do
#      mount -w "$MOUNT_POINT/$DISK" 2> /dev/null
      mount -w "$MOUNT_POINT/$DISK"
      MOUNT_RES=$?
      if [ "$MOUNT_RES" = "0" ]; then
          MOUNT_OK=yes
          break
      fi
    done

results in:

mount: can't find /media/backup_0 in /etc/fstab or /etc/mtab
mount: can't find /media/backup_1 in /etc/fstab or /etc/mtab
mount: can't find /media/backup_2 in /etc/fstab or /etc/mtab
...

even when a disk with label backup_1 (or 2 etc.) is connected.

When I am logged into the desktop, fstab looks like this (note, no /dev/sdb1):

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b205e324-66d4-4e0f-a675-17c0845b6bdb /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda5
UUID=28037f58-ceb0-4dc7-bac3-62a476d8f9b0 none            swap    sw
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

and /etc/mtab looks like this (it does contain a /dev/sdb1 entry):

$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sdb1 /media/backup_1 ext3 rw,noexec,nosuid,nodev,sync,data=ordered 0 0

When I log out of the desktop and log into a text console (Ctrl-Alt-F1), the /dev/sdb1 entry has vanished from mtab (and is of course still absent from fstab).  This makes me suspect that the external drive is only mounted when someone logs into the desktop.

Under Fedora, /etc/fstab was not supposed to be user-edited, but was automatically maintained by something called fstab-sync.  As a result, my Fedora fstab used to contain entries like:

/dev/sdb1  /media/backup_1  ext3  pamconsole,exec,noauto,managed 0 0

where the mount point used to change automatically according to the disk label (presumably under the control of fstab-sync), and mtab used to contain something like

/dev/sdb1 /media/backup_1 ext3 rw,nosuid,nodev 0 0

How should my script detect and mount a connected USB external drive when no-one is logged in?

Any help appreciated,
Johsch

---

