---
title: "GRUB Error 18 with windows hard drive"
date: 2008-11-05
forum: General Help
---

### Post by winrowc on 2008-11-05
I have a hard drive with a windows installation on it, and another which I am currently using with ubuntu. I want to be able to transfer the video files on the first hard drive to my ubuntu one, and then wipe that windows one and just use it with ubuntu. Im sure if I just wiped it now and connected it, I wouldn't be having many problems, but I need those files first. I tried connecting it to see if ubuntu could at least recognize the drive, but I got a grub error (error 18) and couldn't do anything. Is there any hope for me or am I going to have to burn those video files somehow and everything else on that hard drive and then wipe it? And if I do end up having to do that, and just connect it (making sure the jumpers are correct), will it just work?

---

### Post by caljohnsmith on 2008-11-05
So without the Windows drive connected, you can boot the Ubuntu drive just fine? If that is true, when you connect the Windows drive, can you set your BIOS to still boot the Ubuntu drive first? That should solve your problem I think, but let me know how it goes.

---

### Post by winrowc on 2008-11-11
I tried that and its still happening. GRUB Error 18 seems to mean that its trying to boot to Ubuntu (that's why its using GRUB, my Windows drive doesnt have GRUB) but it cant. So my problem is with GRUB and that I have a new drive connected that it wasn't originally setup with. Is there a way I can fix this in GRUB? like I say, the drives are properly set up as master and slave, its just GRUB that has the problem with the new configuration, even though Ubuntu is still the Master.

---

### Post by ciscosurfer on 2008-11-11
.
.
[http://ubuntuforums.org/showthread.php?t=791034](http://ubuntuforums.org/showthread.php?t=791034)
.
.

---

### Post by caljohnsmith on 2008-11-11
While you have your Windows drive connected, if you can boot your Live CD, how about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And next, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

