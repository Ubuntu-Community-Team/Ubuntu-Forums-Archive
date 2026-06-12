---
title: "Attempts to install a second hard drive has me totally lost..."
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by ZeusABJ on 2008-01-12
On my Windows machines I've always used a two disk internal hard drive configuration. I use one disk for running my OS and programs while the other is devoted exclusively for data storage. I'm running Ubuntu on a separate machine and decided I'd like the same exact configuration on that PC. I bought a second hard drive, installed it and used gparted to format it to ext3. After a reboot the disk shows up under "Places --> Computer" and I can right click to mount it, but that seems to be as far as I can get. I can't seem to write any data to the drive and it tells me "Permissions could not be changed" every time I try to make it writable. 

I'm not sharing anything off these machines so security an permissions are really not an issue. All I'm wanting here is a simple data-only drive that I can keep files, audio and video on that is accessible from all my user accounts. Also there is a "recovery" aspect here in that I'd want to be able to remove the drive and place it in another computer to recover the data if the computer ever dies (similar to an ordinary hard drive formatted to NTFS under WIndows). Surely there is a way to do this. Can anyone help me?

---

### Post by logos34 on 2008-01-12
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(>scroll down to bottom)

---

### Post by ZeusABJ on 2008-01-12
Thanks for the quick response! I also found this tutorial just a few minutes ago:

[http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/)

I'll try them both and post my results.

---

### Post by ZeusABJ on 2008-01-13
Well, I was able to make this work (finally) by using elements of this guide:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

along with this command "gksudo nautilus" which allowed me to browse nautilus as root so I could create and set permissions on the the directory I was using as my mount point. Still this is sort of bizarre for me. Under Gutsy my Windows partitions can be mounted with full read/write access with a simple right click. It seems a bit backwards that mounting a Linux partitions on my Linux machine would be more difficult than mounting a Windows partition. Hopefully this will be addressed in future releases (for those of us that are not CLI aficionados). I really like GParted personally (as it it pretty similar to Disk Management in Windows). It would be awesome if some sort of component for mounting and assigning permissions to partitions could be incorporated into that program.

Thanks!

---

### Post by logos34 on 2008-01-13
Be very careful when mucking around using gksudo nautilus--one little slip and you could easily mess something up.  I highly advise you get used to the terminal--the more you use it the easier it gets.  

If you have the correct fstab line 

> ... ext3 defaults 0 0 

and you've set ownership & permissions with '-R' recursive, you shouldn't be having any problem.

> It seems a bit backwards that mounting a Linux partitions on my Linux machine would be more difficult than mounting a Windows partition. Hopefully this will be addressed in future releases (for those of us that are not CLI aficionados). I really like GParted personally (as it it pretty similar to Disk Management in Windows). It would be awesome if some sort of component for mounting and assigning permissions to partitions could be incorporated into that program.

If you want a gui, there's this storage manager config tool (not connected to gparted):

> $ apt-cache show psydm

---

