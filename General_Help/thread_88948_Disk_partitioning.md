---
title: "Disk partitioning"
date: 2005-11-11
forum: General Help
---

### Post by Bachstelze on 2005-11-11
I currently have 3 partitions : 1 for the root filesystem, 1 for /home and one with Win XP. But I figured out I don't need it anymore, so if I format my XP partition, how could I assign the extra free space to another partition without reformating everything ?

---

### Post by earobinson on 2005-11-11
gparted is a great easy program for doing this!

Edit: changed gpartition typo to gparted sorry for the typo

---

### Post by Bachstelze on 2005-11-11
How do you install it ? I can't find it in Synaptic... My soures.list must be f***ed up :/

---

### Post by earobinson on 2005-11-11
here is a good site for a good sources.list [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Bachstelze on 2005-11-11
I fixed it, but I still cannot find 'gpartition'. I assume the prog you spoke of is 'gparted'.

---

### Post by aysiu on 2005-11-11
[QUOTE=HymnToLife]I fixed it, but I still cannot find 'gpartition'. I assume the prog you spoke of is 'gparted'.[/QUOTE] Yes, gparted is the program you're looking for.

---

### Post by macaronikazoo on 2005-11-12
hey I'm trying to do the same thing.  is there some graphical front end for gparted?  how do you use it?  I tried running parted in the terminal and I didn't really understand what to do.

---

### Post by bartc on 2005-11-12
[QUOTE=macaronikazoo]hey I'm trying to do the same thing.  is there some graphical front end for gparted?  how do you use it?  I tried running parted in the terminal and I didn't really understand what to do.[/QUOTE]
GParted is the graphical front end for libparted. If you install gparted using Synaptic Package Manager, GParted should appear under `System Tools' in the `Applications' menu and should open the graphical editor...

---

### Post by earobinson on 2005-11-14
[QUOTE=HymnToLife]I fixed it, but I still cannot find 'gpartition'. I assume the prog you spoke of is 'gparted'.[/QUOTE]
ya gparted is the program sorry for the typo

---

### Post by darknuala on 2005-11-15
Delete the ntfs partition.  Change it to ext3, there is a convert option.
You have to change it in etc/fstab, name it, and then mount it.  I had a similar situation occur, but I'm pressed for time.  Once I named mine in etc/fstab, I did this:
sudo mkdir /media/hdd1
ln -s /media/hdd1 ~/hdd1
sudo umount /dev/hdd1
sudo mount /dev/hdd1

sudo chown username /media/hdd1

of course this is my setting. I'm sure there's smaller details I am forgetting, but that is the jist of it.

---

