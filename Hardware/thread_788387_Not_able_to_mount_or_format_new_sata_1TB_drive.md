---
title: "Not able to mount or format new sata 1TB drive"
date: 2008-05-09
forum: Hardware
---

### Post by Colonel Forbin on 2008-05-09
I have just installed a new western digital 1 TB sata hard drive, and although i can find it in places as a scsi drive, I am unable to mount it.
When I go to qtparted I get a message that it is scanning all drive partitions (1) and that progress is 100%, but that window hangs, will not close without closing qtparted. Also in the terminal window I get a message that the files system was not cleanly unmounted and I should run ef2sk (I think). Would really love to get my new toy going tonight.

Thanks in advance.

Colonel Forbin

---

### Post by hallgeirl on 2008-05-09
Hi, have you tried partitioning it with something else than parted, for instance cfdisk, then mounting it manually with the mount command?

EDIT: I didn't read your post well enough. First of all, just try a 
# sudo e2fsck -f /dev/sdxx
in the console to see if you can find some errors with that. sdxx should be replaced with the actual device name of your partition (for instance sdb1). If this doesn't fix your problem, go ahead and try the steps below. Oh, and be sure of the device name so you don't accidentally delete the partitions of your other disks. :)
If you don't know the device name, try a
# sudo fdisk -l
This will list your partitions.

Try:
# sudo cfdisk /dev/sdx
(Do your partitioning using the instructions on screen. Note that you need to specify the harddrive device name here, not the partition. For instance sdb or sdc)
# sudo mkfs.ext3 /dev/sdxx
(This creates an ext3 file system on the disk)
# sudo mount /dev/sdxx /media/yourmountpoint
(And finally mounts it.)

I've had some trouble with parted myself (the Gnome version though), so I simply don't use it. It seems not to handle 6 disks very well. O_o. Maybe especially old ones? (5+ years old)

Good luck.:)

---

### Post by Colonel Forbin on 2008-05-09
Thanks for the help. I was able to partition and format it, but I don't seem to know how to mount it. What would the variable /yourmountpoint be. sda?

---

### Post by hallgeirl on 2008-05-09
> **Colonel Forbin said:**
> Thanks for the help. I was able to partition and format it, but I don't seem to know how to mount it. What would the variable /yourmountpoint be. sda?

yourmountpoint is just a folder you need to make where you can mount the drive. You can name it whatever you want. Make it like this:
# sudo mkdir /media/yourmountpoint
or, if you want another name than "yourmountpoint":
# sudo mkdir /media/1tbdisk
or
# sudo mkdir /media/diskwithmuchstuffonit

Then mount it as described above (replace "yourmountpoint" with whatever name you chose for the folder). I should say though, it's probably not recommended to mount it like this during normal usage, since Ubuntu should be able to take care of the mounting for you. I think you may need a reboot though for Ubuntu to handle that right (detecting the partition etc.). But for testing if mounting the disk even works, this should be ok.

Off to bed, so good luck to you. :)

EDIT: Oh, I should mention a "problem" (not really a problem but it was annoying) when I started formatting my disks in Ubuntu... If you see that you can't write to the disk once it's mounted, you will need to change the permissions of the mount point like this:
# sudo chmod 777 /media/yourmountpoint
As an alternative (or in addition to the first method), you could simply set yourself as owner of the mount point:
# sudo chown yourusername /media/yourmountpoint

---

### Post by Colonel Forbin on 2008-05-09
That did it mate. Thanks again for the help. I'm a newbie, but I always seem to be able to find the answer here.

---

