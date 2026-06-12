---
title: "Adding new drives"
date: 2008-07-22
forum: General Help
---

### Post by Drezliok on 2008-07-22
I am adding another sata drive for storage and replaceing my CD burner with a DVD burner.

I am unwilling to just reinstall Ubuntu to get these to work. I have searched the forums in several sections.


How do I add a new unformatted drive?

How do I replace a CD burner with a DVD Burner?


I'm pretty sure the burners aren't just "swappable".
The drive has sat inside my pc hooked up for a week while I look for the solution on my own.



Thankyou for your time
Drezliok

---

### Post by northern lights on 2008-07-22
They're pretty much swappable indeed.

The new hardware should be recognized first boot after integration into your system.

---

### Post by Spaceman9 on 2008-07-22
InstallingANewHardDrive [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Adding new hard drive [http://ubuntuforums.org/showthread.php?t=251653](http://ubuntuforums.org/showthread.php?t=251653)

Add another Hard Drive to Ubuntu [http://www.xawk.com/ubuntu-add-hard-drive.html](http://www.xawk.com/ubuntu-add-hard-drive.html)

[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)

---

### Post by scragar on 2008-07-22
Gparted is the easiest way to set up your drive when it's in run Gparted, pick the new drive from the drop down at the top and choose to add a new partition(if ones already there skip this whole step down to **using it & editing fstab**), choose for yourself what you want to make it, but I'd recommend EXT3 if you don't want to have to defrag it, or VFAT(basicly fat32 I think) if you want compatability with windows.
**USING the drive**
run:```
sudo fdisk -l
```
skip to the last half, you should have something like:```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   **big number**   **smallish number**  **Linux?**
```anyway, that's the partition name, time to mount it so you can finally use it:
```
sudo mkdir /media/HD2
sudo mount **/dev/sdb1** /mediaHD2
```
you can now start using it, next thing to do is automounting.
**Editing fstab**
go to a terminal and open the run box(alt+F2), in the run box type:```
gksudo gedit  /etc/fstab
```then in the terminal run:```
mount | grep **/dev/sdb1**
```take the type and make a note of it, then add this line to the end of your fstab:```

**/dev/sdb1** /media/HD2     **TYPE**    defaults       0       2
```


All done. As for the DVD drives they are swapable without any problems, just replace it once you've shut the computer down.

---

