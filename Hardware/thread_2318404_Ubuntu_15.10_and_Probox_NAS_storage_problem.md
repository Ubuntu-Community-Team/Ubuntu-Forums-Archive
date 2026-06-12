---
title: "Ubuntu 15.10 and Probox NAS storage problem"
date: 2016-03-25
forum: Hardware
---

### Post by mike.lussier on 2016-03-25
Good afternoon to all. 
I have seen this problem not once but three times now on three different systems. 
I'm running Ubuntu  15.10 desktop. I have 4 Probox NAS Units. each with four 2TB drives. a total of 16 drives / 32TB storage, 
The problem is system reboots. The NAS drives don’t come back up automatically.  From terminal if I do a df -h I dont see the drives. If open up "Disks" and the drives are there but not mounted and this always happens. I have to manually have to mount them individually after a reboot. 

I really would like to get the system to fully come up on its own. This is my media server. 

Thank you

---

### Post by TheFu on 2016-03-27
I have a new Probox - it isn't the NAS model, it is the eSATA/USB3 model. 

Using LVM with some of the storage and since it is eSATA connected, it seems to be just another internal disk.  I know there is an issue with these systems not powering on after a power loss. A physical button must be pressed, which sucks.  It is mounted through the /etc/fstab, just like any other LV.  

So, if you'll post the /etc/fstab, and output from a few commands (sudo lvs, sudo blkid, sudo lsblk), maybe we can help?  There aren't any GUI tools to mount in the way you need, I'm afraid.   GIO/gvfs just isn't a good idea for this sort of storage and that is what all the file manager tools use.  I've never used "Disks", so cannot help with it, but I'd guess that it uses gvfs.

Oh - I don't run non-LTS releases, so don't know if there are any specific issues for 15.10.  Still on 14.04 here and will be until at least June, perhaps another year.  Newer isn't always better.  I'm running PlexMS on it, but the renderers are in other rooms. Can't have a noisy "server" in the viewing rooms.

---

