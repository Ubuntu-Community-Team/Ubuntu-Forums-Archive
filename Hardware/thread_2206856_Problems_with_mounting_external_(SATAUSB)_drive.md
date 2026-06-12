---
title: "Problems with mounting external (SATA/USB) drive"
date: 2014-02-21
forum: Hardware
---

### Post by oygle on 2014-02-21
I have a 500 Gb external drive. It has a switch to use either USB or ESATA connection. I can use it okay with USB, but as there is a lot of files to copy to it, I would prefer to use the SATA/ESATA connection.

Have modified /etc/fstab to include the mount parameters. Reboot and the computer just hangs for about 5 mins at post BIOS, trying to auto detect the external drive I think. It does into Ubuntu and a screen with options to Skip, Wait, etc. All up it will not recognise the drive in ESATA mode. When I try to do a manual mount, I get an error message:


```
sudo mount -a
[sudo] password for fred: 
mount: special device [COLOR=#0000ff]UUID=43eb-0004[/COLOR] does not exist
```

Here is some info:

> fred@fred:~$ **sudo blkid**
/dev/sda1: UUID="[COLOR=#0000ff]43eb-0001[/COLOR]" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="[COLOR=#0000ff]43eb-0002[/COLOR]" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="[COLOR=#0000ff]43eb-0003[/COLOR]" TYPE="swap" 
fred@fred:~$ 
fred@fred:~$ **ls /dev/disk/by-uuid/ -alh**
total 0
drwxr-xr-x 2 root root 100 Feb 21 19:08 .
drwxr-xr-x 5 root root 100 Feb 21 19:08 ..
lrwxrwxrwx 1 root root  10 Feb 21 19:08 [COLOR=#0000ff]43eb-0001[/COLOR] -> ../../sda1
lrwxrwxrwx 1 root root  10 Feb 21 19:08 [COLOR=#0000ff]43eb-0002[/COLOR] -> ../../sda3
lrwxrwxrwx 1 root root  10 Feb 21 19:09 [COLOR=#0000ff]43eb-0003[/COLOR] -> ../../sda5
fred@fred:~$ 
fred@fred:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=[COLOR=#0000ff]43eb-0001[/COLOR] /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=[COLOR=#0000ff]43eb-0002[/COLOR] /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=[COLOR=#0000ff]43eb-0003[/COLOR] none            swap    sw              0       0
# / external hard drive - 500Gb                                                                                                                                                     
UUID=[COLOR=#0000ff]43eb-0004[/COLOR] /media/externaldisk               ext3    errors=remount-ro 0       1                                                                     
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0                                                                                                          
//192.168.1.100/Win95B  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0                                                                                              
fred@fred:~$                                                                                                                                                                     
fred@fred:~$ **sudo lshw -class disk**                                                                                                                                               
[sudo] password for fred:                                                                                                                                                          
  *-cdrom                                                                                                                                                                           
       description: CD-R/CD-RW writer                                                                                                                                               
       product: CD-RW SOHR-5239S                                                                                                                                                    
       vendor: LITE-ON                                                                                                                                                              
       physical id: 0.0.0                                                                                                                                                           
       bus info: scsi@5:0.0.0                                                                                                                                                       
       logical name: /dev/cdrom2                                                                                                                                                    
       logical name: /dev/cdrw2                                                                                                                                                     
       logical name: /dev/sr1                                                                                                                                                       
       version: 2S08
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: ST3500320AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SD15
       serial: 9QM5N21A
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0003fa35
  *-cdrom
       description: DVD-RAM writer
       product: DRW-2014S1T
       vendor: ASUS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 2TiB (2199GB)
fred@fred:~$ 
fred@fred:~$ **sudo blkid -o full -s UUID**
/dev/sda1: UUID="[COLOR=#0000ff]43eb-0001[/COLOR]" 
/dev/sda3: UUID="[COLOR=#0000ff]43eb-0002[/COLOR]" 
/dev/sda5: UUID="[COLOR=#0000ff]43eb-0003[/COLOR]" 
fred@fred:~$ 
fred@fred:~$ **/usr/bin/udisks --mount /dev/sdb**
Mount failed: Error mounting: mount: you must specify the filesystem type

fred@fred:~$ 
fred@fred:~$ **mount**
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext3 (rw)
gvfs-fuse-daemon on /home/fred/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fred)
//192.168.1.100/Win95B on /media/windowsshare type cifs (rw)
fred@fred:~$ 
fred@fred:~$ **ls -al /dev/disk/by-uuid/**
total 0
drwxr-xr-x 2 root root 100 Feb 21 19:08 .
drwxr-xr-x 5 root root 100 Feb 21 19:08 ..
lrwxrwxrwx 1 root root  10 Feb 21 19:08 [COLOR=#0000ff]43eb-0001[/COLOR] -> ../../sda1
lrwxrwxrwx 1 root root  10 Feb 21 19:08 [COLOR=#0000ff]43eb-0002[/COLOR] -> ../../sda3
lrwxrwxrwx 1 root root  10 Feb 21 19:09 [COLOR=#0000ff]43eb-0003[/COLOR] -> ../../sda5
fred@fred:~$ 


I can't figure out why this external drive won't mount in SATA mode. Hmm, GParted says /dev/sdb is 2 Tb (it's only 500 GB I think) and "unallocated"  ??

**PLEASE** note, wherever you see either [COLOR=#0000ff]43eb-0001, 43eb-0002, 43eb-0003 or 43eb-0004[/COLOR], these are not the correct UUID, only for display purposes.

---

### Post by sudodus on 2014-02-21
The computer I'm using right now is booted from an SSD connected via eSATA. There should be no particular difficulties with eSATA.

Your drive mounts properly when connected via USB. So the disk is OK, and the filesystem is OK.

I think something is wrong with the eSATA connection:

- the eSATA port in the computer (or electronics 'behind it')
- the cable
- the eSATA port in the external casing (or electronics 'behind it')

Can you test the external drive in another computer with eSATA?

Can you test with another cable?

Can you take the disk out of the casing and test it directly in a SATA port?

---

### Post by oygle on 2014-02-21
> **sudodus said:**
> The computer I'm using right now is booted from an SSD connected via eSATA. There should be no particular difficulties with eSATA.

I have been looking at a replacement computer (Dell Optiplex 9020) and would like to get a SSD. Good to know others are using them.

> **sudodus said:**
> Your drive mounts properly when connected via USB. So the disk is OK, and the filesystem is OK.

The KDE partition manager says the drive has unallocated space ? I looked in the sys logs and found ..

> 
21/02/14 19:49:59	asus64	kernel	[ 2530.037539] EXT3-fs (sdb): error: can't find ext3 filesystem on dev sdb.
21/02/14 19:49:59	asus64	kernel	[ 2530.062161] EXT4-fs (sdb): VFS: Can't find ext4 filesystem
21/02/14 20:31:17	asus64	ata_id[4262]	HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument


> **sudodus said:**
> I think something is wrong with the eSATA connection:

- the eSATA port in the computer (or electronics 'behind it')
- the cable
- the eSATA port in the external casing (or electronics 'behind it')

Can you test the external drive in another computer with eSATA?

Can you test with another cable?

Can you take the disk out of the casing and test it directly in a SATA port?

I will check all of that, except I don't have another cable and the other computer is only SATA (internal). I'm wondering if I should reformat it to EXT4 ? It does have todays latest backup on it though.

---

### Post by sudodus on 2014-02-21
> **oygle said:**
> The KDE partition manager says the drive has unallocated space ? I looked in the sys logs and found ..

Maybe something is bad with the disk (physical or logical defect) after all
> 
I will check all of that, except I don't have another cable and the other computer is only SATA (internal). I'm wondering if I should reformat it to EXT4 ? It does have todays latest backup on it though.

There are eSATA to SATA cables.

If you do not intend to connect the drive to Windows, it will be more efficient to use ext4.

If you want to or have to play very safely, you'll get another external drive, so that you will have a backup all the time. But I think the risk is small, that the computer (or file system) will be damaged while you re-format the external drive and make a new backup.

---

### Post by oygle on 2014-02-21
> **sudodus said:**
> Maybe something is bad with the disk (physical or logical defect) after all

Had to reboot numerous times, as a few boots just hung. One msg at BIOS was about HDD failure, so looks like that drive is on the way out. Last time I poweed down, powered off the external, powered up the external drive, rebooted, and a msg about 679 days since checking, so it went into checking the drive. I waiting 15 mins or so, then pressed "C", and when it booted up, the drive mounted okay. I can see it appear in Dolphin and KDE partition manager recognises it. Tried a few commands to see the UUID, and that worked out.

I still think a reformat would be the best idea long term, to EXT4.

---

### Post by sudodus on 2014-02-21
Have you checked the S.M.A.R.T. information? If OK, then go ahead and reformat it with ***gparted***!

Good luck :-)

---

### Post by oygle on 2014-02-21
Thanks, yes I ran a quick test and all the S.M.A.R.T. information was okay. Will reformat it tomorrow as it's late at night here.

Thanks for all your help.  :)

---

### Post by Morbius1 on 2014-02-21
> fred@fred:~$ **sudo blkid**
/dev/sda1: UUID="43eb-0001" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="43eb-0002" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="43eb-0003" TYPE="swap" 
Can someone explain to me how that's possible?

A UUID in the form of '43eb-0001' is that of a Fat32 partition not a Linux partition which has the form of "076426af-cbc5-4966-8cd4-af0f5c879646"

And this line references a UUID that does not exist:
> [COLOR=#0000cd]**UUID=43eb-0004**[/COLOR] /media/externaldisk               ext3     errors=remount-ro 0       1                                                                      
You might want to run blkid in a way that resets its cache:
```
sudo blkid -c /dev/null
```

---

### Post by SeijiSensei on 2014-02-21
```
21/02/14 19:49:59 asus64 kernel [ 2530.037539] EXT3-fs (sdb): error: can't find ext3 filesystem on dev sdb.
```

This error indicates you are trying to mount the entire device, /dev/sdb, as a filesystem.  You must mount the partitions on the device, e.g., /dev/sdb1, not the device itself.

---

### Post by oygle on 2014-02-21
> **Morbius1 said:**
> Can someone explain to me how that's possible?

A UUID in the form of '43eb-0001' is that of a Fat32 partition not a Linux partition which has the form of "076426af-cbc5-4966-8cd4-af0f5c879646"

And this line references a UUID that does not exist:

You might want to run blkid in a way that resets its cache:
```
sudo blkid -c /dev/null
```

My apologies. I have made a note to ignore the actual UUID.  :)

> **SeijiSensei said:**
> ```
21/02/14 19:49:59 asus64 kernel [ 2530.037539] EXT3-fs (sdb): error: can't find ext3 filesystem on dev sdb.
```

This error indicates you are trying to mount the entire device, /dev/sdb, as a filesystem.  You must mount the partitions on the device, e.g., /dev/sdb1, not the device itself.

Thanks for pointing that out. Am about to reformat the drive. Booting with it turned on takes a very long time, so I will just make one partition, and modify /etc/fstab accordingly to sdb1

---

### Post by oygle on 2014-02-22
GParted didn't take long. I thought it would reformat the whole drive, it just changed it to EXT4 and wiped all the data (which is okay)
The line in /etc/fstab for the mount of the external is .

> # / external hard drive - 500Gb                                                                                                                                                     
UUID=[COLOR=#0000FF]43eb-0004[/COLOR] /media/externaldisk               ext4    errors=remount-ro 0       1

and it is mounted but I'm having permission errors. What do I change to give access to "guest" and no password please ?

[COLOR=#0000FF]43eb-0004 [/COLOR][COLOR=#000000]is used for privacy purposes only.[/COLOR][COLOR=#0000FF][/COLOR]

---

### Post by sudodus on 2014-02-22
If the partition is mounted on /media/externaldisk and you can see it and manage it with sudo (superuser do alias root permissions), you are now able to give any directory the access you want.

For example:

You can make a shared subdirectory and give user/group/others read/write/execute permissions (or set permissions for the whole partition)
```

sudo mkdir /media/externaldisk/shared
sudo chmod ugo+rwx /media/externaldisk/shared

```

The files that are created in this directory should be available for all logged in users except guest. But if you copy files to the directory and preserve their permissions, you may have to change them afterwards to let the other users access them.

As guest I can see that a file exists in the directory /home/shared, but I am not allowed to open it. I can also see the /tmp directory and create files there, but not open files created by other users. I tried it in Lubuntu version 13.10.

I guess the system is made like this for security reasons and I don't know how to increase the permissions for the guest user.

If it is not OK for you to create normal user (for example 'friends') and set log in without password for 'friends', you have to wait for help from someone else.

---

### Post by oygle on 2014-02-22
Thanks for explaining that. Have done the **cmod** and all files under that now are okay for accessing, viewing, writing. I'm not concerned with other users, as I'm the only one who uses this computer. The only reason I mentioned **guest** was because another mount had this in /etc/fstab

> 
//192.168.1.100/Win95B  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0


so I thought I had to modify this line ..

> 
# / external hard drive - 500Gb
UUID=[COLOR=#0000FF]43eb-0004[/COLOR] /media/externaldisk               ext4    errors=remount-ro 0       1


in the same manner, to enable access to everyone else (other than sudo). It's all working fine now, so I will mark the thread as solved. Thanks for your help.

---

### Post by sudodus on 2014-02-22
I'm glad it works :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by oygle on 2014-02-23
I don't think I'm mounting this correctly, after having read  [https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/) , and the problems I had with [File system root has only 0 bytes disk space remaing]("http://ubuntuforums.org/showthread.php?t=2207307")

I only want the mount to be physical on the external drive, and logical on /dev/sda1. Seems it was physical on /dev/sda1 _as well as_ physical on the external drive.

I'm sure a "mount point" can be logical, acting like a symbolic link. Like in ~/.gvs path

Can someone explain please.

---

### Post by oygle on 2014-02-25
Now when I boot and the external drive is NOT powered on, Ubuntu hangs, no message. There used to be a message about "press S to skip".

Anyway, I press "S" even though there is no message, and Ubuntu boots up okay.

Also, Ubuntu at boot, tries 3 times to access a shared mount on another computer, when that computer is powered off.

It's not a clean boot, possibly the lines in /etc/fstab need modifying slightly.

> 
~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=[COLOR="#0000FF"]4ce2075s-8f01[/COLOR] /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation                                                                                                                                        
UUID=[COLOR="#0000FF"]4ce2075s-8f02[/COLOR] /home           ext3    defaults        0       2                                                                                         
# swap was on /dev/sda5 during installation                                                                                                                                         
UUID=[COLOR="#0000FF"]4ce2075s-8f03[/COLOR] none            swap    sw              0       0                                                                                         
# / external hard drive - 500Gb                                                                                                                                                     
UUID=[COLOR="#0000FF"]4ce2075s-8f04[/COLOR] /media/externaldisk               ext4    errors=remount-ro 0       1                                                                     
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0                                                                                                          
//192.168.1.100/Win95B  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0 


[COLOR="#0000FF"]4ce2075s-8f0n[/COLOR] are not the real UUID's

---

### Post by sudodus on 2014-02-26
If you use the option 'noauto' for the drives that are not always connected, the computer will not complain, but it will not automatically mount them either.

Modify /etc/fstab like this

```
# external hard drive - 500Gb                                                                                                                                                       
UUID=[COLOR=#0000FF]4ce2075s-8f04[/COLOR] /media/externaldisk                ext4 [COLOR=#ff0000]   noauto[/COLOR],errors=remount-ro 0       1                                                                      
```

-o-

So you should mount them manually when it is time to do it. If you use a label it will be easy.

For example the label 'data': Use the full and correct UUID to specify the external disk (instead of [COLOR=#0000FF]4ce2075s-8f04[/COLOR])

```
sudo tune2fs -L data UUID=[COLOR=#0000FF]4ce2075s-8f04[/COLOR]...
```

and then you can mount with

```
sudo mount -L data
```

---

### Post by oygle on 2014-02-26
> **sudodus said:**
> If you use the option 'noauto' for the drives that are not always connected, the computer will not complain, but it will not automatically mount them either.

Thanks for explaining that. I will modify /etc/fstab as you have instructed and give the external drive a label. I must say that 13.10 has less problems with mounting, than 12.04

Oygle

---

