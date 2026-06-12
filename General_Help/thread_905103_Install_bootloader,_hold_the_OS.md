---
title: "Install bootloader, hold the OS?"
date: 2008-08-30
forum: General Help
---

### Post by MaxIBoy on 2008-08-30
I need to install a bootloader on a hard drive without installing an OS. Basically, Windows XP doesn't like being on the second hard drive, and the second hard drive doesn't have a bootloader on it.


Ideally, I'd just pick the second hard drive in the BIOS boot menu when I want to boot Windows. Then, this newly installed bootloader would kick in. Otherwise, if I select the other hard drive, my current GRUB installation will kick in.


I'd prefer GRUB, because then I could just copy over the right menu.lst entry. However, any bootloader will do.

---

### Post by p_quarles on 2008-08-30
This should still work:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by MaxIBoy on 2008-08-30
So, if my first hard drive (the one which already has GRUB on it) is hd0, and my second hard drive (the one with Windows XP) is hd1:
```
sudo grub
find /boot/grub/stage1
root (hd0,<ubuntu installation partition>)
setup (hd1) #note that I typed setup hd1 instead of setup hd0
quit
```

Would this work?


My other option is to just unplug the first hard drive, and install some random Linux distro to the empty space on the second hard drive, and let that distro install GRUB. However, I was planning on growing my XP partition to fill that hard drive, and it's also an ugly solution.

---

### Post by p_quarles on 2008-08-30
> **MaxIBoy said:**
> 
Would this work?
As far as I can see, yes.

More importantly, I don't think you can damage anything by trying that, so it's worth doing.

---

### Post by MaxIBoy on 2008-08-30
I'll try it tomorrow (too late tonight, I need to sleep, I don't feel "sharp" right now.) And if my system becomes unbootable, it's your fault, okay?;)

---

### Post by MaxIBoy on 2008-08-30
Well, it didn't fix the problem, but nothing broke.

---

### Post by caljohnsmith on 2008-08-30
If you have Grub on your first HDD, I think the solution to your problem is much simpler than installing Grub on the Windows HDD and switching boot order. Just edit your Grub's menu.lst as follows:
```
title  Windows
root   (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
That fools the Windows HDD into thinking it is the first in the boot order, and it will boot correctly. If Windows is not on the first partition of your second HDD, make sure you modify the (hd1,0) accordingly. Let me know how it goes.

---

### Post by EmanresuusernamE on 2008-08-30
From what I can tell, you just need to change your boot.ini file in your windows partition.  Could you post your C:\boot.ini file?

---

### Post by MaxIBoy on 2008-08-30
> **caljohnsmith said:**
> If you have Grub on your first HDD, I think the solution to your problem is much simpler than installing Grub on the Windows HDD and switching boot order. Just edit your Grub's menu.lst as follows:
```
title  Windows
root   (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
That fools the Windows HDD into thinking it is the first in the boot order, and it will boot correctly. If Windows is not on the first partition of your second HDD, make sure you modify the (hd1,0) accordingly. Let me know how it goes.


I'll try that, thanks.





> **EmanresuusernamE said:**
> From what I can tell, you just need to change your boot.ini file in your windows partition.  Could you post your C:\boot.ini file?```
[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer

```


Think I may see the problem. I don't know how to understand that .ini file, but from the looks of it Windows think it's on the first disk, second partition (which is no longer true, I use the new hard drive for Linux now and the new disk is now the first disk; my old disk now has only one partition.)

---

### Post by caljohnsmith on 2008-08-30
> **MaxIBoy said:**
> 
```
[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)[COLOR="Red"]partition(2)[/COLOR]\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer

```
Think I may see the problem. I don't know how to understand that .ini file, but from the looks of it Windows think it's on the second partition (which is no longer true, I use the new hard drive for Linux now.)
Yes, if Windows is on the first primary partition, the above should use partition(1). That previous Windows entry I gave you for menu.lst assumes your Windows is on the first partition, so it should work. If you have any more problems though, please post the output of:
```
sudo fdisk -lu
```

---

### Post by MaxIBoy on 2008-08-30
All right, I'll try what you've suggested, let me just get a bootCD in there and go.

---

