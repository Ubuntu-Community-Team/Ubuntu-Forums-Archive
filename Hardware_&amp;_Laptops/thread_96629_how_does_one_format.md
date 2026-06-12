---
title: "how does one format?"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by groovywombat on 2005-11-29
ok maybe i'm completely inept, but for the life of me I can't figure out how to format my hdds.
I'm trying to add a RAID 0 and I go to that disk utility under system, and it shows the two drives, one drive shows that it is 160gb as the RAID shoudl be, and the other shows not much of anything.  i try and partition the drive within the utility and it just sits there working the drive really hard, and does nothing.  except slow my computer down a hell of a lot.  so after leaving it like that for 8 hrs i reboot the computer with no change.  is there a better way to do this?
thanks

---

### Post by earobinson on 2005-11-29
I searched the forums for (format had drive) and I found this

[http://www.ubuntuforums.org/showthread.php?t=96326&highlight=format+hard+drive](http://www.ubuntuforums.org/showthread.php?t=96326&highlight=format+hard+drive)

---

### Post by groovywombat on 2005-11-29
well, gparted only shows my HDD as two seprate HDDs (hde and hdf) which the disk partitioner does as well, but hde is only 80gb whereas in the disk manager it's 160gb

---

### Post by earobinson on 2005-11-29
can you post a screen shot (my guess is that you are miss reading the data)

---

### Post by groovywombat on 2005-11-29
perhaps I am, well here are all of my screenshots
[http://www.cdsupreme.com/screenshots/snapshots.html]("http://www.cdsupreme.com/screenshots/snapshots.html")

thanks for the help

---

### Post by earobinson on 2005-11-29
hum you seem to be reading them right ... I guess I will look into this further and try and get some help.

can you post this info for me:
```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by SickTwist on 2005-11-29
The new GNOME Disks Manager will enable you to format a partition (make sure that it is not mounted when attempting to format it).

System --> Administration --> Disks

---

