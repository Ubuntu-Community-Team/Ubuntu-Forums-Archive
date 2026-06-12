---
title: "Grub Error 15 Please HELP!!"
date: 2008-09-05
forum: General Help
---

### Post by shengzhoumi on 2008-09-05
When I try to boot Ubuntu, the system goes straight to Grub 1.5 Error 15.

I was working on optimizing Ubuntu with this tutorial:[http://www.ubuntu-unleashed.com/2008/04/tweak-and-optimize-ubuntu-linux-boot.html](http://www.ubuntu-unleashed.com/2008/04/tweak-and-optimize-ubuntu-linux-boot.html). However, it froze my system when I tried to restart. Now I can't even get to the through grub because of error 15.

I have tried following this tutorial on how to fix grub ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)), however, I cannot get past step 2 because it gives me: Error 15: File not found. 

As of now, I can only access Ubuntu through a live cd. Help would be really appreciated!!!

---

### Post by Fixman on 2008-09-05
> **shengzhoumi said:**
> When I try to boot Ubuntu, the system goes straight to Grub 1.5 Error 15.

I was working on optimizing Ubuntu with this tutorial:[http://www.ubuntu-unleashed.com/2008/04/tweak-and-optimize-ubuntu-linux-boot.html](http://www.ubuntu-unleashed.com/2008/04/tweak-and-optimize-ubuntu-linux-boot.html). However, it froze my system when I tried to restart. Now I can't even get to the through grub because of error 15.

I have tried following this tutorial on how to fix grub ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)), however, I cannot get past step 2 because it gives me: Error 15: File not found. 

As of now, I can only access Ubuntu through a live cd. Help would be really appreciated!!!

Post your /boot/grub/menu.lst file.

---

### Post by shengzhoumi on 2008-09-05
It's empty

---

### Post by caljohnsmith on 2008-09-05
When you say your menu.lst is empty, are you looking at /boot/grub/menu.lst on your Live CD? If so, you need to mount your Ubuntu partition from the Live CD and access menu.lst that way:
```
sudo fdisk -lu
```
Figure out which is your Ubuntu partition in the form sdaX, use that:
```
sudo mount /dev/sdaX /mnt
cat /mnt/boot/grub/menu.lst
ls -lR /mnt/boot
```
Please post the output of all the above commands, including fdisk.

---

### Post by shengzhoumi on 2008-09-05
Here are the outputs of all the commands:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008c540

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74846834    37423386   83  Linux
/dev/sda2        74846835    78140159     1646662+   5  Extended
/dev/sda5        74846898    78140159     1646631   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
cat: /mnt/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ ls -lR /mnt/boot
ls: cannot access /mnt/boot: No such file or directory

---

### Post by drs305 on 2008-09-05
SuperGrub Disk: [http://www.supergrubdisk.org/index.php]("http://www.supergrubdisk.org/index.php")

It easily handles Grub Error 15 and will make your life simpler... If you don't use it this time, keep it handy for the next time.  ;-)

---

### Post by caljohnsmith on 2008-09-05
OK, from the Live CD, let's first make sure sda1 is not mounted:
```
sudo umount /dev/sda1
```
Now we'll mount it to a known location:
```
sudo mount /dev/sda1 /mnt
```
Next show the contents of the root directory:
```
ls -l /mnt
```
Please post the output of all the above.

---

### Post by shengzhoumi on 2008-09-05
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ ls -1 /mnt
lost+found

---

### Post by caljohnsmith on 2008-09-05
Shengzhoumi, from the output you posted it looks like your Ubuntu partition, sda1, is entirely empty except that "lost+found" folder. It doesn't look like Ubuntu was even installed. I don't know what happened, but you should try reinstalling Ubuntu again.

---

### Post by shengzhoumi on 2008-09-05
Oh Crap. I had a lot of important files on there for school. Crap Crap Crap...

---

### Post by caljohnsmith on 2008-09-05
> **shengzhoumi said:**
> Oh Crap. I had a lot of important files on there for school. Crap Crap Crap...
If that is the case, then don't reinstall just yet; you can use a program like "photorec" to try and recover your files. But can you give some details of what happened between when Ubuntu was working and when all of the sudden it stopped working, and now you seem to have an entirely empty Ubuntu partition?

Also, look inside that "lost+found" folder and see if it has any of your files. If you still have sda1 mounted, just do:
```
ls /mnt/lost+found
```
If it says permission denied, just do:
```
sudo -i
ls /mnt/lost+found
```

---

### Post by wolfen69 on 2008-09-05
while in the live cd, do ```
sudo su
```then ```
nautilus
``` then navigate to /boot/grub/menu.lst on your ubuntu drive. copy and paste the file here.

---

