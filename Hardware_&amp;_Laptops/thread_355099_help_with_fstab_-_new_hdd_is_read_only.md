---
title: "help with fstab - new hdd is read only"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by nfriedly on 2007-02-06
I just got a new sata hard drive and I followed this guide [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) to install it and everything went perfect up to the point that the guide stopped. (fstab)

I can get the drive to show up fairly easily, but I can not get it to become writable.

here's what my current fstab is:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=25b5b8e1-a377-4373-b4d3-782de2ad52f1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=acb88dc8-c6d7-4240-b3f3-f20500c6edc3 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
# windows - added by nate
/dev/hdb1    /media/windows ntfs  nls=utf8,umask=0222 0    0
/dev/sda1    /media/500g 	ext3	defaults,rw	0	0
```

when I log in, 500g is on my desktop and it's read only.


I've tried everything I could think of for the options:
rw
rw,user
defaults
defaults,errors=remount-ro
rw,user,auto,exec,sync,suid,dev
and a lot more...

any ideas? here's what my sudo lshw -C disk puts out in case that helps:

 ```
 *-disk                  
       description: SCSI Disk
       product: WL500GSA1672
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WOL240005296
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@1:0.0.0,1
          logical name: /dev/sda1
          capacity: 465GB
          capabilities: primary
  *-disk:0
       description: ATA Disk
       product: ST3120023A
       vendor: Seagate
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 3.33
       serial: 3KA0Y2N8
       size: 111GB
       capacity: 111GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 108GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          capacity: 2957MB
          capabilities: extended partitioned partitioned:extended
  *-disk:1
       description: ATA Disk
       product: SAMSUNG SP1604N
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: TM100-24
       serial: S013J10X799544
       size: 149GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
     *-volume
          description: HPFS/NTFS partition
          physical id: 1
          bus info: ide@0.1,1
          logical name: /dev/hdb1
          capacity: 149GB
          capabilities: primary bootable
  *-cdrom:0
       description: CD-R/CD-RW writer
       product: ATAPI CD-RW 52XMax
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 220D
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdc
  *-cdrom:1
       description: DVD reader
       product: Pioneer DVD-ROM ATAPIModel DVD-114 0125
       vendor: Pioneer
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: E1.25
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio dvd
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdd
```

Thanks in advance ):P

---

### Post by taurus on 2007-02-06
Replace the last line in /etc/fstab with this line.

```
/dev/sda1    /media/500g 	  ext3    defaults     0	 1
```
Now, you just need to change the ownership from root to whatever your login name is, assuming it's **nfriedly**, of /media/500g.

```
sudo chown -R **nfriedly**:**nfriedly** /media/500g
```
Reboot and see if you, **nfriedly**, can write to /media/500g now.

---

### Post by nfriedly on 2007-02-06
that did it! thanks!

UPDATE:

I went and edited the wiki entry a bit: [https://help.ubuntu.com/community/InstallingANewHardDrive#head-4f68b98d10cc828f4f3c3bba92aff84a1e31d4c6](https://help.ubuntu.com/community/InstallingANewHardDrive#head-4f68b98d10cc828f4f3c3bba92aff84a1e31d4c6)

Think you could take a look and make sure it seems accurate?

---

### Post by WW on 2007-02-07
One suggestion: According to 'man fstab', the last digit (the fs_passno field) of your entry for this disk should be 2, not 1. 
> The sixth field, (fs_passno), is used by the fsck(8) program to  determine the order in which filesystem checks are done at reboot time.  The root filesystem should be specified with a fs_passno of  1,  and  other filesystems  should  have a fs_passno of 2.

---

### Post by taurus on 2007-02-07
> **nfriedly said:**
> 
I went and edited the wiki entry a bit: [https://help.ubuntu.com/community/InstallingANewHardDrive#head-4f68b98d10cc828f4f3c3bba92aff84a1e31d4c6](https://help.ubuntu.com/community/InstallingANewHardDrive#head-4f68b98d10cc828f4f3c3bba92aff84a1e31d4c6)

Think you could take a look and make sure it seems accurate?

If you want to use gedit as your text editor, then you need to use gksudo, not sudo since you will run into all kind of trouble later.  Therefore, it would look like this.

```
gksudo gedit /etc/fstab
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by nfriedly on 2007-02-07
Alright, got that patched up a bit. 

I have one more question though: I remember it saying something about forcing a fscheck every 20 mounts or every 180 hours (or something like that). Does that apply even if the fs_passno is set to 0?

---

### Post by taurus on 2007-02-07
If you set the last digit to 0, then there won't be any checking or fscking at all.

---

### Post by red1916 on 2007-02-08
Hi,

I had quite similar problem as you. I wanted to install a new HD as Vfat.  

Anytime I mounted the new installed HD it will remove write permissions for users so only root could write on it. This only happend with Vfat filesystem, not with ext3.

Check the file /etc/mtab and edit the file for you new HD. Mine was like this... 

/dev/hdb1 /media/hdb vfat rw,nosuid,nodev 0 0

and I changed to 

/dev/hdb1 /media/hdb vfat rw,utf8,umask=007,gid=46 0 0


For the options I just copy the ones that were written for Hda. This is the HD were ubuntu was installed originally.

now, any user can access to that hd

---

### Post by nfriedly on 2007-02-08
yea I think it has something to do with permissions / ownership - yours has a umask and gid. Mine I did chown on. I only log in as me, so that isn't a problem.

Either way, we're both working and that's what counts ^_^

---

### Post by charles nicholls on 2007-03-09
I had just found a very windowy way to alter permissions.
I have just installed a sata drive and found it needed root to open, In the terminal type "sudo nautilus" and browse to the drive, right clicking  on the drive and selecting properties brings up a window that allows changing permissions. I didnt think it would work but after a restart, surprisingly it does. I can now write to the drive.

---

### Post by taurus on 2007-03-09
> **charles nicholls said:**
> I had just found a very windowy way to alter permissions.
I have just installed a sata drive and found it needed root to open, In the terminal type "**sudo nautilus**" and browse to the drive, right clicking  on the drive and selecting properties brings up a window that allows changing permissions. I didnt think it would work but after a restart, surprisingly it does. I can now write to the drive.

I think you should use "gksudo nautilus" instead of "sudo nautilus" next time.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by charles nicholls on 2007-03-15
Thanks for that, can you tell me what the difference it makes?

---

