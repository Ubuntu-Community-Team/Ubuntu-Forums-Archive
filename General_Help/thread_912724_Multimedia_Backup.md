---
title: "Multimedia Backup"
date: 2008-09-07
forum: General Help
---

### Post by latinoheat69 on 2008-09-07
I'm going to buy an external hard drive soon so I can store all my multimedia files, so I was thinking if this was possible, which I think is.
1. Install Ubuntu into the external hard drive.
2. Copy all my music and videos to the Ubuntu installation from Windows Vista.

So, will Windows recognize the files and let me access them if I plug in the HDD into Vista? Also will I be able to just plug in the HDD on any PC and boot from it into Ubuntu?

Thanks.

---

### Post by banewman on 2008-09-07
Windows can't see linux filesystems without using a third party app.
You could install ubuntu and make a ntfs partition on the external drive...
Any comp that you want to boot an external drive with needs to be set up in the bios to boot from usb first.
Hope it helps :)

---

### Post by latinoheat69 on 2008-09-07
So, Ubuntu can be installed on an NTFS partition?
Thanks.

---

### Post by vanadium on 2008-09-07
DO NOT install Ubuntu on an external disk. Forget about walking to a computer and booting with an external disk. Use a live CD for that.

If you are going to dual boot, install Ubuntu on a partition of an internal disk. 10 GB is enough. You can create links in your home directory to your user data on your Windows partition, your multimedia, etc. The only data that will reside on your linux partition will be the configuration data of applications, and this does not need a lot of space.

You can keep your external disk with ntfs (you will probably buy it this way). Ubuntu can read/write. However, Ubuntu will not automount an ntfs disk that is not 'clean' (not properly closed). An ntfs disk is properly closed by Windows if you disconnect it safely using the icon in the tray, or when you completely shutdown Windows (NOT when you hibernate).

---

### Post by sanemanmad on 2008-09-07
>  Ubuntu can read/write. However, Ubuntu will not automount an ntfs disk that is not 'clean' (not properly closed). An ntfs disk is properly closed by Windows if you disconnect it safely using the icon in the tray, or when you completely shutdown Windows (NOT when you hibernate).

Thanks!

---

