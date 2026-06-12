---
title: "WD My Passport : Mounts and I can save files but I can't see or access them!"
date: 2016-11-24
forum: Hardware
---

### Post by simon-dolley on 2016-11-24
I've just got a new WD My Passport external hard drive to back up my files and also save a few extra ones

I can run the back up and also save files across but when I come to look at them or access them the drive appears to be empty

However when I try to save the files again or create a new folder in there with the same name as one I have already done, it comes up with something along the lines of "that filename already exists"... 

So the files are there i just can't see or access them, any ideas?

Ps I am a ubuntu luddite so please use simple no technobabble speak where possible!

---

### Post by yancek on 2016-11-24
Is Ubuntu the only operating system you have installed?
Are the partitions on the external drive using Linux filesystems?
How are you trying to access the partitions?  Generally they are available under the /media/username directory.  
Are you trying to access them as root (using the sudo command) and what are the owner:group and permissions of the mount point (directory)?
Run this command to get that info:  ls -l  /media/username  (replace 'username' with your actual user name).

---

