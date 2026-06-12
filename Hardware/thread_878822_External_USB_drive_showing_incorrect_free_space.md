---
title: "External USB drive showing incorrect free space"
date: 2008-08-03
forum: Hardware
---

### Post by twistedneck on 2008-08-03
My new external Western Digital usb drive is formated using ex3.  its got 591MB free according to gparted, but shows only 20.6 gig free on that drive (when viewing in samba share smb://twistedubuntu/sandbox OR when viewing under /mnt/usb650 - same) - also, i tried copying more than 21gigs to that drive and it stops at 20.6g.

Why is the full size of the external usb drive not showing up as free space in nautilus?  the partition is 591MB free according to Gparted.  Yes, i did reformat, no change - ex3, same free space, same problem. hmmm..

Even weirder, why is it showing the same exact free space as my normal internal hard drive?  both show 20.6g free?

fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=a754b0df-2458-40f0-a757-1ee5c09c8a91 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e8ce185e-4fcd-4fd5-ba62-32a13a10f27c none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1 	/mnt/usb650 auto defaults,umask=000   0    0

```




samba share in smb.conf

```

[sandbox]
path = /mnt/usb650
#valid users = sandbox
guest ok = yes
read only = no
writable = yes
create mask = 0777
directory mask = 0777

```

Finally, trying fdisk -l it can see my new drive on /dev/sdb, but df -h doesn show it.
```
  
twistedneck@twistedubuntu:~$ sudo fdisk -l
[sudo] password for twistedneck: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbace54bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281   83  Linux
twistedneck@twistedubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   47G   21G  70% /
varrun                506M  1.4M  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   52K  506M   1% /dev
devshm                506M  204K  506M   1% /dev/shm

```

---

### Post by twistedneck on 2008-08-03
Success! 

to get all the external usb hard drive space to show up i had to change formats to NTFS.

I reformatted my external hard drive with NTFS and changed the call out accordingly in the fstab file to nfts-3g.

to format the drive with NTFS i used gparted, but i had to add on an option called ntfsprogs.  Then the file option for ntfs came right up in gparted.

Now i can see all of the drive space on my external hard drive.

---

### Post by twistedneck on 2008-08-04
Warning for all you usb hard drive users who want to map that new drive to a samba share..

Ubuntu will auto mount the usb drive like it or not even if you went through the trouble of mounting it already in fstab.  Ubuntu just picks the next available mount /dev/sdc1 and mounts it to /media/disk.  Then it disables your mount, in my case /dev/sdb1 was mounted to /mnt/usb650.

my samba share is now /media/disk.

oh yea, dont forget to turn off the drive timeout or sleepmode.  you can do that via command line

```
sudo hdparm -S 0 /dev/sdb1
```

or edit your /etc/hdparm.conf file by adding it on at the very end of the file.

```
command_line {
       hdparm -S 0 /dev/sdb1
}

```

---

