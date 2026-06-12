---
title: "Permission denied to access files on second hard drive"
date: 2016-09-03
forum: Hardware
---

### Post by cupofcalculus on 2016-09-03
I installed a second hard drive, and moved my data over to it.  Then I did a fresh install of Ubuntu Studio (previous distro was Mint) on the main hard drive.  I've searched the net and ubuntu forums, and tried to follow some advice that I found, but I guess I'm not doing it right.

I can access several files and folders, but not all.  What's the "best"/recommended way of getting permission to read and write to the new hard drive?

---

### Post by yancek on 2016-09-03
Partitions on external drives are generally accessible under /media/username (replace username with your actual name).  Did you copy the data as root, using sudo?  You can find the owner and permissions on the partitions with the command:  ls -l /media/username.

---

### Post by cupofcalculus on 2016-09-03
The second hard drive path is:
/media/nathan/DataWarehouse/

I might have copied it as root.  But it seems odd that some files I have access to, but not others.  Here is the result of the ls -l /media/username:

$ ls -l /media/nathan
total 4
drwxr-xr-x 10 root root 4096 Sep  1 20:45 DataWarehouse

---

### Post by yancek on 2016-09-03
The owner:group is root:root and the permissions shown give read, write and execute permission to root (using sudo in your case) and only read and execute to other users.
If all the sub-directories/files are the same, the results are the same.  So you will need to either use sudo to modify/write to anything with those permissions or use the chown command to change the owner to nathan.

---

### Post by cupofcalculus on 2016-09-03
I had to read and experiment a bit, but finally figured it out.  Thank you very much.

Using * at the end of the folder path definitely sped things up, but with folder names that have spaces in them is going to take a bit ore time.

---

