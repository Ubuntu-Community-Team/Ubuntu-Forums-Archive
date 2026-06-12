---
title: "New harddisc to add space to /home/..."
date: 2009-04-27
forum: Hardware
---

### Post by Grimmy on 2009-04-27
Hopefully a straightforward question...

I'm running low on space on my home partition, and I want to add a new hard disc and the space to appear as the home.

When I put the disc in, is it just a case of adding it to fstab with the mount point as /home  (or /home/username ?) or would I have to do something with symlinks to increase the available space?

---

### Post by cariboo on 2009-04-27
It depends on how you do it. Do you want the new hard drive to replace your current directory? Do you want to sym-link it to a folder in your home directory? If you intend to use it to replace your home directory, temporarily mount it and copy the contents of your home directory to the new drive, Remove your old home directory, than remount your new hard drive to /home/<user>, where <user> is your user name. You can make the changes needed to fstab to get the drive to mount automagically.

---

### Post by Grimmy on 2009-04-27
I was hoping to be able to add more space to the existing home, or rather, a paticular users home folder. 

I have a whole load of files in /home/samba which I share on the network using Samba.   I want to make the additional space provided by a new drive available for more files.

---

### Post by Grimmy on 2009-05-02
Found this thread:

[http://ubuntuforums.org/showthread.php?t=1072396](http://ubuntuforums.org/showthread.php?t=1072396)

This describes the same thing as what I want to do, but it looks like symlinking is really the only option.

---

