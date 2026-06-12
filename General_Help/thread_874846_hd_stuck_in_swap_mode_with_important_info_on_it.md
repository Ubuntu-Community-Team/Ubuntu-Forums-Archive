---
title: "hd stuck in swap mode with important info on it"
date: 2008-07-30
forum: General Help
---

### Post by shortridge11 on 2008-07-30
I use psydm to manage my little home file server.  It was fine for a while, but then it started doing weird things, like changing the names of the mounted discs and duplicating them and etc.  I could usually fix it after messing with it for 30 minutes and a lot of rebooting (weird for ubuntu...) but i didn't give it any thought.  Now one of my hds is stuck in swap mode and i have no idea how that happened.  I checked out the filesystem on GParted and it still says it's mounted as xfs.  However, the mountpoint is gray and unaccessible.  I'm running 7.10 ubuntu, and i would appreciate any help with this.

also- while checking through the other partitions in psydm, for some reason the normal swap partition in psydm says that it's mounted as xfs for some reason, but GParted says it's still swap.  I'm confused as hell.  I tell psydm to forget the config file for the real swap, but if i retart my machine then it goes back to thinking the real swap is an xfs partition.  I tried unchecking the "Swap Device" checkbox in options for the hd that isn't a swap drive, but when i click ok it just goes back to being in swap mode and that doesn't change anything.

---

### Post by vanadium on 2008-07-30
You will probably need to fix one and another by hand. psydm can be a very handy tool, but it has limitations and might have caused some inconsistencies in your /etc/fstab.

You might already tell if there is a problem with /etc/fstab from the command "sudo mount -a".

---

### Post by shortridge11 on 2008-07-30
***@********:~$ sudo mount -a
mount: /dev/sda1 already mounted or /media/TV2 busy
mount: according to mtab, /dev/sde1 is already mounted on /media/TV2
mount: special device /dev/sdc2 does not exist
mount: special device /dev/sdc3 does not exist

that's what it tells me? i'm not sure what to do with that.  And that only gave me the breakdown for one harddrive.  How do i look at the other 5?

---

### Post by vanadium on 2008-07-30
For sure your /etc/fstab is not in order. If you want to have us look into the issue, then post the output of

```

sudo fdisk -l
mount
cat /etc/fstab

```

---

### Post by shortridge11 on 2008-07-30
***@*****:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000183d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   82  Linux swap / Solaris
/dev/sda2   *         244        2675    19535040   83  Linux
/dev/sda3            2676       60801   466897095   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005d4a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ca427

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000347af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux

Disk /dev/sde: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000efe41

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       77825   625129281   83  Linux

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6fc86fc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   83  Linux
***@*****:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-15-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/Movies1 type xfs (rw)
/dev/sdd1 on /media/Movies2 type xfs (rw)
/dev/sda3 on /media/TV type xfs (rw)
/dev/sde1 on /media/TV2 type xfs (rw)
/dev/sdf1 on /media/Movies3 type xfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sdc1 on /media/Misc type xfs (rw)
***@*****:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0
# /dev/sda2
UUID=ffe4990f-3825-42a5-be41-0fbeb7028a1d  /               ext3         defaults,errors=remount-ro  0  1
# /dev/sdb1
UUID=01cae850-1ce5-4744-a08d-356f921d2619  /media/Movies1  xfs          defaults                    0  2
# /dev/sdc1
UUID=eb6a8b74-7f33-404c-8d3d-7c2eb1a184c0  /media/Movies2  xfs          defaults                    0  2
# /dev/sda1
UUID=b8d517c1-ac84-42cd-8b49-a297afc918dc  none            swap         sw                          0  0
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec            0  0
/dev/sdb1                                  /media/Movies1  xfs          defaults                    0  0
/dev/sda3                                  /media/TV       xfs          defaults                    0  0
/dev/sdd1                                  /media/Movies2  xfs          defaults                    0  0
/dev/sda1                                  /media/TV2      xfs          defaults                    0  0
/dev/sde1                                  /media/TV2      xfs          defaults                    0  0
/dev/sdf1                                  /media/Movies3  xfs          defaults                    0  0
/dev/sdc1                                  /media/Misc     swap         defaults                    0  0
/dev/sdc2                                  /media/sdc2     ext3         defaults                    0  0
/dev/sdc3                                  /media/TV       xfs          defaults                    0  0


-i went to gparted and i could somehow mount it, and now i can access it, but psydm still thinks it's a swap.  Is there a way to fix the inconsistancies between my fstab file and psydm?

---

### Post by vanadium on 2008-07-30
Your /etc/fstab does contain references to sdc2 and sdc3 while these do not exist on your system. Thus, delete the lines starting with /dev/sdc2 and /dev/sdc3 from your /etc/fstab.

Also remove the line starting with /dev/sda1. This is in reality your swap partition which is already mounted above using its UUID.

According to the output of mount, all of your drives are mounted, despite the inconsistencies in your /etc/fstab.

After changing /etc/fstab, check whether "sudo mount -a" is still producing output. If it does not, then your /etc/fstab is consistent.

You probably should not use psydm anymore to manage your system.

---

### Post by shortridge11 on 2008-07-30
thanks for your help, it all works now.

---

### Post by finni100100 on 2009-12-08
i am having pretty much the same issue how ever my issue is that my sda is my 750GB SATA and my ubuntu 9.10 install is on sdb i have ran the scripts as mentioned above and my out put is as follows 

```
jason@SRV01:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002de2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91201   732572001   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001dfc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18707   150263946   83  Linux
/dev/sdb2           18708       19457     6024375    5  Extended
/dev/sdb5           18708       19457     6024343+  82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e10a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e7494

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       18389   147709611   83  Linux
/dev/sdd2           18390       19457     8578710   83  Linux

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4ab1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       19457   156288321   83  Linux
jason@SRV01:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
/dev/sdc1 on /media/sdc1 type ext4 (rw,noexec,nosuid,nodev)
/dev/sdd1 on /media/sdd1 type ext4 (rw,noexec,nosuid,nodev)
/dev/sdd2 on /media/sdd2 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /media/sde1 type ext4 (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/jason/.Private on /home/jason type ecryptfs (ecryptfs_sig=aab65ff4b0d41f2e,ecryptfs_fnek_sig=0e58278c4a462574,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/jason/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jason)
/dev/sda1 on /media/437b1160-80b9-492e-8ecf-cd8a022a6f26 type ext4 (rw,nosuid,nodev,uhelper=devkit)
jason@SRV01:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc          proc         defaults               0  0  
# / was on /dev/sdb1 during installation
UUID=22727a7d-0842-48fd-9e73-8dcce6408722   /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sdb5 during installation
#UUID=08b8b917-8146-47e1-9be7-196c224aa8d2  none           swap         sw                     0  0  
/dev/scd1                                   /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/scd0                                   /media/cdrom1  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/mapper/cryptswap1                      none           swap         sw                     0  0  
/dev/sdc1                                   /media/sdc1    ext4         user                   0  0  
/dev/sdd1                                   /media/sdd1    ext4         user                   0  0  
/dev/sdd2                                   /media/sdd2    ntfs         user                   0  0  
/dev/sde1                                   /media/sde1    ext4         user                   0  0  
uuid=437b1160-80b9-492e-8ecf-cd8a022a6f26   /media/437b1160-80b9-492e-8ecf-cd8a022a6f26    ext4         user                   0  0 
jason@SRV01:~$ 

``` 

any help would be greatly appreciated as the 750 is were my files for my media server is located and would like to be able to not have to manually mount the drive when it starts  

thanks in advance, finni

---

