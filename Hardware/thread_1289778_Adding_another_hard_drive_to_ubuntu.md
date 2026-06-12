---
title: "Adding another hard drive to ubuntu?"
date: 2009-10-12
forum: Hardware
---

### Post by cooltuyul on 2009-10-12
i just got a 1 tb hd. im trying to use it but when i go to "places" then "computer" i see "mass storage drive" which i think is the drive. when i click on it, is says "Unable to mount location Can't mount file"
what do i do?

---

### Post by Boondoklife on 2009-10-12
Has this drive been used before? You might need to format it if it has not.

---

### Post by oldfred on 2009-10-12
Download Gparted since it is not normally installed as you cannot edit mounted partitions or use the liveCD. Gparted will let your create partitions and format the hard drive. You may not want to make it one large partition, but that is up to you. Is it going to be all data, possible partitions for other operating systems, a new /home or what ever you want. If it is shared with windows do you want part of it NTFS or ext3 or ext4 for Ubuntu only.

You then should see the partitions but if you want to permanently mount them you either edit fstab or download Storage Device Manager.

partitioning
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by cooltuyul on 2009-10-12
i have gparted install but how do i use it? and its brand new, too.

---

### Post by oldfred on 2009-10-12
These should help you understand how it works. If it is a blank drive you just go out and use it, you do not have to worry about losing data. (Just do not select your working drive):)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by cooltuyul on 2009-10-13
okay i got the hd mounted. however, its under root and i cant copy, cut or paste! also i have to type in the password! how do i change it so that i can access it like my main hd?

---

### Post by nzadLithium on 2009-10-13
What format did you make your drive?
How did you mount it? If it was by command line what was the command? If its in fstab paste the line u added to fstab.

---

### Post by oldfred on 2009-10-13
See these for info on fstab.
see this for fstab info:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

You can also download storage device manager which allows you to use a GUI to edit fstab and set up permanent mounting of partitions.

I mount some partitions in my home for easy access.

---

