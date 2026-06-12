---
title: "No permission to new partition."
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by ripzippysf on 2009-05-12
I'M NEW TO UBUNTU SO PLEASE BREAK DOWN YOUR ANSWER TO VERY SIMPLE STEPS IF POSSIBLE.

I created a new partition and it's listed as ext3 file system.  I mounted it but, I cannot do anything because it says I don't have permissions for that drive.  If I look at the permissions tab for that drive it just says the permissions for the disk cannot be determined.  

I've seen some solutions online that are command line.  The only problem is they don't have enough steps to help me.  I don't know how to tell which volume I'm on, how to change that in the terminal window, etc.  At this point the largest partition on my computer will not allow me any access.  I'm not even sure I have to do any of this through the command line.  

Any help would be great!

---

### Post by abhiram7 on 2009-05-23
hi

in case if you are still looking for a solution.

Ubuntu by default gives umask22 file permission for the directories and files. By this the super user has the permission to read write and execute the file or directory. But the groups and other users will only have read and execute permission(no write) to the file. To provide the write permission for the directory use the command chmod.

in the terminal type

sudo chmod u+w  /media/(name of the directory where u want write permission)

by the above command u give write permission (+w) to all the users accessing the file or directory. And u should be able to write in the new partition.


try it and it should work :)

---

