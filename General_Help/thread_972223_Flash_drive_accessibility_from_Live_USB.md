---
title: "Flash drive accessibility from Live USB?"
date: 2008-11-05
forum: General Help
---

### Post by ericks13 on 2008-11-05
I recently installed Ubuntu 8.10 (with persistence) onto my flash drive (Sony 8GB) and I have no problem booting or saving changes.  However, I can no longer use my flash drive AS a flash drive.  By that I mean that I can't access other data on it while booted up from it, and any data I save while booted up can't be read when I'm using the flash drive in another OS.  When I try to detect the USB drive, I'm told it can't be mounted.  Are there compatibility patches I can install to get by this, or am I going to have to start carrying around two flash drives?

---

### Post by snowpine on 2008-11-05
You can use Gparted to create a separate data partition on your USB drive.

---

### Post by ericks13 on 2008-11-06
Do I do that before or after I install onto it?  I think the installer automatically partitioned it during installation.

---

### Post by snowpine on 2008-11-06
It's not too late to repartition without having to reinstall.
Boot to a different Linux install (not from the USB) or from a Live CD. Then use 'gparted' and you should be able to shrink down the partition and add a new one.

---

### Post by C.S.Cameron on 2008-11-06
Remember that Windows can only see the first partition on a flash drive.

To share stuff between your persistent flash drive and other systems, (windows), you can create a folder in filesystem/cdrom.
You can read and write to this folder from Ubuntu or Windows.

The maximum size this folder can hold depends on how much space you leave after selecting persistence space in the U-C install.
Thus, if you are using a 4G flash drive, the filesystem will take 700 MB and if you use 2.3 GB for "Stored in reserved extra space" you will have about 1 GB left over for files in this folder.

Have not figured out how make a link to this folder on the Ubuntu desktop

---

