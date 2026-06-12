---
title: "[SOLVED] can I re-install kernel or recover files from live cd?"
date: 2008-11-12
forum: General Help
---

### Post by Guitar John on 2008-11-12
My computer (Dell 4700, 160GB, 2.8 GHz, 2.5 MB) has crashed.  It kernel panics immediately after I hit the power button.  

I can boot to a live cd and I can see my home folder but I am denied access to most of my files.  If I could access the files and copy then to my remote HD, I would probably just reinstall, but I would rather fix the existing system.  

What I tried so far:
[chroot into the hard drive]("http://ubuntulinuxtipstricks.blogspot.com/2008/05/kernel-panic-cpu-too-old.html") from live cd.  Did not work.  

 ```
sudo chroot /dev/sda1
```

---

### Post by AndyCooll on 2008-11-12
For recovering files, usually once the Live CD is up and running you need to mount the relevent folders, then open up Nautilus, navigate to the folder you wish to copy and then copy the files to another location.
So it may go something like as follows:
```
sudo mkdir /mnt/temp
sudo mkdir /mnt/backup
sudo mount -tnfs /dev/sda1 /mnt/temp
sudo mount -tnfs /dev/sda3 /mnt/backup
gksudo nautilus
```
(Where sda3 is the partition/location where you are going to copy the files too).

:cool:

---

### Post by Guitar John on 2008-11-12
Good News/Bad News

I was able to boot into *Recovery Mode* using an earlier Kernal.  I had to try several before I found one that would work.

But from there, I was able to log in and copy all of my files and settings onto my remote hard drive.

The system itself seems to be unstable, so rather than mess with it any further, and I should probably do a re-install.  I had planned on sticking with the LTS until the next LTS release, but there are some features in Intrepid that have me intrigued so, here we go.

Thank you for your reply.

---

