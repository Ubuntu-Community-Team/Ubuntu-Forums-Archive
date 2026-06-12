---
title: "CD/DVD drive not visible in ubuntu"
date: 2012-04-01
forum: Hardware
---

### Post by jamieofm on 2012-04-01
Hi all, i posted this below in Hardware originally but havent got anywhere with that, have spent several hours searching on the net. I know my drive works as i can run a windows boot cd and it would boot from the cd. 

I am new to Ubuntu and am having trouble with getting my system to read my DVD drive / CD drive. 

The drive i know is fine & works perfectly under windows. However it does not show up in Ubuntu. 

I am using Ubuntu 11.1. 

I have read the forums and tried a few things, typing 'mount' gives the following output

```
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jamie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jamie)
```


the command cat /etc/fstab gives the following

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=f40b564f-e99d-4908-b508-aa9eeb1d0f7e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e988b1a6-8980-42dc-bcfc-0f54ce360b01 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=9855fd20-ee0b-4bce-a1a7-726d97b77914 none            swap    sw              0       0
```


The output of 'sudo lshw -C disk' gives 

```
*-disk                  
       description: ATA Disk
       product: SAMSUNG SP2504C
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: VT10
       serial: S09QJ1GL623770
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0002aa7f
  *-disk
       description: ATA Disk
       product: SAMSUNG SP1604N/
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: TM10
       serial: S0DNJ10YB03388
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0003d240
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdd
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sde
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sdf
```

This command 'sudo hdparm -I /dev/dvd' gives:

/dev/dvd: No such file or directory

The output of 'sudo dmesg | grep -i dvd' OR 'sudo dmesg | grep -i CD-ROM

gives absolutely nothing. 

I tried the Disk Utility package and that does not show up the DVD / CD-ROM

'ls -al /dev/hd*' gives
ls: cannot access /dev/hd*: No such file or directory

same for 'ls -al /dev/sr*'

Any help much appreciated !

---

### Post by CharlesA on 2012-04-02
Can you post the entire output of:

```
lshw
```

I checked on one of my boxes and it was listed as:

```
 *-cdrom
                description: DVD reader
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio dvd
                configuration: status=nodisc

```

---

### Post by jamieofm on 2012-04-02
Ok, 

So I have solved this problem. Lots of searching etc led me to pull the DVD / CD drive out of the system and have a look if it was set to 'Slave' or 'Master' via the pins on the rear of the player. 

The switch was set to 'Slave', i moved this across to 'Master' replaced the drive in the PC hooking it up again to it's connections and hey presto everything is fine ! Plays DVD's and audio CD's etc no problem. 

Solved. 

Now maybe someone smart can explain why Ubuntu does not like the drive set as Slave whilst windows doesnt seem to care. 

Hope this helps someone else.

---

### Post by CharlesA on 2012-04-02
Was it hooked as slave on its own channel? I know Windows can be touchy about that too.

It all depends on your BIOS and how it reports the hardware to the OS.

---

### Post by jamieofm on 2012-04-02
Sorry CharlesA, not sure what you mean by 'it's own channel'. The drive must have been set to 'slave' since the machine was bought, so installed like that in the factory. Never had a problem with it previously. 

Anyway, making that change seemed to cure the issue. I don't understand why that would be or even the difference between 'Master' and 'Slave' as far as DVD drives are concerned.

---

### Post by CharlesA on 2012-04-02
I meant, was it hooked up to the same cable the hard drive was or was it on it's own cable?

---

