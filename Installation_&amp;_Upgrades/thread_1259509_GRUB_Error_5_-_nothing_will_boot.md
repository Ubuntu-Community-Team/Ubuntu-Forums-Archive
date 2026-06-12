---
title: "GRUB Error 5 - nothing will boot"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by izziere on 2009-09-06
My laptop has a single hard drive with 3 partitions: Vista, Vista recovery partition and Ubuntu 8.04.  For some time it has booted well from GRUB.

I installed an XP VM on virtualbox and it all went well.  When I shutdown, though, it would no longer boot up (and yes, the CD drive is empty!)  I get GRUB Error 5 and then silence.

I believe I may have stuffed up the MBR.

So, here is the output of fdisk -l:

```
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x447f284d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10629    85377192    7  HPFS/NTFS
/dev/sda2           18008       19457    11647125    7  HPFS/NTFS
/dev/sda3           10630       18007    59263785    5  Extended

Partition table entries are not in disk order

```

Now this morning there was an sda5.

As Google is apparently my friend I managed to find boot_info_script and this little gem, run via Ubuntu live CD says:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x447f284d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   170,754,446   170,754,384   7 HPFS/NTFS
/dev/sda2         289,282,455   312,576,704    23,294,250   7 HPFS/NTFS
/dev/sda3         170,754,885   289,282,454   118,527,570   5 Extended
Invalid MBR Signature found
Empty Partition


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="561A89B81A8995A1" TYPE="ntfs"
/dev/sda2: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

All-in-all, not a satisfactory day.  Can anyone help me please?

---

### Post by presence1960 on 2009-09-06
well your Ubuntu partitions are gone! They are no longer there. First you need to follow the advice given for sda1 and sda2. Boot the Ubuntu Live Cd and choose "try ubuntu without any changes". When the desktop loads open a terminal and run this command : ```
mount -t ntfs-3g /dev/sda1 sda1 -o force
``` then look on the desktop for the icon for that sda1. Right click and choose unmount.

do the same for sda2 by running this command in terminal ```
mount -t ntfs-3g /dev/sda2 sda2 -o force
``` Then look for the icon on desktop for sda2 and unmount it by right clicking and choosing unmount.

if the commands don't work because of permissions put sudo in front of them.

If this does not work I hope you made a set of bootable recovery CDs/DVDs prior to this. Because you can not mount your recovery partition to restore your factory image.

---

### Post by izziere on 2009-09-06
Thanks mate.

Mounting and unmounting worked, but GRUB was still throwing its toys out the pram, so out come the recovery disks.

Again.

Thanks for trying.  Just glad I have all my files saved centrally on a server.  Which reminds me, I must back them up this year.

---

### Post by presence1960 on 2009-09-06
> **izziere said:**
> Thanks mate.

Mounting and unmounting worked, but GRUB was still throwing its toys out the pram, so out come the recovery disks.

Again.

Thanks for trying.  Just glad I have all my files saved centrally on a server.  Which reminds me, I must back them up this year.

GRUB will not work because there is no menu.lst since your Ubuntu partitions are gone.

---

