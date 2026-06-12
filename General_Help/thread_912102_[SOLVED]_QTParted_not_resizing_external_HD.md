---
title: "[SOLVED] QTParted not resizing external HD"
date: 2008-09-06
forum: General Help
---

### Post by JockVSJock on 2008-09-06
I have Ubuntu 7.04 and I bought a Western Digital External 500 GB HD that connects via USB. 

The file format on the external HD is fat32 and I want to shrink that to 100GB and then create a ext3 partition to start backing up my files on a daily basis from my pc to the external HD. 

I've installed QTParted v0.4-5-cvs and running it as Root.  The external HD is mounted as /dev/sda1 and when I right-click on that partition and select Resize, and then shrink the fat32 partition and say ok, I get a generic qtparted window with an OK button.  

What am I do wrong with this, so I can correct this?

thanks

---

### Post by pbotros1234 on 2008-09-06
All I can say is use GParted, maybe QTParted has some missing dependencies thats not letting it work on Ubuntu?

---

### Post by JockVSJock on 2008-09-06
Ok, I'll try GParted and report back my result. 

The weird thing is that I got no errors when trying to install/run QTParted. 

thanks

---

### Post by JockVSJock on 2008-09-06
gparted is outputting the following error: 

```

root@ladytron:/usr/bin# ./gparted
terminate called after throwing an instance of 'Glib::OptionError'
Aborted (core dumped)

```

I am becoming root from sudo, from the command line. 

I tried to log in as root from the login screen and looks like I am unable to. 

Can't remember why file I have to modify to have Ubuntu to start up in runlevel 3 and then start x. 

thanks

---

### Post by JockVSJock on 2008-09-07
UPDATE:

I was able to work thru with a friend.  He advised that the disk has to unmounted first before resetting the file system. 

We did that and it worked.  

However, I don't recall seeing any info on unmounting the disk first in any documentation that I looked at online.

BTW, this post can be shown as solved and/or closed. 
  

thanks

---

### Post by regomodo on 2008-09-07
#

---

