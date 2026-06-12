---
title: "[SOLVED] Upgrading to 8.10 - what files do I need to back up..."
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by akelsall on 2008-12-11
I've been having various issues with my printer and VirtualBox and thought I'd upgrade to 8.10 to see if that fixes any of those issues.

Currently, I have separate root, home, and swap partitions (not to mention several other partitions such as /music, /photos/ etc). So, I have a few questions about upgrading:

1. When I install 8.10 on the current root partition,will it create an additional home directory?  Before I ever installed Ubuntu, I read that it's good practice to keep your /home on a separate partition so it's not wiped out if you have to reinstall the kernel. So, will I end up with two /home directories after the upgrade?

2. I ran across an article that detailed how to backup up all installed packages. How can I determine which of those I installed after the initial install of 8.04? 

3. Other than re-installing the packages I personally installed, and backing up sources.list and my /etc directory, is there anything else I should back up prior to upgrading?

Thanks,

Andy

---

### Post by Partyboi2 on 2008-12-11
> 1. When I install 8.10 on the current root partition,will it create an additional home directory? Before I ever installed Ubuntu, I read that it's good practice to keep your /home on a separate partition so it's not wiped out if you have to reinstall the kernel. So, will I end up with two /home directories after the upgrade? 
If you don't set your current /home partition as the new /home partition then it will create /home folder on /. So when you get to the partitioning stage of the install choose "manual" and make sure the box to format / is ticked and that you reset the mount point to / and for your /home partition that you reset the mount point to /home.
You can also upgrade using the network upgrade option or by using the alternate cd.

---

### Post by akelsall on 2008-12-11
Thought of a few other files to backup:

.bashrc
.bash_aliases
/boot/grub/menu.lst

Can anyone think of others I need to backup before trying a fresh install?

thanks,

Andy

---

### Post by akelsall on 2008-12-18
Ended up solving this one on my own. See the following link for more details:

[http://ubuntuforums.org/showthread.php?t=1013990](http://ubuntuforums.org/showthread.php?t=1013990)

---

