---
title: "softRAID reliability concerns - Broken mirrors"
date: 2008-06-20
forum: Hardware
---

### Post by ericcat on 2008-06-20
Firstly, huge thanks to all the people who have posted their experiences and solutions here in the past.  You've helped me out big time.

Now comes my problem.  I've got a fairly new system up and running sweetly.  I'm impressed, my wife is impressed with Ubuntu Hardy.

I've built the system around a Gigabyte mainboard and AMD AM2 CPU.  I have two 160GB SATA drives with filesystems and swap configured at installation time as software RAID 1 mirrored. Whilst the mainboard can support hardware RAID, it's really fakeRAID and it didn't work for me. 

After installation and daily use I didn't really bother to check the status of the RAID config until I started playing with Nagios.

Now, I find with great regularity that I have broken mirrors.  For example:
```
paul@eric:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid1 sda5[0] 
      129916992 blocks [2/1] [U_] 
      
md2 : active raid1 sda3[0] sdb3[1] 
      5116608 blocks [2/2] [UU] 
      
md1 : active raid1 sda2[0] sdb2[1] 
      25599488 blocks [2/2] [UU] 
      
md0 : active raid1 sda1[0] sdb1[1] 
      200704 blocks [2/2] [UU] 
      
unused devices: <none> 
```

This usually involves me doing up to four "mdadm --add" commands to resilver the mirrors.

Here's the output from "df -h":
```
Filesystem            Size  Used Avail Use% Mounted on 
/dev/md1               25G  6.2G   17G  27% / 
varrun                1.9G  124K  1.9G   1% /var/run 
varlock               1.9G     0  1.9G   0% /var/lock 
udev                  1.9G   92K  1.9G   1% /dev 
devshm                1.9G   12K  1.9G   1% /dev/shm 
lrm                   1.9G   43M  1.8G   3% /lib/modules/2.6.24-19-generic/volatile 
/dev/md0              190M   84M   97M  47% /boot 
/dev/md3              123G   15G  103G  13% /home 
gvfs-fuse-daemon       25G  6.2G   17G  27% /home/paul/.gvfs
``` 

Here's my /etc/fstab:
```
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/md1 
UUID=2abc6276-416c-43a2-994f-b85ddc254f90 /               ext3    relatime,errors=remount-ro 0       1 
# /dev/md0 
UUID=ea94129d-6ed2-4c96-a1d2-800fab941152 /boot           ext3    relatime        0       2 
# /dev/md3 
UUID=dae7bacc-d640-4af1-a229-ba7e81fc22a0 /home           ext3    relatime        0       2 
# /dev/md2 
UUID=48e645b5-d72c-4387-a2c9-b93ed1de8f6e none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0 
```

Has anyone encountered this problem?  Any fixes?
I first thought that is was caused by an automatic backup running when I shut down the machine, but the broken mirrors still occur now that I have stopped automatic backups.

---

### Post by am4c130d on 2008-06-20
I have a similar setup and do not experience this problem.  The main difference between your setup and mine is that I built mine long after install and use device names and not UUIDs in the fstab.

After running blkid, mdadm --detail and fstab -l, I concluded that the there were many contradictory UUIDs spplicable to each physical disk partition and array, that the device names were reliable and specific id for actual array block devices, and independent of the device labels assigned during boot so they met the same criteria as the UUIDs.  I am sure that there is a UUID that is appropriate for each array, I just wasn't confident of which one to use.  

I've subsequently confirmed that I can change the disk device names allocated during boot by moving my SATA connectors around, thus changing the members in /proc/mdstat, without any issues to reliable booting etc.

As you are using two disks, it seems unlikely that one array becomes unstable, whereas the other three are stable, unless the individual array is not being assembled correctly.  If that were the case, then the array itself is either not being reference correctly, or it was not built correctly.  I would recommend using the device names in fstab and see if that increases the relability or not.  If it does, it is probably the UUIDs that you are using that are not the correct ones for the array to be correctly assembled.  If it does not, back off the data on /home, stop the array, delete the array (this is actually hard to do), confirm that the superblock is erased, and then rebuild the array.  For me, erasing the superblock was the last step between dubious operation and very reliable operation.

Other things to check, verify that the block type of the devices making the array are set to fd  - linux RAID - as I've had some weirdness there as well.

I hope this helps.

Thanks

Alan

---

### Post by ericcat on 2008-06-20
Hi Alan,

Thanks for the pointers.  I've changed my fstab file to point to the actual /dev/md? devices rather than UUID and will monitor performance.

The underlying devices are all of type "mdraid" according to "blkid".

I'd like to get this stable before I move on to converting /home to an encrypted partition (something I should have done on install, oh well).

---

### Post by ericcat on 2008-06-22
I found these and similar lines in my messages file:

```
Jun 21 22:49:59 eric kernel: [  445.961130]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 21 22:50:04 eric kernel: [  449.525985] ata2: port is slow to respond, please be patient (Status 0xd0)
Jun 21 22:50:09 eric kernel: [  451.744266] ata2: device not ready (errno=-16), forcing hardreset
Jun 21 22:50:09 eric kernel: [  451.744273] ata2: hard resetting link
Jun 21 22:50:09 eric kernel: [  451.951132] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 21 22:50:09 eric kernel: [  451.961682] ata2.00: configured for UDMA/133
Jun 21 22:50:09 eric kernel: [  451.961695] ata2: EH complete
Jun 21 22:50:09 eric kernel: [  451.962477]          res 51/84:f0:4f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Jun 21 22:50:10 eric kernel: [  452.097135] ata2: soft resetting link
Jun 21 22:50:10 eric kernel: [  452.164932] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 21 22:50:10 eric kernel: [  452.175490] ata2.00: configured for UDMA/133
Jun 21 22:50:10 eric kernel: [  452.175498] ata2: EH complete
Jun 21 22:50:10 eric kernel: [  452.176272]          res 51/84:f0:4f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Jun 21 22:50:10 eric kernel: [  452.310945] ata2: soft resetting link

```

The drive in question has power and is spinning, but I think I may have a faulty SATA cable.  It is loose in the drive's socket and easily falls out.  It looks like the securing clip has broke.  Will replace the cable.

Simple hardware problem after all!

---

