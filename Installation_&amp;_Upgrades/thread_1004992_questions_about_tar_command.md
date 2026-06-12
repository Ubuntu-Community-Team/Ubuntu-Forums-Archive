---
title: "questions about tar command"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by pr1mal on 2008-12-07
So i used tar to back up a partition and now how that backup. I am trying to restore the file to a partition.  
Only problem is inside of the tar the hierarchy is /media/disk-1/ACTUALINFO

so i need to do a command like 
sudo tar -xvpzf /media/passport/ubunt.tgz -C /media/disk-3/

but what that does is make the partition mounted to disk-3 contain the folder media within that disk-1 and within that is all the files that need to be on the root.  
So i think there is some tar syntax to untar the files two levels in to the root, i just dont know how

thanks much

---

