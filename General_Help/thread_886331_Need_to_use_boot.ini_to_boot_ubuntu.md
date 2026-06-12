---
title: "Need to use boot.ini to boot ubuntu"
date: 2008-08-11
forum: General Help
---

### Post by scuba steve12k8 on 2008-08-11
I installed Windows XP AFTER I installed Ubuntu, so the boot manager is acting all gay and whatever, I need to find out the way to have the boot.ini file so it will let me able to chose Ubuntu as well as Windows in the boot menu.

I am about to completely format, but may not... still thinkin about it, but if i do, i take it i should install windows first?

---

### Post by damoxc on 2008-08-11
You don't need to do a format, all you need to do is put in the Ubuntu cd, and then choose the "Rescue a broken system" option from the initial menu. The start of this will seem like the installer but that you will be presented with a list of options, one of which is "Reinstall Grub". Choosing this one will replace Windows' boot manager with grub which will allow you to boot into both Ubuntu and Windows.

---

### Post by sandysandy on 2008-08-11
have a look here

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

[http://ubuntuforums.org/showthread.php?t=236846](http://ubuntuforums.org/showthread.php?t=236846)

regards

---

### Post by scuba steve12k8 on 2008-08-11
> **damoxc said:**
> You don't need to do a format, all you need to do is put in the Ubuntu cd, and then choose the "Rescue a broken system" option from the initial menu. The start of this will seem like the installer but that you will be presented with a list of options, one of which is "Reinstall Grub". Choosing this one will replace Windows' boot manager with grub which will allow you to boot into both Ubuntu and Windows.

Thanks, This will save me tons of time :P

---

### Post by Mgiacchetti on 2008-08-11
Well, there is a way.

First, when you install Ubuntu, make sure to install grub (the advanced button at step 6 of 6 during install) to the linux drive NOT THE WINDOWS DRIVE.

If you have installed grub to the windows drive, you need to do recovery console from the xp cd and run a FIXMBR.

Now you need to [do grub]("http://ubuntuforums.org/archive/index.php/t-24113.html") on the Ubuntu partition

now after setup the computer will NOT see UBUNTU, this is ok.  Just boot to windows normally and go get a program called [BOOTPART]("http://http://members.aol.com/gvollant/bootpa22.zip")

put the exe in your c:\ drive, and drop to cmd prompt and c:\bootpart

this will display all your drives/partitions contained on your computer starting with 0 going to whatever 

find the number that corresponds with the LINUX NATIVE drive, this is Ubuntu, (if your first partition is windows and your second is ubuntu your choice will be 1)

Now type 
```

bootpart 1 c:\ubuntu.lnx LBA Ubuntu 8.04

```This will grab the Grub from partition 1 (actually the second partition) and save that as ubuntu.lnx, on the C drive, and add a line to BOOT.INI to give the option to boot to that at boot time.

---

