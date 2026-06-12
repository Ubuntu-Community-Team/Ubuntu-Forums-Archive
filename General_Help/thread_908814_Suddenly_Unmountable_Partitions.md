---
title: "Suddenly Unmountable Partitions"
date: 2008-09-02
forum: General Help
---

### Post by raywood on 2008-09-02
I am using Hardy x64 in a WinXP dual boot.  I boot into Windows and I see my NTFS partitions, and can access them.  I boot into Ubuntu and go to File Browser > Computer.  I can see my NTFS partitions plus my ext3 partitions.  I have previously accessed them in Ubuntu but have recently reinstalled the OS.  Now, when I click on one of the NTFS partitions in File Browser > Computer, I get this:
> 
Cannot mount volume.

Your are not privileged to mount the volume <volname>.

When I try it as root, double-clicking on one of the NTFS partitions listed on the left side of the File Browser display, I get this:
> 
Cannot mount volume.

Unable to mount the volume 'PROGRAMS'.

and the Details are:

> fuse: failed to access mountpoint /media/PROGRAMS: No such file or directory

The main message is the same if I try to open an ext3 partition as root, but the Details differ slightly:

> mount: mount point /media/VMS does not exist

So -- what is going on?

---

### Post by iaculallad on 2008-09-02
Post the whatever displays when you issue the following terminal commands below:

```
cat /etc/fstab
sudo fdisk -l
sudo blkid
```

---

### Post by raywood on 2008-09-02
Mystery solved:  sudo mkdir /media/CURRENT and so forth, for each of my partitions' names, and then reboot.  I just had forgotten to create mount points.  Thanks for your quick reply.

---

