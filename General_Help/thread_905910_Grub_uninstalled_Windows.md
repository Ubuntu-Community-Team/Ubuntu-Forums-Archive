---
title: "Grub uninstalled Windows"
date: 2008-08-30
forum: General Help
---

### Post by pat_riedacher on 2008-08-30
I have linux and windows dual booted but i had a really horrible windows virus so i had to reinstall windows which got rid of my Grub is there any way i can install it again either on windows or the boot cd/install disc for ubuntu?

---

### Post by pat_riedacher on 2008-08-30
please help someone

---

### Post by cdtech on 2008-08-30
Boot into the Live CD.

When you get to the desktop open a terminal and enter:
```
sudo grub
```
This will give you a "grub" prompt, type:
```
$ grub > find /boot/grub/stage1
```
This will return the location of the stage1 file. Whatever was returned from the find command use it in the next command:
```
$ grub > root (**hd?,?**)
```
Again use the value from the find command i.e. if find returned (**hd0,1**) then you would enter root (**hd0,1**)
Next enter the command to install GRUB to the MBR (of the primary drive):
```
$ grub > setup (**hd0**)
```
This installs GRUB to the MBR of the primary drive (hd0).
Exit grub:
```
$ grub > quit
```

---

### Post by pat_riedacher on 2008-08-30
thanks for the help

---

### Post by cdtech on 2008-08-30
> **pat_riedacher said:**
> thanks for the help

Your welcome, good luck.......

---

### Post by pat_riedacher on 2008-08-30
yeah sory didn't work i got this error sent back
> 
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

grub> 



---

### Post by pat_riedacher on 2008-08-30
please help me someone

---

### Post by cdtech on 2008-08-30
I just did a reply. Have you tried to do a reboot yet?

---

### Post by pat_riedacher on 2008-08-31
yesh i did i send you a reply back saying it what should i try now?

---

### Post by cdtech on 2008-08-31
What do you get when you try:
```
grub-install /dev/sda1
```

---

### Post by pat_riedacher on 2008-08-31
> root@ubuntu:~# grub-install /dev/sda1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:~# 

thats what i get

---

### Post by pat_riedacher on 2008-08-31
i really don't wantto have to install linux again

---

### Post by caljohnsmith on 2008-08-31
OK, to help troubleshoot your problem, from the Live CD please post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda6 /mnt
ls -l /mnt/boot/grub
cat /mnt/boot/grub/menu.lst
```
After that, run testdisk:
```
sudo testdisk
```
Select "no log", then select your HDD, "proceed", "Intel", and then "analyze". Please post the output of that screen.

---

