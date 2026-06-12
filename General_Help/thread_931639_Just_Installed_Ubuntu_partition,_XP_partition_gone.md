---
title: "Just Installed Ubuntu partition, XP partition gone?!?!?!?!"
date: 2008-09-27
forum: General Help
---

### Post by tlovaj on 2008-09-27
Hey guys I just installed ubuntu on my dv6636nr laptop using the guide at this site [http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575).  I downgraded my lappy from vista to xp, and on the boot up where you can select partitions it says vista/longhorn but no xp.  selecting vista/longhorn gives me an error.  What did I do wrong help!!!

---

### Post by PocketDog on 2008-09-27
How did you downgrade, and what's the error you get?

---

### Post by dimeotane on 2008-09-27
I hear your pain... been there before.  Linux and Windows can coexist peacefully on the same machine, but it can be painful getting there.
I think you're talking about needing to restore your MBR master boot record.

google search topics like: "recover xp bootloader"
"XP MBR recovery" for more info

[http://www.neowin.net/forum/lofiversion/index.php/t292614.html](http://www.neowin.net/forum/lofiversion/index.php/t292614.html)
[http://www.brunolinux.com/01-First_Things_To_Know/Restoring_the_XP_MBR.html](http://www.brunolinux.com/01-First_Things_To_Know/Restoring_the_XP_MBR.html)


linux uses GRUB for it's bootloader.

[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)

---

### Post by dimeotane on 2008-09-27
I hear your pain... been there before.  Linux and Windows can coexist peacefully on the same machine, but it can be painful getting there.
I think you're talking about needing to restore your MBR master boot record.

google search topics like: "recover xp bootloader"
"XP MBR recovery" for more info

[http://www.neowin.net/forum/lofiversion/index.php/t292614.html](http://www.neowin.net/forum/lofiversion/index.php/t292614.html)
[http://www.brunolinux.com/01-First_Things_To_Know/Restoring_the_XP_MBR.html](http://www.brunolinux.com/01-First_Things_To_Know/Restoring_the_XP_MBR.html)


linux uses GRUB for it's bootloader.

[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)


It's quite possible the XP partition is still there, its just that the bootloader is not set up correctly to access it and boot windows XP.

---

### Post by tlovaj on 2008-09-27
is this something i'm going to have to do everytime?

---

### Post by tlovaj on 2008-09-27
HOw can i get it so that GRUB will see xp on boot up?

---

### Post by TeXtonyx on 2008-09-27
From what you've written so far, I can't tell that you have ever booted Windows XP.
Run fixmbr from your XP cd install disk, the option is in Recovery Console.
See if you can boot XP then. Then you can use a Ubuntu live cd to open a terminal and
then reinstall grub. It takes about 15 minutes, mostly loading the cd. The code:
sudo grub
grub> find /boot/grub/stage1
root (hd0,1) [just an example, use what the find command reports to you, this is "from"]
setup (hd0,1) [just an example, this is where it goes "to" setup (hd0) writes to the MBR
grub> quit
I've seen people spend hours trying to fix their grub menu.lst to boot XP when that
approach will never work because XP isn't bootable. So take the steps to ensure that
XP boots first since fixing grub to include XP and Ubuntu just means reinstalling grub.

---

### Post by tlovaj on 2008-09-28
Actually I've had xp for quite sometime, and decided to install ubuntu for school (sorry for the lack of information). After installing Ubuntu, the GRUB menu listed vista instead of xp as the other operating software. After trying to fix the problem with the suggestion (using xp cd and then going in to fix the boot.ini file with fixmbr/fixboo ) I received the \system32\hal.dll error. boot.cfg or trying to repair it has not been effective.  I'm down to the choice of re-installing xp and then installing ubuntu over it again.  But I'm not too sure if its going to work. Any ideas?

---

### Post by meierfra. on 2008-09-28
Are you still able to boot into ubuntu? (If not you need to reinstall Grub, click on FixGrub in my signature).

To fix your Windows problem we need more information.

Did you get any error messages when you tried to boot XP from Grub menu? 

Boot into  Ubuntu, open a terminal (Applications->Accessories->Terminal) and 
post the output of 

```
sudo fdisk -l
 
cat /boot/grub/menu.lst

sudo mount /dev/sdXY /mnt

ls /mnt

cat /mnt/boot.ini

```

(Here /dev/sdXY is  the device name of windows partion. Its something like /dev/sda2.  "sudo fdisk -l" tells you exactly what it is)

---

### Post by Sef on 2008-09-28
> Boot into  Ubuntu, open a terminal (Applications->Accessories->Terminal) and 
post the output of 

     Code:
     sudo fdisk -l
That it is needed to check if you overwrote XP.   That code will tell us.   If there is an NTFS there, then likely you did not overwrite XP.  If there is no NTFS there, then you overwrote XP.

---

### Post by Ms_Angel_D on 2008-09-28
> **tlovaj said:**
> is this something i'm going to have to do everytime?

Just for future reference you may want to check these tutorial's they have been quite handy to me ;)

[http://ubuntuforums.org/showthread.php?t=904645](http://ubuntuforums.org/showthread.php?t=904645)

---

### Post by TeXtonyx on 2008-09-28
meierfra is rather expert in fixing this kind of problem. Your drive is called sda, and your
first partition is sda1 where you normally find XP which is NTFS. sudo fdisk -l reports
which file system is installed on sda1. If you made a mistake and installed Ubuntu to the
same partition that XP existed upon, then you have overwritten XP and XP will need to 
be reinstalled. There is a slight amount of risk to resizing the XP partition which is a 
default choice during the install of Ubuntu from the live cd. I think it is better to resize 
the disk before installing Ubuntu, and leave the free space created as unallocated. Test
XP afterwards. The benefit is that now during the Ubuntu install one can choose to use
the largest unallocated space, and the size of that space has already been determined  by
you from your prior to Ubuntu install resizing. After that just follow the defaults. Also,
if it turns out you have to reinstall XP, you can decide how much of the disk you want
to use for XP then, so there will be no need to resize later. Vista is capable of resizing
disks but then to plan ahead with it you would've needed to know you wanted ubuntu.

---

### Post by davidryder on 2008-09-28
Assuming that your XP partition still exists and it exists on the first partition of the first hard drive, you can boot into Ubuntu and try this:

```
sudo gedit /boot/grub/menu.lst
```

Scroll down to the vista entry and change it to the following

```

title Microsoft Windows XP
root (hd0,0)
makeactive
chainloader +1 
```

---

