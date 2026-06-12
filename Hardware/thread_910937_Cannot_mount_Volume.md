---
title: "Cannot mount Volume"
date: 2008-09-05
forum: Hardware
---

### Post by rish99 on 2008-09-05
Hi, I am newbie. This topic might seem redundant but I have read and tried hundred different posts and have not been successful.

I have a WD passport 160 GB external drive. Recently I have been getting an error with Vista. My hard drive is recognized by Vista but it gets stuck if I ran an application anywhere relating to the drive. I cannot browse through the drive. 

I tried running the file on my dual boot Ubuntu. It recognized it. It gave me an error that it was not shutdown properly. I checked the forums then, and I think I messed it up further. 

Now whenever I connect the drive, it gives an error that it cannot mount the drive as I do not have enough privileges. I tried writing a code in the terminal for troubleshooting it (/etc/fstab and others). It gives me permission denied. 
But after messing around with it for a long time, I still cannot do anything with the hard drive. 

Just to give a little background.
My laptop's hard drive has 4 partitions. 3 partitions are using NTFS, Vista and 1 for the Ubuntu. I am not too sure what format the external hard drive is in, but it might be NTFS also. 

I have also messed a lot with the terminal, might have messed with the system too much. I was looking for root, have tried a lot of sudo commands, have installed something related to NTFS through terminal.

Any and all would be greatly appreciated.

---

### Post by bigbrovar on 2008-09-05
install this tool **ntfs-config** from synatics .. u would find it under /applications/systemtools/ntfs-config/

once launched it would display or the ntfs drive mounted on ur computer .. choose a name for the drive u want them to be mounted (make sure u dont leave spaces between names) and u are done

---

### Post by rish99 on 2008-09-05
That only mounted the partitions. I dont really need to mount the partitions. My goal is to access my external hard drive and save my data. The external hard drive still says that "Cannot mount Volume", you are not privileged to mount the volume.

---

### Post by rish99 on 2008-09-05
any help? :(

---

