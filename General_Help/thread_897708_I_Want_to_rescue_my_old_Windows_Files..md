---
title: "I Want to rescue my old Windows Files."
date: 2008-08-22
forum: General Help
---

### Post by Lehona on 2008-08-22
Hi @ll,

My Windows System is crashed and i want to rescue my files. I open my Harddrive (with Ubuntu) but i become an error:

Unable to mount the system.

I aren't a pro with Ubuntu, so i hadn't any Idea, what i can do to rescue my files. 

I hadn't a Linux Life CD.

With best Regards, Lehoan

---

### Post by linux_tech on 2008-08-22
Accessing windows partitions thru ubuntu involves a few steps. You need to create a folder, mount it, edit fstab, and then install ntfs3g to read it.
[http://psychocats.net/ubuntu/mountwindows#fstab](http://psychocats.net/ubuntu/mountwindows#fstab)
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by WRDN on 2008-08-22
linux_tech, if Lehona has installed Ubuntu, then the Windows MBR no longer exists so cannot be corrupted (it was overwritten by GRUB).

What is the full error message?

You should be able to mount the drive manually.
First, type the following in the Terminal:

```
sudo fdisk -l
```

This will list the devices, and you will be able to identify which partition Windows is installed on (look for "NTFS" under the System column). Now, type:

```
sudo mkdir /media/windows
```

This is the mount point for the drive.

Finally, type:

```
sudo mount /dev/[device] /media/windows
```

This will mount the drive in /media/windows

If that does not work, you could try forcefully mounting the drive:

```
sudo mount /dev/[device] /media/windows -o force
```

---

### Post by Lehona on 2008-08-22
Thx, WRDN, i mouted the disk forcefully and it works. Now I can rescue my files.

---

