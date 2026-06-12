---
title: "SATA Software Raid0 Troubles"
date: 2004-10-21
forum: Hardware &amp; Laptops
---

### Post by darrenism on 2004-10-21
Having some troubles configuring my sata raid0 in Ubuntu.  I have successfully created a mountable, useable disk stripe within ubuntu but as soon as I reboot it reports:

mount: wrong fs type, bad option, bad superblock on /dev/md0,
       or too many mounted file systems
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)

I press  CTRL-D and I can continue booting.

At the partitioning phase of the installer, I flagged 3 SATA drives as to be part of a raid and then created the raid through the menus.

It won't mount.



My fstab:

# &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;       &lt;dump&gt;  &lt;pass&gt;
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/md0        /nirvana        ext3    defaults        0       2
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

My Raidtab

raiddev /dev/md0
        raid-level 0
        nr-raid-disks 3
        nr-spare-disks 0
        persistent-superblock 1
        chunk-size 4
        device /dev/sda
        raid-disk 0
        device /dev/sdb
        raid-disk 1
        device /dev/sdc
        raid-disk 2

Help?  I'm almost positive I used the installer correctly to set up the raid, but I could have screwed up.  Is ext3 the filesystem to use?  

If I use the steps listed on 
[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html)  it all works but as soon as I reboot it dies.

Help!

---

