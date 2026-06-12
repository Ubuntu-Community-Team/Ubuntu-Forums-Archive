---
title: "Help with disk mounting issues"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by Richard_2007 on 2007-04-03
Hello I have a sda type drive a new sata drive and have successfully loaded ubuntu edgy onto it. I partioned it as follows:

sda 1 root
sda 2 home
sda 3 swap

Now although fdisk finds it fine and in fact Im up on it right now. It is not in my mounted drives.

In etc/fstab it looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d143009a-3325-4b6b-a952-bf71b27607b0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=b16b8996-e57f-438e-bd2b-b81d624ac399 /home           ext3    defaults        0       2
# /dev/hda1
UUID=A674A85274A82751 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=423B-2BDF  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=B6C02F03C02EC987 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=ee1f39c3-19e5-43ad-b8e5-b5de129e5d79 /media/hdb2     ext3    defaults        0       2
# /dev/hdb3
UUID=4b174b83-c523-4ada-9f10-d8ee7f0c905b /media/hdb3     ext3    defaults        0       2
# /dev/sda3
UUID=53e8ffc4-f2a0-48c9-a2c7-1e989f3f7049 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

How do I get the sda 1 and 2 mounted in gnome so I can copy my old windoze doc files to home and also view linux files on sda 1?

Another issue is that Hdb4 doesnt appear in this table at all. How do I enable it?

Finaly will my old files be safe in home in the event of an upgrade or a reload?

Thanks so much
Richard:confused: :guitar:

---

### Post by Sammi on 2007-04-03
[www.ubuntuguide.org]("http://www.ubuntuguide.org/") offers some good info on this.

Specifically these two sections:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Hard_Drive](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Hard_Drive)

---

### Post by Richard_2007 on 2007-04-04
Thanks sammy. These links are helpful but deal only with windows ntsf or fat files while my sda drives are formated in linux ext. 

Nor do they address how safe it is to have data you wish to preserve on the sda2 drive set up as home.

I figure I have to edit the /etc/fstab table but am not sure what to put for linux type ext partitions.

Thanks so much

Richard:confused: :guitar:

---

### Post by jjordan on 2007-04-04
OK, stay with me here we are going to cover a little ground.

From your fstab file (BTW: great job posting that!) it looks like sda2 is mounted on /home.

Linux has a diffirent way of looking at drives, you will not get a drive letter for each drive like you do in Windows.  You don't list how large you made each partition but that will be a good way for you to see if your mounting plan is working.  It has been a while since I used Gnome but if you right click on the **/home** directory in Nautilus and look at the properties it should list the size, it may also list the device (such as /dev/sda2).  I believe that your sda2 partition is mounted just fine and you should be able to see that by looking at the size and device in Nautilus. 

It is safe to copy your files there and should not be effected if you reinstall Ubuntu or another Linux distribution.  (Just remember not to format that partition) There should be a directory with your user name inside the /home directory such as **/richard** that is where you should copy files you want access to. One thing to keep in mind though is that many of your configuration files will be written to your Home directory (such as /home/richard) so if you reininstall, some configuration files will remain.  

If several people are going to use the computer and you want them all to have access to these files then it would be better to mount it in a different location and give everyone access to it.  Write back and I will cover that if needed.


-j




The swap partition will not show up in Nautilus.

---

