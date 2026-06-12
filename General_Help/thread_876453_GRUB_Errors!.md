---
title: "GRUB Errors!"
date: 2008-07-31
forum: General Help
---

### Post by DivinityX on 2008-07-31
ok, about 6 hours ago i restarted my computer after formating one of my partions to a FAT32, i got a GRUB error 17 and couldn't get to the boot menu, so i put in the UBUNTU CD and reformatted it into an ext3. It got rid of the Error 17, but now i have Error 15. I searched it up and I've found it means file not found. Before I formated the partion, i had UBUNTU Studio on there, i never liked it, and it just took up space, so i got rid of it, so I'm pretty sure GRUB still thinks it exists and doesn't wanna start without it...I've looked into trying to reinstall GRUB but so far, everything i find is either old, doesn't work, or I don't have the tools to do it. can you help me out?

---

### Post by nbayiha on 2008-07-31
Did you try to reinstall grub using livecd ? 
You said the thread u were using are either old either useless for you , can you please tell us which thread you did read ?

Follow this link here i did explain how to reinstall GRUB .

[http://ubuntuforums.org/showthread.php?t=871762](http://ubuntuforums.org/showthread.php?t=871762)

---

### Post by rraj.be on 2008-07-31
To reinstall GRUB do the following

```
Boot into live cd
```

open terminal

type
```

sudo grub

find /boot/grub/stage1
```

if it returns like (hdX,Y)

type ```
root (hdX,Y)

setup (hdX)

quit

sudo reboot
```

thats it.

---

### Post by Diabolis on 2008-07-31
As the post above mine says, reinstall grub.

The errors:
> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.



> 
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.


Source: [grub page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by DivinityX on 2008-07-31
> **rraj.be said:**
> To reinstall GRUB do the following

```
Boot into live cd
```

open terminal

type
```

sudo grub

find /boot/grub/stage1
```

if it returns like (hdX,Y)

type ```
root (hdX,Y)

setup (hdX)

quit

sudo reboot
```

thats it.

I tried this but i still got Error 15...is there anything else i can do?

---

### Post by Diabolis on 2008-07-31
Reinstalling grub should work.

Steps to reinstall grub:
```

sudo grub
find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

So the output of the **find** command is the input of **root**.

If you can't boot, you can follow this steps from a live-cd.

Error 15: [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by DivinityX on 2008-07-31
IT WORKED!!! Thanks! But now i have another problem...

[http://ubuntuforums.org/showthread.php?p=5499925#post5499925](http://ubuntuforums.org/showthread.php?p=5499925#post5499925)

---

### Post by Diabolis on 2008-07-31
OK, don't forget to mark the thread as solved.

---

