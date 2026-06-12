---
title: "not detecting slace hd"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by broekskw on 2007-12-29
ok was going to install ubuntu 7.10 on a second drive (slave) on my main computer win xp, here is my problem,

after installing slave hd 30gb maxtor model# 33073u4 and rebooting, in the boot up screen it shows a slave drive,in control panel,systems,hardware,device manager,disk drives it shows it there also,also in bios it is there also, but when i go to my computer it's not showing a second hd:confused::confused:

i tried to install ubuntu to see if it detected my hd but it did not,

i have a p4xfcp motherboard 

any suggestions ??

help:confused:

---

### Post by taurus on 2007-12-29
So, you are running Ubuntu from the LiveCD right now?  If that's the case, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L.

---

### Post by broekskw on 2007-12-29
will hook everything up again and run from live and post output

thanks

---

### Post by taurus on 2007-12-29
Make sure at least the BIOS can detect your second harddrive first though.

---

### Post by broekskw on 2007-12-29
ok hooked everything up again and running from live cd 7.10, but do not have any menu bars at the top left to go into command line??

---

### Post by broekskw on 2007-12-29
sorry forgot to reboot with disc in cd rom

ok lets try your command (hope i can remember how to input this)
ok forgot how to input this command, some where on the left side top menu bars??

---

### Post by broekskw on 2007-12-29
ok sorry again but looked at your post and followed your directions and here is my output

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae4eae4e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11e03cb1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3644    29270398+  83  Linux
/dev/hdb2            3645        3736      738990    5  Extended
/dev/hdb5            3645        3736      738958+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 



so i see that is shows the slave hd there but with linux already installed.
i did install ubuntu 6.10 on this hd in another computer first to see if it would work without any problems, then was going to install in my main computer.

so how do i upgrade to 7.10 or delete 6.10 and start all over agian

Thanks
:)

---

### Post by taurus on 2007-12-29
Click the install icon on the desktop and when you get to the partition part, pick the Manual.  Then, mount /dev/hdb1 to / and /dev/hdb5 as swap.  Don't forget to put a check mark for /dev/hdb1 to format it to ext3.

That should be it.

---

### Post by broekskw on 2007-12-29
ok will try this out

so when you say  mount /dev/hdb1 to / and /dev/hdb5 as swap. Don't forget to put a check mark for /dev/hdb1 to format it to ext3.

is this another word for selecting??

---

### Post by broekskw on 2007-12-29
ok almost there but i get this error message and do not understand how to fix this, can anyone help this old guy out

---

### Post by taurus on 2007-12-29
You need to change the mount point for /dev/hdb1 from /media/hdb1 to /.

---

### Post by broekskw on 2007-12-29
thanks taurus got it working, know just need to do some more reading to get my ati video card  and sound card going. creative lab sound card.

wish me good luck on this 

thanks all:popcorn:

---

### Post by sutley on 2008-01-09
Hello all,

I'm trying to install Ubuntu 7.10 but it doesn't seem to be able to detect my hard drive. I have run

#sudo gparted

and no drives are detected. The same for when I run

#sudo fdisk -l

However when I use Knoppix I can see the hard drive without any problems. I actually used Knoppix to create a 1GB swap file and a 78GB EXT3 partition before rebooting the Ubuntu Live CD and trying the commands above again. Still no luck.

Does anyone have a answer/solution?

Thanks,
Sam

---

