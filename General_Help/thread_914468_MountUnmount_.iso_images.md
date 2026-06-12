---
title: "Mount/Unmount .iso images"
date: 2008-09-08
forum: General Help
---

### Post by laytek on 2008-09-08
Hi, I want to mount CD .iso image files without having to burn the image to a CD first. Looking around, I have found this: [https://help.ubuntu.com/community/ManageDiscImages](https://help.ubuntu.com/community/ManageDiscImages). I have carefully followed the instructions listed under "Integrate Disk Image Mounting/Unmounting into Gnome (Nautilus)".

I am pleased to say that Mounting a disk image works perfectly. However, when I right click on the desktop icon of the image I just mounted, there is no "Unmount Disk Image" selection available. So, I am thinking there is a problem with the UNMOUNTING Nautilus Action Schema. It appears that the desktop entry file was not created, so maybe the problem is in the MOUNT Nautilus Action Schema. Has anyone used this before? Is it working correctly?

Thanks,
LayTek

---

### Post by mb_webguy on 2008-09-08
Personally, I use gmount-iso (which is in the repositories).  It's a GUI tool that makes mounting and unmounting an ISO extremely simple.

---

### Post by laytek on 2008-09-08
Thanks mb_webguy,

I have used gmount-iso. I would like to get the other working though, because it is integrated into Nautilus. You simply browse in Nautilus to the .iso, right click and select mount. Voila - it is mounted, with a desktop icon. If it were working, it is better.  ;)

LayTek

---

### Post by mempman on 2008-09-08
> **laytek said:**
> Hi, I want to mount CD .iso image files without having to burn the image to a CD first. Looking around, I have found this: [https://help.ubuntu.com/community/ManageDiscImages](https://help.ubuntu.com/community/ManageDiscImages). I have carefully followed the instructions listed under "Integrate Disk Image Mounting/Unmounting into Gnome (Nautilus)".

I am pleased to say that Mounting a disk image works perfectly. However, when I right click on the desktop icon of the image I just mounted, there is no "Unmount Disk Image" selection available. So, I am thinking there is a problem with the UNMOUNTING Nautilus Action Schema. It appears that the desktop entry file was not created, so maybe the problem is in the MOUNT Nautilus Action Schema. Has anyone used this before? Is it working correctly?

Thanks,
LayTek


try this:

mount /directory/file.iso /mnt/mount-location -o loop=/dev/loop0

---

### Post by laytek on 2008-09-09
Thanks mempman,

That is certainly the best way when using the CLI. However, I am still trying to work on the posted solution, because it uses a GUI and is integrated with nautilus. It appears that the problem has to do with gvfs that appeared in Hardy.

LayTek

---

### Post by Sycron on 2008-09-09
A friend of mine was using acetone iso to mount iso's.

---

