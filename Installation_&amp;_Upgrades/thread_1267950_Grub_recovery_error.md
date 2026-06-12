---
title: "Grub recovery error"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by iluvatar85 on 2009-09-16
Hello, 
I've recently installed Windows 7 in my notebook, but I've encountered a problem during the recovery of GRUB.
I've booted an ubuntu live cd, mounted all the partition, checked the disk order with ```
sudo fdisk -l
```, checked the list of disk device with ```
ls /dev/ | grep sd
```. 
Everything look perfectly good, I've done this many time so I didn't expect problems...
But when I enter in the grub interactive command line (grub> ), the command ```
root (hd0,2)
``` give me an error 21 disk not found, and I've seen that grub cannot recognize any disk since the use of the tab key with ```
root (hd
``` give me nothing.
The command ```
find /boot/grub/stage1
``` tells me that it couldn't find anything...
Now I'm struck with windows only, unable to restore the MBR. Any idea? Any solution?

Thank you in advice and forgive me for my English. :)


Edit: I've seen that there is a guide for the grub install, should I delete this thread and ask there?```

```

---

### Post by ajgreeny on 2009-09-16
If you are using 9.04 follow the guide below.  You did not say if you used the command **sudo grub** in the live CD.  If you did not, that may be the problem. I know a lot of this below is similar to what you did, but try again.

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by iluvatar85 on 2009-09-16
Thank you so very much, I didn't remember if I've run grub as super-user, 99% the problem is there. So lame of me. XD

Oook, let's go live.

Edit: Yes, there was the problem. Thank you! :D

---

### Post by ajgreeny on 2009-09-16
Whoopee!!!  Glad it was solved so simply.

---

