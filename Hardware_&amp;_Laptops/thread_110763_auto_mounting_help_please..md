---
title: "auto mounting help please."
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by PolarBear64 on 2005-12-31
Thanks in advance to any help.

I have a second hard drive that was windows NTFS well windows just went bye for good.

 #1     I used Gparted to reformat and repartition my second drive to 3 fat32 partitions

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10199    81923436   83  Linux
/dev/sda2           10200       14023    30716280   83  Linux
/dev/sda3           14024       14593     4578525   83  Linux

 #2     now i am having trouble getting them auto mounted,

        I created the three new entries in the media folder like when I made the windows version of this drive show up.
                              /media/flac
                              /media/ogg
                              /media/backup              (i am working on some music archives and conversions)

then I tried to setup /dev/sda1 to auto mount and when I run sudo mount -a it tells me unknown filesystem type 'fat32'

here is my fstab also

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1	/media/flac	fat32	unmask=000 0 0

any insight to this still learning Linux user would be greatly appreciated.

---

### Post by PolarBear64 on 2005-12-31
ok,  got the hard drive partitions mounted now need to figure out how to set the permisions so I can read/write to them

---

### Post by PolarBear64 on 2005-12-31
Ok, got it all working,

Switched to only using 2 partitions how ever.

so what I did was-

1)    used gparted and partitioned my second drive.

2)    made new folders in media
                sudo mkdir /media/yourpartitionname
                repeat sudo for all partitions

3)   edited read/write permision on folders
                sudo chmod -R 777 /media/yourpartionname
                repeat for all partion folders in media that you created

4)   edited fstab
                **_NOTE_**- you can backup your fstab if you want now cant remember the command as I didnt worry about this (it was easy enough to remove the entries I made when I messed up)
                
                sudo gedit /etc/fstab
                you will need to know your drive designation now also and what file type
                I used fat32 so if I ever have to I can hopefully read this drive in windows
                my drive was /dev/sda1 and /dev/sda2 designating my partitions.
                so I added-
                    /dev/sda1/     media/yourpartitionname     vfat     umask=000  0  0
                add entries for all partitions you made then save and close
                only know this will work for fat32 partitions

5)     then ran     sudo mount -a
                and walla I had my new partitions.  now if I can figure out how to take them off the desk top and just use them through the nautilus file browser I will be in buisness.

Hope this helps some one else out a bit as I was having trouble finding what I needed in the forum I assembled this from about 9 different posts and the wiki.

---

### Post by Gandalf on 2006-01-03
even if you finally got it working, just for the record, keep [thid](http://ubuntuguide.org/#windows) in your bookmark

---

