---
title: "ipod woes in xubuntu feisty (&quot;umount&quot; fails, mount point changes on reboot)"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by stairwayoflight on 2007-06-14
Hi,

I am having some trouble with my fat32 ipod video (5.5g). I have used this in the past with gnome/ubuntu with no problems.

First, it mounted fine but after file transfers wouldn't unmount (I had just done a "factory restore" from a windows itunes). Both umount and eject reported that the device was busy. So I rebooted my machine. On poweroff I disconnected the ipod. After a reboot I reconnected it. Now it mounts at `/media/IPOD_` instead of `/media/IPOD`.

For some reason umount succeeded now. My question is, **what do I need to do to make sure I can eject or umount my ipod when it doesn't want to?**

I have another $.50 item to throw in here, deleting files within thunar on the ipod resulted in a trash folder on the drive. I am unable to delete the trash folder with thunar. Delete seems to thow it inside itself up the file hierarchy. I did this a couple times by mistake. One of the folder levels appears as `.Trash-1002$1`. I can't navigate to that level or delete it or past it in bash. How do I remove the trash?

Thanks for the help.

---

