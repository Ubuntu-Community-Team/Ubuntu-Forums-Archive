---
title: "repartitioning using parted command"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by manojpawar on 2009-09-25
hi,
   I am using 
                  $ sudo parted
command for resizing my partition I seen in my gparted tool that in the  Partition tool on toolbar> resize/move option in hidden, thats why i am using this command but i m confused about
      how to use 
                   (parted)resize number start end 
command
    here is my partition sizes
partition         file system    mount point  size             sizeused       unused          first sector       lastsector
/dev/sda5      ext3                       /        13.97GiB       13.27GiB     716.62MiB       176136723       205439219
/dev/sda6      ext3               /home        45.50 GiB    18.58 GiB     26.91 GiB       205439283       300849254
/dev/sda7    linux swap                        5.59 GiB                                                   300849318       312576704

i dont want to lose my data.Please guide me

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by dreamingdarkness on 2009-09-25
It's better to be safe and run the partitioning tool from a LiveCD or other boot-disk. You'll want a Ubuntu LiveCD of the type of Ubuntu you have installed. 
To resize the Linux partitions, you want to use the Gparted/Partition Editor to do the resizing it helps to have the visual guide. 
You want to use the LiveCD because you can't work on a partition that is 'mounted', which means one the computer is currently working with or looking at.

---

