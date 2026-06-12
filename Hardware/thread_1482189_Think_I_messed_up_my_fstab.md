---
title: "Think I messed up my fstab"
date: 2010-05-13
forum: Hardware
---

### Post by Elvish Legion on 2010-05-13
I was trying to install NWN and I noticed that I was unable to manually mount/unmount my dvd drive.  Noticing it was not in fstab I edited and added it 

fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7cf8e291-cd9c-495b-8122-5586cf40f242 none            swap    sw              0       0
```
```

sudo lshw -C disk 
  *-disk                  
       description: ATA Disk
       product: ST980411ASG
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: DE13
       serial: 5TF020TY
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00063e30
  *-cdrom
       description: DVD-RAM writer
       product: DVD+-RW TS-U633A
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/_DVD
       version: D200
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/_DVD
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted
```



```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7cf8e291-cd9c-495b-8122-5586cf40f242 none            swap    sw              0       0
/dev/sr0  	/cdrom  	auto  	ro,noauto,user,exec  
```

The first fstab is my original  the second is the edited one.

Now when I insert a cd or dvd the drive just spins and spins.  I am unable to watch dvd movies (I could before the edit) its like the computer doesn't detect the cd

---

### Post by dino99 on 2010-05-13
are the codecs installed (look at synaptic and medibuntu repo)

---

### Post by Elvish Legion on 2010-05-13
Reverting my fstab to my original one everything works fine but if I try to edit my fstab so I can control my cdrom (IE mount /cdrom) I can no longer play dvds

---

### Post by IcarusR on 2010-05-13
My fstab has my cd/dvd drive listed as /dev/scd0 

> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

You could try using the above line in your fstab.

---

### Post by Elvish Legion on 2010-05-13
Here is how I fixed it

Edited my fstab: Added 
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0  to my fstab 

Then I did

sudo mkdir /media/cdrom0

Thats what my problem was.  /media/cdrom0 did not exist so the system wasn't sure what was going on

[Source]("http://www.linuxconfig.org/HowTo_mount_cdrom_in_linux") of info

---

