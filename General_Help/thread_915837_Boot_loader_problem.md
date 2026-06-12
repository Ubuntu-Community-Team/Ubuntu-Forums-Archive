---
title: "Boot loader problem"
date: 2008-09-10
forum: General Help
---

### Post by deb_untu on 2008-09-10
I tried 8.04 live CD.Everything worked well.

Since I have 256 MB RAM,I choose the 2nd option(install option).

It could boot and start installing.

[U]Everything goes well until 94% of the installation and installer suddenly crashes without any message.

This happens exactly at 94% (configuring boot loader).
[/U]
I tried to install several times & the problem is the same.

I have Debian installed on (/dev/sda13)& it has installed its own grub on mbr. 
Kubuntu at (/dev/sda10), grub installed on its home partition.

I also tried to install after uninstalling the grub(on mbr) installed by the Debian (grub 0.97).

Still I have the same problem.

Please help me.
Thanks.

---

### Post by Titan8990 on 2008-09-10
I don't have a solution for you but out of curiosity, you have 13 partitions on a single drive???

---

### Post by deb_untu on 2008-09-10
> **Titan8990 said:**
> I don't have a solution for you but out of curiosity, you have 13 partitions on a single drive???

Not 13 only 10.
/dev/hda1  C:\

/dev/hda5 D:\
.....hda6 E:
........7 F:
........8 G:
........9 swap
........10 for Kubuntu 7.04
........11 for /home
........12 for above problem
........13 for Debina4.0

---

### Post by caljohnsmith on 2008-09-10
Deb_untu, having a Ubuntu install hang at 94% when it tries to install Grub is known bug that can be circumvented by formatting your Ubuntu partition to be ext2 instead of ext3. If that works and you get Ubuntu installed successfully, you can "upgrade" your file system from ext2 to ext3 with the following command:
```
sudo tune2fs -j /dev/sdXY
```
Replace sdXY with your Ubuntu partition of course. After that, I believe the only thing you will need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2". If you need help with that let me know.

---

### Post by deb_untu on 2008-09-10
> **caljohnsmith said:**
> Deb_untu, having a Ubuntu install hang at 94% when it tries to install Grub is known bug that can be circumvented by formatting your Ubuntu partition to be ext2 instead of ext3. If that works and you get Ubuntu installed successfully, you can "upgrade" your file system from ext2 to ext3 with the following command:
```
sudo tune2fs -j /dev/sdXY
```
Replace sdXY with your Ubuntu partition of course. After that, I believe the only thing you will need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2". If you need help with that let me know.

 deb_untu wants your help.
Yes I do need.

I had even tried to install 8.04 with ext2,reiserfs & ext3 with manual partition.
But problem exists.

I have installed Debian4.0 on /dev/hda13 with reiserfs and also kubuntu(7.04) on /dev/hda10 with reiserfs.

I have noticed during installation that the installer can identify the fileesystem (reiserfs) but not the disk used by the filesystem.

kubuntu(7.04) on /dev/hda10 with reiserfs.
which has gub installed on its own root partition.

if kubuntu 7.04 can work why can't 8.04 ?

seeking your help,
thanks.
deb_untu is online now   	Forward Message

---

### Post by caljohnsmith on 2008-09-10
Try installing Ubuntu without Grub, and if that works, then I can help you install Grub afterwards. Also, please post the following:
```
sudo fdisk -lu
```

---

### Post by deb_untu on 2008-09-11
> **caljohnsmith said:**
> Try installing Ubuntu without Grub, and if that works, then I can help you install Grub afterwards. Also, please post the following:
```
sudo fdisk -lu
```

I did as you said (installing 8.04 without grub);This time I could pass 94% but _at 95% I got this error message:_

" An error occurred while install packages

E:Directory 'target/var/log/apt' missing
The following packages are in a broken state.
          
                 ----blank---

_This may be due to an old installer image, or it may be due to a bug in some of the packages listed above._
More details can be found in /var/log/syslog. The installer will try to continue any way, but may fail at a later point, & will not be able to install or remove other packages(possibly including itself) ......
_You should first look for newer version of your installer image or failing that report the problem to your distributor_ "

I could not see any broken packages. This appears once again at 100% (error occurred while removing packages).

I have copied all files which were in /var/log (syslog & dmseg).
I can post all those if you want.
see if you can do something about this.

Thanks

---

### Post by caljohnsmith on 2008-09-11
Next time when you boot the Live CD, choose the option where the Ubuntu CD does a self-check and see if it returns any errors. Also, do you know if your HDD is in good health? How old is it? Do you have a HDD diagnostics CD or similar that came with your HDD, so you can check your HDD's integrity? Also, go ahead and post the end of your dmesg after the failed install:
```
dmesg | tail
```

---

### Post by deb_untu on 2008-09-11
I have attached both dmesg an /var/log/syslog files.

---

### Post by deb_untu on 2008-09-11
> **deb_untu said:**
> I have attached both dmesg an /var/log/syslog files.
 Sorry, Here it is.

---

