---
title: "BOOTLOGD enabled -&gt; /var/log/boot.log does not exist"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by cccc on 2009-07-09
hi

I have enabled bootlog in /etc/default/bootlogd:```
 
BOOTLOGD_ENABLE=Yes
``` on Jaunty with Gnome, restarted the machine, but NO boot log messages.
Is it a BUG?

---

### Post by cccc on 2009-07-13
perhaps a BUG?

---

### Post by cccc on 2009-07-18
I've done the Upgrade to Karmic.

/var/log/boot exists, but it has only this one entry:```

(Nothing has been logged yet.)
```

---

### Post by cariboo on 2009-07-18
Are you having boot problems? the reason bootlogd isn't enabled by default, is that it slows boot time by quite a bit.

---

### Post by Rocket2DMn on 2009-07-18
Do you have /var mounted on a separate partition?  Perhaps you don't have write access?  If you think this may be the case, please post the output of
```
sudo fdisk -l
df -h
mount
```

---

### Post by cccc on 2009-07-18
```

# sudo fdisk -l

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64f3fb95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7593    60990741    7  HPFS/NTFS
/dev/sda2            7594        8900    10498477+  83  Linux
/dev/sda3            8901        9725     6626812+   f  W95 Ext'd (LBA)
/dev/sda5            8901        9163     2112516   82  Linux swap / Solaris
/dev/sda6            9164        9725     4514233+  83  Linux

# df -h
System plików            rozm. u&#380;yte dost. %u&#380;. zamont. na
/dev/sda2             9,7G  4,8G  4,5G  52% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  340K 1012M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  236K 1013M   1% /dev
tmpfs                1013M     0 1013M   0% /dev/shm
/dev/sda6             4,2G  1,9G  2,2G  46% /home
/dev/sda1              59G   13G   46G  22% /windows

# mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw,relatime)
/dev/sda6 on /home type ext3 (rw)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ania/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ania)

```

---

### Post by Rocket2DMn on 2009-07-18
According to [https://launchpad.net/ubuntu/+source/sysvinit](https://launchpad.net/ubuntu/+source/sysvinit) bootlogd was disabled in Ubuntu because upstart handles its functionality now.  Is there a particular reason you are trying to use it?

---

### Post by cccc on 2009-07-18
bootlogd seems to be not installed.

# /sbin/bootlogd
bash: /sbin/bootlogd: No such file or directory

I cannot find a bootlogd program in /usr directory:

# find /usr -type f -name "bootlogd"
#

Perhaps bootlogd was in Ubuntu forgotten or not installed by default.

Under Debian Etch, Lenny etc. it works perfectly.

---

### Post by Rocket2DMn on 2009-07-18
It's not a bug, the link I gave you in my last post tells us that it was intentionally removed from Ubuntu.  Ubuntu uses Upstart to control init scripts as system boot.  I think Debian uses sysv-rc-init or some such program, and RHEL uses the chkconfig/service utility.

---

### Post by akwala on 2009-07-25
> **Rocket2DMn said:**
> According to [https://launchpad.net/ubuntu/+source/sysvinit](https://launchpad.net/ubuntu/+source/sysvinit) bootlogd was disabled in Ubuntu because upstart handles its functionality now. 

Where can one find the Upstart log? If logging needs to be enabled, how can one do it?

---

### Post by akwala on 2009-11-09
> **akwala said:**
> Where can one find the Upstart log? If logging needs to be enabled, how can one do it?
See:

[LIST]
[*][http://www.linuxquestions.org/questions/linux-general-1/howto-workaround-broken-upstart-boot-logging-746468/#post3637957](http://www.linuxquestions.org/questions/linux-general-1/howto-workaround-broken-upstart-boot-logging-746468/#post3637957)
[*][https://bugs.launchpad.net/upstart/+bug/328881](https://bugs.launchpad.net/upstart/+bug/328881)
[/LIST]
 
****

---

### Post by robhauge on 2009-11-16
Can someone please give a simple answer? How to enable startup log on 9.10 server ?

I will use it to debug some problems with an usb to serial converter. The usb to serial converter worked with kernel 2.6.28.

---

