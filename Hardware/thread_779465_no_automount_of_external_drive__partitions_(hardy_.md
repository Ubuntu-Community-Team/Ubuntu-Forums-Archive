---
title: "no automount of external drive / partitions (hardy 8.04)"
date: 2008-05-02
forum: Hardware
---

### Post by pressed on 2008-05-02
i made 3 partitions: windows, ext3 (file system) and ext3 (home)

in gutsy my windows partition used to mount automatically, now it no longer does that. I also noticed that when I wanted to mount my external hard drive it did not automount.  

when mounting my external drive using the mount command, i got an error that the folder in /media did not exist. So I created one and mounted successfully. 

This made me think the same might work for my partitions, so I went to Computer and tried to manually specify a mount point, but i get the error message *"mount point cannot contain /"* Now the drives are visible but I can't even manually mount them because the mount point option is no longer available in Computer.... agh. All I want is for my other partitions to mount automatically upon boot.

---

### Post by pressed on 2008-05-02
by the way, fdisk -l gives .. no output. gparted is able to show my partitions but my windows partition gives *unable to read the contents of this filesystem*, even though i can boot off it. I have run scandisk and defrag from windows.

---

### Post by pressed on 2008-05-03
I solved my problem by doing the following:
sudo nautilus
(double click on drives in nautilus)
right click on drives in desktop and remove custom mount options

i still have no idea in what file those mount_point options were stored...

---

