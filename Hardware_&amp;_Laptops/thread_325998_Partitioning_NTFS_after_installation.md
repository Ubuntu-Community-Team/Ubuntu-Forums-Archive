---
title: "Partitioning NTFS after installation"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by jck3j on 2006-12-26
Hi all,

I, being a relative new user of ubuntu, did not account for a fat32 drive that could be accessed by my dual boot system during installation. I am trying to go only ubuntu after i become more comfortable with it. in the interim, i need to create a fat32 drive that holds all of my songs/ pictures/ school documents etc. so i can access them with ubuntu and xp (if necessary). i have tried to use gparted, but i am not having much luck. i have tried unmounting the ntfs drive, but gparted comes up with an error. is it even possible to resize the ntfs drive without wiping it completely?  i just need some direction.

---

### Post by taurus on 2006-12-26
Before you resize it, you first need to unmount it.  Then, gparted should be able to resize and convert the new partition to fat32/vfat if you want...

Otherwise, you can do that from the LiveCD too.

---

### Post by rsambuca on 2006-12-26
There are also drivers available for Windows to read and write to ext2/ext3 drives which you can find [[COLOR="DarkOrchid"]here[/COLOR]]("http://www.fs-driver.org/").

As another alternative, there is a driver for linux that allows read and write access NTFS drives, but it is currently a Beta version.

---

### Post by jck3j on 2006-12-26
I am having trouble fully unmounting it i guess. I have attached what my error looks like. I cannot resize the ntfs drive for some reason (i'm assuming because of the error). I have defragged my ntfs drive and it is 49% full. To unmount the drive, i clicked on the icon on the desktop and clicked "unmount volume." It remounts when i reboot ubuntu. is there a better way to do this that might allow me to resize to create some extra space for a fat32 partition?

---

### Post by rsambuca on 2006-12-26
I would suggest using the gParted live CD.  You can download the iso file from [[COLOR="DarkOrchid"]here[/COLOR]]("http://gparted.sourceforge.net/")

The gParted live CD version is a later version than that found on ubuntu.  It also has the benefit of running off of a live CD, so you don't have to worry about any of your partitions being mounted.  Of course back up your sensitive data first just in case.

---

### Post by taurus on 2006-12-26
You probably mount it through /etc/fstab so just put a # in front of the line for your ntfs filesystem...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by jck3j on 2006-12-26
Unfortunately I am on vacation and did not bring any spare blank cds. i have already downloaded the iso and tried a virtual mount using gisomount from the package manager. do you know if this can work, or for best results should i just wait to get home and mount the iso to a cd?

---

### Post by rsambuca on 2006-12-26
I've never tried using gisomount.  Sorry, can't help ya there.  I just remember that I tried shrinking my NTFS drive from ubuntu but couldn't, but the gParted live CD worked like a charm.

---

### Post by jck3j on 2006-12-26
ok thank you. i will wait until i can get a blank cd to mount the iso and i will post how it works. thank you for your help.

---

### Post by jck3j on 2006-12-28
the gparted livecd works great.

---

