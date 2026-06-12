---
title: "Unable to Write CD's, Mounts Write-Protected"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by TheIdiotThatIsMe on 2008-02-29
Howdy!

I've started having troubles with CD's in Ubuntu. I currently run Ubuntu 7.10, and never had a problem until recently. For some reason, when I put a CD into my drive it gives me the error:

Cannot mount volume.
Unable to mount the volume 'CDROM'.

Details
mount: block device /dev/scd1 is write-protected, mounting read-only mount: Not a directory.


However, if I enter a DVD in, it is able to mount the DVD just fine. This happens on both my internal and external drives. Around the same time, I also noticed that my other partitions stopped automounting and now require a password and then mounts to "disk" and "disk-1" respectively.

---

### Post by jan quark on 2008-02-29
can you please post the output of these terminal commands

```
mount
```
```

cat /etc/fstab
```
```

ls -la /media
```

---

### Post by TheIdiotThatIsMe on 2008-02-29
Mount:

```
anthony@Phoenix:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

cat fstab:

```
anthony@Phoenix:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0744094d-70da-41e6-a1a5-c61260bcbda1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1EF42F7BF42F5475 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=45D3-ECF8  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=cd6744e0-f495-4b95-81c6-07e305eb5459 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec     0       0

```

ls -la /media:

```
anthony@Phoenix:~$ ls -la /media
total 20
drwxr-xr-x  5 root root 4096 2008-02-29 11:28 .
drwxr-xr-x 22 root root 4096 2008-02-19 16:08 ..
lrwxrwxrwx  1 root root    6 2007-11-06 01:27 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-11-06 01:27 cdrom0
lrwxrwxrwx  1 root root   45 2007-11-14 07:12 .directory -> /etc/kubuntu-default-settings/directory-media
-rw-r--r--  1 root root    0 2008-02-29 11:28 .hal-mtab
lrwxrwxrwx  1 root root   42 2007-11-14 07:12 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxr-xr-x  2 root root 4096 2007-11-06 01:27 sda1
drwxr-xr-x  2 root root 4096 2007-11-06 01:27 sda4

```

Any ideas?

---

### Post by Yellow Pasque on 2008-02-29
Can you run a few more commands for me?
```
sudo lshw -C disk
cd /dev; ls -l | grep cd
```

---

### Post by TheIdiotThatIsMe on 2008-03-02
sudo lshw -C disk:

```
anthony@Phoenix:~$ sudo lshw -C disk
[sudo] password for anthony:
  *-disk                  
       description: SCSI Disk
       product: ST980829A
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.05
       serial: 3PK05BM8
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-4082N
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: CQ04
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
```

cd /dev; ls -l | grep

```
anthony@Phoenix:~$ cd /dev; ls -l | grep cd
lrwxrwxrwx 1 root   root             4 2008-03-01 13:55 cdrom -> scd0
lrwxrwxrwx 1 root   root             4 2008-03-01 13:55 cdrw -> scd0
lrwxrwxrwx 1 root   root             4 2008-03-01 13:55 dvd -> scd0
lrwxrwxrwx 1 root   root             4 2008-03-01 13:55 dvdrw -> scd0
crw-rw-rw- 1 root   tty         2, 221 2008-03-01 08:55 ptycd
brw-rw---- 1 root   cdrom      11,   0 2008-03-01 08:55 scd0
crw-rw---- 1 root   cdrom      21,   1 2008-03-01 08:55 sg1
lrwxrwxrwx 1 root   root             4 2008-03-01 13:55 sr0 -> scd0
crw-rw-rw- 1 root   tty         3, 221 2008-03-01 08:55 ttycd
anthony@Phoenix:/dev$ 
```

---

### Post by TheIdiotThatIsMe on 2008-03-12
Is there any other information that might help?

---

### Post by Yellow Pasque on 2008-03-12
> 
mount: block device /dev/scd1 is write-protected, mounting read-only mount: Not a directory.
I'm not sure why it's trying to mount /dev/scd1 (something wrong with HAL?).

Try linking scd1 to scd0
```
cd /dev
sudo ln -s scd0 scd1
```

---

### Post by TheIdiotThatIsMe on 2008-04-22
> **Temüjin said:**
> I'm not sure why it's trying to mount /dev/scd1 (something wrong with HAL?).

Try linking scd1 to scd0
```
cd /dev
sudo ln -s scd0 scd1
```

I have two seperate drives, one internal and one external. I mostly use the external one more often since the internal randomly pops out under use, and the external is scd1.

---

