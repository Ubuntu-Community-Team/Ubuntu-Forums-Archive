---
title: "DVD's run, but not Data CD's?"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by MaintainerZero on 2007-06-06
Hello all,

I have been using Ubuntu since the launch of Feisty on my Dell Inspiron 6000 laptop.  I have had a few minor issues, but nothing to write home about, as I've been able to troubleshoot almost everything on my own.  This particular issue, though, has me stumped.

My optical drive is able to read and play DVD's with no issue.  It is also able to read and play audio CD's.  For some reason, however, it is completely unable to mount data CD's.  I put a data CD in the drive, and get the following error:

Cannot mount volume.
Invalid mount option when attempting to mount the volume 'UDF Volume'.

I've tried various fixes in other threads on issues similar to this one (from my own limited perspective), including installing UDFtools, but still can't get this to work.  I have tried a few different data CD's, and have verified that they work on other machines (though they are all Windows machines).

Anyone able to help me resolve this?  I desperately need access to this data.

edit: here's the results of some tests...not sure how to interpret this stuff, but it clearly isn't working

$ dmesg | tail
[  278.048000] sr0: Current: sense key: Medium Error
[  278.048000]     Additional sense: L-EC uncorrectable error
[  278.048000] end_request: I/O error, dev sr0, sector 716048
[  278.048000] Buffer I/O error on device sr0, logical block 179012
[  278.076000] sr 1:0:0:0: SCSI error: return code = 0x08000002
[  278.076000] sr0: Current: sense key: Medium Error
[  278.076000]     Additional sense: L-EC uncorrectable error
[  278.076000] end_request: I/O error, dev sr0, sector 716052
[  278.076000] Buffer I/O error on device sr0, logical block 179013
[  278.552000] UDF-fs: No fileset found

$ sudo mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0312c4a-4817-4022-b9f2-b7667fb383df /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8f7840f3-4626-4280-856c-194f1c16b6c6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto user,noauto     0       0

---

### Post by MaintainerZero on 2007-06-06
updated with a few command line tests' data

---

