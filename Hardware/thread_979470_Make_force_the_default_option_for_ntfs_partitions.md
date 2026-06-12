---
title: "Make force the default option for ntfs partitions"
date: 2008-11-12
forum: Hardware
---

### Post by lazychris2000 on 2008-11-12
I was wondering if there was a way to make ntfs partitions mount automatically using the -o force option.  I have considered adding a whole lot of lines into the fstab file so that /dev/sdb1, /dev/sdb2, sdc1, etc will do it, but that seems needlessly complicated.
Basically, I am lazy...I do alot of computer repairs for people and dont want to manually mount their harddrives with the command line so I can get to their data on my system.  I wanna be able to just plug the drive and it will mount, forcing it if need be.  Also, my wife has a nasty habit of just unplugging usb harddrives and such from her computer while it is running windows, so it always pops up and says that you need to do this to make it.  Yes, I know, I can add a line in fstab so that /dev/sdb1 will mount as /media/external, but what if I have my digital camera's memory card plugged in and it is /dev/sdb1?
Any help would be greatly appreciated!

---

### Post by ciscosurfer on 2008-11-12
Two points: look into ntfs-config (it's in the repos), and consider associating your drives by uuid.

---

