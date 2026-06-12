---
title: "Dual boot"
date: 2008-08-25
forum: General Help
---

### Post by kidstar64 on 2008-08-25
I have Ubuntu installed and i want to install vista along side it on the same drive, how woudl i go about doing this. ive tried before but windows had overridden the boot loader and i could not boot into ubuntu.

---

### Post by cybrsaylr on 2008-08-25
I have 2 dual boot systems that run fine.
You have to install Windows first then install Ubuntu so there will be no problems with the boot loader.

---

### Post by -Zeus- on 2008-08-25
incorrect.  go ahead and boot to the live cd, and make vista a nice big partition.  then install vista to that, boot back to the live cd, and open a terminal.  you should follow what this looks like.

```
ubuntu@ubuntu:~$ sudo grub

grub> root (hd0,0)
grub> setup (hd0)
grub> exit
```

That will restore the GRUB boot-loader.  Then you will have to add the windows entry by hand.  Boot to Ubuntu and type ```
sudo gedit /boot/grub/menu.lst
```

Put something like this at the bottom.
```
title   Windows Vista
root (hd0,1)
makeactive
chainloader +1
```

NOTE that you will have to replace (hd0,**0**) and (hd0,**1**) with whatever your partition numbers are.  do a sudo fdisk -l, see what is mounted on "/".  It will probably be /dev/sda1.  Subtract 1 from the last number, in this case you end up with "0".  Then do a "ls /dev/sda*" and replace (hd0,1) with 1 less than the highest numbered sda.  so if ls /dev/sda* says ```
sda
sda1
sda2
```, then your GRUB entry would be root(hd0,1)

---

### Post by mb_webguy on 2008-08-25
You can install Windows after Ubuntu, but then you'll have to reinstall GRUB.

---

### Post by Patb on 2008-08-25
> You have to install Windows first then install Ubuntu so there will be no problems with the boot loader.
Not quite. Kidstar, although it is usually simplest to install windows first and ubuntu last, there is an option to repair the MBR if you do it the other way around. See [this link]("http://ubuntuforums.org/showthread.php?t=224351").

Hope this helps. Cheers, Pat.

---

