---
title: "Problem mounting 4G windows formatted Ipod"
date: 2005-02-28
forum: Hardware &amp; Laptops
---

### Post by hegleran on 2005-02-28
I was reading some other threads concerning Ipod support, and I think my problem might be slightly different, so here goes:
After some research on how to get Ipod functionality in Linux I took the following steps.
First, I installed gtkpod with no problems, the application launches, and sees my locally stored music.
Second, I created a diretory for my Ipod mount point: /media/ipod
After determining that the ipod is recognized as /dev/sdb1, I modified /etc/fstab to reflect the mount point directory that I created.  I did not set the volume to automatically mount.  I set fstab to automatically detect the filesystem.
When I connect the ipod, then right click on on the icon that appears on the desktop (it is now listed as Ipod instead of /dev/sdb1, so that is encouraging), I get an error stating that it could not mount the volume because the file system is not recognized.
Any ideas as to why linux is not recognizing my windows formatted (so I'm assuming fat32) ipod?  Linux can see my external hdd just fine,which is also fat32, mounting, and manipulating the file system is no problem.
Pardon my ignorance, I'm very new to ubuntu, and linux in general.  I appreciate any and all feedback!

---

### Post by hegleran on 2005-03-01
I discovered my problem.
It appears as though hotplug might not be functioning quite perfectly.
If I plug my ipod in after ubuntu boots, no problems at all.  If I boot ubuntu with ipod already connected, it can't mount.
Any ideas how to get hotplug to properly mount upon boot?

---

