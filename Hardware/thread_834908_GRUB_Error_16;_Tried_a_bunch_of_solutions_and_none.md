---
title: "GRUB Error 16; Tried a bunch of solutions and none of them work"
date: 2008-06-19
forum: Hardware
---

### Post by sithguy on 2008-06-19
I recently installed Ubuntu on a laptop(IBM Thinkpad T41) with Windows XP, on a partition specifically created for it. However, when I attempted to restart I get

```
GRUB Loading stage1.5


GRUB loading, please wait...
Error 16
```

I reinstalled GRUB two different ways, [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and
[http://ubuntuforums.org/showthread.php?t=196983](http://ubuntuforums.org/showthread.php?t=196983).

I tried using the Super GRUB disk but I get  
```
Error 15: File not found
Booting 'Not Lucky'
pause SGD has NOT succeeded
SGD has NOT succeeded
```


I also tried this:[http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Grub_solution](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems#Grub_solution)
but I continue to get the error.

I will provide any information you would like to know in order to help solve this problem.

Thanks in advance
-Sithguy

---

### Post by sithguy on 2008-06-20
I also attempted to use the fixmbr command in both a Windows XP and Windows 2003 disc but after this I get this when I boot up.

```
Error loading operation system
```

Still confused,
-Sithguy

---

### Post by sithguy on 2008-06-20
I tried to reinstall the GRUB boot-loader and now I'm getting a GRUB Geom Error.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
My advice is...erase "/" partition. Create fat32 partition in its place. Safe-Erase it. Format anew ext3 partition for "/". Install ubuntu again and after installation directly reboot into it. Look if you have any error messages showing up during install and reboot.

---

### Post by disneyfriedhistory on 2009-06-25
Any luck with this post?  This just happened to me as well. 

I have a T30, which is similar to the T41.  This morning I woke up and it was stuck, with the numlock and capslock keys flashing.  I tried to restart it and got the same message as sithguy.  

I haven't run any upgrades in a few days, but I have definitely restarted the computer a few times.  So I don't think it's associated with any upgrades.  

A few other things I've noticed: The CD/DVD drive likes to pop open randomly.  Earlier in the week I woke up to find them computer off (I know it was on when I went to bed, because it was supposed to wake me up!)  But this time, when I turned it on, it started up fine.  

Anyways, I'll post if i find a fix, but I would love to hear a solution before I start pecking around.

---

