---
title: "FSTAB Problem"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by TmP on 2008-04-09
Hey Peoplez!

I have a bit of a bugger - Hardy mounted my FAT32 partitions as read only root owned ....

Can you please help me configure my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=dbc2094e-88b3-4b4d-8d16-bb04abb21941 /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=fa50933c-cebd-4f47-bf44-252747e97938 /home           ext3    defaults        0       2
# /dev/sda1
UUID=0434-0DE3  /media/sda1     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=47F7-FE48  /media/sda9     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=fcbca012-8629-4902-93f7-cc13e3c6514b /mimi           ext3    defaults        0       2
# /dev/sda8
UUID=6b570e88-c07d-45ed-9a83-7f9421facf8e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 

Thank you SO much!

---

### Post by TmP on 2008-04-09
Hey!

Nobody's helping and Im doing stupid stuff to my fstab...

This may be my last restart..

Help?

---

### Post by Princey on 2008-04-09
You'd have to manually mount the partition. Give me a minute let me locate an old thread where I gave the directions. Will edit my post with the link.

Here's the [link]("http://ubuntuforums.org/showthread.php?t=471578").

---

### Post by sisco311 on 2008-04-09
according to the fstab the partitions are mounted with:
user = root
group = plugdev

read/write/execute permission for user(root)
read/write/execute permission for group(plugdev)
no permissions for others

```
id
```to check if you are a member of the plugdev group

```
ls -al /media/sda1
```to check if the partition is mounted with the correct permissions and owner

what happens when you mount the partition manually:
```
sudo umount /dev/sda1
sudo mount -t vfat -o utf8,umask=007,gid=46 /dev/sda1 /media/sda1
```

---

### Post by TmP on 2008-04-09
Hey!

Thanks for your suggestions!

I would like to edit the FSTAB so that it mounts the sda1 and sda9 partitions for read-write access for all users

As you pointed out, currently the key points at the root. Would you have any suggestions on how to change this?

# /dev/sda1 UUID=0434-0DE3  /media/sda1     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda9 UUID=47F7-FE48  /media/sda9     vfat    utf8,umask=007,gid=46 0       1

I always have such problems with my new releases of Ubuntu

Also, when loading the system, fsck pops up every time and performs a check quoting that this check was last done in 2005. I guess this is due to the installed defaults.

I'm looking for a solution that will fix this once and for all. ThankX!

---

### Post by Yellow Pasque on 2008-04-09
You could change the umask to 000 or put your users in the plugdev group.
```
gksudo gedit /etc/group
```
Also, you can change the last digit in each fstab line to 0 to avoid the fsck check. Just remember to check it manually.

---

### Post by TmP on 2008-04-10
Hey!

Thank you for the suggestion, but wouldn't putting my users in the plugdev group endanger my system?

Thanx!

---

### Post by Yellow Pasque on 2008-04-10
Well, if you're looking for a "sanitary" solution, change the gid=46 to 100 and add your users to that group.
users:x:100:

---

### Post by TmP on 2008-04-10
And that did the job!

Sweet.

Thanx!

[IMG]http://mine.icanhascheezburger.com/completestore/Youdaman128417894696386637.jpg[/IMG]

---

