---
title: "One of my HHD not showing"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by joplass on 2005-03-05
I have used this computer with Fedora and Mandrake.  During Ubuntu installation the partition level showed me both hard drives a 20G and a 10G.  Of course I let Ubuntu format the bigger one hoping that it will make both available to me after installation but unfortunately I can only see the 20G one.  The 10G which is slave is nowhere to be found.  I even install kde hoping that Kdisk free will show me something different, no luck.  
How can I activate the other hard drive and be able to access it?

---

### Post by bored2k on 2005-03-05
[QUOTE=joplass]I have used this computer with Fedora and Mandrake.  During Ubuntu installation the partition level showed me both hard drives a 20G and a 10G.  Of course I let Ubuntu format the bigger one hoping that it will make both available to me after installation but unfortunately I can only see the 20G one.  The 10G which is slave is nowhere to be found.  I even install kde hoping that Kdisk free will show me something different, no luck.  
How can I activate the other hard drive and be able to access it?[/QUOTE]
 [http://ubuntuguide.org/#listmounteddevices](http://ubuntuguide.org/#listmounteddevices)

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by doitashimashite on 2005-03-05
If the 10 Gb is primary slave, then check which partitions it has:

$ sudo fdisk -l /dev/hdb

This will give you a list of its partitions. Let's say you want to mount the first partition under /mnt:

$ sudo mount /dev/hdb1 /mnt

---

### Post by joplass on 2005-03-05
Thanks to you both.  

doitashimashite,
I have the drive mounted and I can get to it.

bored2k,
I save those two links because I will need them in the future.

---

### Post by joplass on 2005-03-18
I really did not come back on this thread because I did not need that hard drive and I did not want to be a pain.  But now I need it.  Now to the problem:
Like I mentioned above this is my slave hard drive.  Sometimes the system finds it at boot and I can mount it and access it.  Some other times the system does not find it at boot and you know the rest.
Furthermore, there are times I start my Ubuntu box and no hard drives is found at boot including the master drive that contains Ubuntu.  Very annoying at times.
?Any solution gents??? 8-[

---

